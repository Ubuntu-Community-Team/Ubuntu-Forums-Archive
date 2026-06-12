---
title: "C# MonoDevelop0.01 Ubuntu 6.06"
date: 2006-08-11
forum: Programming Talk
---

### Post by Alf Stockton on 2006-08-11
I am attempting to learn C# programming using the book Visual C# .NET 2003 Kick Start but the 1st program I try does not compile.
The source looks like:-
class ch01_01

{

    static void Main()

    {

        System.Console.WriteLine("Hello from C#.");
        System.Console.WriteLine("Press any key to continue");
        System.Console.ReadLine();

    }

}

and the error given is :-

Building Solution ch01_01

Building Project: ch01_01 Configuration: Debug
Performing main compilation...

Build failed. Couldn't create a remote process.

Where do I fix this please?

---

### Post by moma on 2006-08-11
Does this  compile ? 

Create a new C#, "Console Project" and test this code.

```
using System;

namespace abc
{
	class MainClass
	{
		public static void Main(string[] args)
		{
			Console.WriteLine("Hello World!");
		}
	}
}
```

---

