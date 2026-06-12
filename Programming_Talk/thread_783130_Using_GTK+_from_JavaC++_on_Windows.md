---
title: "Using GTK+ from Java/C++ on Windows"
date: 2008-05-05
forum: Programming Talk
---

### Post by Shining Arcanine on 2008-05-05
I have to write a program for my final project in my Java class. My program must be written in Java and it must be cross platform compatible (meaning it will run on two different operating systems).

At the same time, I am writing a completely different program for my final project in my C++ class and I would like to write a GUI for it. I have much more flexibility in writing it than I do with my Java program, which must be strictly Java.

Rather than learning two completely different APIs, I would like to use GTK+ in place of the AWT and Swing libraries for my Java program and in place of Winforms for my C++ application. I have spoken to both of my professors and this is acceptable.

My question is, how do I do it? If someone could point me towards or provide me with directions for getting simple Hello World applications running in both languages on Windows using GTK+ (preferably in Visual Studio for C++ and Eclipse for Java), I should be able to work from there.

---

### Post by LaRoza on 2008-05-05
> **Shining Arcanine said:**
> I have to write a program for my final project in my Java class. My program must be written in Java and it must be cross platform compatible (meaning it will run on two different operating systems).

At the same time, I am writing a completely different program for my final project in my C++ class and I would like to write a GUI for it. I have much more flexibility in writing it than I do with my Java program, which must be strictly Java.

Rather than learning two completely different APIs, I would like to use GTK+ in place of the AWT and Swing libraries for my Java program and in place of Winforms for my C++ application. I have spoken to both of my professors and this is acceptable.

My question is, how do I do it? If someone could point me towards or provide me with directions for getting simple Hello World applications running in both languages on Windows using GTK+ (preferably in Visual Studio for C++ and Eclipse for Java), I should be able to work from there.

For Java, use the simplist solution: Swing. My wiki has references for Java and C++ GUI toolkits including GTK+.

You are using something originally for C in Java and C++. IMO, you are making things hard on yourself. GUI toolkits are not that different from each other, and for this using two different toolkits to fulfil the requirements makes sense. 

For your projects, I recommend Swing for Java and Winforms (if that is what it is called) for C++. 

You are using two different IDE's, and I can imagine the issues with getting them to work with GTK+ ports.

Benefits of using GTK+:
[list]
[*]Similiar ports of another toolkit for different languages.
[/list]
Drawbacks of using GTK+:
[list]
[*] Will be difficult to get working in Eclipse and Visual Studio (even if possible, I doubt the VS creators considered that possibility)
[*] Java may not be crossplatform, depending on the availability/quality of the ports.
[*] C++ will be using a library not generally used for its intended target (if you are using VS, I assume this is only going to be run on Windows)
[*] The professors may not be willing to try to get them working, be nice to them. Many instructors frown on students who makes their lives difficult no matter how clever they are.
[/list]

Benefits of using Swing/Winforms:
[list]
[*] They will work with the greatest ease
[*] Instructors will not be hassles
[*] You will learn two tools that are in demand. Most Java jobs want you to know the JFC, which is why they probably use Java in the first place.
[*] You will spend less time trying to get things working, and more time learning and coding.
[/list]
Drawbacks of using Swing/Winforms:
[list]
[*] Learning more than one API (which is also a plus, as they are both useful)
[/list]

---

### Post by mike_g on 2008-05-05
I started out using swing, and have also had a bit of a play around with GTK+ in C. Swing is very easy to use and the java documentation is very good. Alot of the UI stuff is similar between Swing and GTK+, so if you know Swing then it will be easier to pickup GTK. I'd definitely start out with Swing though if youre using Gtk with Java youre going to need a wrapper for it and I expect there will be cases where its difficult to figure out what to do when all the documantation is in C.

---

### Post by Shining Arcanine on 2008-05-05
It is called GDI32, rather than Winforms (that is for .NET), as I had thought. However, I would much rather use a cross-platform cross-language API for my programs, as both Swing (and Java for that matter) and GDI32 are proprietary and I do not like writing code that makes use of proprietary APIs (or proprietary languages, but my university is forcing Java on me).

