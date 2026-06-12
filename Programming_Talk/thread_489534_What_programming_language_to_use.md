---
title: "What programming language to use?"
date: 2007-07-01
forum: Programming Talk
---

### Post by Pconfig on 2007-07-01
Hey all,

I'm planning on writing a business application for my dad's company. I know there are nice packages to buy and stuff but i just want to learn how to develop bigger applications in the meanwhile. I want the application to work under both windows and Linux (Ubuntu).

Now I've been looking at a few different programming languages but i don't seem to find the right one. Or I'm looking at them in a wrong way.

C++ - Hard to build a Gui for that works under both windows and linux?
Java - Works a bit slow
Visual C++/# - Only works under windows and is memory intensive
PHP - Doesn't fully support object orientated programming and requires a web based application

Anybody has an idea what the most used language is for business applications? I need alot of flexibility, object orientated programming and something that works well with a database server.

---

### Post by gpolo on 2007-07-01
If you can't answer this yourself, it is unlikely you will be developing "bigger" applications.

---

### Post by Pconfig on 2007-07-01
Thanks for your constructive reply..

---

### Post by Smygis on 2007-07-01
"C++ - Hard to build a Gui for that works under both windows and linux?"
Not if you use wxWidgets or GTK.

"Java - Works a bit slow"
Not that slow, But its just loves your RAM.

"Visual C++/# - Only works under windows and is memory intensive"
You migt get it to work with mono.

"PHP - Doesn't fully support object orientated programming and requires a web based application"
PHP is indeed a bad choice for this.

In my opinion:
Best: Python, wx or GTK for GUI
Second: C++, wx or GTK for GUI
Third: Java

Using Python, You can write calculation intense parts of the app in C++.

---

### Post by Frosty Cold Drink on 2007-07-01
> **Pconfig said:**
> C++ - Hard to build a Gui for that works under both windows and linux?
As mentioned, wxWidgets is nice. I'd pick that over GTK.
> Java - Works a bit slow
Not true. Many serious Java programmers would beat you for saying that. Apps won't run as fast as well optimized native code, but to say Java is "slow" is just wrong. There is gcj, but I wouldn't advise that.
> Visual C++/# - Only works under windows and is memory intensive
C# can be compiled and run on Linux with Mono.
> PHP - Doesn't fully support object orientated programming and requires a web based application
PHP does not require you to make a web-based application. You could do command line or curses.

> Anybody has an idea what the most used language is for business applications? I need alot of flexibility, object orientated programming and something that works well with a database server.
C++ is the most widely used.

All these missconceptions say that you shouldn't even be asking what language to use at this point.

---

### Post by Pconfig on 2007-07-01
> **Frosty Cold Drink said:**
> 
Not true. Many serious Java programmers would beat you for saying that. Apps won't run as fast as well optimized native code, but to say Java is "slow" is just wrong. There is gcj, but I wouldn't advise that.


From my experience java programs always tend to feel a little slower then native programs. And yes, i know some major apps are build with it

> **Frosty Cold Drink said:**
> 
C# can be compiled and run on Linux with Mono.

I'm still pretty new to the whole linux scene. I didn't know that.

> **Frosty Cold Drink said:**
> 
PHP does not require you to make a web-based application. You could do command line or curses.

Ok true, But that of course isn't what I'm looking for.

I might look a little unexperienced and maybe i am. But i've got a good understanding of how object orientated programming works. I've made some small things and i've been playing around alot and i want to take my programming to a higher level. I'm sure it won't be easy to get a project of that seize off but i know i can manage it.

Anyway, thanks for the replies and I'll let you guys know which one i chose. Going to read some guides about python and wxWidgets first. The wxWidgets thing looks pretty cool.

---

### Post by brooksbp on 2007-07-01
> PHP - Doesn't fully support object orientated programming and requires a web based application

PHP _does_ support OOP - PHP5 - and does not require a web based application.  You'd be writing a web based application... but the language doesn't depend on anything.

There are a few issues with your situation here..

The first question you should be asking yourself is whether this application could be implemented as a web application.  If so, you'd save a ton of development time and may spend a little more on servers.  If you have to have a desktop application then it will take a significant ammount of time and you'll have to worry about cross-platform compatibility.  I'd rather worry about cross-browser compatability than cross-platform compatability.

If you have to write a desktop application, try to use a framework that wont make your head swell everytime you sit down to develope this thing.  Try to use a language that has already taken care of cross-platform issues for you like Python and Ruby.  Python has great GUI support and is easy to develop.

