## 1. OOP

### 1.1 Concept

A class is a template for objects, and an object is an instance of a class.

**Class**: a description of a class of things with the same and similar attributes, behavior patterns, and functional processes

```javascript
// A class is a user defined blueprint or prototype from which objects are created.  It represents the set of properties or methods that are common to all objects of one type. 
```

**Objects**：instance

```java
//a class named "Main" with a variable x:
public class Main {
  int x = 5;
//an object called "myObj":
  public static void main(String[] args) {
    Main myObj = new Main();
    System.out.println(myObj.x);
  }
}
```

### 1.2 Syntax

 modifier class {

​		Attribute

​        Constructor

​        Method   }

```java
// Create a Main class
public class Main {
  int x;  // Create a class attribute

  // Create a class constructor for the Main class
  public Main() {
    x = 5; 
  }
  public static void main(String[] args) {
    Main myObj = new Main(); // Create an object of class Main (constructor)
    System.out.println(myObj.x); // Method
  }
}
```
### 1.3 Constructor 

Definition: a method with the same name as the class with no return value. When (New) creates an object, some information is initialized at the same time, which has the function of transferring values; At the same time, there are two forms of constructors: parameterless and parameterless. 

```java
// Example
public class User {

	private String name;
	private int age;
	private String id;
	private String adr;
	private int score;
// Overload -- method 
	User(String name,int age,String id) {
		this.name = name;
		this.age=age;
		this.id=id;
	}

	 User(String name, int age, String id, String adr, int score) {
		this.name = name;
		this.age = age;
		this.id = id;
		this.adr = adr;
		this.score = score;
	}
	
	User(int age) {
		// this : refer to self in subclass
		// super : refer to parent in subclass
		this.age = age;
	}
}

public class UserManage {
	public static void main(String[] args) {
		// User user = new User();	
		// The constructor User() is undefined
		User user2 = new User(18); 
//		user.age=18;
//		user.name="xm";
//		user.id="0123";
		User user3 = new User("小虎", 19, "0124");
		User user4 = new User("小虎2", 19, "0124");
		User user5 = new User("小虎2", 19, "0124","地址： XXX市",100);
```

```java
// Example
```

```java
public class MethodDemo02{
	public static void main(String[] args) {
		// 下面是针对求和方法的调用
		int sum1 = add(1, 2);
		int sum2 = add(1, 2, 3);
		double sum3 = add(1.2, 2.3);
		// 下面的代码是打印求和的结果
		System.out.println("sum1=" + sum1);
		System.out.println("sum2=" + sum2);
		System.out.println("sum3=" + sum3);
	}

	// 下面的方法实现了两个整数相加
	public static int add(int x, int y) {
		return x + y;
	}
	// 下面的方法实现了三个整数相加
	public static int add(int x, int y, int z) {
		return x + y + z;
	}
	// 下面的方法实现了两个小数相加
	public static double add(double x, double y) {
		return x + y;
	}
}
```

### 1.4 Singleton

The class that only has one object.

Private/static

```java
class Singleton {
	static Singleton instance = new Singleton();
	public static Singleton getInstance() {
		return instance;
	}
	private Singleton() {}
	public void print() {
		System.out.println("hello");
	}


	public static void main(String args[]) {
		Singleton s = Singleton.getInstance();
		s.print();
	}
```



## 2. Data type：

<img src="/Users/cathyqin/Library/Application Support/typora-user-images/image-20210601111216157.png" alt="image-20210601111216157" style="zoom:500%;" />    

```javascript
// == 与equals 在 引用数据类型 对象比较 与基本数据类型 变量 比较
In general both equals() and “==” operator are used to compare objects to check equality but here are some of the differences between the two:

1.  == is an operator for reference comparison (address comparison) and .equals() is method for content comparison.

In simple words, == checks if both objects point to the same memory location whereas .equals() evaluates to the comparison of values in the objects.

```

```java
// Example
// the concept of == operator
public class Test {
    public static void main(String[] args)
    {
        String s1 = new String("HELLO");
        String s2 = new String("HELLO");
        System.out.println(s1 == s2);
        System.out.println(s1.equals(s2));
    }
}
```

```javascript
// Output
false
true
```

```javascript
//Explanation: Here we are creating two objects namely s1 and s2.

- Both s1 and s2 refers to different objects.
- When we use == operator for s1 and s2 comparison then the result is false as both have different addresses in memory.
- Using equals, the result is true because its only comparing the values given in s1 and s2.
```

```java
// equals
public boolean equals(Object anObject) {
        if (this == anObject) {
            return true;
        }
        if (anObject instanceof String) {
            String aString = (String)anObject;
            if (!COMPACT_STRINGS || this.coder == aString.coder) {
                return StringLatin1.equals(value, aString.value);
            }
        }
        return false;
}
```

## 3.Modifier

| Modifier  | Description                                                |
| --------- | ---------------------------------------------------------- |
| Public    | The code is accessible for all classes                     |
| Private   | The code is only accessible within the declared class.     |
| Default   | The code is only accessible in the same package.           |
| Protected | The code is accessible in the same package and subclasses. |

