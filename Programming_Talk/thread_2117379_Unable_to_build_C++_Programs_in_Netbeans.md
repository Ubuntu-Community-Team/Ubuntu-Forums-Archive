---
title: "Unable to build C++ Programs in Netbeans"
date: 2013-02-18
forum: Programming Talk
---

### Post by Mike10562013 on 2013-02-18
I'm currently in a programming class with University of Phoenix.  My problem is that whenever I try to build a program (even just a simple Hello World program", it didn't show up any errors in my amazing program, yet it always says, "Build Failed".  Last time I turned a homework assignment in, the feedback I got from the teacher was that it built and ran perfectly.  Not so on my Ubuntu 12.10 installation.  I have installed the g++ compiler.  I'm beyond frustrated at this point.  I have installed it through the Ubuntu Software Center and also downloaded it for Linux from the netbeans website.  Neither made a difference.  Please help!

---

### Post by albandy on 2013-02-18
> **Mike10562013 said:**
> I'm currently in a programming class with University of Phoenix.  My problem is that whenever I try to build a program (even just a simple Hello World program", it didn't show up any errors in my amazing program, yet it always says, "Build Failed".  Last time I turned a homework assignment in, the feedback I got from the teacher was that it built and ran perfectly.  Not so on my Ubuntu 12.10 installation.  I have installed the g++ compiler.  I'm beyond frustrated at this point.  I have installed it through the Ubuntu Software Center and also downloaded it for Linux from the netbeans website.  Neither made a difference.  Please help!

Try building and executing the project attached. It's a simply hello world. untar it to your NetBeansProjects folder and open it.

Let me know it it works.

---

### Post by Nr90 on 2013-02-18
Try building the file from commindline with -Wall.
You'll learn more compiling that way as well.

---

### Post by Mike10562013 on 2013-02-18
Getting ready to try it in a second albandy.  Nr90...is there just a simple way to do it so I can test programs while I'm writing them without having to go into command line to build it and then finally be able to test it?  Sometimes I make very small differences and it would just seem like a waste of time.  I'm going to have to be honest here, coupled with Unity and Windows looks more and more appealing.  :-/

---

### Post by Mike10562013 on 2013-02-18
albandy, now it's saying build successful but the run failed.

---

### Post by Bucky Ball on 2013-02-18
*Thread moved to **Programming Talk**.*

---

### Post by albandy on 2013-02-18
> **Mike10562013 said:**
> albandy, now it's saying build successful but the run failed.

Can you paste the output console logs?

---

### Post by Mike10562013 on 2013-02-18
/home/mike1056/NetBeansProjects/CppApplication_2/dist/Debug/GNU-Linux-x86/cppapplication_2: 1: /home/mike1056/NetBeansProjects/CppApplication_2/dist/Debug/GNU-Linux-x86/cppapplication_2: Syntax error: Unterminated quoted string

RUN FAILED (exit value 2, total time: 377ms)

---

### Post by albandy on 2013-02-18
> **Mike10562013 said:**
> /home/mike1056/NetBeansProjects/CppApplication_2/dist/Debug/GNU-Linux-x86/cppapplication_2: 1: /home/mike1056/NetBeansProjects/CppApplication_2/dist/Debug/GNU-Linux-x86/cppapplication_2: Syntax error: Unterminated quoted string

RUN FAILED (exit value 2, total time: 377ms)

Please, make an screenshot of the main.cpp window

---

### Post by Mike10562013 on 2013-02-18
Here's the screenshot!

---

### Post by albandy on 2013-02-18
This makes no sense.
Try this:
delete or rename the .netbeans folder in your home (this will delete all configurations)
rename the NetBeansProjects folder
create a new NetBeansProject folder
Open Netbeans
Try again the project I've uploaded here.

---

