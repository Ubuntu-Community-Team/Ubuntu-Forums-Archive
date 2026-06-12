---
title: "Programming in linux - where to start"
date: 2006-07-30
forum: Programming Talk
---

### Post by hedonistic.heathen on 2006-07-30
Let me preface this by saying that I've just completed my first programming course (no previous programming experience) that focused on C++ and Microsoft Visual Studio exclusively.  I found visual studio to be very easy to use from a beginners perspective.  I would, however, like to toy around with programming in  linux (I've been dual booting and learning my way around linux in ubuntu since the dapper release), but I'm having difficulty finding an open source linux IDE that is as beginner friendly as visual studio.

I've tried eclipse and anjuta, but have been unsuccessful in my attempts to build and compile a simple 'hello world' program - I've googled and asked around on irc to try and resolve the problem, but haven't had any luck.  I've also toyed around with vim and emacs, but I don't know how to go about finding a linker/compiler or even how to use a stand alone linker/compiler.  

In my opinion the best way to learn is to jump in and do it, even if I don't fully understand all the ins and outs of a given IDE.  So I'd like to find an IDE or some combination of vim and a compiler that would allow me to create a functional program with relatively little hassle (i.e. write code, build/compile, run executable).  Also, it would be nice if I could find an IDE that allowed me to try out languages besides C++ (python in particular).  Eclipse seemed like the logical choice, I installed it and the C++ and Python extensions, but when I try to build a solution I get a "cannot run make" error and I find the eclipse wiki to be horribly organized and generally unhelpful. 

Anyone have any suggestions?  

Thanks in advance for the help.

---

### Post by VDM on 2006-07-30
Generally it comes down to vim/emacs with autoconf/make etc. 
A bash script is handy for a small project as well.
Else kdevelop comes close to a decent IDE.

gcc main.cc -o main

One can say many things about Microsoft, but their development tools generally rock. Atleast the IDE+docs do :)

---

### Post by Lord Illidan on 2006-07-30
Anjuta is also cool.

You need to install the build-essential package.

```
sudo apt-get install build-essential
``` to start compiling programs.

Python is also a good language.

---

### Post by commodore on 2006-07-30
And it seems that Microsoft's keyboards and mice are also very good.

I don't know why people talk so confusingly to beginners always :D? The best compiler in the world is the GNU C compiler which is often called gcc and to which VCM referred to. You can get it with the build-essential package like Lord Illidan said. You don't need a compiler for python though.

---

### Post by Lord Illidan on 2006-07-30
> **commodore said:**
> And it seems that Microsoft's keyboards and mice are also very good.

I don't know why people talk so confusingly to beginners always :D? The best compiler in the world is the GNU C compiler which is often called gcc and to which VCM referred to. You can get it with the build-essential package like Lord Illidan said. You don't need a compiler for python though.

You are wrong there. Don't say stuff like Gcc is the best in the world. It may be the best for you, but for others it is not. A well known magazine held a review of linux compilers and gcc came out second to the Intel C Compiler.

And the magazine is our very own LXF..

For python you still need the python interpreter..But it is installed as default, I think.

---

### Post by Daverz on 2006-07-31
> **hedonistic.heathen said:**
>  Also, it would be nice if I could find an IDE that allowed me to try out languages besides C++ (python in particular).

You don't need an IDE for Python.  Any decent editor that can handle tabs correctly will do.  For me the whole point of languages like Python is that they free you from monolithic environments like IDEs.

For C and C++ development, you should make some effort to learn the basics of make, even if you'll usually rely on the IDE to generate it for you most of the time.  O'Reilly has a nice little book on make, and also one on gnu tools.

---

### Post by misterE0 on 2006-07-31
you don't need an ide if you're just writing code, but if you'd like to use one, anjuta is nice.  Gedit does nice formatting as well (gedit does nice code coloring when you save the file).  Basically if you want to write a python prog, make the program in whatever text editor/ide you like and then execute "python filename.py" from a console.  There are plenty of good getting started tutorials around the net.  

As far as c/c++ goes, you can create your program with whatever editor you like again, and then compile it with "gcc filename.c" or "g++ filename.cpp".  Once it is compiled, an executable will be created called "a.out".  Simply type "./a.out" from the console and your program will run.

---

### Post by Drakx on 2006-08-01
Failing all of the above try out kdevelop, that may or maynot suit your needs :) for python I don't know why but I prefer IDLE ;-)

---

### Post by jjtechno on 2006-08-01
I too am a noob. I just finished c++ and vb.net at school. Someday I want to be a professional programmer. (Get paid for it)Time will tell.
Anyway, I am running the CodeBlocks IDE on Dapper and so far NO problems.
I went with an IDE because it seemed like V and the other editors had a syntacs and language requirement as well. I may be wrong here though.I recognise I am wet behind the ears, so some of you professionals please chime in here.
regards

---

### Post by Lord Illidan on 2006-08-01
> **jjtechno said:**
> I too am a noob. I just finished c++ and vb.net at school. Someday I want to be a professional programmer. (Get paid for it)Time will tell.
Anyway, I am running the CodeBlocks IDE on Dapper and so far NO problems.
I went with an IDE because it seemed like V and the other editors had a syntacs and language requirement as well. I may be wrong here though.I recognise I am wet behind the ears, so some of you professionals please chime in here.
regards
There's nothing wrong with using an ide. Some elitists might tell you to do everything in vi and e-macs, but that's **not** a requirement for professional programming.

---