I am planning to test both of my programs on both Windows and Ubuntu, which made using GTK+ preferable to using GDI32, as to my knowledge, GDI32 requires WINE on Linux, which is a can of worms that I do not want to open, especially in the context of the massive amount of time I have spent on backend code for my C++ project.

I am looking at QT4 and it seems to support both Java and C++ on Windows and Linux, which should make it perfect as far as utilitarian concerns go. Unfortuantely, it is also proprietary, but I do not seem to have many options, so the very least I can try to pick the one that is the most open. Are there any technical issues that I am missing here or should this be fairly straightforward?

---

### Post by tseliot on 2008-05-05
Why don't you use QT4?
QT4 for C++ and QT Jambi for Java. You can use both of them in Eclipse, see [this page]("http://trolltech.com/developer/downloads/qt/eclipse-integration-download").

Documentation and examples for [QT4 and C++]("http://doc.trolltech.com/4.3/index.html").
Documentation and examples for [QT Jambi and Java]("http://doc.trolltech.com/qtjambi-4.3.4_01/doc/html/com/trolltech/qt/qtjambi-index.html").

P.S.
> In addition, Qt Jambi also enables C++ programmers to easily integrate their Qt code with Java by providing the Qt Jambi generator.

---

### Post by tseliot on 2008-05-05
> **Shining Arcanine said:**
> I am looking at QT4 and it seems to support both Java and C++ on Windows and Linux, which should make it perfect as far as utilitarian concerns go. Unfortuantely, it is also proprietary, but I do not seem to have many options, so the very least I can try to pick the one that is the most open. Are there any technical issues that I am missing here or should this be fairly straightforward?
QT is not proprietary (it's GPL). [Explanation]("http://trolltech.com/developer/knowledgebase/179/"):
> If you want to develop Open Source Software, you are welcome to use our Qt Open Source Edition

If you don't want to develop Open Source Software (for example to keep your source code secret or to produce commercial software), you must purchase a commercial edition of Qt.

---

### Post by Shining Arcanine on 2008-05-05
> **tseliot said:**
> Why don't you use QT4?
QT4 for C++ and QT Jambi for Java. You can use both of them in Eclipse, see [this page]("http://trolltech.com/developer/downloads/qt/eclipse-integration-download").

Documentation and examples for [QT4 and C++]("http://doc.trolltech.com/4.3/index.html").
Documentation and examples for [QT Jambi and Java]("http://doc.trolltech.com/qtjambi-4.3.4_01/doc/html/com/trolltech/qt/qtjambi-index.html").

P.S.
The more I read about QT4, the more I think I might a mistake when I asked my professors about using GTK+. I will work on getting hello world applications running in all combinations of Java/C++ on Windows/Ubuntu and work from there. Thanks for the suggestion.

> **tseliot said:**
> QT is not proprietary (it's GPL). [Explanation]("http://trolltech.com/developer/knowledgebase/179/"):
I was mistaken then. This is much better than what I had originally thought. I am curious, given that GTK+ is used to write Gnome and Gnome is used on Ubuntu Linux, will it be much of a hassle to get QT4 working on Ubuntu Linux or will it be a simple "sudo apt-get install?"

---

### Post by LaRoza on 2008-05-05
> **Shining Arcanine said:**
> It is called GDI32, rather than Winforms (that is for .NET), as I had thought. However, I would much rather use a cross-platform cross-language API for my programs, as both Swing (and Java for that matter) and GDI32 are proprietary and I do not like writing code that makes use of proprietary APIs (or proprietary languages, but my university is forcing Java on me).

I am planning to test both of my programs on both Windows and Ubuntu, which made using GTK+ preferable to using GDI32, as to my knowledge, GDI32 requires WINE on Linux, which is a can of worms that I do not want to open, especially in the context of the massive amount of time I have spent on backend code for my C++ project.

Are there any technical issues that I am missing here or should this be fairly straightforward?

You are a student? Use the tools and platform expected for assignments is my advise.

Java is not proprietary, and is open source as much as it can be at the moment. 

Wine is very good and easy to use. I never had trouble with it.

You can do anything you want, but I do suggest using what your professors expect. Knowing Java is good for jobs.

---

### Post by LaRoza on 2008-05-05
> **Shining Arcanine said:**
> 
I was mistaken then. This is much better than what I had originally thought. I am curious, given that GTK+ is used to write Gnome and Gnome is used on Ubuntu Linux, will it be much of a hassle to get QT4 working on Ubuntu Linux or will it be a simple "sudo apt-get install?"

If you have the libraries installed, it is no hassle.

---

### Post by sloggerkhan on 2008-05-05
I was just asking about this. Apparently you can make Java look gtk even if it's swing.
[http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html](http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html)
There's also a GTK for java library, but I had trouble with it. If you figure it out, please let me know. The examples had some things I didn't follow.
[http://java-gnome.sourceforge.net/](http://java-gnome.sourceforge.net/)

---

### Post by tseliot on 2008-05-05
> **Shining Arcanine said:**
> I am curious, given that GTK+ is used to write Gnome and Gnome is used on Ubuntu Linux, will it be much of a hassle to get QT4 working on Ubuntu Linux or will it be a simple "sudo apt-get install?"
Type:
```
sudo apt-get install qt4-dev-tools qt4-designer qt4-doc
```

then (just in case):
```
sudo update-alternatives --config qmake
```

and select /usr/bin/qmake-qt4

I can also recommend kdevelop (IDE)

---

### Post by Shining Arcanine on 2008-05-05
> **LaRoza said:**
> You are a student? Use the tools and platform expected for assignments is my advise.

Java is not proprietary, and is open source as much as it can be at the moment. 

Wine is very good and easy to use. I never had trouble with it.

You can do anything you want, but I do suggest using what your professors expect. Knowing Java is good for jobs.

Java is proprietary according to Bjarne Stroustrup:

[http://www.research.att.com/~bs/bs_faq.html#Java](http://www.research.att.com/~bs/bs_faq.html#Java)

> **tseliot said:**
> Type:
```
sudo apt-get install qt4-dev-tools qt4-designer qt4-doc
```

then (just in case):
```
sudo update-alternatives --config qmake
```

and select /usr/bin/qmake-qt4

I can also recommend kdevelop (IDE)

Cool, thankyou so much.

---

### Post by sloggerkhan on 2008-05-05
I was certain that iced tea java is open...
[http://en.wikipedia.org/wiki/IcedTea](http://en.wikipedia.org/wiki/IcedTea)
See wikipedia for details. I guess they still have a small % encumbered code.

---

### Post by Asham on 2008-05-05
Slightly off topic, my apologies:

In Java 6 the look and feel for GTK is pretty good. Very good actually. It has some glitches but not that many. It was much much worse prior to Java 6 so its come a long way.

I haven't seen any good lookin Java applications based on either SWT or Swing in KDE yet. :(

---

### Post by imdano on 2008-05-05
> **Shining Arcanine said:**
> Java is proprietary according to Bjarne Stroustrup:

[http://www.research.att.com/~bs/bs_faq.html#Java](http://www.research.att.com/~bs/bs_faq.html#Java)That information is out of date.  From Java's wikipedia page:
> The original and reference implementation Java compilers, virtual machines, and class libraries were developed by Sun from 1995. As of May 2007, in compliance with the specifications of the Java Community Process, Sun made available most of their Java technologies as free software under the GNU General Public License. Others have also developed alternative implementations of these Sun technologies, such as the GNU Compiler for Java and GNU Classpath.There are still a few parts of java which aren't GPL'ed yet, but they will be.

---

### Post by jespdj on 2008-05-07
If you really want to use GTK+ in Java, then did you do a Google search?

You'll find this: [http://java-gnome.sourceforge.net/](http://java-gnome.sourceforge.net/)

---

