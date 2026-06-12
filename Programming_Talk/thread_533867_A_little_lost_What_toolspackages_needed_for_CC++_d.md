---
title: "A little lost: What tools/packages needed for C/C++ dev?"
date: 2007-08-24
forum: Programming Talk
---

### Post by shaggy999 on 2007-08-24
So I've moved from Windows to Linux. I'm used to Java programming and I've done a little bit of C/C++ in the past, but never got into it. But now I want to really learn it. I'm not satisfied w/ the performance of Java -- even with JIT compiling. So I'm trying to figure out what packages I need for development. Obviously I need the C/C++ compiler, but I need a linker/debugger/etc. Also what standard libraries are commonplace? Is there something equivalent to JUnit for C/C++? What packages do I need to apt-get?

I don't need an IDE. I plan to use a basic text editor and compile by hand and stuff. I'm searching around, but I can't find a place that says: "Here's the tools you need". With java I knew I just needed to download jdk & junit. Any help appreciated!

---

### Post by Paul820 on 2007-08-24
Open a terminal: Applications->Accessories->Terminal and type
> sudo apt-get install build-essential
This will install all you need to build C and C++ programs, including gdb, the GNU debugger.

---

### Post by basketballer on 2007-08-24
So now i've done all that and it has finished.
Shouldn't i get that program in the 'Programming' menu ?? coz i didn't.

Forgive my lack of experience, I am a freshman student in computer science. i only knew 1 program for C++ programming and that was on Windows.
so help here?

and would this work for Java programming ? coz i'm taking this course next semester.

---

### Post by Paul820 on 2007-08-24
That's just the compiler, debugger and associated headers for it. It won't appear in any menus. Write your program in the text editor like you said you were going to do and then compile it in the terminal. As for java, not a clue, never used. Someone else might be able to help you there.

---

### Post by cstudent on 2007-08-24
Everything you need: [http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu)

---

### Post by shaggy999 on 2007-08-24
> **Paul820 said:**
> Open a terminal: Applications->Accessories->Terminal and type

This will install all you need to build C and C++ programs, including gdb, the GNU debugger.


Thank you! That's exactly what I needed to get started.

---

### Post by CptPicard on 2007-08-24
> **shaggy999 said:**
>  I'm not satisfied w/ the performance of Java -- even with JIT compiling. 

May I ask what exactly are you doing?

I do heavy number-crunching, genuinely algorithms that require brute force and there is no way around it. I have done some testing and JIT-compiled Java is barely faster than C if done right (mostly using primitives in speed-intensive parts).

Swing is slow, yes, but that's just Sun's over-engineering.. :)

---

### Post by slavik on 2007-08-24
also, consider installing dd, it doesn't use gtk/qt but is a really nice graphical front end to gdb (no other like it that I have seen, but would love to be proved wrong).

edit: just found kdbg :) it's in the repos.

---

### Post by basketballer on 2007-08-27
How can i compile some program i wrote in text editor using Terminal??

---

### Post by Lord Illidan on 2007-08-27
> **basketballer said:**
> How can i compile some program i wrote in text editor using Terminal??

If it is C,
```

gcc nameofprogram.c -o nameofprogram
./nameofprogram
```
If it is c++
```

g++ nameofprogram.cpp -o nameofprogram
./nameofprogram
```

Substitute nameofprogram with your program, of course.

---

### Post by basketballer on 2007-08-27
Thank You :ks

---

### Post by d_h_benson on 2007-10-29
Hi,

Like the person who started this thread, I'm also new to Ubuntu and would like to write C programs from the terminal command line.  I've tried following the instructions above to install the 'build-essential' packages, but I get an error:

>>
dave@dave-desktop:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
>>

Does anyone know why this is happening?

Also, I'm hoping to write some OpenGL/glut programs.  Are there any other packages I'll need? 

(Please excuse the silly questions: I'm a student and a newbie.)

Best,



Dave

---

### Post by Lacrimstein on 2007-10-29
EDIT: lol, I should read the thread before I post... XD

---