![image-20210601114918976](/Users/cathyqin/Library/Application Support/typora-user-images/image-20210601114918976.png)

## 4. Encapsulation

### 4.1 General:

to make sure that "sensitive" data is hidden from users. To achieve this:

- declare class variables/attributes as `private`
- provide public **get** and **set** methods to access and update the value of a  `private` variable

### 4.2 Get and set

The `get` method returns the variable value, and the `set` method sets the value.

```java
public class Person {
  private String name; // private = restricted access

  // Getter
  public String getName() {
    return name;
  }

  // Setter
  public void setName(String newName) {
    this.name = newName;
  }
}
// error
public class Main {
  public static void main(String[] args) {
    Person myObj = new Person();
    myObj.name = "John";  // error
    System.out.println(myObj.name); // error 
  }
}
public class Main {
  public static void main(String[] args) {
    Person myObj = new Person();
    myObj.setName("John"); // Set the value of the name variable to "John"
    System.out.println(myObj.getName());
  }
}

// Outputs "John"
```

```javascript
// Example explained
The get method returns the value of the variable name.

The set method takes a parameter (newName) and assigns it to the name variable. The this keyword is used to refer to the current object.
```

### 4.3 Why Encapsulation?

- Class attributes can be made **read-only** (if only use the `get` method), or **write-only** (if  only use the `set` method)

- Flexible: the programmer can change one part of the code without affecting other parts

- Increased security of data

## 5.Polymorphism

### 5.1 Extend

The `extends` extends a class (indicates that a class is inherited from another class).

In Java, it is possible to inherit attributes and methods from one class to another. We group the "inheritance concept" into two categories:

- **subclass** (child) - the class that inherits from another class
- **superclass** (parent) - the class being inherited from

```java
class Animal {
  public void animalSound() {
    System.out.println("The animal makes a sound");
  }
}
class Pig extends Animal {
  public void animalSound() {
    System.out.println("The pig says: wee wee");
  }
}
class Dog extends Animal {
  public void animalSound() {
    System.out.println("The dog says: bow wow");
  }
}
class Main {
  public static void main(String[] args) {
    Animal myAnimal = new Animal(); 
    // Create a Animal object
    Animal myPig = new Pig();  
    // Create a Pig object
    Animal myDog = new Dog();  
    // Create a Dog object
    myAnimal.animalSound();
    myPig.animalSound();
    myDog.animalSound();
  }
}
```

### 5.2 Override

When the method in the parent class cannot meet the needs of the subclass, the subclass can rewrite the method of the parent class to meet the needs. If a child inherits his father's house, he can redecorate it. (must extend)

- **Overriding and Access-Modifiers :** be public, but not private, in the subclass.

```java
// A Simple Java program to demonstrate
// Overriding and Access-Modifiers

class Parent {
	// private methods are not overridden
	private void m1()
	{
		System.out.println("From parent m1()");
	}
	protected void m2()
	{
		System.out.println("From parent m2()");
	}
}
class Child extends Parent {
	// new m1() method
	// unique to Child class
	private void m1()
	{
		System.out.println("From child m1()");
	}
	// overriding method
	// with more accessibility
	@Override
	public void m2()
	{
		System.out.println("From child m2()");
	}
}
// Driver class
class Main {
	public static void main(String[] args)
	{
		Parent obj1 = new Parent();
		obj1.m2();
		Parent obj2 = new Child();
		obj2.m2();
	}
}
```

```javascript
// Output 
From parent m2()
From child m2()
```

- **Static/Final methods can not be overridden**

```java
// A Java program to demonstrate that
// final methods cannot be overridden
  
class Parent {
    // Can't be overridden
    final void show() {}
}
  
class Child extends Parent {
    // This would produce error
    void show() {}
}
```

```javascript
13: error: show() in Child cannot override show() in Parent
    void show() {  }
         ^
  overridden method is final
```

### 5.3 Static

The `static` keyword is a non-access modifier used for methods and attributes. Static methods/attributes can be accessed without creating an object of a class.

```java
// Example1
public class Main {
  // Static method
  static void myStaticMethod() {
    System.out.println("Static methods can be called without creating objects");
  }

  // Public method
  public void myPublicMethod() {
    System.out.println("Public methods must be called by creating objects");
  }
  // Main method
  public static void main(String[ ] args) {
    myStaticMethod(); // Call the static method
    // myPublicMethod(); This would output an error

    Main myObj = new Main(); // Create an object of Main
    myObj.myPublicMethod(); // Call the public method
  }
}
```

```java
// Example2
public class StaticTest{
	String name;
	static String id;
	
	public void printInfo() {
		System.out.println(name);
		System.out.println(id);
	}
	public static void main(String[] args) {
		StaticTest st1 = new StaticTest();
		st1.name = "ST1";
		st1.id = "1011";
		
		StaticTest st2 = new StaticTest();
		st2.name = "ST2";
		st2.id = "2022";
		
		StaticTest st3 = new StaticTest();
		st3.name = "ST3";
		st3.id = "3033";
		
		StaticTest.id = "9899";
		st1.printInfo();
		st2.printInfo();
		}
}
```

