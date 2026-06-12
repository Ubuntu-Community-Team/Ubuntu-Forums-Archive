---
title: "hello world+arguments. Not understanding."
date: 2009-11-09
forum: Programming Talk
---

### Post by mickmouse13 on 2009-11-09
this is a sample i got from some sight you type ```
./hello.exe A B C D
``` the letters can be anything. and then this says helloworld,tells the number of letters, and then shows you the letters. What i get is HOW does it print {0} in line 10 if it has not been defined yet? The only thing i can see is that it runs through and kinda copy and pastes it to like ten from line 13... but why would it be done that way? im new but it seems like it would be better to do all the math and what ever and then use the WriteLine commands..  I hope i have been clear if anyone can explain these couple of lines it would be nice. 
```
// Hello3.cs
// arguments: A B C D
using System;

public class Hello3
{
   public static void Main(string[] args)
   {
      Console.WriteLine("Hello, World!");
      Console.WriteLine("You entered the following {0} command line arguments:",
         args.Length );
      for (int i=0; i < args.Length; i++)
      {
         Console.WriteLine("{0}", args[i]); 
      }
   }
}
```
so the outcome is like this.
```
Hello, World!
You entered the following 4 command line arguments:
A
B
C
D

```

---

### Post by ve4cib on 2009-11-09
> **mickmouse13 said:**
> What i get is HOW does it print {0} in line 10 if it has not been defined yet?

If what has not been defined yet?  args?  args.Length?

When you run your program

> ./Hello.exe A B C D

the shell creates args and passes that to your program.  So the shell effectively calls:

```
 Hello3.Main(["A","B","C","D"]) 
```

args has 4 elements in it (the strings A, B, C, and D).  Its contents and length have been defined by the OS before it's been passed into your program.

Does that help at all?

---

### Post by mickmouse13 on 2009-11-09
I have a much better understanding now, thanks but i am still confused how Args goes into {0} before its defined, it seems like its not defined till AFTER its written...


is it like.. "{0}" is a place holder, then later in the program its filled in?

---

### Post by ve4cib on 2009-11-09
"{0}" is simply a placeholder in your string.  It's basically saying "Put argument zero here".

So when you say 

```
Console.WriteLine("{0}", args[i]);
```

the computer interprets it as "Take whatever value args[i] has and print that out."  The computer automatically replaces "{0}" with the value of args[i].  i is defined in your loop to be some value in the range 0 <= i < args.Length.  args.Length was set by the shell when you ran your program, as was args[0], args[1], etc...

---

### Post by mickmouse13 on 2009-11-09
thanks that cleared it up.

---