You should also consider Adobe Labs' AIR (Adobe Integrated Runtime).  This framework allows for cross-platform desktop development using familiar Adobe products and web application languages.  A pretty sweet thing.

---

### Post by pmasiar on 2007-07-01
> **Pconfig said:**
> Anybody has an idea what the most used language is for business applications? I need alot of flexibility, object orientated programming and something that works well with a database server.

You need to make up your mind about what kind of application you are going to create. The fact you consider both C++ and PHP suggest you did not decided between traditional GUI desktop program and web-based application. They are very, very different beasts, with different approaches.

That said, in both areas I would recommend to use Python: wxPython for GUI, and TurboGears or Django (depending on what kind of app you do) for web apps. Python is more flexible than PHP for web apps, but fully OO, you will be able to get app running sooner  than if using Java or C++. Yes, your app will be 2% slower in Python than in Java - but most of the time is spend in database processing, outside of your control, so even using slightly slower language will mot make measurable difference.

Python (and Ruby) are fastest in *speed to the market* sense.

You need to talk to someone responsible for IT in your dad's company, they may have some preferences for database and stuff. But if they tell you to do it in C++ or Java, ask them to do prototype in Python. It will be ready in 1/3 time needed for Java version, trust me.

---

### Post by ablegreen on 2007-07-01
> **Pconfig said:**
> 
C++ - Hard to build a Gui for that works under both windows and linux?
Java - Works a bit slow
Visual C++/# - Only works under windows and is memory intensive
PHP - Doesn't fully support object orientated programming and requires a web based application


Are you kidding? As long as the application works, that's all it matters.

---

### Post by Tomosaur on 2007-07-01
> **ablegreen said:**
> Are you kidding? As long as the application works, that's all it matters.

What if it works, but it takes fifteen minutes to load and the GUI is bright pink and orange?

---

### Post by ablegreen on 2007-07-01
> **Tomosaur said:**
> What if it works, but it takes fifteen minutes to load and the GUI is bright pink and orange?

Well we won't know until this guy tells us what kind of app he wants to dev.

---

### Post by maddog39 on 2007-07-01
> **Pconfig said:**
> Hey all,

I'm planning on writing a business application for my dad's company. I know there are nice packages to buy and stuff but i just want to learn how to develop bigger applications in the meanwhile. I want the application to work under both windows and Linux (Ubuntu).

Now I've been looking at a few different programming languages but i don't seem to find the right one. Or I'm looking at them in a wrong way.

C++ - Hard to build a Gui for that works under both windows and linux?
Java - Works a bit slow
Visual C++/# - Only works under windows and is memory intensive
PHP - Doesn't fully support object orientated programming and requires a web based application

Anybody has an idea what the most used language is for business applications? I need alot of flexibility, object orientated programming and something that works well with a database server.
Your totally off (wrong) about PHP. PHP 5 is ENTIRELY object oriented and there are Gtk+ and Qt bindings for it. All you need is php5-cli and php5-dev, doesnt need a webserver or anything. There are also OpenGL and SDL bindings as well.