```javascript
// Output
ST1
9899
ST2
9899
```

```javascript
// Explain
After adding the static keyword to the id attribute, the object no longer has the age attribute,

The id attribute will be uniformly managed by the  class,

That is, multiple objects only correspond to one id attribute,

If an object changes the id attribute, other objects will be affected.

```

### 5.4 Final

- The `final` keyword is a non-access modifier used for classes, attributes and methods, which makes them non-changeable (impossible to inherit or override).

- The `final` keyword is useful when you want a variable to always store the same value, like PI (3.14159...).

- The `final` keyword is called a "modifier".

```java
// Set a variable to `final`, to prevent it from being overridden/modified:
public class Main {
  final int x = 10;

  public static void main(String[] args) {
    Main myObj = new Main();
    myObj.x = 25; // will generate an error: cannot assign a value to a final variable
    System.out.println(myObj.x);
  }
}
```

## 6.  Abstraction

### 6.1 Abstract Classes and Methods

Data **abstraction** is the process of hiding certain details and showing only essential information to the user.
Abstraction can be achieved with either **abstract classes** or interfaces.

The `abstract` keyword is a non-access modifier, used for classes and methods:

- **Abstract class:** is a restricted class that cannot be used to create objects (to access it, it must be inherited from another class).

- **Abstract method:** can only be used in an abstract class, and it does not have a body. The body is provided by the subclass (inherited from).

An abstract class can have both abstract and regular methods:

```java
abstract class Animal {
  public abstract void animalSound();
  public void sleep() {
    System.out.println("Zzz");
  }
}
```

From the example above, it is not possible to create an object of the Animal class:

```java
Animal myObj = new Animal(); 
// will generate an error
```

To access the abstract class, it must be inherited from another class. Here is to convert the Animal class in the polymorphism to an abstract class:

```java
// Abstract class
abstract class Animal {
  // Abstract method (does not have a body)
  public abstract void animalSound();
  // Regular method
  public void sleep() {
    System.out.println("Zzz");
  }
}

// Subclass (inherit from Animal)
class Pig extends Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
}

class Main {
  public static void main(String[] args) {
    Pig myPig = new Pig(); // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}
```

```javascript
// Output
The pig says: wee wee
Zzz
```

### 6.2 Interfaces

An `interface` is a completely "**abstract class**" that is used to group related methods with empty bodies:

```java
// Example
interface Animal {
  public void animalSound(); // interface method (does not have a body)
  public void run(); // interface method (does not have a body)
}
```

To access the interface methods, the interface must be "implemented" by another class with the `implements` keyword. The body of the interface method is provided by the "implement" class:

```java
// Interface
interface Animal {
  public void animalSound(); // interface method (does not have a body)
  public void sleep(); // interface method (does not have a body)
}

// Pig "implements" the Animal interface
class Pig implements Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
  public void sleep() {
    // The body of sleep() is provided here
    System.out.println("Zzz");
  }
}

class Main {
  public static void main(String[] args) {
    Pig myPig = new Pig();  // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}
```

- Like **abstract classes**, interfaces **cannot** be used to create objects (in the example above, it is not possible to create an "Animal" object in the Main Class)
- Interface methods do not have a body - the body is provided by the "implement" class
- On implementation of an interface, it must override all of its methods
- Interface methods are by default `abstract` and `public`
- Interface attributes are by default `public`, `static` and `final`
- An interface cannot contain a constructor (as it cannot be used to create objects)

## 7. UI

### 7.1 

```javascript
create JFrame object;

set class attributes, including 
setTitle(), 	setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE), setSize(),
setVisible(true);

set flowLayout;

create components object, including
JButton
JLabel
JTextField
ImageIcon/JLabel: Dimension, setPreferredSize()

Liquid layout:add()
setVisible(true)

```

