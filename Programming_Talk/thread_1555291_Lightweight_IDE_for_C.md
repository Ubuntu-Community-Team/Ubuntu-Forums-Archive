---
title: "Lightweight IDE for C"
date: 2010-08-17
forum: Programming Talk
---

### Post by Jaiichi on 2010-08-17
Well, if anyone else saw in my other thread, I'm putting the thought of Assembly on hold for now, and wanting to get a headstart on learning some C syntax. All I'd like to know is what is an effective and preferably lightweight IDE that I can use on an Ubuntu Netbook.

My experiences with certain Java IDEs such as Eclipse and Netbeans, although I found many useful features built in, they really bogged down my computer (And this was on my main laptop).

The 3 that I'm looking at more are Anjuta, Code::Blocks, and CodeLite. Has anyone used any of these before, or have their own personal recommendations? Thanks!

---

### Post by Bachstelze on 2010-08-17
C is a small enough language that it doesn't need an IDE IMO.  The syntax is dead simple, and the K&R book is sufficient as a library reference.

---

### Post by Jaiichi on 2010-08-17
The main reason I'm looking for an IDE just so I don't need to keep a terminal open for every compile I do, my netbook is only 10" so I don't want to be juggling the source files and the terminal and the running program in my limited screen space.

---

### Post by Bachstelze on 2010-08-17
An IDE wouldn't really help.  Unless you want to code graphical programs, you will need an open terminal to run your program anyway.  What I personally do is: one terminal tab with vim for the code, one for the compilation/running, and possibly one for man pages.

---

### Post by GenBattle on 2010-08-17
If you have eclipse rolling around already you could use the eclipse C/C++ Development Tools (CDT) [http://www.eclipse.org/cdt/](http://www.eclipse.org/cdt/)

Course eclipse is not exactly light-weight, but it will certainly be complete.

---

### Post by Zorgoth on 2010-08-17
emacs works as an IDE for purposes like that - you can do all your compiling and debugging (gdb) in the same window.

---

### Post by eranif on 2010-08-19
> **Jaiichi said:**
> The 3 that I'm looking at more are Anjuta, Code::Blocks, and CodeLite. Has anyone used any of these before, or have their own personal recommendations? Thanks!

I recommend on codelite. It is the least known of the three, but from my point of the view, the best one among them.

It provides the best code-completion, code-assistant, code navigation ,wizards, built-in doxygen comment generator and an excellent gdb integration (and much more)

it is the only one that uses the MI interface of gdb - this interface allows it to de-reference any pointer and handle it as an object (i.e. you can query any pointer in the form of a tree) and more.

Disclaimer: 
I am writing this, but you should know that I am the author of codelite ;)

Eran

---

### Post by cthulhu_54 on 2010-08-19
Vi(m) is the lightest, just a terminal. 
I use Emacs, since it can do anything.
(and running gdb in emacs with gdb-many-windows is just amazing)

EDIT:
[http://emacs-fu.blogspot.com/2009/02/fancy-debugging-with-gdb.html](http://emacs-fu.blogspot.com/2009/02/fancy-debugging-with-gdb.html)

---

### Post by interval1066 on 2010-08-19
Emacs is still kind of heavy for some. Gedit (if you're using the Gnome desktop) has syntax coloring and is already installed. Then if you don't mind installing something you can try Geany which has everything gedit has plus a few more things like a symbols tree/documents/compiler messages views, a little more ide like yet still pretty light.

---

### Post by Lootbox on 2010-08-19
I second the Geany recommendation. It's lightweight and you can compile in the editor window as well.

---

### Post by jon zendatta on 2010-08-20
Gedit == (light && tastie)

---

### Post by Jaiichi on 2010-08-20
Thank you! Geany is exactly the type of thing I was hoping to use.

But now a new problem is showing up... I wanted to do a quick test so I threw a 'hello, world' java program down (hahah...). And I got this:

Error: could not open 'I:\JRE\lib\i386\jvm.cfg

Uhm... I tried changing the path for this back to C:\ multiple times in the past. It seems successful each time I've tried, it asks me to reboot to enable the change, but then it changes back to I:\

I've never even used I:\ on this computer. This isn't some sort of malware is it?

---

### Post by schauerlich on 2010-08-20
ed.

---

### Post by dv3500ea on 2010-08-20
> **Jaiichi said:**
> Thank you! Geany is exactly the type of thing I was hoping to use.

But now a new problem is showing up... I wanted to do a quick test so I threw a 'hello, world' java program down (hahah...). And I got this:

Error: could not open 'I:\JRE\lib\i386\jvm.cfg

Uhm... I tried changing the path for this back to C:\ multiple times in the past. It seems successful each time I've tried, it asks me to reboot to enable the change, but then it changes back to I:\

I've never even used I:\ on this computer. This isn't some sort of malware is it?

Are you using Ubuntu? It's just that 'I:\JRE\lib\i386\jvm.cfg' and 'C:\' are Windows paths. To compile and run a java program [openjdk-6-jre]("apt:openjdk-6-jre") and [openjdk-6-jdk]("apt:openjdk-6-jdk") installed. If your java source file was at ```
/home/user/hello.java
``` you would run:
```

cd /home/user
javac hello.java
java hello.class

```
in a terminal.

Compiling and running the program should work in Geany though.

---

### Post by Jaiichi on 2010-08-20
> **dv3500ea said:**
> Are you using Ubuntu? It's just that 'I:\JRE\lib\i386\jvm.cfg' and 'C:\' are Windows paths. To compile and run a java program [openjdk-6-jre]("apt:openjdk-6-jre") and [openjdk-6-jdk]("apt:openjdk-6-jdk") installed. If your java source file was at ```
/home/user/hello.java
``` you would run:
```

cd /home/user
javac hello.java
java hello.class

```
in a terminal.

Compiling and running the program should work in Geany though.


No, Java is working totally fine on my Ubuntu Netbook, but this is a Windows laptop that I'm on, and I've been unable to properly update Java or use it for a while. Sorry for the confusion.

---

### Post by Finalfantasykid on 2010-08-20
> **Bachstelze said:**
> C is a small enough language that it doesn't need an IDE IMO.  The syntax is dead simple, and the K&R book is sufficient as a library reference.

Ya I mainly just use a text editor when writing in c, although an IDE can certainly make work more efficient when dealing with large programs.

> I recommend on codelite. It is the least known of the three, but from my point of the view, the best one among them.

It provides the best code-completion, code-assistant, code navigation  ,wizards, built-in doxygen comment generator and an excellent gdb  integration (and much more)

it is the only one that uses the MI interface of gdb - this interface  allows it to de-reference any pointer and handle it as an object (i.e.  you can query any pointer in the form of a tree) and more.

Disclaimer: 
I am writing this, but you should know that I am the author of codelite :wink:

Eran

I have used codelite, and I agree that it is a very good IDE.

---

