---
title: "(Java) Somewhat Simple Question about Arrays"
date: 2010-01-19
forum: Programming Talk
---

### Post by s3a on 2010-01-19
I am reading a little bit ahead before my next semester of school starts and I do not understand why I can't solve the following problem taken from my text book:

> Checkpoint 8.13: Look at the following method header: **public static void myMethod(double[] array)**
Here is an array declaration: **double[] numbers = new double[100];**
Write a statement that passes the numbers array to the myMethod method.

Here is my code:
```
import java.util.Scanner;
public class arraysandarraylistcheckpoint8
{
	public static void main (String[] args)
	{
		// 8.13
		double[] numbers = new double[100];
		myMethod(numbers);
		public static void myMethod(double[] array)
		{
			for(int index = 0; index < array.length; index++)
			{
			array[index] = 5;
			}
		}
	}
}
```
I wrote some unnecessary code such as the for loop with the array[index] = 5; but isn't the only requirement to solve that problem simply a matter of calling the myMethod method by "giving" an array (**myMethod(numbers);**)? Also, what's the proper term for "giving?"

Any input would be greatly appreciated!
Thanks in advance!

P.S.
The error message is as follows:
> deniz@debian:~$ cd '/media/PROGRAMMING/Programming'
deniz@debian:/media/PROGRAMMING/Programming$ javac arraysandarraylistcheckpoint8.java
arraysandarraylistcheckpoint8.java:53: illegal start of expression
		public static void myMethod(double[] array)
		^
arraysandarraylistcheckpoint8.java:53: illegal start of expression
		public static void myMethod(double[] array)
		       ^
arraysandarraylistcheckpoint8.java:53: ';' expected
		public static void myMethod(double[] array)
		             ^
arraysandarraylistcheckpoint8.java:53: '.class' expected
		public static void myMethod(double[] array)
		                                     ^
arraysandarraylistcheckpoint8.java:53: ';' expected
		public static void myMethod(double[] array)
		                                          ^
5 errors
deniz@debian:/media/PROGRAMMING/Programming$

---

### Post by Rany Albeg on 2010-01-19
works fine now.
[PHP]import java.util.Scanner;
public class arraysandarraylistcheckpoint8
{
	public static void main (String[] args)
	{

		double[] numbers = new double[100];
		myMethod(numbers);		
	}
	public static void myMethod(double[] array)
	{
		for(int index = 0; index < array.length; index++)
		{
			array[index] = 5;
		}
	}
}[/PHP]

problem:myMethod located in main.

```
rany@rany-laptop:~$ cd Desktop/
rany@rany-laptop:~/Desktop$ javac arraysandarraylistcheckpoint8.java 
rany@rany-laptop:~/Desktop$
```

---

### Post by s3a on 2010-01-19
Thanks!

---

### Post by s3a on 2010-01-20
(Double post)

---

### Post by NovaAesa on 2010-01-20
[quote="s3a"]Also, what's the proper term for "giving?"[/quote]You **invoke** the method *myMethod* **passing** it the reference *numbers*.

---

### Post by LKjell on 2010-01-21
> **NovaAesa said:**
> You **invoke** the method *myMethod* **passing** it the reference *numbers*.
However some books I have encounter says it is a pointer. Even thought it is incorrect it might be viewed that the numbers are pointing to other address. Reference from referring just does not sound as good as pointer.

So if you do encounter a book that says you are passing a pointer it just means you are passing an Object (Like String) or an Array by their memory address. Primitive types (int, long, double etc) are passed by value.

---

### Post by NovaAesa on 2010-01-21
> **LKjell said:**
> So if you do encounter a book that says you are passing a pointer it just means you are passing an Object (Like String) or an Array by their memory address. Primitive types (int, long, double etc) are passed by value.
Everything is passed by value in Java ;)

---

### Post by LKjell on 2010-01-21
Just semantics... If you say everything is passed by value then you bound to hit the wall since you are not defining anything. Yes technically you are passing the reference as a value. but still you are passing a reference and not the value of each data types in the object.

To clarify this you are passing a reference. But the reference get copied.

---