```java
//import 引入需要使用的类的路径   import  包路径.类名；

import javax.swing.JLabel;
import javax.swing.JTextField;
import javax.swing.ImageIcon;
import javax.swing.JFrame;

public class MyUI {
	
	// 初始化界面的方法 
	public void showLoginUI() {
		// 创建窗体对象 
		// java.awt.Frame loginui = new java.awt.Frame(); // 旧款
		JFrame loginui = new JFrame();
		// 设置相关属性 
		// 标题
		loginui.setTitle("登录界面 ");
		//String title =  loginui.getTitle();// 获取标题 
		// 默认关闭选项 
		loginui.setDefaultCloseOperation(javax.swing.JFrame.EXIT_ON_CLOSE);
		/**
		 * 窗体的四种关闭选项 
		 * DO_NOTHING_ON_CLOSE, HIDE_ON_CLOSE, DISPOSE_ON_CLOSE, or EXIT_ON_CLOSE
		 */
		// 尺寸 
		loginui.setSize(500,600);
		// 可视化
		loginui.setVisible(true);// 可视化  让窗体在屏幕上显示 
		
		java.awt.FlowLayout  fl = new  java.awt.FlowLayout();
		loginui.setLayout(fl);// 设置属性 
		//java.awt.FlowLayout  flL =(FlowLayout) loginui.getLayout();
// 获取属性 
		
		// 添加组件 按钮  输入框   文字 图片 
		// java.awt.Button btn = new java.awt.Button("登录");
		javax.swing.JButton btn = new javax.swing.JButton("登录");
		
		// 标签 ： 只显示内容 自己是透明的 
		JLabel nameJla = new JLabel("账号: ");
		JLabel pwdJla = new JLabel("密码: ");
		
		// 输入框 
		JTextField nameIn = new JTextField();
		JTextField pwdIn = new JTextField();
		
		// 标签：  图片   项目根目录  项目文件夹下 
		ImageIcon imgicon = new ImageIcon("img/sn.jpg");// 参数 ： 图片的路径+名字+格式
		JLabel imgjla = new JLabel(imgicon);// 标签加载图标对象 
		
		// 设置尺寸 
		java.awt.Dimension dim = new java.awt.Dimension(410,35);// 尺寸对象 
		nameIn.setPreferredSize(dim);// 组件设置尺寸 
		pwdIn.setPreferredSize(dim);
		
		
		// 根据流式布局器的顺序来排列 
		// 流式布局器： 根据顺序 从左至右，依次摆放，摆不下的时候就换行 ，整体居中
		loginui.add(imgjla);// 加载图片标签至窗体上
		
		loginui.add(nameJla);
		loginui.add(nameIn);
		
		loginui.add(pwdJla);
		loginui.add(pwdIn);
		loginui.add(btn);// 加载到窗体上
		
		loginui.setVisible(true);// 再可视化  让窗体在屏幕上显示 
		
	}
	public static void main(String[] args) {
		MyUI myui = new MyUI();
		myui.showLoginUI();
	}
```

### 7.2 After adding interfaces:

```javascript
  //create object BtnListener bl
		BtnListener bl = new BtnListener();
	//add ActionListener
		btn.addActionListener(bl);
	
	//implements ActionListener abstraction method
		public class BtnListener implements ActionListener { 
				// Called when the button is clicked
			public void actionPerformed(ActionEvent e) {
				System.out.println("按钮被点击了！！");
			}
		}
```

```java
package cathy0526;

import javax.swing.JFrame;
import java.awt.FlowLayout;
import javax.swing.JButton;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class UI {
	public void initUI(){
		
		JFrame jf = new JFrame();
		jf.setTitle("login page");
		jf.setSize(500,700);
		jf.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		// 组件添加 
		// 设置布局
		FlowLayout fl = new FlowLayout();
		jf.setLayout(fl);
		JButton btn = new JButton("login");
		jf.add(btn);
		jf.setVisible(true);
		
		btnListener bl = new btnListener();
		btn.addActionListener(bl); 
	}
	class btnListener implements ActionListener {
		public void actionPerformed(ActionEvent e) {
			System.out.println("Press the button");
			
			JFrame jf = new JFrame("Press the Button");
			jf.setSize(500,100);
			jf.setVisible(true);
		}
	}
	public static void main (String[]args) {
		UI ui = new UI();
		ui.initUI();
	}
}
```

### 7.3 Adding getText() to get the textfield string

```javascript
Login process: 
user input
click the login button
get the string from the input 
verify the name and password
output
```

```java
package cathy0527;

import java.awt.*;
import javax.swing.*;

public class UI {
//	public abstract void test();

	public void initUI() {
		JFrame jf = new JFrame();
		jf.setTitle("登录界面");
		jf.setSize(500, 700);
		jf.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

		// 组件添加
		// 设置布局
		FlowLayout fl = new FlowLayout();
		jf.setLayout(fl);
		JButton btn1 = new JButton("登录");
		JButton btn2 = new JButton("注册");

		// 输入框
		JTextField namein = new JTextField();
		JPasswordField pwdin = new JPasswordField();

		// 设置尺寸
		Dimension dim = new Dimension(450, 35);
		namein.setPreferredSize(dim);
		pwdin.setPreferredSize(dim);

		jf.add(namein);
		jf.add(pwdin);
		jf.add(btn1);
		jf.add(btn2);

		jf.setVisible(true);

		// 按钮注册监听器：
		// ActionListener al = new ActionListener(); 不能创建对象
		// 就需要创建一个类 具体实现 ACtionListener
		BtnListener bl = new BtnListener();
		// Cannot instantiate(实例化) the type ActionListener
		btn1.addActionListener(bl);// ActionListener 类型的参数
		btn2.addActionListener(bl);

		// 对监听器的输入框属性 进行 赋值本方法中实例化的 输入框对象引用
		// 1、 set方法 
		bl.setNameIN(namein);
		bl.setPwdIN(pwdin);
		// 2、直接赋值 
		//bl.namein = namein;
	  // bl.pwdin = pwdin;
	}
	public static void main(String[] args) {
		UI ui = new UI();
		ui.initUI();
	}
}
```

