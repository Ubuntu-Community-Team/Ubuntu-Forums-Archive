---
title: "Program in C# practicing the Exit command...can anyone help?"
date: 2008-01-27
forum: Programming Talk
---

### Post by zivxx on 2008-01-27
hey everyone i built this program:

// main program
using System;
public class switching
{
	public static void Main()
	{
		string Exit="";
		while (Exit !="exit")
		{
			if (Exit!="1"&&Exit!="2"&&Exit!="3")
			{
				Console.Write("choose a menu");
				Console.Write("1");
				Console.Write("2");
				Console.Write("3");
				Exit=Console.ReadLine();
			}
		}
	}
}


//program 1
if (Exit=="1")
{
	using System;
	public class First
	{
		public static void Main()
		{
			int a,b,c;
			a=int.Parse(Console.ReadLine());
			b=int.Parse(Console.ReadLine());
			c=a+b
			Console.Write("what menu would you like to go back to?(for the main menu choosing something which is not 1 2 or 3)");
			Exit=Console.ReadLine();
		}
	}
}


//program 2
if (Exit=="2")
{
	using System;
	public class Second
	{
		public static void Main()
		{
			int a,b,c;
			a=int.Parse(Console.ReadLine());
			b=int.Parse(Console.ReadLine());
			c=a+b;
			Console.Write("what menu would you like to go back to?(for the main menu choosing something which is not 1 2 or 3)");
			Exit=Console.ReadLine();
		}
	}
}


//program 3
if (Exit=="3")
{
	using System;
	public class Third
	{
		public static void Main()
		{
			int a,b,c;
			a=int.Parse(Console.ReadLine());
			b=int.Parse(Console.ReadLine());
			c=a+b;
			Console.Write("what menu would you like to go back to?(for the main menu choosing something which is not 1 2 or 3)");
			Exit=Console.ReadLine();
		}
	}
}



and when building i get this error:

Building Project: talks (Debug)
Performing main compilation...
Compilation failed: 1 error(s), 0 warnings

/home/ziv/Desktop/asd/talks.cs(24,1): error CS8025: Parsing error


Build complete -- 1 error, 0 warnings

---------------------- Done ----------------------

Build: 1 error, 0 warnings



but i don't really understand whats the problem...can anyone help me?

---

### Post by LaRoza on 2008-01-27
Use php or code tags so people can read it.

---

### Post by popch on 2008-01-27
> **zivxx said:**
> 
and when building i get this error:

Building Project: talks (Debug)
Performing main compilation...
Compilation failed: 1 error(s), 0 warnings

/home/ziv/Desktop/asd/talks.cs(24,1): error CS8025: Parsing error


Build complete -- 1 error, 0 warnings

---------------------- Done ----------------------

Build: 1 error, 0 warnings



but i don't really understand whats the problem...can anyone help me?

Read what the computer writes on your screen.  There's some problem in your file 'talk.cs', presumably at line 24. The compiler says it does not parse properly.

Hint: cross your t's and dot your i's

---

### Post by zivxx on 2008-01-27
never mind ive read the paper my friend wrote to me once again and,

// main program
using System;
public class switching
{
	public static void Main()
	{
		string Exit="";
		while (Exit !="exit")
		{
			if (Exit!="1"&&Exit!="2"&&Exit!="3")
			{
				Console.Write("choose a menu");
				Console.Write("1");
				Console.Write("2");
				Console.Write("3");
				Exit=Console.ReadLine();
			}
			//program 1
				if (Exit=="1")
			{
				int a,b,c;
				a=int.Parse(Console.ReadLine());
				b=int.Parse(Console.ReadLine());
				c=a+b;
				Console.Write(c);
				Console.Write("what menu would you like to go back to?(for the main menu choosing something which is not 1 2 or 3)");
				Exit=Console.ReadLine();
			}
			//program 2
			if (Exit=="2")
			{
				int a,b,c;
				a=int.Parse(Console.ReadLine());
				b=int.Parse(Console.ReadLine());
				c=a+b;
				Console.Write(c);
				Console.Write("what menu would you like to go back to?(for the main menu choosing something which is not 1 2 or 3)");
				Exit=Console.ReadLine();
			}
			//program 3
			if (Exit=="3")
			{
				int a,b,c;a=int.Parse(Console.ReadLine());
				b=int.Parse(Console.ReadLine());
				c=a+b;
				Console.Write(c);
				Console.Write("what menu would you like to go back to?(for the main menu choosing something which is not 1 2 or 3)");
				Exit=Console.ReadLine();
			}
		}
	}
}


and it works :)

---

