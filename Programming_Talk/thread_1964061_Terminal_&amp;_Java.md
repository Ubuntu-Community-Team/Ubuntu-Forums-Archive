---
title: "Terminal &amp; Java"
date: 2012-04-23
forum: Programming Talk
---

### Post by Novus Anima on 2012-04-23
Hey, I was wondering if Java outputs could be done via the Terminal. Sort of a rhetorical question, but I am rather new to this Terminal aspect of things. Yes, I understand most of it and I am actually getting used to moving files, copying files, and using chmod on folders and files. However, I am rather stumped when it comes to other things such as getting Java output, Python output, and even LUA output. Now I know Lua uses lExecutor, but I heard of my friend using the Terminal to edit his code and output it to the Terminal. I might be interpreting his words wrong, but if I could get some clarification that would be great.

---

### Post by r-senior on 2012-04-23
If you have a Java program that produces output using System.out.println, or System.err.println, the output will appear in a terminal if you run that program from a terminal.

The out and err refer to the standard output and standard error streams and the terminal will, by default, display both these streams when you run a Java program from the command line.

---

### Post by Novus Anima on 2012-04-23
> **r-senior said:**
> If you have a Java program that produces output using System.out.println, or System.err.println, the output will appear in a terminal if you run that program from a terminal.

The out and err refer to the standard output and standard error streams and the terminal will, by default, display both these streams when you run a Java program from the command line.

So could it be possible for me to add even more if I had such a Java program? For example: JOption dialogs and applet windows. Also, are you aware of such Java programs? I currently have the basic Java installation, but I don't think I have anything that would enable things in the Terminal.

---

### Post by r-senior on 2012-04-23
Are you thinking of writing your own programs in Java, or are you looking for existing applications written in Java?

---

### Post by Novus Anima on 2012-04-23
> **r-senior said:**
> Are you thinking of writing your own programs in Java, or are you looking for existing applications written in Java?

My plans are to write my own programs in Java, and to execute them in the Terminal to test, debug, etc.

---

### Post by r-senior on 2012-04-23
Yes, you can do that. Most Java developers use an integrated development environment (IDE) because it helps with managing projects, running and testing code. But you can run programs from the terminal and you can create a user interface with windows, buttons and so on.

For programming questions and guides, have a look at the Programming Talk section of the Ubuntu forums:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

See the Read Me First sticky thread at the top and follow links for Java.

---

### Post by Iowan on 2012-04-23
Moved to Programming Talk by request.

---

### Post by 11jmb on 2012-04-23
Most java developers prefer an IDE, because it increases productivity, but for beginners, I suggest developing with a text editor and command line interface, because an IDE can get in the way of learning.

If you have a JAVA source called HelloWorld.java, just open a terminal, cd into HelloWorld's directory, and use the following two commands:

```
javac HelloWorld.java
```
this compiles your source file and creates HelloWorld.class (java bytecode)


```
java HelloWorld
```
this runs HelloWorld.class

---

### Post by KdotJ on 2012-04-23
I totally agree with 11jmb on this. If you're beginning Java, do yourself a favour and do it bay hand to start with... compile in the terminal and run. You will learn a great deal more this way in my opinion. 

Also just my advice; if you're making simple Java based terminal programs to start, don't use JOptionPanes for output and input etc. Do it all through the terminal. It will be neater and you won't have to pull in the needed libraries to display GUI stuff.

---

