---
title: "Best language for someone not trying to work in the industry"
date: 2008-04-27
forum: Programming Talk
---

### Post by Warpnow on 2008-04-27
I have no intention of working in the computer industry. I only want to be able to make some small programs. Hobbyist type things. So I want it to be easy to pick up, cross platform, and realtively simple.

From what I understand I have basically three options in this category: Java, RealBasic and Python.

Does anyone have any advice on which to learn?

Also...Realbasic lists itself as free for linux but you have to buy documentation to get it...what is up with that?

---

### Post by tamoneya on 2008-04-27
PYTHON.  Let me show you: [http://xkcd.com/353/](http://xkcd.com/353/)

---

### Post by Can+~ on 2008-04-27
I second python, it's multiplatform, it comes with the default ubuntu installation and with MacOS.

Open a terminal and type "python", you can get an interactive shell and do small experiments there, later you move on to building applications.

I learnt with the Alan.Gauld guide, it's pretty good (except for the colors). Download a backup of the page, since I know that site is sometimes unstable.

[http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/)

---

### Post by Warpnow on 2008-04-27
Is Python as easy to pick up and start coding with as Basic?

---

### Post by tamoneya on 2008-04-27
python is very easy and very powerful.  You can burn through the tutorial on their website in one sitting if you have previous programming experience.  Otherwise you may go a little slower and it will take you a day or two. 

[http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)

---

### Post by Can+~ on 2008-04-27
> **Warpnow said:**
> Is Python as easy to pick up and start coding with as Basic?

Start with it, see if you feel comfortable.

Some basic snippets:

The typical example:
[PHP]print "Hello world"[/PHP]

A conditional
[PHP]if condition and condition or condition:
	doSomething()[/PHP]

A list (dynamic content)
[PHP]a = [1, "hello", 3.14]
print b[2] #Prints "3.14"[/PHP]

A tuple (static content)
[PHP]b = (1, "hello", 3.14)
print b[1] #Prints "hello"[/PHP]

A dictionary
[PHP]myDict = {"key":5, "pan":"cakes" }
print myDict["pan"] # Prints cakes[/PHP]

A loop
[PHP]for i in (1, 3, 6):
	print i # Prints 1 3 6[/PHP]

---

### Post by midnightray on 2008-04-27
Shoot me down. Java, mainly due to NetBeans and its nice IDE with helpful tips for bad code (suggesting the imports etc). GUI buiding it easy and its powerful.

Out of interest, I'm learning Python so I can compare, is there a similar IDE to netbeans with colouring, helpful error messages, suggests e.g. like when you do myVar. (lists options).

---

### Post by Wybiral on 2008-04-27
> **midnightray said:**
> Shoot me down. Java, mainly due to NetBeans and its nice IDE with helpful tips for bad code (suggesting the imports etc). GUI buiding it easy and its powerful.

Out of interest, I'm learning Python so I can compare, is there a similar IDE to netbeans with colouring, helpful error messages, suggests e.g. like when you do myVar. (lists options).

Yes, eclipse with the PyDev plugin. It's pretty nice.

---

### Post by Warpnow on 2008-04-27
I've been doing some more research.

Python seems very useful...but from what I've read its much harder to develop GUI apps in python than it is in RealBasic or Java...is that the case?

The thing that annoys me about java is the roundabout way programs must be loaded into the program. RealBasic creates real execs and binaries, which is a plus.

I understand that python is BETTER than RealBasic or Java...but is it as easy to pick up and learn? I have no intention of ever taking on a large scale project. I want to do small things.

---

### Post by Can+~ on 2008-04-27
python is great for small apps.

And for GUI programming, I use GTK with the glade interface, so I make design a window in glade, then link it on Python and, that's it.

---

### Post by pmasiar on 2008-04-27
Python is EASIER to learn than Java, because of it's dynamic typing. Java's static typing and static exception checking is much clumsier. Also, Java forces you to OOP from hour 1, Python is much more flexible and intuitive.

And GUI: EasuGUI is simplest (even if lacking fancy features) GUI, bar none.

Python community is famously striving to use dynamic typing, introspection and other cool tricks (hidden inside libraries) to get you very simple and intuitive API. 

Java is for huge ('enterprisey') apps, and Basic is on it's way to become obsolete.

Read [http://www.paulgraham.com/hundred.html](http://www.paulgraham.com/hundred.html) - Language for next hundred years why.

---

### Post by WitchCraft on 2008-04-27
> **Warpnow said:**
> I've been doing some more research.

Python seems very useful...but from what I've read its much harder to develop GUI apps in python than it is in RealBasic or Java...is that the case?

The thing that annoys me about java is the roundabout way programs must be loaded into the program. RealBasic creates real execs and binaries, which is a plus.

I understand that python is BETTER than RealBasic or Java...but is it as easy to pick up and learn? I have no intention of ever taking on a large scale project. I want to do small things.


The answer is: it depends on how you do it.

When you want to program on native API's then that's going to be very difficult, because the calling structure of C and Python aren't quite the same.

However, since you want it to be cross-platform, you need to program GUI's in a toolkit. Usually, in C++, one uses wxWidgets. And wxWidgets has a binding, called wxPython, which allows you to easily write wxWidgets applications (= GUI's) in Python. It's very useful, because wxWidgets can do much more than just GUI's.

However, if you want to make full use of EVERY feature of EVERY API, you would need to learn C++, and neither Python, nor Java, nor RealBasic can do this.

I personally recommend you using Python. It's easy, has powerful libraries, works on every major platform, and you can write programs fast.

RealBasic is a piece of worthless crap (IMHO), that was primarily designed for the MacIntosh generica because of the success of Microsoft's Visual Basic, and that takes you long to start the program, and generally to do anything in it, and you won't have anything like wxWidgets, if you work across platforms with it, you will end up having Endian-issues, and if RealBasic doesn't provide a functionality, you're just stuck. And it certainly is not free of charge, and neither is it free of bugs...

Java on the other hand still has many fellowers, mainly because it's said that you can port a Java program to another platform without any additional work, and that it will work on this platform. However, AFAIK, this belongs to the empire of nice-sounding fairy-tales. I've never seen a Java program (that did more then just hello world) that actually worked on any platform without crashing either on program start, program end or right in the middle, not to mention porting a Java program to another platform, e.g. Windows, where Microsoft has been doing and is still doing its best to prevent Java from working... I personally hate Java, because it takes ages for a program to start, and because it says that Java works independent of the machine you run it, which is a lie, and that with Java you have no problems if you call a function that is only on a newer version of an OS, and not on an older one - when it simply replaces this so called version-independence by the version-dependence of the Java virtual machine... I personally have never seen a programming language that killed more IT-startups companies then Java...

So in short, I recommend Python. It's good, it's free, it's easy and it works, and it works across platforms, and it's pretty much without bugs, and with wxPython, writing GUIs is as easy as it can get. I've never seen a programming language that easy and that powerful before. Additionaly, with freeze you can compile your Python programs to C sourcecode, which can then be compiled in a native application...

---

### Post by LaRoza on 2008-04-27
> **Warpnow said:**
> I have no intention of working in the computer industry. I only want to be able to make some small programs. Hobbyist type things. So I want it to be easy to pick up, cross platform, and realtively simple.

From what I understand I have basically three options in this category: Java, RealBasic and Python.

Does anyone have any advice on which to learn?

Also...Realbasic lists itself as free for linux but you have to buy documentation to get it...what is up with that?

No Basic!

See my web site one what to learn. Since you are a hobbyiest, you have can do anything you want (just like me)

---

### Post by midnightray on 2008-04-28
> **WitchCraft said:**
> 
I've never seen a Java program (that did more then just hello world) that actually worked on any platform without crashing either on program start, program end or right in the middle, not to mention porting a Java program to another platform, e.g. Windows, where Microsoft has been doing and is still doing its best to prevent Java from working...


So wrong, at my university we are forced to use Windows machines in labs. I then can just email myself my Java writen on a WINDOWS machine and it compiles and runs perfectly on my Ubuntu laptop.
The statement is very incorrect, I for example, had to develop a secure Java chat room that had encryption, certificates, threading and used alot of the API. It works perfectly on Windows or Ubuntu. Infact, the server can be running on my Vista box and Ubuntu / Linux laptops can connect and use it.

Research before you flame a good language.

---

### Post by JudgeFudge on 2008-04-28
> **midnightray said:**
> So wrong, at my university we are forced to use Windows machines in labs. I then can just email myself my Java writen on a WINDOWS machine and it compiles and runs perfectly on my Ubuntu laptop.
The statement is very incorrect, I for example, had to develop a secure Java chat room that had encryption, certificates, threading and used alot of the API. It works perfectly on Windows or Ubuntu. Infact, the server can be running on my Vista box and Ubuntu / Linux laptops can connect and use it.

Research before you flame a good language.

Totally agree. It is standard practise in commercial programming shops to develop on Windows machines and then deploy to servers running either Windows, Unix, Linux or other (I often deploy to AS/400s). I have never had a problem due to cross platform issues (nor has anyone I work with). The only problem is with having different versions of supporting libraries (easily fixed).

Not sure how true this holds up for Swing or other Java GUI programming, but really, Java is used 99.9% of the time with server side apps with web interfaces.

---

### Post by CptPicard on 2008-04-28
> **midnightray said:**
> 
Research before you flame a good language.

Cross-platformness, esp. when desktop GUIs are excluded, and big library are indeed Java's strong points. But that's pretty much where they end.. :) Java, just as a language, is fairly uninteresting, really. And this from a guy who mostly codes professionally in Java exactly because Java is a good compromise between development speed, cross-platform compatibility and execution speed.