```java
package cathy0527;

import java.awt.event.*;
import javax.swing.*;
/**
 *	动作监听器接口  ActionListener 的实现类 按钮监听器类BtnListener
 * @author Administrator
 *
 */
public class BtnListener implements ActionListener {
	JTextField namein;
	JPasswordField pwdin;

	public void setNameIN(JTextField namein) {
		this.namein = namein;
	}
	public void setPwdIN(JPasswordField pwdin) {
		this.pwdin = pwdin;
	}

	// 按钮被点击时调用
	public void actionPerformed(ActionEvent e) {
		// 获取按钮上的字符串 
		String btnstr  = e.getActionCommand();
		System.out.println(btnstr+" 按钮被点击了！！");
		
		if(btnstr.equals("登录")) {
			// 必须是 按钮点击之后 
			// 再获取输入框中的字符串
			String nameStr = namein.getText();
			String pwdStr = pwdin.getText();
			// 输出打印  
			System.out.println(nameStr + " " + pwdStr);
			// 验证账号密码 
			 if(nameStr.equals("admin")&&pwdStr.equals("admin123")) {
				System.out.println("登陆成功！！");
				JFrame jf = new JFrame("登陆成功！！");
				jf.setSize(300, 100);
				jf.setVisible(true);
			}else {
				System.out.println("登陆失败");
				JFrame jf = new JFrame("账号或者密码错误！！");
				jf.setSize(300, 100);
				jf.setVisible(true);
			}
		}else if(btnstr.equals("注册")) {
			System.out.println("注册");
			JFrame jf = new JFrame("欢迎注册 ！！");
			jf.setSize(300, 100);
			jf.setVisible(true);
		}
	}
}
```

- Notes on ActionEvent:

```
区分点击的按钮是哪个, ActionEvent 事件信息的记录者 
      监听到按钮被点击之后，调用监听器响应方法
      同时会传入一个参数 ActionEvent类型
      整个事件，关键的信息会存在ActionEvent 的这个对象中传入 监听器响应方法 
               
      从 ActionEvent参数上 获取相关信息：
          按钮上上字符串
          获取按钮对象 
```

### 7.4 Adding Graphics:

#### 7.4.1 A Line:

```java
package cathy0529;

import java.awt.Graphics;
import javax.swing.JFrame;

public class ShapeUI {
	public static void main(String[] args) {
		ShapeUI sui = new ShapeUI();
		sui.initUI();
	}
	public void initUI() {
		JFrame jf = new JFrame();
		jf.setTitle("图形图像编程");
		jf.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		jf.setSize(700,600);
		jf.setVisible(true);
		
    // Interface MouseListener 
		ShapeListener sl = new ShapeListener();
		jf.addMouseListener(sl);
		// 获取 Graphics 图形绘制对象 
		Graphics g = jf.getGraphics();
		sl.setGraphics(g);
	}
}
```

```java
package cathy0529;

import java.awt.Graphics;
import java.awt.event.MouseEvent;
import java.awt.event.MouseListener;

public class ShapeListener implements MouseListener {
	int x1, y1, x2, y2;
	Graphics g;
	
	public void setGraphics(Graphics g) {
		this.g=g;
	}
	@Override
	public void mouseClicked(MouseEvent e) {
		System.out.println("（原地按下释放）点击"+e.getX()+"=x  y="+e.getY());
	}
	@Override\
	public void mousePressed(MouseEvent e) {
		x1 = e.getX();//坐标（相对于窗体）  按键 （左右键区分 ） 点击次数
		y1 = e.getY();
		int buttonid = e.getButton();
		System.out.println(buttonid+"按下"+x1+"=x1 y1="+y1);
	}
	@Override
	public void mouseReleased(MouseEvent e) {
		x2 = e.getX();
		y2 = e.getY();
		int buttonid = e.getButton();
		g.drawLine(x1,y1,x2,y2);
		System.out.println(buttonid+"释放"+x2+"=x2 y2="+y2);
	}
	@Override
	public void mouseEntered(MouseEvent e) {
		System.out.println("进入");
	}
	@Override
	public void mouseExited(MouseEvent e) {
		System.out.println("离开");
	}
}
```

#### 7.4.2 A Rectangular/circle

```java
package cathy0601;

import java.awt.Color;
import java.awt.FlowLayout;
import javax.swing.JButton;
import javax.swing.JFrame;

public class DrawPad {
	
	DrawLintener dl = new DrawLintener();// 全局的 

	public void initUI() {
		JFrame jf = new JFrame();
		jf.setTitle("图形图像绘制");
		jf.setSize(800, 600);
		jf.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		// 流式布局
		FlowLayout fl = new FlowLayout();
		jf.setLayout(fl);
		jf.setVisible(true);
		// 按钮 动作监听
		// 窗体 鼠标监听
		jf.addMouseListener(dl);

		// 获取 Graphcis 画笔
		dl.g = jf.getGraphics();
		System.out.println("画笔：" + dl.g);
	}

	public static void main(String[] args) {
		DrawPad dp = new DrawPad();
		dp.initUI();
	}
}
```



