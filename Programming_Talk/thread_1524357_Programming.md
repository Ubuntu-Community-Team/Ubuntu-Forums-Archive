---
title: "Programming"
date: 2010-07-05
forum: Programming Talk
---

### Post by Nithingp on 2010-07-05
I am using Ubuntu 10.04,recently i installed blassic and g++.The installation completed successfully .But i am not able to use g++ and blassic neither from applications menu nor from terminal
When typing blassic in terminal the following message is displayed
[SIZE=4][COLOR=Red]blassic: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
[/COLOR][/SIZE]
When typing g++ in terminal 
[SIZE=5][COLOR=Red]g++: no input files[/COLOR][/SIZE]
What is the possible solution?Please help

---

### Post by kellemes on 2010-07-05
You need to install libstdc++5 but latest Ubuntu offers libstdc++6 instead..
[How to install version 5..]("http://www.hackourlives.com/ubuntu-10-04-lucid-lynx-libstdc-so-5/")

g++ is a compiler so you have to tell it what to compile, and how.
[man g++]("http://linux.die.net/man/1/g++")

---

### Post by Nithingp on 2010-07-05
> **kellemes said:**
> You need to install libstdc++5 but latest Ubuntu offers libstdc++6 instead..
[How to install version 5..]("http://www.hackourlives.com/ubuntu-10-04-lucid-lynx-libstdc-so-5/")

g++ is a compiler so you have to tell it what to compile, and how.
[man g++]("http://linux.die.net/man/1/g++")

What To do,to run blassic directly from applications menu instead using terminal?

---

### Post by kellemes on 2010-07-05
> **Nithingp said:**
> What To do,to run blassic directly from applications menu instead using terminal?

Don't know about blassic but it seems to be a commandline based interpreter.. so terminal indeed.

By the way, if you want to use some sort of Basic on Linux there are better options available, blassic seems to be old and unmaintained.

One example..
[gambas]("http://gambas.sourceforge.net/en/main.html")

---

### Post by lkjoel on 2010-07-05
> **Nithingp said:**
> I am using Ubuntu 10.04,recently i installed blassic and g++.The installation completed successfully .But i am not able to use g++ and blassic neither from applications menu nor from terminal
When typing blassic in terminal the following message is displayed
[SIZE=4][COLOR=Red]blassic: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
[/COLOR][/SIZE]
When typing g++ in terminal 
[SIZE=5][COLOR=Red]g++: no input files[/COLOR][/SIZE]
What is the possible solution?Please help
What I did when that happened to me, was to find libstdc++.so, then add a link to it at the same folder, but renaming the link to libstdc++.so.5.
I know that this is not the best Idea, but it worked for me.

---

### Post by Nithingp on 2010-07-10
After installing 'libstdc++6 ' blassic is working fine
Thank you.

---

### Post by Nithingp on 2010-07-10
What To do,to run blassic directly from applications menu instead using  terminal?

---

### Post by lisati on 2010-07-10
Moved to "Programming Talk"

> **Nithingp said:**
> What To do,to run blassic directly from applications menu instead using  terminal?
Once you've compiled your program, you can add a shortcut to your menus.
Right-click on your menu, then click on "Edit menus", and you're on the way.

---

### Post by MasterMind Karthik on 2010-07-10
Wait...

I think you can compile and run your c++ programs with GCC

In terminal, type:
```

gcc myprogram.cpp -o my program

```
then type
```

./myprogram

```

The -o would specify the compiled output to be stored as myprogram. If you didnt specify it, it would by default be named as a.out

Hope it works;)

---

### Post by d3v1150m471c on 2010-07-10
can you post the exact code you're using with g++?

edit:
> **MasterMind Karthik said:**
> Wait...
I think you can compile and run your c++ programs with GCC


g++ passes commands to gcc to compile c++. gcc is for C.

---

### Post by crazyfuturamanoob on 2010-07-10
Calling g++ directly is like using a toothbrush to wash your car. I recommend installing an IDE (such as Code::Blocks) or at least using sconstruct or makefiles to compile your programs.

---

### Post by nvteighen on 2010-07-10
> **crazyfuturamanoob said:**
> Calling g++ directly is like using a toothbrush to wash your car. I recommend installing an IDE (such as Code::Blocks) or at least using sconstruct or makefiles to compile your programs.

No. It isn't.

Knowing how the compiler works, what compiling means and does are key to later take advantage of any IDE's features and be able to manually correct automatically-caused misbehaivor.

---

### Post by lkjoel on 2010-07-10
> **crazyfuturamanoob said:**
> Calling g++ directly is like using a toothbrush to wash your car. I recommend installing an IDE (such as Code::Blocks) or at least using sconstruct or makefiles to compile your programs.
How do you make a makefile?

---

### Post by trent.josephsen on 2010-07-10
> **lkjoel said:**
> How do you make a makefile?
Like this:
```
vi Makefile
```

Seriously, there are tons of resources about make.  Start with make(1) for an overview and ask Google about the syntax.

---

### Post by sjarczyk on 2010-07-13
I think the OP is coming from MS world, and what he wants is to start something like MVS, calling g++... There's no point to explain differences between MS and Unices programming here but, from the other hand, simple answers like 'man gcc' are not enough... Maybe someone knows a good tutorial, something like 'Linux for Windows programmers HOWTO'... :-)

---

### Post by lkjoel on 2010-07-17
> **sjarczyk said:**
> I think the OP is coming from MS world, and what he wants is to start something like MVS, calling g++... There's no point to explain differences between MS and Unices programming here but, from the other hand, simple answers like 'man gcc' are not enough... Maybe someone knows a good tutorial, something like 'Linux for Windows programmers HOWTO'... :-)
What I am looking for is 'MS Windows for Linux programmers HOWTO'.
I want to know how to create .bat files, and if that syntax is even 1% like .sh files!

---

### Post by sjarczyk on 2010-08-10
> **lkjoel said:**
> What I am looking for is 'MS Windows for Linux programmers HOWTO'.
I want to know how to create .bat files, and if that syntax is even 1% like .sh files!
So I'm little confused... Linux programmer, fighting with:
> 
When typing g++ in terminal
[SIZE=5][COLOR=Red]g++: no input files[/COLOR][/SIZE]
What is the possible solution?Please help
 is not typical... I'd say, it's unusual... :-)

---

### Post by wmcbrine on 2010-08-10
> **lkjoel said:**
> I want to know how to create .bat files, and if that syntax is even 1% like .sh files!Maybe 10%. Batch is a very crippled language, if you can even call it that. There are some alternatives in Windows, like VBS.

---

### Post by interval1066 on 2010-08-11
> **lkjoel said:**
> What I am looking for is 'MS Windows for Linux programmers HOWTO'.
I want to know how to create .bat files, and if that syntax is even 1% like .sh files!

No, not really. Batch files are not like shell scripts; for one thing shells are infinitely more useful than that turd cmd.com. Try to get above param passing with a batch file, its an incredible pain requiring you to compile a new com program to take and process the input. That said, even so, if you're familiar with batch files you have a leg up on those that don't. Batch and shell scripts are at least in the same general forest. Different paths...

---

### Post by WitchCraft on 2010-08-11
g++ sourcefile.cpp -o outfile.exe

But use scons, that you can use on windows + linux.
Geany is a good editor. Keep away from vi, unless you need to work on the command-line.
Makefiles, you can use on windows, too, with mingw + msys.

makefiles is like a batch file that compiles one file after another, with some options, like linking to libraries xy, ab, cd etc.

---

