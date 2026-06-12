---
title: "Java, Class, Constructor and Method Help"
date: 2007-09-18
forum: Programming Talk
---

### Post by Magneticgravity on 2007-09-18
class MyClass {
    //field, constructor, and method declarations
}


Can someone just give me a few real examples of the above code. Im currently reading a guide on Java and am a tad confused on what each of these are exactly.


Ive been reading the Java Tutorials, and am now reading the 'Classes' Section: [http://java.sun.com/docs/books/tutorial/java/javaOO/classes.html](http://java.sun.com/docs/books/tutorial/java/javaOO/classes.html)

Could someone give me maybe some examples using all of the things mentioned in that section and tell me which bit is which, as it seems they tell me about each component but don't fit it all together in the end.

By the way, Im still a big Java noob, so please have mercy :)

---

### Post by tenmillionmilesaway on 2007-09-18
Hi,
This might help:

```
public class MyClass
{
	//a field is basically just a global variable (available to all methods in the class)
	private String myStringField = ""; 
	public String myStringField2 = "";
	
	//a constructor is what you call to create an object of this classes type
	//this is the default constructor and isnt really needed
	public MyClass()
	{
		//you can initialise fields here eg
		myStringField = "hello";
	}
	
	//you can also pass in parameters into the contructor eg
	public MyClass(String field2)
	{
		myStringField2 = field2;
	}
	
	//methods are well methods eg
	public void aMethod()
	{
		System.out.println(myStringField);
	}
}
```

You could also look in the hello ubuntu in every language thread (sticky) at the Java examples.  A hello world app would be the best place to start, then gradually make more complex things.

---

### Post by Fixman on 2007-09-18
A class is like a "variable container"

```
public class A
{
  public int a ;
  public String b ;
} ;

//...

A re ;
re.a = 54 ;
re.b = "Hi" ;

```

You can also define functions inside that class. You can use private variables that are only accesible to functions

```
 public class A
{
  public int a ;
  private int b ;

  public void setb (int n)
  {
    b = n ;
  }

  public int resurnsum()
  {
    return a + b ;
  }
} ;

//...

A re ;
re.a = 5 ;
//re.b = 47 (Error on this line: A.b is private
A.setb (74) ;
System.out.writeln (re.returnsum()) ; //prints 79

```

A constructor is a function that is executed when the class is created, they must be public. If they take arguments, a variable is inizialized as:

```
A re(78)
```

Obviously, constructors can be overloaded. Note that if you create a constructor with arguments, the default constructor (the one with no argumaents) will be erased if not explicity defined before.

To declare a constructor, you must define a function with the name of the class and NO RETURN TYPE (not even void)

```
 public class A
{
  public int a ;
  private int b ;

  public void setb (int n)
  {
    b = n ;
  }

  public int resurnsum()
  {
    return a + b ;
  }

  A()
  {
    a = 44 ;
    b = 0 ;
  }

  A(int h)
  {
    a = h ;
    b = 0 ;
  }

  A(int h, int g)
  {
    a = h ;
    b = g ;
  }
} ;

//...

A q ;
A w (7) ;
A e (9, 4) ;

System.out.writeln (q.returnsum()) ; //prints 44
System.out.writeln (w.returnsum()) ; //prints 7
System.out.writeln (e.returnsum()) ; //prints 13

e = A(4, 2) ; //YES! they also work on literals!
System.out.writeln (e.returnsum()) ; //prints 6
```

EDIT: Seconded!

---

### Post by Ramses de Norre on 2007-09-18
> **Fixman said:**
> 
A constructor is a function that is executed when the class is created, they must be public. 

An object is created, a class is loaded, there is only one instance of your class but you'll create a lot of objects that are instances of that class.

A real world example of a class I made: ```
package worlds;

/**
 * @author Ramses de Norre
 */
public class Coordinate
{
	private final int x;
	private final int y;
	
	public Coordinate(int x,int y)
	{
		this.x=(x>=0)?x:0;
		this.y=(y>=0)?y:0;
	}
	
	public final int getX()
	{
		return this.x;
	}
	
	public final int getY()
	{
		return this.y;
	}
	
	@Override
	public int hashCode()
	{
		return getX()^getY();
	}
	
	@Override
	public boolean equals(Object coordinate)
	{
		return(coordinate==null || ! Coordinate.class.equals(coordinate.getClass()))?false:
			(((Coordinate)coordinate).getX()==this.getX() && ((Coordinate)coordinate).getY()==this.getY());
	}
	
	// Due to strange Coordinates in the Figuur class this method may look a little weird, but it works ;)
	Coordinate getCoordinateTo(Direction dir)
	{
		switch(dir)
		{
		case UP:
			return new Coordinate(this.getX(),(this.getY()>0)?this.getY()-1:0);
		case DOWN:
			return new Coordinate(this.getX(),this.getY()+1);
		case EAST:
			return new Coordinate(this.getX()+1,this.getY());
		case WEST:
		default:
			return new Coordinate((this.getX()>0)?this.getX()-1:0,this.getY());	
		}
	}
}

```

This class represents two-dimensional coordinates which have 2 integers as instance variables (those are your fields), one constructor which takes two integers and a couple of methods of which two are overriding methods from Object. Don't mind if you don't get all the code, it's the basic design that I want to show.

---

### Post by pbrockway2 on 2007-09-19
Java constructors need *not* be public.

Instances of a class are obtained by using "new".  For instance:
```
    /**
     * Example class.
     * Compile with:
     *     javac -cp . A.java
     * Run with:
     *     java -cp . A
     */
public class A {
  public int a;
  private int b;

    /**
     * Constructs an A with default values - 42 and zero
     */
  public A() {
    a = 42;
  }

  public A(int h) {
    a = h;
  }

  public void setB(int n) {
    b = n;
  }

  public int getSum() {
    return a + b;
  }

  public static void main(String args[]) {
    
    A q = new A();
    A w = new A(7) ;
  
    System.out.println(q.getSum()); //prints 42
    System.out.println(w.getSum()); //prints 7

    q.setB(1);
    System.out.println(q.getSum()); //prints 43
  }
}
```

---

