---
title: "Java: final static methods, why?"
date: 2009-06-25
forum: Programming Talk
---

### Post by andrew222 on 2009-06-25
I got into a debate with someone today who told me that we can't have a java method be declared as final and static.  We tried it out on Eclipse and I proved him wrong.  

If a method is static, it is statically bound and can not be overridden.  Also, with a final method, it can not be overridden because the method is written inline.

Is there a benefit of having a method being both final and static?  

Or is it allowed in java because the two keywords don't effect each other adversely?

---

### Post by Reiger on 2009-06-25
Technically you can have static methods override other methods...

```

public class Main {

	/**
	 * @param args the command line arguments
	 */
	public static void main(String[] args) {
		System.out.println("From «Bar»:");
		Bar.test();
		System.out.println("From «Foo»:");
		Foo.helloWorld();
	}
}

class Foo {

	public static void helloWorld() {
		System.out.println("Hello world!");
	}
}

class Bar extends Foo {

	public static void helloWorld() {
		System.out.println("Hello World!");
	}

	public static void test() {
		helloWorld();
	}
}

```

If a Method or Member is static it means it should be accessed as is common in function/procedural languages.
If a Method is final it must not be overriden. Final has the following uses:
(a) Final code can be considered the definitive copy of something. This means that a more optimal representation can be used for this code as the possibility of future overrides need not be factored in (remember the JVM has no other way of knowing when a method will be overriden due to its on-demand class loading mechanism)
(b) Final variables only take up one `value' inside the heap/stack: useful for constants.
(c) Final can be used to `lock down' a piece of code.

---

### Post by Can+~ on 2009-06-25
> Java: final static methods, why?

[why not?]("http://www08.wolframalpha.com/input/?i=why%3F") :KS

---

### Post by Ariel David Moya Sequeira on 2009-06-26
It is possible to declare final static attributes so some problems can be avoided while declaring certain methods in a certain way. Don't ask me what kind of "certain" conditions must be met so you HAVE TO use the "final static" declaration; I just know that from experience.

To simply follow the KISS philosophy, you won't need to use a "final static" attribute unless you create a very complex program and everything is just messed up. "final" does not disturb the way "static" works, so it's possible to have both combined. Although, its use is not quite recommended.

---

### Post by jespdj on 2009-06-26
> **Reiger said:**
> Technically you can have static methods override other methods...
No, this is not overriding - the static method in the subclass is hiding the static method in the superclass, but it is not overriding it.

Static methods are not polymorphic - if you have a reference to a superclass which really refers to an instance of a subclass and you call a static method on it, the method in the **superclass** will be called, not the method in the subclass, as happens with non-static methods.

```
class Foo {
	public static void hello() {
		System.out.println("Foo says hello");
	}
}

class Bar extends Foo {
	public static void hello() {
		System.out.println("Bar says hello");
	}
}

public class Test
{
	public static void main(String[] args) {
		Foo obj = new Bar();
		obj.hello();	// Prints "Foo says hello" - NOT "Bar says hello"
	}
}
```

---

### Post by HotCupOfJava on 2009-06-26
I'll interject here (since I haven't seen this yet) that final static methods and members can be accessed using the class name and dot operator WITHOUT having an instantiated object on the heap. In other words, if you have a class Foo, you can simply say Foo.method() or Foo.MEMBER without first having to declare a variable bar = new Foo(). It is not required by the compiler to type static members' names in all caps, but it is a good coding convention to follow. You typically see this in situations where there is a static integer that a class will use for options - i.e. JOptionPane.ERROR_MESSAGE.

---

### Post by Habbit on 2009-06-26
> **HotCupOfJava said:**
> It is not required by the compiler to type static members' names in all caps, but it is a good coding convention to follow. You typically see this in situations where there is a static integer that a class will use for options - i.e. JOptionPane.ERROR_MESSAGE.
Actually, this is used just for constants of primitive types, and not for either methods or final static variables of class types.

---

### Post by HotCupOfJava on 2009-06-26
> **Habbit said:**
> Actually, this is used just for constants of primitive types, and not for either methods or final static variables of class types.

Well, they ARE static types, and Strings are included with the primitives in those cases (although Strings are a very special case in Java, aren't they?)

---

### Post by andrew222 on 2009-06-28
The call to a1.m1() in main resolves to A's version of m1(), but 
  B's version of m1() hides A's m1().
  
   We're not usually worried about this because I think we are careful 
   when we invoke a static method to use the name of the class that 
   introduces it.
   
   if A's m1() is a final static method then B's m1() will never get
   called from b1.m1(), and an Error will be thrown to the compiler
   (ie. compile time error).  If a static method is final it prevents
   us from hiding it in the next immediate subclass.

```


public class Test {

	/**
	 * @param args
	 */
	public static void main(String[] args) 
	{
			A a1 = new B();
			B b1 = new B();
			/*WARNING: "the static method m1() should be accessed 
			 * from the type A in a static way"
			 * */
			try
			{
				a1.m1();
				b1.m1();
			}
			catch(Throwable e)
			{
				e.toString();
				e.getMessage();
				e.printStackTrace();
			}
	}
}

class A 
{
	public static /*final*/  void m1()
	{
		System.out.println("A a1 = new B();\na1.m1();\ncalled from A's m1(), no polymorphism\n\n");
	}
	
}

class B extends A
{
	public static final  void m1()
	{
		System.out.println("B b1 = new B();\nb1.m1();\ncalled from B's m1()");
	}
	
}


```


**With A's m1() as a final static method**

```

A a1 = new B();
a1.m1();
called from A's m1(), no polymorphism


java.lang.Error: Unresolved compilation problem: 
	Cannot override the final method from A

```


**With A's m1() as a non-final static method**
```

A a1 = new B();
a1.m1();
called from A's m1(), no polymorphism


B b1 = new B();
b1.m1();
called from B's m1()[HTML][/HTML]

```

---

### Post by soltanis on 2009-06-29
I'm pretty sure static means "make this accessible without instantiating the object", whereas final means "do not allow this method to be extended".

---

