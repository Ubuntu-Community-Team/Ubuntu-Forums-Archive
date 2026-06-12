---
title: "Call methods after a method -&gt; Weird ? (java)"
date: 2012-11-04
forum: Programming Talk
---

### Post by vikkyhacks on 2012-11-04
How can this be possible ???

> package pack;

public class A {
	
	public static void main(String[] args) {		
		A a = new A();		
		System.out.println("Class details : "a.getClass().getName());
	}
}
OUTPUT: 

Class details : pack.A	


... How can we call a method after calling a method, cos java does not allow methods inside a method.

As far as i know, is this not how we call a function ?

*> package_name.class_name.method_name*
1. How were they able to call getName() after calling getClass() ?
2. Are there any other ways of calling a method other than the one I quoted above ?

 help me I am a beginner ....

---

### Post by spjackson on 2012-11-04
This idiom is known as [method chaining]("http://en.wikipedia.org/wiki/Method_chaining"). getClass returns an object and getName is called on that object.

---

### Post by vikkyhacks on 2012-11-04
thanks, that solved it !!!:)

---

### Post by muteXe on 2012-11-05
I use it a lot, but one downside is you can't do any checks on any of the 'intermediate returns' for null.
> 2. Are there any other ways of calling a method other than the one I quoted above ?

You can also use reflection: [http://docs.oracle.com/javase/tutorial/reflect/index.html](http://docs.oracle.com/javase/tutorial/reflect/index.html)

but i only really use this when I'm writing unit tests and need access to private methods etc.

---

### Post by fhqiihcy on 2012-11-05
[IMG]http://allkindsofpic.info/images/giai.gif[/IMG]:)thank you!

---