```java
package cathy0601;

import java.awt.Graphics;
import java.awt.event.MouseEvent;
import java.awt.event.MouseListener;

public class DrawLintener implements MouseListener {
	int x1, y1, x2, y2;
	Graphics g;
	
	public void setGraphics(Graphics g) {
		this.g=g;
	}
	@Override
	public void mouseClicked(MouseEvent e) {
		System.out.println("（原地按下释放）点击"+e.getX()+"=x  y="+e.getY());
	}
	@Override\
	public void mousePressed(MouseEvent e) {
		x1 = e.getX();//坐标（相对于窗体）  按键 （左右键区分 ） 点击次数
		y1 = e.getY();
		int buttonid = e.getButton();
		System.out.println(buttonid+"按下"+x1+"=x1 y1="+y1);
	}
	@Override
	public void mouseReleased(MouseEvent e) {
		x2 = e.getX();
		y2 = e.getY();
		int buttonid = e.getButton();
    g.drawLine(x1, y1, x2, y2);
	// 矩形 矩形的左上角  宽 高 
    g.drawRect(Math.min(x1, x2), Math.min(y1, y2), Math.abs(x2-x1), Math.abs(y2-y1));
  // 圆形		外切矩形的左上角  宽 高 
    g.drawOval(Math.min(x1, x2), Math.min(y1, y2),Math.abs(x2-x1), Math.abs(y2-y1));
		
	}
	@Override
	public void mouseEntered(MouseEvent e) {
		System.out.println("进入");
	}
	@Override
	public void mouseExited(MouseEvent e) {
		System.out.println("离开");
	}
}
```

### 7.4.3 Recursion 

#### 7.4.3.1 Recursion

- Recursion is the technique of making a function call itself. This technique provides a way to break complicated problems down into simple problems which are easier to solve.

```java
// Use recursion to add all of the numbers up to 10.
public class Main {
  public static void main(String[] args) {
    int result = sum(10);
    System.out.println(result);
  }
  public static int sum(int k) {
    if (k > 0) {
      return k + sum(k - 1);
    } else {
      return 0;
    }
  }
}
```

```javascript
When the sum() function is called, it adds parameter k to the sum of all numbers smaller than k and returns the result. 
10 + sum(9)
10 + ( 9 + sum(8) )
10 + ( 9 + ( 8 + sum(7) ) )
...
10 + 9 + 8 + 7 + 6 + 5 + 4 + 3 + 2 + 1 + sum(0)
10 + 9 + 8 + 7 + 6 + 5 + 4 + 3 + 2 + 1 + 0
```

Since the function does not call itself when `k` is 0, the program stops there and returns the result.

- Halting Condition:

Just as loops can run into the problem of infinite looping, recursive functions can run into the problem of infinite recursion. Infinite recursion is when the function never stops calling itself. Every recursive function should have a halting condition, which is the condition where the function stops calling itself.

```java
public class Main {
  public static void main(String[] args) {
    int result = sum(5, 10);
    System.out.println(result);
  }
  public static int sum(int start, int end) {
    if (end > start) {
      return end + sum(start, end - 1);
    } else {
      return end;
    }
  }
}
```

```java
/**
	 * 	递归矩形 
	 * @param x
	 * @param y
	 * @param w
	 * @param h
	 * 1、当 w < 3 的时候 就停止 方法执行
	 * 2、自己加个count 变量 控制递归层数 
	 * 
	 * 	结束方法执行 
	 * 	return 
	 */
	public	void drawMyRect(int x,int y,int w,int h) {
		if(w<30) {
			return;
		}

//		g.drawRect(x, y, w, h);
		g.fillRect(x+w/3, y+h/3, w/3, h/3);
		// 第一层 
		drawMyRect(x, y, w/3, h/3);
		drawMyRect(x+w/3, y, w/3, h/3);
		drawMyRect(x+2*(w/3), y, w/3, h/3);
	}
	
```

```javascript
//	Random number:
		Random random = new Random();
	int rannum = random.nextInt(10);// 0-9 
		// 从0开始 （包括 0）   到 10 不包括10	
	
	随机负数：-5 - 4 
	int rannum = random.nextInt(10)-5;

	随机： 5-15
	int rannum = random.nextInt(10)+5;
```

```java
//递归骰子
	    void drawDice(Graphics g) {
			java.util.Random random = new java.util.Random();
			int ax, bx, cx, px, ay,by, cy,py;
			int w = 800, h = 600;
			ax = random.nextInt(w);
			bx = random.nextInt(w);
			cx = random.nextInt(w);
			px = random.nextInt(w);
			
			ay = random.nextInt(h);
			by = random.nextInt(h);
			cy = random.nextInt(h);
			py = random.nextInt(h);
			
			for (int i = 0; i < 10000; i++) {
				int tempx = 0;
				int tempy = 0;
				int r = random.nextInt(3);
				
				if(r == 0) {
					tempx = (ax + px)/2;
					tempy = (ay + py)/2;
			        g.drawLine(tempx, tempy, tempx, tempy);
				} else if (r == 1) {
					tempx = (bx + px)/2;
					tempy = (by + py)/2;
				} else if (r == 2) {
					tempx = (cx + px)/2;
					tempy = (cy + py)/2;
				}
				px = tempx;
				py = tempy;
				
			}
		}
```

