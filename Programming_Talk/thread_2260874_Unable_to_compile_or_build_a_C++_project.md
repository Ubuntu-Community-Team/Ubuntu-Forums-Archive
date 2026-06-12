---
title: "Unable to compile or build a C++ project"
date: 2015-01-14
forum: Programming Talk
---

### Post by tommy17 on 2015-01-14
Hi i am using ubuntu 14.04 in VMplayer window 7. I install netbeans 8, java jk 8 and g++ compiler through the terminal. Using netbeans i created a simple C++ "hello world" projects but is unable to build and compile. Below is the screenshot of error. Please help thanks

---

### Post by TheFu on 2015-01-15
Open a terminal.[B]
g++ hello.cpp -o hello[/B]
Did that work? Of course, change the input filename to match whatever you named yours.

IMHO, when learning it is best to avoid IDEs - they have hundreds of options, most are buried 3-levels down in the dialogs.  After all, Linux is an IDE for C/C++ programmers already. No need for an all-in-one program to complicate things, IMHO.

If you learn how to do it with 3 windows, you'll never be confused by any IDE again.
* editor
* make
* debugger
Master that, THEN configure the IDE of choice for your desires. I'd skip the kitchen-sink IDEs for now.  A minimal IDE like **geany** might be best to start.  It is like the TurboC or TurboC++ IDEs that millions of people learned by using with just a few settings.  

BTW - I still use 3 windows myself
* vim - my editor of choice
* gmake - I prefer Makefiles over project builds. Same outcome, not funky binary files to get corrupted
* xxgdb - Ok - so this is a little lazy. gdb is fine, but ... 

Some might have a 4th window for their version control tool.  I can type **git commit .** in the make window as a new feature is completed.

---

### Post by schragge on 2015-01-15
The build fails because NetBeans tries to run compiler through [distcc]("http://manpages.ubuntu.com/manpages/trusty/en/man1/distcc.1.html"), but package *distcc* is not installed.

+1 to **TheFu**'s advice. IDEs may be useful for big projects. For beginners, they just add additional level of complexity.

---

