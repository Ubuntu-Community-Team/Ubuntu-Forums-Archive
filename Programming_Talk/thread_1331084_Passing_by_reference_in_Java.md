---
title: "Passing by reference in Java"
date: 2009-11-19
forum: Programming Talk
---

### Post by swappo1 on 2009-11-19
I can't get this code to compile.  How do I pass by reference in Java?
```
public class Practice
{
	public static void main(String[] args)
	{
		DoubleClass courseScore = new DoubleClass();
	
		getScore(courseScore);
	}

	public static void getScore(DoubleClass score)
	{
		double s = 10.0;
	
		score.setNum(s);
	}
}
```
Errors:
```
Practice.java:10: cannot find symbol
symbol  : class DoubleClass
location: class Practice
	public static void getScore(DoubleClass score)
	                            ^
Practice.java:5: cannot find symbol
symbol  : class DoubleClass
location: class Practice
		DoubleClass courseScore = new DoubleClass();
		^
Practice.java:5: cannot find symbol
symbol  : class DoubleClass
location: class Practice
		DoubleClass courseScore = new DoubleClass();
		                              ^
3 errors

```

---

### Post by doas777 on 2009-11-19
I believe that you want "Double" not "DoubleClass". "double" is the primative, whereas "Double" (capital d) is the class form.

---

### Post by swappo1 on 2009-11-19
This is from the example in my textbook and it uses DoubleClass.

---

### Post by era86 on 2009-11-19
> **swappo1 said:**
> This is from the example in my textbook and it uses DoubleClass.

You may need to define the class DoubleClass before trying to create one.

---

### Post by myrtle1908 on 2009-11-19
> **swappo1 said:**
> This is from the example in my textbook and it uses DoubleClass.

Well then you will need the DoubleClass class.  Do you have it?  Is it in the classpath when you compile?  The compiler thinks otherwise.

---

### Post by TennTux on 2009-11-19
I believe, as doas777 states, that your compile errors are because Java does not know what DoubleClass is. You will have to provide it or use Double (or java.lang.Double which is it's full name). You could also use double, the non-object version too.

As for your actual issue. Java does not really have a pass by reference. Every thing is assumed to be pass by value. So you have to trick it by passing a pointer to a pointer as C++ people would think of it. In this case you would use an array of Doubles. The array would be the value and each element would then be the references. See modified example below:

```

public class Practice
{
	public static void main(String[] args)
	{
		Double[] courseScore = new Double[1];
		courseScore[0]	= new Double(5) ;

		System.out.println("Before: " + courseScore[0]) ;	
		getScore(courseScore);
		System.out.println("After: " + courseScore[0]) ;

		double[]	courseScore2	= new double[1] ;
		courseScore2[0]	= 7.0 ;
		System.out.println("Before: " + courseScore2[0]) ;
		getScore(courseScore2) ;
		System.out.println("After: " + courseScore2[0]) ;
	}

	public static void getScore(Double[] score)
	{
		score[0]	= new Double(10.0) ;
	}

	public static void getScore(double[] score)
	{
		score[0]	= 14.0 ;
	}
}

```

I hope this helps.

---

### Post by doas777 on 2009-11-19
I am pretty sure it is "Double" you are looking for. it is a class wrapper for the double type, so that it can be passed the way you want. it "auto-boxes" double values so that conversion is easy.
[http://java.sun.com/j2se/1.4.2/docs/api/java/lang/Double.html](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/Double.html)
[http://java.sun.com/j2se/1.5.0/docs/guide/language/autoboxing.html](http://java.sun.com/j2se/1.5.0/docs/guide/language/autoboxing.html)

---

### Post by swappo1 on 2009-11-19
Ok, I just figured out that DoubleClass is defined in the appendix.  
> Java does not really have a pass by reference. Every thing is assumed to be pass by value.
Why wouldn't Java have a way to pass by reference?  This is a major disappointment.  I use pass by reference a lot  in C++.  Up until now, I have not really liked Java. Unfortunately the class I am taking is teaching Java.  I think I am now convinced that I don't like Java and much prefer C++.

---

### Post by TennTux on 2009-11-19
As a long time programmer of C, C++ and Java. I believe you are going through the, "What I know is better than what I'm learning" stage. The languages are different and each has their strengths. After you get to know java well, assuming you don't talk your self into hating it, you will find that the way you approach the design of code will avoid the pitfalls of Java. I'm sure someone who knows java would complain about many of the issues in C++ like memory leaks and some of the cryptic ways C++ programmers write code. If this is for part of a course or a tutorial it may be that the instructor wants you to see how to accomplish various tasks. I would suggest you keep an open mind and look for Java's strengths and you may also find that C++ and Java each have their place.

---

### Post by akoskm on 2009-11-19
Is the class DoubleClass defined in the same package like your main program?

---

### Post by CptPicard on 2009-11-19
To make the pass-by-reference matter more clear... in Java, primitives are passed by value, objects are passed by value-of-reference. All objects are handled through reference types which is a kind of "pointer"; the contents of the object itself are not copied in passing them.

Pass-by-reference in the sense of C++ where the reference is not a value in its own right but actually *is* the referred to thing is not fundamentally necessary; I very rarely miss it in Java. Just use more indirection if needed. I am not even really sure how the key distinction of C++ references -- ability to use them as lvalues for assignment back into the object itself -- would work in the context of Java, as the language is built around the idea of "all objects are at the end of a pointer".

---

### Post by A_Fiachra on 2009-11-19
> **swappo1 said:**
> This is from the example in my textbook and it uses DoubleClass.


Read the page before the example .... the author either defines DoubleClass or this example is not intended to be a working example.

(Which is why Bjarne Stroustrup's book on C++ is a massive pain in the ***, but that is another discussion.)

Also, always remember that cutting and pasting code from the web (or, for that matter, typing it out from a book) without understanding exactly what the code is doing and how is like eating gum off the street.

---