```Java
// 递归分形
void drawIfs(Graphics g,int localX, int localY) {
	    	double a = -1.8, b = -2.0, c = -0.5, d = -0.9;
			double x = 0, y = 0;
			
			for (int i = 0; i < 50000; i++) {
				double tempx = Math.sin(a * y) + c * Math.cos(a * x);
				double tempy = Math.sin(b * x) + d * Math.cos(b * y);
				
				x = tempx;
				y = tempy;
				
				int px = (int)(tempx * 100) + localX;
				int py = (int)(tempy * 100) + localY;
				g.drawLine(px, py, px, py);
			}
	    }
	    void drawMyRect(Graphics g, int x, int y, int w,int h) {
	    	if (w <  30) {
	    		return;
	    	}
	    	g.fillRect(x + w / 3, y + h /3, w / 3, h / 3);
	    	drawMyRect(g, x + w / 3, y + h / 3, w / 3, h / 3);
	    	drawMyRect(g, x + 2 * (w / 3), y + 2 * (w / 3), w / 3, h / 3);
	    }
```

### 7.4.4 重绘保存

```
  直线： 两个端点坐标
	矩形：按下 释放 坐标 
	圆：		按下 释放 坐标 
	递归矩形： 按下 释放 坐标 
	迭代分形： 按下的坐标
	骰子分形： 最开始的随机八个坐标值 
```

方法： 绘制图形的方式 

- 将图形创建为一个类，作为对象保存所有数据	
- 将图形对象存入数组中，然后在 重写 JFrame 的 paint方法中绘制出来 

```java
package cathy0604;

import java.awt.Color;
import java.awt.FlowLayout;
import java.awt.Graphics;

import javax.swing.JButton;
import javax.swing.JFrame;
/**
 *  继承 JFrame 才可以重写刷新方法 paint 
 *  在绘制窗体本身之余（super.paint(g);），也绘制我们自己保存的图形
 * @author Administrator
 *
 */
public class DrawPad extends JFrame {
 final static long serialVersionUID = 1;
 String[] btnstrs= {"直线","矩形","圆","递归分形","迭代分形","骰子图形"};
 Shape[] shapes;// 保存图形数组 
 DrawLintener dl = new DrawLintener();// 全局的鼠标  动作监听器  
 public void initUI() {
  // JFrame jf = new JFrame();// 换成 继承的方式 
  setTitle("图形图像绘制");
  setSize(800, 600);
  setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
  // 流式布局
  FlowLayout fl = new FlowLayout();
  setLayout(fl);
   
  // 遍历创建按钮 
  for (int i = 0; i < btnstrs.length; i++) {
   JButton btn = new JButton(btnstrs[i]);
   add(btn);
   btn.addActionListener(dl);
  }
  setVisible(true);
  // 按钮 动作监听
  
  // 窗体 鼠标监听
  addMouseListener(dl);

  // 获取 Graphcis 画笔
  dl.g = getGraphics();
  System.out.println("画笔：" + dl.g);
 }
 /**
  *  可视化 以及改变窗体大小的时候 自动调用 
  */
 int count=0;
 @Override // 重写注解 防止重写失误
 public void paint(Graphics g) {
  super.paint(g);
  
  shapes = dl.shapes;// 将 监听器中的 数组对象引用 赋值给 shapes 
  //将存储的图形  -- 刷新时再绘制 绘制图形
  System.out.println("paint"+count++);
  for (int i = 0; i < shapes.length; i++) {
   Shape shape = shapes[i];
   if(shape==null) {
    return;
   }
   shape.drawShape(g);
  }
 }
 public static void main(String[] args) {
  DrawPad dp = new DrawPad();
  dp.initUI();
 }
}
```

```java
package cathy0604;

import java.awt.Color;
import java.awt.Graphics;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.MouseEvent;
import java.awt.event.MouseListener;

public class DrawLintener implements MouseListener, ActionListener {
	// 坐标
	int x1, y1, x2, y2, x3, y3, x4, y4, x5, y5;
	Graphics g;
	String btnstr = "";

	// 存储图形的数组
	Shape[] shapes = new Shape[100];
	int size = 0;

	@Override
	public void actionPerformed(ActionEvent e) {
		// 获取按钮字符串
		btnstr = e.getActionCommand();
	}

	public void mouseClicked(MouseEvent e) {
	}

	@Override
	public void mousePressed(MouseEvent e) {
		x1 = e.getX();
		y1 = e.getY();
	}

	@Override
	public void mouseReleased(MouseEvent e) {
		x2 = e.getX();
		y2 = e.getY();
		// 绘制图形
		Shape shape = new Shape(btnstr, x1, y1, x2, y2, Color.BLACK);
		shape.drawShape(g);

		// 存储图形对象
		shapes[size] = shape;//shapes[size++] = shape;
		size++;
	}

	@Override
	public void mouseEntered(MouseEvent e) {

	}

	@Override
	public void mouseExited(MouseEvent e) {
	}
}
```

