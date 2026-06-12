---
title: "How can I continue using Linux when my class is using Microsoft Visual C++"
date: 2008-01-26
forum: Packaging and Compiling Programs
---

### Post by bcasanov on 2008-01-26
I am currently taking my first class in programming in C++.  The professor is advocating using Microsoft Visual C++ 6, but I have told him that I am using Linux and asked if I could use a Linux compiler instead like gcc, or IDEs like Kdevelop, Geany, or Anjunta.  The professor said I could, but with the exception that... the code must work on one of the Microsoft compilers to receive any credit. If it works, there is no problem. If it does not, he will have no way of debugging it for his compiler, hence he cannot determine if I really did check for errors in my code and use the debugger.  Because of this, he cannot cannot determine partial credit (which means that my score will be the full amount or zero). 

As well, it is likely that he will have to recompile the Linux library since libraries are not compatible across platforms.  He is willing to work with me, but he asked if I can first find if I can get Visual C++ 6 to work with Linux.  I am not confident, however, that it will work for us. He said that if I choose to follow the Linux route, I should have a fall-back to the Microsoft versions just in case.  Besides, I will have to do team projects with others who are most likely using Microsoft Visual C++.

Before giving up on the Linux option, is there any way to have a Linux compiler that can have the same libraries as the Microsoft Visual C++ one? 

Thank you

---

### Post by MadMan2k on 2008-01-26
tell your prof to test your programs with MinGW/Cygwin on windows. Especially in the latter case he will have exactly the same libraries like you.

---

### Post by Falter on 2008-01-26
You could use a VM...

---

### Post by LaRoza on 2008-01-26
If you are using Standard C++, you can use the code on any compliant compiler.

As a student, and an IT major (I assume), you should have Windows also.

---

### Post by Zugzwang on 2008-01-28
> **bcasanov said:**
> 
As well, it is likely that he will have to recompile the Linux library since libraries are not compatible across platforms.  He is willing to work with me, but he asked if I can first find if I can get Visual C++ 6 to work with Linux.  I am not confident, however, that it will work for us. He said that if I choose to follow the Linux route, I should have a fall-back to the Microsoft versions just in case.  Besides, I will have to do team projects with others who are most likely using Microsoft Visual C++.
Thank you

Recompiling linux libraries is unlikely to work with Visual C++. As LaRoza pointed out, you can use g++ if you program "pure" C++. Unfortunately, even in general programming classes, it is quite likely that you are asked to use functions that won't work on the linux platform. A typical example is the Hello world example (in C, not C++):
[php]
#include <stdio.h>
#include <conio.h>

main()
{
 printf("Hello\nWorld!");
 getch();
}
[/php]
You won't get this to work in linux because there is no getch function (although there exists a workaround using "getchar" - but that's not precisely the same!). So if you are asked to write a program that prints "Hello world" and then quit after pressing (almost) any key, you can't solve it easily. Note that this is also not possible in C++ (without using the standard C functions), but the tutors in programming classes usually don't care about that.

However, as LaRoza  also pointed out, you could use a VM. Quite a few universities offer Windows and Visual C++ for free if they have a "MSDN AA" contract with Microsoft. You could install this into a VM and use it from there.

Finally, your University may offer you access to a "Windows Terminal Server" on which also Visual C++ is installed. There are Linux programs for accessing such a server although it's quite likely that debugging won't work that way (since you might require admin rights to debug). So you can solve the problems using kdevelop or whatever, load the files up and check if you can compile them there.

---

### Post by plugwash on 2008-01-30
if you don't have windows availible on your own machines can't you use a public uni machine at least to test it before submitting.

---

