---
title: "Three debugging problems (ddd + gdb)"
date: 2009-01-09
forum: Programming Talk
---

### Post by mael15 on 2009-01-09
hi there,
 
 First of all, ddd works "somehow" but I get an error message that I cannot explain when I try to debug my c++ programm. Before debugging begins I have to ignore two other messages:
 
 a) when i start ddd from the shell, it shows: "ddd: Symbol `_XmStrings' has different size in shared object, consider re-linking" but the program runs anyway
 
 b) when i start running my program to debug it from ddd, a window says "starting xterm" but nothing happens. after clicking "cancel" ddd continues to work.
 
 c) in my program, the error occurs when i use wxDialog->showModal() and ddd show the following 6 times: "Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -4 and height 20"
I already searched the whole project code for "-4" without success.
 
 I would not mind the first two errors, but maybe they are connected?
 I am using Ubuntu 8.10 with gdb 6.8-debian.
 
 The third error also occurs with gdb (without using ddd). I searched a lot about this third error but only found something about other programms having bugs, no real solution.
 
 Thanx!

---

### Post by drunken_sapo on 2009-02-11
any news on this? I have the same "starting xterm..." problem.
have you been able to fix it?

---

### Post by galagatron on 2010-02-27
In order for DDD to be able to open xterm, you have to install xterm (it's not installed by default in Ubuntu).

```
sudo apt-get install xterm
```

---

### Post by dwhitney67 on 2010-02-27
> **mael15 said:**
> hi there,
 
 First of all, ddd works "somehow" but I get an error message that I cannot explain when I try to debug my c++ programm. Before debugging begins I have to ignore two other messages:
 
 a) when i start ddd from the shell, it shows: "ddd: Symbol `_XmStrings' has different size in shared object, consider re-linking" but the program runs anyway
 
 b) when i start running my program to debug it from ddd, a window says "starting xterm" but nothing happens. after clicking "cancel" ddd continues to work.
 
 c) in my program, the error occurs when i use wxDialog->showModal() and ddd show the following 6 times: "Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -4 and height 20"
I already searched the whole project code for "-4" without success.
 
 I would not mind the first two errors, but maybe they are connected?
 I am using Ubuntu 8.10 with gdb 6.8-debian.
 
 The third error also occurs with gdb (without using ddd). I searched a lot about this third error but only found something about other programms having bugs, no real solution.
 
 Thanx!

I sure wish these were the only problems the applications I debug would have.  :-)

As for the first problem (a), how are you compiling your project?  Is it indeed up to date?  Try running 'make' (or use the appropriate g++ command) to ensure that all modules have been built.

For the second problem (b), how are you launching ddd?  I typically launch it from the command line, giving the application name, and on occasion the application's PID.  For example
```

ddd myApp &

# or

ddd myApp 12345 &   # use this when the application is already running

```

For the third problem (c), just ignore it.  I have yet to see a platform where ddd did not complain about one thing or another.  I'm sorry I cannot help more with this, but don't let it bother you.

---

