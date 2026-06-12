---
title: "[SOLVED] Help with setting up GNU C"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Sunfist on 2008-08-16
I have looked all over and cant find a guide on how to actually get linux and gnu's c compiler set up to operate. I didnt know whether to post here or in development but here is more active and it IS a newb type question. SO, I am not completely new to running a command line compiler. I know I have a c compiler somewhere in my linux installation, I also have at least 2 editors VI and Emacs, (maybe more :)) Problem is I know I am going to have to set up some sort of config file or environment variables to tell the compiler where to find the source code to compile and the linker on where to find the libraries, also to set any compile/link switchs. Which does linux c use, a file or variables. Maybe there is a front end or some type of IDE that makes all of this a lot easier? I have Netbeans, which says it can be used to compile c as well as java, but I am thinking it too would have to be told where the compiler/libraries were and what switches to use ect. Any direction would be helpfull.

---

### Post by ibuclaw on 2008-08-16
For the entire list of gcc functions.
```
man gcc
```
But, for your information. The most standard way to compile code is a simple:
```
gcc -Wall -o **prog** *prog*.c
```
If you have any specific link libraries, then you include "-l" in the line.

ie:
```
gcc -Wall -o **prog** *prog*.c -lncurses -lpanel
```

Or if you wish to automate it in a script, then you can learn how to write a [Makefile]("http://www.wlug.org.nz/MakefileHowto") and simplify the compile line into a simple command.
```
make
```

Regards
Iain

---

### Post by Sunfist on 2008-08-16
when I type gcc -o filename, I get a message saying gcc: no input file. I can see the source code file, so I know its there.

---

### Post by mali2297 on 2008-08-16
> **Sunfist said:**
> when I type gcc -o filename, I get a message saying gcc: no input file. I can see the source code file, so I know its there.

You need to specify the source file,
```

gcc -o filename filename.c

```

---

### Post by Sunfist on 2008-08-16
Thanks Martin that was it, one more question. How do I run the resulting program. I seem to remember some cryptic (to me anyway) command like .filename or something like that, and is there a debugger available for this compiler?

---

### Post by mali2297 on 2008-08-16
> **Sunfist said:**
> Thanks Martin that was it, one more question. How do I run the resulting program. I seem to remember some cryptic (to me anyway) command like .filename or something like that, and is there a debugger available for this compiler?

If the executable is located in the current directory, use
```

./filename

``` 
to run it.

---

### Post by Sunfist on 2008-08-16
Nevermind the last post, I figured it out and it actually works..thanks for the help.

---

### Post by jrothwell97 on 2008-08-16
You need to run ./*appname* because the program almost certainly won't be in a defined program path. However, the ./ means "the current directory", so just run "./filename". Think of this as meaning "(run) filename in the current directory".

---

