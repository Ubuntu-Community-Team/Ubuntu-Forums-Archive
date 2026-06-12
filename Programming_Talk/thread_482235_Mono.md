---
title: "Mono"
date: 2007-06-23
forum: Programming Talk
---

### Post by kd5ob on 2007-06-23
I'm a former Fortran, Cobol, C, commercial programmer who's also worked in SAP and Lawson development systems.   I had to switch p;rofessions to become a truck driver thanks to overseas exportation of jobs.

Anyway, I decided I would try and learn some C# and use my MONO development included in UBUNTU.
I'm running the latest versoin of UBUNTU and opened up monodoc and started reading the getting started section where we find the 'HELLO WORLD" example.  It is as follows.

kd5ob@roam:~/Desktop/Mono$ cat hello.cs
using System;  
class Hello  
{  
   static void Main() {  
      Console.WriteLine("hello, world");  
   }  
}  

kd5ob@roam:~/Desktop/Mono$ csc hello.cs
Error: illegal character in line 3: #\{
*** Shell command terminated with exit status 70: /usr/bin/chicken hello.cs -output-file hello.c -quiet
kd5ob@roam:~/Desktop/Mono$ 

I know this stuff is supposed to be BETA right now but I think from reading the MONO forums there are several people running MONO software all over the place and just feel the example HELLO WORLD from their own documentation should run right!    

I wonder what went wrong.

Well, for now, back to python.

Thanks 
Charlie

---

### Post by msumurph on 2007-06-23
I copied your code, which I thought looked correct, compiled it, and ran it with no problem.

I used:

**mcs hello.cs**

to compile, and

**mono hello.exe**

to execute.  It displayed "hello, world" as expected.

The Mono C# compiler is mcs (or gmcs).  I noticed you tried csc.  That may be the problem.

Hope this helps!

---

### Post by WW on 2007-06-23
csc is part of the Chicken Scheme-to-C compiler; it is not the C# compiler.

---

