---
title: "Namespce does not exists"
date: 2008-03-12
forum: Programming Talk
---

### Post by true_friend on 2008-03-12
I have a little problem...
I am learning C# 2005 on Mono 1.2.6 and MD .18 Beta. It gives me this error when I try to compile this example. 
```
mcs Main.cs
Main.cs(2,7): error CS0234: The type or namespace name `Generic' does not exist in the namespace `System.Collections'. Are you missing an assembly reference?
Main.cs(2,1): error CS0246: The type or namespace name `Collections.Generic' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 2 error(s), 0 warnings

```
The actual cod is here
```
using System;
using System.Collections.Generic;
using System.Text;


namespace SymbolicConstants
{
   class SymbolicConstants
   {
      static void Main(string[] args)
      {
         const int FreezingPoint = 32;   // degrees Fahrenheit
         const int BoilingPoint = 212;

         System.Console.WriteLine("Freezing point of water: {0}",
              FreezingPoint);
         System.Console.WriteLine("Boiling point of water: {0}",
              BoilingPoint);

         BoilingPoint = 21;

      }
   }
}

```
I tried the Mono Class Library, it shows that System. Collections.Generic is there in .NET 2. Why the compiler is giving error. Is there any other one to use like 'gmcs'?
Regards

---

### Post by {BzF}~JOKesTER on 2008-03-13
Try Installing The G++ Package

Open A Terminal And Type:

apt-get update

And:

apt-get install g++

Hope This Helps You!!!

---

### Post by themusicwave on 2008-03-13
It appears that Mono supports generics based on this:
[http://www.mono-project.com/CSharp_Compiler](http://www.mono-project.com/CSharp_Compiler)

maybe you have the old version of Mono?

Mono is not a perfect implementation of C# and some things don't work on it.

If you don't absolutely need C# I really recommend learning Java instead, it is 100% complete on every operating system.  It is roughly equivalent to C#.  Sometimes I think of C# as a proprietary revamping of Java.  C# is Microsoft's answer to Java and also their attempt to lock it down.

Also, C# was only ever meant to run on Windows so it will never be quite right on Linux.  Mono will always lag behind the Microsoft C# version.

If you still want to learn C# though I wish you the best.  It's not a bad language, I use it at work for some projects that require it.  Mainly for plugins to another application that can only be written in C#.

---

### Post by themusicwave on 2008-03-13
Are you using mcs, gmcs or smcs?

That site says mcs is .Net 1.1 which didn't have generics.

Try using one of the others.  smcs is the newest one.

---

### Post by true_friend on 2008-03-16
Problem solved by using gmcs.
Thnx

---

### Post by x88a on 2008-06-05
i am having the same problem
however, it doesnt solve with gmcs.
what should i do?
pls help
tq

---

### Post by true_friend on 2008-06-09
there are three compilers gmcs, smcs and mcs, 
What version of C# you are targetting?

---