```java
package cathy0604;

import java.awt.Color;
import java.awt.Graphics;

public class Shape {
	String shapeType="";
	int x1,y1,x2,y2;
	Color color=Color.BLACK;
	// 构造方法 
	/**
	 * 直线  矩形 圆 递归矩形 
	 * @param shapeType
	 * @param x1
	 * @param y1
	 * @param x2
	 * @param y2
	 * @param color
	 */
	public Shape(String shapeType, int x1, int y1, int x2, int y2, Color color) {
		this.shapeType = shapeType;
		this.x1 = x1;
		this.y1 = y1;
		this.x2 = x2;
		this.y2 = y2;
		this.color = color;
	}
	/**
	 * 	迭代分形
	 * @param shapeType
	 * @param x1
	 * @param y1
	 * @param color
	 */
	public Shape(String shapeType, int x1, int y1,Color color) {
		this.shapeType = shapeType;
		this.x1 = x1;
		this.y1 = y1;
		this.color = color;
	}
	
	
	// 绘制图形的方法 
	public void drawShape(Graphics g) {
		g.setColor(color);
		if (shapeType.equals("直线")) {
			g.drawLine(x1, y1, x2, y2);
		} else if (shapeType.equals("矩形")) {
		// 矩形 矩形的左上角  宽 高 
			g.drawRect(Math.min(x1, x2), Math.min(y1, y2), Math.abs(x2 - x1), Math.abs(y2 - y1));
		} else if (shapeType.equals("圆")) {
			// // 圆形 外切矩形的左上角 宽 高
			g.drawOval(Math.min(x1, x2), Math.min(y1, y2), Math.abs(x2 - x1), Math.abs(y2 - y1));
		} else if (shapeType.equals("迭代分形")) {
			drawIfs(g,x1,y1);// 绘制迭代分形
		} else if (shapeType.equals("递归分形")) {
			drawMyRect(g,Math.min(x1, x2), Math.min(y1, y2), Math.abs(x2-x1), Math.abs(y2-y1));
		}else if(shapeType.equals("骰子图形")) {
			drawDiceShape(g);// 绘制随机骰子图形
		}
		
	}
	// 迭代

		// 绘制随机骰子图形
		void drawDiceShape(Graphics g) {
			// 随机四个点 坐标
			java.util.Random random = new java.util.Random();
			int ax, bx, cx, px, ay, by, cy, py;
			int w = 800, h = 600;
			ax = random.nextInt(w);// 宽高 600
			bx = random.nextInt(w);
			cx = random.nextInt(w);
			px = random.nextInt(w);
			ay = random.nextInt(h);// 宽高 600
			by = random.nextInt(h);
			cy = random.nextInt(h);
			py = random.nextInt(h);

			for (int i = 0; i < 10000; i++) {
				int tempx = 0;
				int tempy = 0;
				int r = random.nextInt(3);// 骰子 从ABC中随机取一个点

				if (r == 0) {
					// 取中点
					tempx = (ax + px) / 2;
					tempy = (ay + py) / 2;
					// 绘制出来
					g.drawLine(tempx, tempy, tempx, tempy);
				} else if (r == 1) {
					tempx = (bx + px) / 2;
					tempy = (by + py) / 2;
					// 绘制出来
				} else if (r == 2) {
					tempx = (cx + px) / 2;
					tempy = (cy + py) / 2;
					// 绘制出来
				}
				// 迭代 p 点
				px = tempx;
				py = tempy;
//				System.out.println("p=" + px);
			}
		}

		// 迭代分形
		void drawIfs(Graphics g,int localX,int localY) {
			double a = -1.8, b = -2.0, c = -0.5, d = -0.9;
			double x = 0, y = 0;

			for (int i = 0; i < 50000; i++) {
				double tempx = Math.sin(a * y) + c * Math.cos(a * x);
				double tempy = Math.sin(b * x) + d * Math.cos(b * y);
				x = tempx;
				y = tempy;
//				System.out.println("x=" + x + " y = " + y);
				// 放大
				int px = (int) (tempx * 80) + localX;
				int py = (int) (tempy * 80) + localY;
				g.drawLine(px, py, px, py);// drawLine 需要的参数是 int类型 像素是整的

			}

		}

		/**
		 * 递归矩形
		 * 
		 * @param x
		 * @param y
		 * @param w
		 * @param h 1、当 w < 3 的时候 就停止 方法执行 2、自己加个count 变量 控制递归层数 结束方法执行 return
		 */
		public void drawMyRect(Graphics g,int x, int y, int w, int h) {
			if (w < 30) {
				return;
			}

//			g.drawRect(x, y, w, h);
			g.fillRect(x + w / 3, y + h / 3, w / 3, h / 3);
			// 第一层
			drawMyRect(g,x, y, w / 3, h / 3);
			drawMyRect(g,x + w / 3, y, w / 3, h / 3);
			drawMyRect(g,x + 2 * (w / 3), y, w / 3, h / 3);
		}
}
```

