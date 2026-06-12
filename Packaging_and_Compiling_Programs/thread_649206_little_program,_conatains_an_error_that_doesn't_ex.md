---
title: "little program, conatains an error that doesn't exist in C#"
date: 2007-12-24
forum: Packaging and Compiling Programs
---

### Post by zivxx on 2007-12-24
the program i built was:
using System;
public class Findx
{
	public static void Main()
	{
		double a,b,c,d,x1,x2;
		Console.WriteLine("enter a value");
		a=double.Parse(Console.ReadLine());
		Console.WriteLine("enter b value");
		b=double.Parse(Console.ReadLine());
		Console.WriteLine("enter c value");
		c=double.Parse(Console.ReadLine());
		d=Math.Sqrt(Math.Pow(b,2)-4*a*c);
		x1=(-b+d)/(a*2);
		x2=(-b-d)/(a*2);
		Console.WriteLine(x1 x2);
	}
}

then when i was trying to compile i got this error:
then when i was trroot@ziv-desktop:/home/ziv/Desktop/monop# mcs findx2.cs
findx2.cs(16,38): error CS1002: Expecting `;'
Compilation failed: 1 error(s), 0 warnings

so i changed the program to this:using System;
public class Findx
{
	public static void Main()
	{
		double a,b,c,d,x1,x2;
		Console.WriteLine("enter a value");
		a=double.Parse(Console.ReadLine());
		Console.WriteLine("enter b value");
		b=double.Parse(Console.ReadLine());
		Console.WriteLine("enter c value");
		c=double.Parse(Console.ReadLine());
		d=Math.Sqrt(Math.Pow(b,2)-4*a*c);
		x1=(-b+d)/(a*2);
		x2=(-b-d)/(a*2);
		Console.WriteLine(x1 x2)      ;
	}
}

(moved the ; to 16,38)
and still got the same error
any ideas?

---

### Post by Majorix on 2007-12-24
We can't help you unless you cleanly paste your code. Please follow the link in my sig.

---

### Post by public_void on 2007-12-25
This line is wrong, like the compiler said.
```
Console.WriteLine(x1 x2);
```I think you want something like:
```
Console.WriteLine("{0} {1}", x1, x2);
```Correct me if I'm wrong, its a long time since I wrote any C#.

---

### Post by zivxx on 2007-12-25
no your'e totaly right, its just fixed it, thanks :)

---

