---
title: "Any way to compile a Java program to an exe?"
date: 2008-07-11
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-07-11
I need to develop a program which will be used on several computers.  I am most comfortable programming it in Java although I could also do it in C++.  But it would either be more basic (command based instead of GUI) or I would have to figure out how to do GUI programming (Windows Environment) using C++.  I am most comfortable with Java and Swing, that's why I was wondering if it was possible to compile the Java program to an executable that does not require the Java Runtime environment.  I guess if the executable turns out to be as big as the Java Runtime Environment (~30 MB) that would be ok for this purpose.  Otherwise, anyone have any recommendations for GUI programming framework in Windows?  Eclipse comes to mind, but I think that might take a while to pickup...I think that's still Java though.

---

### Post by LaRoza on 2008-07-11
> **SNYP40A1 said:**
> I need to develop a program which will be used on several computers.  I am most comfortable programming it in Java although I could also do it in C++.  But it would either be more basic (command based instead of GUI) or I would have to figure out how to do GUI programming (Windows Environment) using C++.  I am most comfortable with Java and Swing, that's why I was wondering if it was possible to compile the Java program to an executable that does not require the Java Runtime environment.  I guess if the executable turns out to be as big as the Java Runtime Environment (~30 MB) that would be ok for this purpose. 


[http://www.excelsior-usa.com/articles/java-to-exe.html](http://www.excelsior-usa.com/articles/java-to-exe.html)

Is your wish to not have the JRE a requirement or just a preference?

---

### Post by CptPicard on 2008-07-11
> **SNYP40A1 said:**
> I need to develop a program which will be used on several computers.

I take it this means cross-platform. Therefore, use Java.

> I am most comfortable programming it in Java although I could also do it in C++.  But it would either be more basic (command based instead of GUI) or I would have to figure out how to do GUI programming (Windows Environment) using C++.

Why? Does not sound you are actually very comfortable with Java if you can't use Swing to get your app cross-platform.

> I am most comfortable with Java and Swing

Good. Use Swing and require the JRE.

> that's why I was wondering if it was possible to compile the Java program to an executable that does not require the Java Runtime environment.

Why? You really should. Compiling everything into an exe us a totally ugly hack that is not recommended for anything really.

> Otherwise, anyone have any recommendations for GUI programming framework in Windows?

Swing. On the JRE.

> Eclipse comes to mind, but I think that might take a while to pickup...I think that's still Java though.

That's SWT with the Eclipse Rich Client framework, which is not necessarily any more Windows-specific. Do you really want to compile into your .exe both Eclipse and the JRE? :)

---

### Post by jespdj on 2008-07-11
> **SNYP40A1 said:**
> ... I was wondering if it was possible to compile the Java program to an executable that does not require the Java Runtime environment.  I guess if the executable turns out to be as big as the Java Runtime Environment (~30 MB) that would be ok for this purpose.
No, you cannot run a Java program without a Java runtime environment. That's like trying to drive a car without an engine in it. The download size for the latest Sun Java 6 JRE for Windows is about 15 MB, not 30 MB.

What you could do is use an installer for your program that installs the JRE if the user doesn't already have it. Have a look at this [list of open source installer generators for Java](http://java-source.net/open-source/installer-generators).

Eclipse is written in Java, but it doesn't use Swing but SWT, which is its own widget toolkit, that needs native libraries.

---

### Post by SNYP40A1 on 2008-07-11
Sorry, I did not explain my requirements fully.  The constraint is that the program needs to be run from about 30-40 different computers, all networked.  I don't care about cross-platform, using Windows only.  However, I have only done GUIs in Swing...well, Swing and .NET in Visual Studio.  I don't have any experience creating programs with GUIs in C++.  I could learn, but this might be a one-time only type of thing and I have other things I need to program as well.  So Swing / Java will do everything I need to do, but I don't want to go around to these 30-40 computers and install Java.  Also, the computers are locked down and I would not have permissions to install Java on them myself, would need to get the help of IT.  Compiling the Java runtime into an EXE is a bit of a messy hack.  But in this case, I would rather have a 30 MB program that took me 1 hour to make than a 30 kb program that took me a day to make.

---

### Post by LaRoza on 2008-07-11
> **SNYP40A1 said:**
> Sorry, I did not explain my requirements fully.  The constraint is that the program needs to be run from about 30-40 different computers, all networked.  I don't care about cross-platform, using Windows only.  However, I have only done GUIs in Swing...well, Swing and .NET in Visual Studio.  I don't have any experience creating programs with GUIs in C++. 
You can use VS to make them (I think) or you can use wxWidgets and its GUI builder (see sticky) for C++.

---

### Post by tinny on 2008-07-11
Publish your application to a web server on your LAN by using [Java Web Start]("http://java.sun.com/products/javawebstart/"). DONE!

> 
You can use VS to make them (I think) or you can use wxWidgets and its GUI builder (see sticky) for C++.


With the full version of VS yes you can. If you are using VS Express this feature is turned off :(

---

### Post by Dancingwllamas on 2008-07-11
You may also want to try [Avian](oss.readytalk.com) to create self contained exe's. I haven't tried it myself, but I know a few people who have had success with it.

---

### Post by SNYP40A1 on 2008-07-12
> **Dancingwllamas said:**
> You may also want to try [Avian](oss.readytalk.com) to create self contained exe's. I haven't tried it myself, but I know a few people who have had success with it.

Avian looks interesting.  I will check it out.  I have VS, but not so much experience programming C++ GUIs.

---

### Post by tosk on 2008-07-13
Yes, it is possible to compile Java bytecode into native executables which do not require the JRE. You can even do Swing.

See: [http://www.thisiscool.com/gcc_mingw.htm](http://www.thisiscool.com/gcc_mingw.htm)

---

### Post by SNYP40A1 on 2008-08-05
I have not fully looked into it yet, but this might be the answer:

[http://gcc.gnu.org/java/](http://gcc.gnu.org/java/)

---

