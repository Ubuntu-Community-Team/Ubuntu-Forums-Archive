---
title: "C# Error on Console.WriteLine()"
date: 2008-05-03
forum: Packaging and Compiling Programs
---

### Post by soul500l on 2008-05-03
Hi,

I'm just back to programming again. I decided to use CSharp or C# and practicing it on Ubuntu Hardy Heron. I use the software called Mono or Mono Develop.

Could anybody help me with this problem? This is my code:

*****************
public class HelloWorld
{
	public static void Main()
	{
		Console.WriteLine ("Hello World from Franz!");
	}
}
*****************

Simple, eh. But this really took me the whole day finding out the solution. Well, what could I say... I'm new to Ubuntu. :lolflag:

I tried to build it. I have an error on the Console.WriteLine part (that's the 5th line). It says:

"The name 'Console' does not exist in the current context(CS0103) HelloWorld.cs"...

What's the solution to this? Could anybody help?](*,)

---

### Post by amingv on 2008-05-03
Not a C# programmer but, isn't it **System**.Console.WriteLine()?

---

### Post by soul500l on 2008-05-03
No, it's not. 

I'll put here the link where I got this tutorial page:

[http://www.csharp-station.com/Tutorials/Lesson01.aspx](http://www.csharp-station.com/Tutorials/Lesson01.aspx)

But I think you mean something like a Java program. 

System.out.println("Hello World");

But I mean C#, though. I appreciate your help man. 

Could anybody tell me still? I really need it to get started. 

Waaah!

---

### Post by amingv on 2008-05-04
Actually, I got it from here:
[http://en.wikibooks.org/wiki/List_of_hello_world_programs#C.23](http://en.wikibooks.org/wiki/List_of_hello_world_programs#C.23)
and the "Hello Ubuntu in all languages" thread.

Besides, the link you provided has this verb:
[PHP]// Namespace Declaration
using System;[/PHP]
which confirms it.

I suggest you double-check that code.

---

### Post by Don9307 on 2008-05-04
The answer is:  Either put using System; at the beginning of the program, or use the fully qualified name:  System.Console.WriteLine(...).  The suggestion to use system.out.println(...) is C code not C#.

---

### Post by soul500l on 2008-05-04
I would probably admit that I am so dumb right now. And I would say I'm sorry for not following the first advice. 

And yeah... Now I seem to get to know how mono works on C#. 

Thanks guys.

---

### Post by Jordanwb on 2008-05-05
As far as I know Mono does just a good a job as the .Net framework. The only thing where you'd need to change anything is absolute file paths.

---

