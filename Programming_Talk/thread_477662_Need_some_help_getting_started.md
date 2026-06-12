---
title: "Need some help getting started"
date: 2007-06-18
forum: Programming Talk
---

### Post by Obeleh on 2007-06-18
Hi Im used to program C  in borland builder

But now I try to learn to program in linux and I cant even get a simple "hello world" program to work

```
#include <stdio.h>

int main()
{
	printf ("hi");
	return 0;
}
```

then I did this in console

```
gcc -c test.c
```

it creates a file called 'test.o"

So I do this in console

```
sh test.o
```

But it returns

> Syntax error: word unexpected (expecting ")")

---

### Post by Modred on 2007-06-18
Using the -c flag on gcc tells it to only work through the compilation step, leaving your byte code unlinked to the libraries.  The **.o** file is equivalent to the unlinked **.obj** files made by some other compilers.  Try the following:

```
gcc -o test.out test.c
```

(Since you've already made a .o file, you could also just do **gcc test.o** to finish the linking.)

After that finishes, run it like so:
```
./test.out
```

---

### Post by LaRoza on 2007-06-18
For future reference: 
```

g++ sourceCode.cpp -o executable.exe

```

Does every thing in one step. G++ is for C++, GCC is for C, but the command is the same. You don't need any extensions, but I put them on to demonstrate the nature of the file.

---

### Post by pmasiar on 2007-06-18
> **Obeleh said:**
> Hi Im used to program C  in borland builder

But now I try to learn to program in linux and I cant even get a simple "hello world" program to work


Programming changed a lot since good ole Borland days... Not even sure if Borland still exists.

Is C important for you? If you forgot most of it, maybe you are better off starting with a simpler, more forgiving language like Python (see wiki in my sig). You can return to C later if you need - your skills will be less rusty.

---

### Post by LaRoza on 2007-06-18
Figures, do you wait around for such posts?

If the OP wants to learn other programming languages, including Python, check my sig, the second to last post in the thread will be easier to understand.

---

### Post by Modred on 2007-06-18
> **pmasiar said:**
> Programming changed a lot since good ole Borland days... Not even sure if Borland still exists.

[http://www.codegear.com/products](http://www.codegear.com/products)

As you can see, Borland is still very much alive and well and still putting out development tools (CppBuilder,JBuilder,etc).  CodeGear is just a split off and renamed Borland Developer Tools Group.

---

### Post by Obeleh on 2007-06-18
Thanx for the help
The "Hello World" worked

> **pmasiar said:**
> Programming changed a lot since good ole Borland days... Not even sure if Borland still exists.

Is C important for you? If you forgot most of it, maybe you are better off starting with a simpler, more forgiving language like Python (see wiki in my sig). You can return to C later if you need - your skills will be less rusty.

I dont know why you think im so "Rusty"  but I guess you think i'm referring to borland c as a language

I study Electronics, Industrial Automation and there we learnt programming in C
at first in Borland builder 4
And nowadays in Borland builder 2005 ( I could be mistaking by a year tho :P)
I've thought myself Visual Basic through some tutorials on the internet. So I know what the benefits can be of a lower level
I've just never learned how to compile in the linux environment because I'm quite new to Linux. I've been reading stuff about it and tried to figure out how to compile a simple hello world but I think I went in the wrong direction somewhere

Back to your question...

I'm sticking with C because I want to start somewhere familiar. And now I can. Yes I was considering learning Python but I want to learn C/C++ some more aswell because school didn't cover everything.
I want to learn all this so I can perhaps some day contribute to the Ubuntu community aswell. 

2 Days a week I go to school and 3 days a week I work as a PLC / SCADA programmer so knowing C will come more handy than knowing Python... for now ;)


PS I waited so long with replying because I was watching a movie :popcorn:

And again... Thanx all

---

### Post by pmasiar on 2007-06-18
> **Modred said:**
> As you can see, Borland is still very much alive and well and still putting out development tools .

That's all right, they are still *alive*. But I remember the times when TurboC (and TurboPascal) was *the best* IDE on the (pre-windows) market.

---

### Post by LaRoza on 2007-06-19
Command line compiling is not just for Linux, you can do it in Windows, I do. If you were to get Dev-C++, for example, you could just use g++ through the command line. All the options are the same.

I like to use the same editor I use for almost all my code, that is why I don't use the Bloodshed IDE, but use its compiler, linker, etc.

---

### Post by vexorian on 2007-06-19
try code::blocks IDE, it would pretty much save you some issues, the only problem is that you'll eventually need to learn about this command line compiling in order to distribute the program, unless you  decide to make binary packages for each platform yourself..

---

### Post by LaRoza on 2007-06-19
> **vexorian said:**
> try code::blocks IDE, it would pretty much save you some issues, the only problem is that you'll eventually need to learn about this command line compiling in order to distribute the program, unless you  decide to make binary packages for each platform yourself..

Command line compiling is easy, you don't need to click on anything, you don't have to wait for a GUI and if the program is CLI, you can compile and run with out taking your fingers off a keyboard.

---