> **JudgeFudge said:**
> 
Not sure how true this holds up for Swing or other Java GUI programming, but really, Java is used 99.9% of the time with server side apps with web interfaces.

If you strictly limit this consideration to server side apps which have a separate web tier, yeah, EJB is pretty dominant. But then again most web apps don't separate the back-end that heavily... and in those domains, Java is just way too cumbersome a tool.

---

### Post by WitchCraft on 2008-04-28
> **JudgeFudge said:**
> Totally agree. It is standard practise in commercial programming shops to develop on Windows machines and then deploy to servers running either Windows, Unix, Linux or other (I often deploy to AS/400s). I have never had a problem due to cross platform issues (nor has anyone I work with). The only problem is with having different versions of supporting libraries (easily fixed).

Not sure how true this holds up for Swing or other Java GUI programming, but really, Java is used 99.9% of the time with server side apps with web interfaces.

OK, to everyone his opinion. I happen to know AS/400 and I must say that there isn't much graphics with AS400, meaning your program is not that much different from a "Hello World" application. If you only do text and number processing, you can as well use C, and just use the respective compiler on the other platform. That is about the same. No wounder when you don't encounter problems when doing this.

But if you do graphics, you will notice problems, with positioning, with encoding (the old UNICODE vs. ASCII vs. ANSI vs. EBCDI story)...

I personally remember best the "electronic tax" application I got a few years ago to fill in my tax declaration... 
Slow as hell (already takes 3 minutes to start up, but it's just a very simple GUI), problems with anti-virus software, not working with the firewall, problems with ANSI/ASCII/UNICODE, transmisson problems, crashing when started up for the second time, crashing on close, problems with the mouse, button is not selected when you click on it, and the list goes on and on and on and on and on... same thing with the Java e-banking program.

And these is Software from institutions you would think they have enough money to pay a decent/qualified Software company... not to mention all the disfunctional Java applets on the internet made by various amateurs. Just horrible.

In short you end-up doing it by hand again (or switching the bank in my case; unfortunately you cannot switch your tax office...). (By the way: I lived in two different states in my country, and they both have different Software for tax declaration, both of them in Java, and both had the problems mentioned above...). Ever since, I DO MY TAX DECLARATION BY HAND again.

Oh, and you cannot inject a shared library across platforms in Java. With C++ you can - across platform... Well, you guys probably never needed that.

This is MY experience with Java. If you made a different one, well, good for you.

---