[http://gtk.php.net/](http://gtk.php.net/)
[http://www.php-qt.org/](http://www.php-qt.org/)
[http://phpsdl.sourceforge.net/](http://phpsdl.sourceforge.net/)
[http://phpopengl.sourceforge.net/](http://phpopengl.sourceforge.net/)

I highly encourage the use of PHP for GUI work, I do it and its awsome.

---

### Post by laxmanb on 2007-07-02
Well... if you have  256 MB+ of RAM on the computers, use Java. It's good for business applications, there are some great dev tools, you can use Netbeans to develop the interface quickly, it's platform-agnostic, and if you use the latest Java version (6update1) on your clients., your apps will look native regardless of platform (Windowsie on Windows/GNOMEish on linux) and you always have JDBC, which is well documented and supported by all major DB vendors(MS SQL Server, MySQL, PostgreSQ, Oracle, etc.)

If your app isn't very complex you can use Java regardless of the RAM in your computers.

---

### Post by ankursethi on 2007-07-02
Java will work wonderfully, so will C#. Both of them can run on Windows as well as Linux (use GTK# with C#, not WinForms). They are both widely used in business.

But I'd say Python. It'll be much more easier for you to develop the entire thing in Python.

---

### Post by Pconfig on 2007-07-02
> **maddog39 said:**
> Your totally off (wrong) about PHP. PHP 5 is ENTIRELY object oriented and there are Gtk+ and Qt bindings for it. All you need is php5-cli and php5-dev, doesnt need a webserver or anything. There are also OpenGL and SDL bindings as well.

[http://gtk.php.net/](http://gtk.php.net/)
[http://www.php-qt.org/](http://www.php-qt.org/)
[http://phpsdl.sourceforge.net/](http://phpsdl.sourceforge.net/)
[http://phpopengl.sourceforge.net/](http://phpopengl.sourceforge.net/)

I highly encourage the use of PHP for GUI work, I do it and its awsome.

Hm last time i checked PHP lacked some features i'd like to use. I already started in php once but then WoW pulled my attention. I finally lost that addiction so i have time for useful things again. I think I'm going to check out how oop really works in php. Sorry for all those misconceptions then. Time to dive in the books again :D

Thanks for all the replies!

---

### Post by Note360 on 2007-07-02
It really depends on what you are doing. I am thinking maybe a actual web application based on a local server might be good. Every one would be able to access it with out any problems. You would just need to build in extra security measures. Also, definately speak to the IT crew. You want them to love you not hate you, they are your bosses for the most part. Basically you are a hired freelance programmer working for a company.

---

### Post by theDentist on 2007-07-02
C/C++ using wxWidgets takes a lot of beating,  Many languages seem to derive their syntax from C/C++ so it's a very good foundation. (OSs seem to be written in it, although I may be wrong and stand corrected if I am, which I am a lot these days  :( )  I use wxWidgets for most things now, but the cross - platform ability is not as straight forward as it is made out to be.

---

### Post by Praill on 2007-07-02
I agree.
Ideally running it off a web server and using PHP/CSS is going to be your guaranteed way for absolute cross platform.

If youre not able to do this java is absolutely the way to go. Dont mess with python and gtk, its just giong to make it hard to install your application on any windows machine. With java you'll just need the JRE (which most stations have) and youre good to go. Java isnt that slow, especially for your standard business application.

---

### Post by mr.farenheit on 2007-07-02
i agree with smygis on using python. there are some ways to integrate some c langouage code into python code

---

### Post by maddog39 on 2007-07-02
> **theDentist said:**
> C/C++ using wxWidgets takes a lot of beating,  Many languages seem to derive their syntax from C/C++ so it's a very good foundation. (OSs seem to be written in it, although I may be wrong and stand corrected if I am, which I am a lot these days  :( )  I use wxWidgets for most things now, but the cross - platform ability is not as straight forward as it is made out to be.
wxWidgets is a C++ only library, and isnt compatible with C.
> 
I agree.
Ideally running it off a web server and using PHP/CSS is going to be your guaranteed way for absolute cross platform.

If youre not able to do this java is absolutely the way to go. Dont mess with python and gtk, its just giong to make it hard to install your application on any windows machine. With java you'll just need the JRE (which most stations have) and youre good to go. Java isnt that slow, especially for your standard business application.

Thats true, a web based interface is going to be the most cross platform. Java can be a slight problem on linux for some people, and Gtk is not very windows friendly (i've tried).

---

### Post by ablegreen on 2007-07-02
Ya seems like most enterprise apps nowadays are on the web.

---

### Post by slavik on 2007-07-03
> **Praill said:**
> I agree.
Ideally running it off a web server and using PHP/CSS is going to be your guaranteed way for absolute cross platform.

If youre not able to do this java is absolutely the way to go. Dont mess with python and gtk, its just giong to make it hard to install your application on any windows machine. With java you'll just need the JRE (which most stations have) and youre good to go. Java isnt that slow, especially for your standard business application.
Yes, especially when 1 person uses IE6, secon IE7 and third is Firefox ... good luck with that ;)

---

### Post by runningwithscissors on 2007-07-03
Python with PyGTK for the GUI library.

It's no fun making desktop apps with Java.

On the other hand, if you don't know any Python at all, I'd say you should start working with whatever you know best.

---

### Post by Praill on 2007-07-03
> **slavik said:**
> Yes, especially when 1 person uses IE6, secon IE7 and third is Firefox ... good luck with that ;)
If you want to be a CSS nazi then ya... look out. Using a standard table layout with old school inline CSS is supported browser-wide since the dark ages though. Most business apps will take this approach to simply save time.

---

