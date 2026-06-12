---
title: "Why aren't more Linux applications written in Java?"
date: 2013-05-23
forum: Programming Talk
---

### Post by WinterMadness on 2013-05-23
Just curious, being that its cross platform, wouldn't that solve a lot of compatibility issues? Moreover, if more programs were written in Java (including those on Windows and Mac) wouldn't it help Linux users as well? why don't more people use Java so they don't have to port things as much?

I know some people dont like Java for various reasons, many of which I agree and disagree with, but the JVM can be helpful. I dont think it slows things down enough to consider speed an issue.

Please answer every question I present if you are able to. Thanks!

---

### Post by xb12x on 2013-05-23
> **WinterMadness said:**
> Just curious, being that its cross platform, wouldn't that solve a lot of compatibility issues? Moreover, if more programs were written in Java (including those on Windows and Mac) wouldn't it help Linux users as well? why don't more people use Java so they don't have to port things as much?

I know some people dont like Java for various reasons, many of which I agree and disagree with, but the JVM can be helpful. I dont think it slows things down enough to consider speed an issue.

Please answer every question I present if you are able to. Thanks!


There are others that are also cross platform. Python is my current favorite.

---

### Post by DaviesX on 2013-05-23
I am not fond of the Java syntax and some other limitations personally. 

> [COLOR=#000000] I dont think it slows things down enough to consider speed an issue.[/COLOR]
A Codecs, renderer, or any low-level library couldn't sustain any slow down, since linux is not only for desktop, there are programs that requires massive computation. 
And it is not good enough for an application either. X11 isn't quite fast already, and Swing for GUI programming is pretty slow, which make it even worst. 

I think Gtk with Glade designer and with c/c++ can handle GUI pretty easily in most cases.

---

### Post by Leuchten on 2013-05-23
> **DaviesX said:**
> I am not fond of the Java syntax and some other limitations personally. 


A Codecs, renderer, or any low-level library couldn't sustain any slow down, since linux is not only for desktop, there are programs that requires massive computation. 
And it is not good enough for an application either. X11 isn't quite fast already, and Swing for GUI programming is pretty slow, which make it even worst. 

I think Gtk with Glade designer and with c/c++ can handle GUI pretty easily in most cases.


You might try the new javafx out (or scalafx with scala). Also, my lab uses java for massive computation purposes.

---

### Post by King Dude on 2013-05-23
It's just the way things are I suppose.

---

### Post by dibakarm on 2013-05-24
Because it makes a site nice.

---

### Post by ehrt74 on 2013-05-24
> **xb12x said:**
> There are others that are also cross platform. Python is my current favorite.


As far as I know, python doesn't have its own windowing system and widgets. Java does (swing).

---

### Post by alan9800 on 2013-05-24
> **ehrt74 said:**
> As far as I know, python doesn't have its own windowing system and widgets. Java does (swing).in python you may use:
[LIST]
[*][the window manager]("http://docs.python.org/release/2.7.3/library/tkinter.html#the-window-manager") available in the Tkinter module; 
[*][the ttk module]("http://docs.python.org/release/2.7.3/library/ttk.html") for widgets. 
[/LIST]

---

### Post by diesch on 2013-05-24
[LIST]
[*]SWING doesn't support much desktop integration for GUI apps
[*]often bad support for low level system functions and native libs
[*]long startup time
[/LIST]

---

### Post by trent.josephsen on 2013-05-24
C'mon, we all know the real reason nobody uses Swing -- it's hideous.

Other languages have (as it seems to me) better support for other windowing toolkits, which is big. Huge, really. There's no reason to limit yourself to Swing when using Java, but if you're not bound to Swing, you're not bound to Java either.

---

### Post by nvteighen on 2013-05-24
Java is actually quite limited in what you can do with it. Think of memory resources: you just shouldn't write a service running on Java if you can get the same thing written in Python with a much smaller memory/CPU footprint. Java is good for standalone programs, defining "standalone" as "stuff that doesn't require interoperation with other stuff", like apps in Android (which is Linux, by the way). But, as soon as you require/want to implement your functionality in some way that may be shared by other applications (in the true UNIX-way), Java is not what you want. If you take a look at most programs you have installed in your system, you'll realize that most of them are designed for interoperability, such that the real functionality is implemented in a C or C++ shared library, which you can link to from many languages (or write a binding, if needed). Hell, you can even call Python code from C and C++!

---

### Post by Leuchten on 2013-05-24
> **trent.josephsen said:**
> C'mon, we all know the real reason nobody uses Swing -- it's hideous.

Other languages have (as it seems to me) better support for other windowing toolkits, which is big. Huge, really. There's no reason to limit yourself to Swing when using Java, but if you're not bound to Swing, you're not bound to Java either.

Java has other java based toolkits available to it, such as SWT, [Pivot]("http://pivot.apache.org/demos/kitchen-sink.html"), and [JavaFX2]("http://www.javaworld.com/javaworld/jw-03-2012/120306-practical-javafx2-1.html?page=1")

> **nvteighen said:**
> Java is actually quite limited in what you can do with it. Think of memory resources: you just shouldn't write a service running on Java if you can get the same thing written in Python with a much smaller memory/CPU footprint. Java is good for standalone programs, defining "standalone" as "stuff that doesn't require interoperation with other stuff", like apps in Android (which is Linux, by the way). But, as soon as you require/want to implement your functionality in some way that may be shared by other applications (in the true UNIX-way), Java is not what you want. If you take a look at most programs you have installed in your system, you'll realize that most of them are designed for interoperability, such that the real functionality is implemented in a C or C++ shared library, which you can link to from many languages (or write a binding, if needed). Hell, you can even call Python code from C and C++!

[http://benchmarksgame.alioth.debian.org/u64q/benchmark.php?test=all&lang=java&lang2=python3&data=u64q](http://benchmarksgame.alioth.debian.org/u64q/benchmark.php?test=all&lang=java&lang2=python3&data=u64q)

Just to clarify this, Python uses less memory than java in general when both are hardly doing any allocations. Java takes about 17000KB just to load the VM into memory, so when you get into ultra small applications,  python's lighterweight vm will always pull out ahead on memory usage (jigsaw should change this though). On the other side of things, java tends to win on memory use as more is needed. As for your cpu footprint, I've never seen any evidence that python is less cpu intensive than java. I've seen plenty of evidence that it is many times more intensive than java though.

As for interoperability, I'm not sure what you mean. Java can interoperate with other programs like shell programs do (piping input in/out), and it's dead easy to write network binding code for java. You can also call Java code from C or C++ and embed a jvm in your c or c++ code. Python and other languages that need to access jvm libraries can use the same methods c uses to access them.

---

### Post by ofnuts on 2013-05-24
> **trent.josephsen said:**
> C'mon, we all know the real reason nobody uses Swing -- it's hideous.

Yes, but it can be made to look much better with little effort...

---

### Post by ofnuts on 2013-05-24
> **nvteighen said:**
> Java is actually quite limited in what you can do with it. Think of memory resources: you just shouldn't write a service running on Java if you can get the same thing written in Python with a much smaller memory/CPU footprint. Java is good for standalone programs, defining "standalone" as "stuff that doesn't require interoperation with other stuff", like apps in Android (which is Linux, by the way). But, as soon as you require/want to implement your functionality in some way that may be shared by other applications (in the true UNIX-way), Java is not what you want. If you take a look at most programs you have installed in your system, you'll realize that most of them are designed for interoperability, such that the real functionality is implemented in a C or C++ shared library, which you can link to from many languages (or write a binding, if needed). Hell, you can even call Python code from C and C++!

Java can be [interfaced both ways with C/C++ bindings](http://en.wikipedia.org/wiki/Java_Native_Interface)

---

### Post by nvteighen on 2013-05-24
OK, I stand corrected :-)

---

### Post by ofnuts on 2013-05-24
> **WinterMadness said:**
> Just curious, being that its cross platform, wouldn't that solve a lot of compatibility issues? Moreover, if more programs were written in Java (including those on Windows and Mac) wouldn't it help Linux users as well? why don't more people use Java so they don't have to port things as much?

I know some people dont like Java for various reasons, many of which I agree and disagree with, but the JVM can be helpful. I dont think it slows things down enough to consider speed an issue.

Please answer every question I present if you are able to. Thanks!

1) because an app written in Java usually ceases to be a "Linux" or "Windows" application, but becomes a "Java application" that runs on both (plus OSX)...

2) because your sample of applications is small. There are plenty of applications out there that you'll never see because they are in-house apps.

3) because the current trend is to deliver all multi-platform apps through a browser instead of having a "thick client", so you don't see the Java, which remains on the server side(*).

4) because people that sell commercial apps may not want to be burdened with the licensing of the Java runtime.

5) because people that sell commercial apps think their code isn't protected well enough (Java is easy to decompile and there is only so much you can do with obfuscators)

6) because with a little care and the adequate graphics library, you can write applications (even very graphics-intensive ones) for several platforms (even if these usually don't include Linux)(see Photoshop... and Gimp).
 

(*) In your daily browsing, you likely interact with a dozen of Java-based servers... A vast majority of them run on Linux... using a Java code was developed/tested on Windows workstations....

---

### Post by shalomshachne on 2013-05-24
Java's biggest weakness is that it is hard to build GUI/Desktop applications to the standard that other Desktop apps have.  That said, for non-GUI applications it is extremely portable.  I develop on Windows and run on Linux, and have never run into any compatibility issues. Compile once run every where, really. We run extremely low latency application (in 50-100 microsecond range), without a problem in Java, so speed is not an issue.

It's the GUI... always the GUI.

---

### Post by Leuchten on 2013-05-24
Sounding a bit like a broken record here, but have you tried the new javafx? It's pretty much intended to replace swing, doesn't focus on Native look&feel anymore, and is much easier to write UIs in than swing ever was. Here is the feature list:

> [COLOR=#333333][FONT=Verdana]
[LIST]
[*]**Java APIs**. JavaFX is a Java library that consists of classes and interfaces that are written in native Java code. The APIs are designed to be a friendly alternative to Java Virtual Machine (Java VM) languages, such as JRuby and Scala.

[*]**FXML and Scene Builder**. FXML is an XML-based declarative markup language for constructing a JavaFX application user interface. A designer can code in FXML or use JavaFX Scene Builder to interactively design the graphical user interface (GUI). Scene Builder generates FXML markup that can be ported to an IDE where a developer can add the business logic.

[*]**WebView**. A web component that uses WebKitHTML technology to make it possible to embed web pages within a JavaFX application. JavaScript running in WebView can call Java APIs, and Java APIs can call JavaScript running in WebView.

[*]**Swing interoperability**. Existing Swing applications can be updated with new JavaFX features, such as rich graphics media playback and embedded Web content.

[*]**Built-in UI controls** **and CSS**. JavaFX provides all the major UI controls required to develop a full-featured application. Components can be skinned with standard Web technologies such as CSS

[*]**Canvas API**. The Canvas API enables drawing directly within an area of the JavaFX scene that consists of one graphical element (node).

[*]**Multitouch Support**. JavaFX provides support for multitouch operations, based on the capabilities of the underlying platform.

[*]**Hardware-accelerated graphics pipeline**. JavaFX graphics are based on the graphics rendering pipeline (Prism). JavaFX offers smooth graphics that render quickly through Prism when it is used with a supported graphics card or graphics processing unit (GPU). If a system does not feature one of the recommended GPUs supported by JavaFX, then Prism defaults to the Java 2D software stack.

[*]**High-performance media engine**. The media pipeline supports the playback of web multimedia content. It provides a stable, low-latency media framework that is based on the GStreamer multimedia framework.

[*]**Self-contained application deployment** **model**. Self-contained application packages have all of the application resources and a private copy of the Java and JavaFX runtimes. They are distributed as native installable packages and provide the same installation and launch experience as native applications for that operating system. See the [Deploying JavaFX Applications]("http://docs.oracle.com/javafx/2/deployment/jfxpub-deployment.htm") document.

[/LIST]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana][/FONT][/COLOR][COLOR=#333333][FONT=Verdana][/FONT][/COLOR]

---

### Post by KdotJ on 2013-05-24
Another reason, is that many people (including this forum) lead other people to believe that you shouldn't use java. 

When new comers arrive in the land of Linux through the typical channels (such as trying out Ubuntu), they come to forums and are bombarded with how they should use python. Python is king. Python rules all. To use java, you have to install the jdk... yuck. Python comes already installed, it must be better.

This gets passed down. The next flock of people join the Linux world, and are given the same information.

Now I personally love Python,  but I've nothing against java and I use it on a day to day basis. 

Sometimes I can't help but wonder if many of these people have actually ever had exposure to large enterprise scale systems that are used in the real world. Java is everywhere... there are hundreds of  thousands of Linux boxes all running Java processes and serverside code.


This is just my opinion, of course, but I'm bored of the java hate.

---

### Post by trent.josephsen on 2013-05-24
Perhaps you haven't noticed that most people don't come to this forum looking for the best way for an experienced programmer to build large enterprise scale applications.

---

### Post by KdotJ on 2013-05-24
Agreed. My post did not intend to sound like people should use Java instead. By all means people should use the right tool for the job.

However, I think people shouldn't say things like "Java is not used on Linux very much" like its a fact, if they are not aware.

---

### Post by WinterMadness on 2013-05-24
Yeah, as far as python goes, I dont like the fact that it doesnt have traditional data types, or isnt strongly typed. Its not that big of a deal, but its a big enough deal to make me use Java for quick applications.

Java's biggest problem for me is that is tries so hard to avoid pointers. There comes a time when you realize pointers are just flat out necessary.

---

### Post by Leuchten on 2013-05-24
True enough, but that doesn't explain the java hate well. Personally I think java is hated on because of what it was in the earlier days, mixed with a dash of being stuck on 1.6 for years. Things are looking better nowadays with java getting lambdas with closures, project jigsaw, the alternative jvm languages and more.

---

### Post by diesch on 2013-05-24
> **Leuchten said:**
> Sounding a bit like a broken record here, but have you tried the new javafx? It's pretty much intended to replace swing, doesn't focus on Native look&feel anymore, and is much easier to write UIs in than swing ever was. 


I think this attitude is actually part of the problem: Users usually actually want a program to support native look & feel as much as possible. Of course thatás m,ore work for a programmer if one wants to be cross-plattform

---

### Post by Leuchten on 2013-05-24
The problem with what exactly? Java focused on native L&F for years and years and years. [JavaFX2 apparently supports native L&F for windows 7 and mac osx,]("http://www.youtube.com/watch?v=xn4avhG8DGU") but [it also has a default look and feel that doesn't look like absolute trash.]("http://www.youtube.com/watch?v=o-iRc9XkgZ0")

Likewise, gtk is crossplatform but doesn't appear to even attempt native look and feel.

I think the problem with swing in the past is that it spent too much time trying to camouflage itself as a native app and not enough time making sure it actually looked good on all platforms.

---

### Post by Vaphell on 2013-05-24
java programs are also annoying because more often than not they require specific version of java than needs to be installed separately, some specific combination of parameters to run (there are tons of threads asking what to do to give minecraft more memory) not to mention you hear all the time about yet another critical security flaw in java.

---

### Post by Leuchten on 2013-05-24
First off, unless something amazing has happened, the security flaws are all in java applets, which is not a huge problem for linux users since you have to manually install the iced-tea plugin alongside the jvm.

Second off, what applications require a specific version of the jvm?  The closest thing I've ever seen is intellij asking for the oracle jvm to be installed instead of openjdk, and that isn't anywhere near necessary.

Minecraft should have a larger max heap size if it's users are getting out of memory errors, but my girlfriend has never mentioned OOM error crashes.

---

### Post by trent.josephsen on 2013-05-24
Ok, I'll be honest. I don't know why other people don't use Java. But as for why I don't use Java? I think it's a horrible, brain-damaged concentration camp of an excuse for a language and the only possible use for it is mitigating the damage that incompetent programmers can do to an established code base. (A use, I will concede, at which it is particularly good.) In particular, the way Java encourages you to solve every single problem by making a new object is incredibly stupid and flies in the face of good design.

The fact of the matter is, though, that I'm a lone amateur when it comes to software, and I can make these criticisms from my armchair. I don't have to train an army of recent CS graduates and interns, most of whom know everything there is to know about big-O notation and next to nothing about architecture or test engineering, into a team of developers that is somehow an asset that helps my company make money. I don't risk losing my job if HR sends me a bunch of unqualified candidates and my boss blames the failure of the project on the fact that I picked "that new language" instead of the "safe" option. I have the luxury of picking the one language I like best with full knowledge that it can only improve my chances of successfully completing my project. And I have the nerve to criticize languages I don't like for implementing features I don't need! Sometimes I shock myself.

(This post is not intended to reflect negatively on any person.)

---

### Post by WitchCraft on 2013-05-24
What do you mean by "applications" ?
First, it doesn't make a lot of sense to write applications in Java, because of Java's long loading time.
The other reason why Java programs aren't good is, Java starts using your entire RAM until there is no more free RAM, and only then will it garbage collect. 
Basically, it's what i would call a "giant memory leak", except that it isn't a leak, it's by design. 
Using all the available RAM might be very good for that one Java application, but it can crash or render unusable any other application that runs at the same time.
And on a computer with low specs, the performance of even running only that one single program will be miserable, to say the least.

Another reason is the "write once, run anywhere" motto. 
That certainly sounds very nice, but in reality it's more like "write once, debug everywhere".
Inappropriate use of codepages (especially in Java applets on the web).
Who doesn't like buttons where you can't read the text ?
I've never seen a Java program that run flawlessly without some tweaking by the user. taskbar.

Take Linux as example. 
When you ran the apt-get installer (when there were still java packages), you still couldn't run Java programs, because the JAVA_HOME environment variable wasn't set. 
Very funny, so the user has to figure out where the hell the JAVA_HOME is, and how the hell to get that into the environment settings.
Certainly not an action that the average garden-variety user perhaps with even questionable english as a foreign language skills is capable of.

Today, you have to figure out how to install java yourself, or you have to figure out how you can add the partner repository to your apt-get list.

On Windows, you have to install Oracle java, and if it isn't installed, the java program won't run out of the box.
Back in the past, downloading the appropriate Java version for your computer was a pain in the ass.
Now it has gotten a bit better, but it's bundled with an annying ask browserbar.
Then, always security updates which don't install themselfs automatically if the user doesn't have administrator rights. 


Then, the GUI of java programs is completely antiquated. 
Who wants a program with gray-and-white menu bars with no gradient, and odd looking symbols ? 
You can't present that, it looks too bad, you can't sell it (because how it looks is the only thing people judge your program before they buy it).


Then there is the version nightmare, and libraries prerequisites, which are sometimes simply missing.

That said, Java is good for dedicated server programs.
The variety where your java program is the only one running on the server, a server with high specs.
Such as a cassandra database server, or a web application running on tomcat.
And that's where it is very successful. 
But on the desktop, java has been dead for ages.
The only reason why java desktop applications still exist, is, that it is taught at universities, and sometimes, there are some more complex special purpose tools that are not available in unmanaged code (C/C++).

---

### Post by KdotJ on 2013-05-24
> **WitchCraft said:**
>  
When you ran the apt-get installer (when there were still java packages), you still couldn't run Java programs, because the JAVA_HOME environment variable wasn't set. 
Very funny, so the user has to figure out where the hell the JAVA_HOME is, and how the hell to get that into the environment settings.
Certainly not an action that the average garden-variety user perhaps with even questionable english as a foreign language skills is capable of.


This has nothing to do with Java. 

There are plenty of package managers thats set JAVA_HOME for you after installing Java. Crunchbang Linux is one such as example... oh yeah and that's using apt-get.

If you have issues setting a path variable, that means you need a better understanding of it. Environment variables are a different matter altogether, not one you can use as an argument against Java.

---

### Post by Leuchten on 2013-05-24
> **WitchCraft said:**
> What do you mean by "applications" ?
First, it doesn't make a lot of sense to write applications in Java, because of Java's long loading time.
The other reason why Java programs aren't good is, Java starts using your entire RAM until there is no more free RAM, and only then will it garbage collect. 
Basically, it's what i would call a "giant memory leak", except that it isn't a leak, it's by design. 
Using all the available RAM might be very good for that one Java application, but it can crash or render unusable any other application that runs at the same time.
And on a computer with low specs, the performance of even running only that one single program will be miserable, to say the least.

This is a really gross simplification of how the garbage collector in java works. [This post on stack overflow]("http://stackoverflow.com/a/1582298") describes how the generational garbage collectors of java 1.6 and 1.7 work.

> Another reason is the "write once, run anywhere" motto. 
That certainly sounds very nice, but in reality it's more like "write once, debug everywhere".
Inappropriate use of codepages (especially in Java applets on the web).
Who doesn't like buttons where you can't read the text ?
I've never seen a Java program that run flawlessly without some tweaking by the user. taskbar.

Can't speak for applets, but I've not heard any complaints about how my company's applications work.


> Then, the GUI of java programs is completely antiquated. 
Who wants a program with gray-and-white menu bars with no gradient, and odd looking symbols ? 
You can't present that, it looks too bad, you can't sell it (because how it looks is the only thing people judge your program before they buy it).

JavaFX2. I've been name-dropping it all over the thread.


> Then there is the version nightmare, and libraries prerequisites, which are sometimes simply missing.

Maven, gradle, and sbt all handle this gracefully.

> But on the desktop, java has been dead for ages.
The only reason why java desktop applications still exist, is, that it is taught at universities, and sometimes, there are some more complex special purpose tools that are not available in unmanaged code (C/C++).

Been a lot of uptick in java based games recently.

> Take Linux as example. 
When you ran the apt-get installer (when there were still java packages), you still couldn't run Java programs, because the JAVA_HOME environment variable wasn't set. 
Very funny, so the user has to figure out where the hell the JAVA_HOME is, and how the hell to get that into the environment settings.
Certainly not an action that the average garden-variety user perhaps with even questionable english as a foreign language skills is capable of.

Today, you have to figure out how to install java yourself, or you have to figure out how you can add the partner repository to your apt-get list.


There are java packages in every major distro, including ubuntu. [You just need to install the openjdk packages.]("https://help.ubuntu.com/community/Java") Also, apt-get not setting JAVA_HOME when java is installed is not java's fault.

---

### Post by ofnuts on 2013-05-25
> **WinterMadness said:**
> Yeah, as far as python goes, I dont like the fact that it doesnt have traditional data types, or isnt strongly typed. Its not that big of a deal, but its a big enough deal to make me use Java for quick applications..
Funny you say that because the strength of Python lies in the quick applications. I do develop/maintain enterprise-grade servers in Java but sometimes I need to write quick code for tests, debug or log analysis and Python is a lot faster.

---

### Post by ofnuts on 2013-05-25
> **trent.josephsen said:**
> Ok, I'll be honest. I don't know why other people don't use Java. But as for why I don't use Java? I think it's a horrible, brain-damaged concentration camp of an excuse for a language and the only possible use for it is mitigating the damage that incompetent programmers can do to an established code base. (A use, I will concede, at which it is particularly good.) In particular, the way Java encourages you to solve every single problem by making a new object is incredibly stupid and flies in the face of good design.

Well, I sort of agree with the idea that Java attracts the less gifted programmers or at least makes its easier for them to <cough>write code</cough> and is more or less advertised as such. But of course writing code is about 25% of the actual developer's work, and Java does nothing to help these people with the remaining 75%.

At the other end of the spectrum there is also a lot of intellectual M10N going on and with the usual frameworks you can't have your first line of output without creating two factories, three layers of "implementation" classes (all of these having all private attributes exposed through public getters and setters) and hooking everything together through an 18KB XML file (*) (just in case  you may one day have to relocate one service on a server in Kazakhstan) with the dubious advantage that your typos, instead of being caught by the compiler, are now translated into strange run-time errors that show up after 10 minutes of server startup.  

The problem with Java isn't the language, it's the users :)

On the other hand, for enterprise grade development, it's part of an "ecosystem" with so many professional-grade open-source tools (units tests, profiling, code coverage, builds, continuous integration, deployment) that it's hard to disregard.

(*) French programmers call it the JPQD framework, where JPQD stands for "J'y Pige Que Dalle" (French slang for "I don't understand anything")

---

### Post by r-senior on 2013-05-25
Java was certainly designed as a simpler alternative to C++ but I don't think it *attracts* less gifted programmers so much as it tends to be a natural choice for in-house business applications -- an environment where large numbers of less committed programmers survive and there's often a horrible legacy of staff turnover and change of direction. These programmers know the business rules and can take advantage of the availability of frameworks to implement them in Java (or C# for that matter) but their managers don't want them to become gifted programmers as much as they want their projects delivered with short-term goals. The frameworks do at least encourage some element of good design but, as you say, it's common for programmers to fall into a JPQD mode. The gifted programmers are usually gifted because of some outside interest, not from the daily grind.

---

### Post by ofnuts on 2013-05-25
> **r-senior said:**
> Java was certainly designed as a simpler alternative to C++ but I don't think it *attracts* less gifted programmers so much as it tends to be a natural choice for in-house business applications -- an environment where large numbers of less committed programmers survive and there's often a horrible legacy of staff turnover and change of direction. These programmers know the business rules and can take advantage of the availability of frameworks to implement them in Java (or C# for that matter) but their managers don't want them to become gifted programmers as much as they want their projects delivered with short-term goals. The frameworks do at least encourage some element of good design but, as you say, it's common for programmers to fall into a JPQD mode. The gifted programmers are usually gifted because of some outside interest, not from the daily grind.
I'm on the other side of the fence (contracting) and the external programmers aren't that much better. When you replace "delivered" by "delivered and working" the skills of the programmers start to make a difference, and the customer also looks at "working". and if over time you want to achieve "working nicely" it's even more important.

The frameworks more often than not also lead to over-design.

---

### Post by Bufeu on 2013-05-26
Short answer:
C is faster and takes less memory.

---

### Post by KdotJ on 2013-05-26
> **Bufeu said:**
> Short answer:
C is faster and takes less memory.

Lol oh dear. 

Now there's a "insert template response" reply if I ever saw one...

---

### Post by CptPicard on 2013-05-26
> **WinterMadness said:**
> Yeah, as far as python goes, I dont like the fact that it doesnt have traditional data types, or isnt strongly typed.

It is strongly typed. An integer is an integer and if you try to use it as anything else, you get a runtime error. What Python is not is statically typed, that is, you do not declare the type (except when constructing the object). 

> 
Java's biggest problem for me is that is tries so hard to avoid pointers. There comes a time when you realize pointers are just flat out necessary.

I would be curious to hear a case of where a pointer is actually necessary in the abstract program design sense, excluding practicalities such as a need to occasionally address memory as it is and the like. As far as abstractions go, a pointer is just a value used for indirection... and a very machine-level, specific concept as such. Indexing into an array is not any different.

---

### Post by slickymaster on 2013-05-27
Java and Linux complement each other nicely. Linux is a stable, powerful OS similar enough in design and other aspects to Sun's own Solaris, and Linux is certainly popular (if not most popular) as a server OS, so it and Java have the server side of things in common as well.
Java brings a lot to this. It's a powerful language and platform, with thorough UI and data structure class libraries. And though the Java hype has somewhat died down, it's still attracting a lot of attention, especially in large corporations.
Developers who are interested in Linux and want to experiment with it can easily be overwhelmed by the typical Linux distribution's development packages. If a developer has no Linux or Unix experience, or if his Unix background comes from dial-up connections in the early 80s, it's a pretty big hill to climb from Linux novice to proficient Linux developer. A Java developer, on the other hand, has to learn less. Yes, there's still the OS itself to conquer, but the development tools and conventions are almost identical to what he's used to on Windows or any other OS with a JDK. Rather than facing a mountain, a Java developer approaching Linux faces a few small hills, resulting in a much smoother and faster "out of the box experience."
There are good reasons for Java and Linux to get together. Are there reasons they shouldn't? Well, Java still has its own personal issues to deal with, like client-side performance and bugs.
Java is currently lacking a critical mass of support from the Linux community. Critical mass is what makes open-source software development work. There's definitely a bias for C (and C++, though to a much lesser extent) in the Linux world because that's what so much of the OS and the GNU tools are written in. Java developers need to create their own critical mass of Java/Linux support and be prepared to be treated as second or third-class Linux citizens until it happens.

---

### Post by WinterMadness on 2013-05-28
> **CptPicard said:**
> It is strongly typed. An integer is an integer and if you try to use it as anything else, you get a runtime error. What Python is not is statically typed, that is, you do not declare the type (except when constructing the object). 



I would be curious to hear a case of where a pointer is actually necessary in the abstract program design sense, excluding practicalities such as a need to occasionally address memory as it is and the like. As far as abstractions go, a pointer is just a value used for indirection... and a very machine-level, specific concept as such. Indexing into an array is not any different.


The reason I like pointers is because when you create data structures, they make a lot of sense. You can have Java handle the pointers for you, but for me, its just easier to think about with pointers, and I know what I'm getting into. My complaint about Java is pretty much subjective.

---

### Post by r-senior on 2013-05-28
Most of the time, at the level Java is typically written, a Java programmer would not create their own data structures, they would take advantage of those that exist in the collections framework -- ArrayList, LinkedList, TreeMap, HashMap, etc. That doesn't make your view wrong, nor does it make Java a bad language. It's a case of choosing the right tool for the job. If I want to knock a nail in, it doesn't mean a screwdriver is a bad tool.

---

### Post by CptPicard on 2013-05-28
> **WinterMadness said:**
> The reason I like pointers is because when you create data structures, they make a lot of sense. You can have Java handle the pointers for you, but for me, its just easier to think about with pointers, and I know what I'm getting into. My complaint about Java is pretty much subjective.

I guess you need the pointer to make its value semantics to be obvious, while in Java you have to have the understanding that a Java reference is, semantically, a kind of handle for the actual contents of the value.

When it comes to the actual ability implement data structures (or understand their implementation), this has no meaning.

And I do understand you say it is a subjective preference, I just have always been a bit at odds with the pointer-worshipping crowd :p

@r-senior, using already implemented, well-tested collection classes is a just good practice in any language... it's called software engineering.

---

### Post by Leuchten on 2013-05-28
> **WinterMadness said:**
> The reason I like pointers is because when you create data structures, they make a lot of sense. You can have Java handle the pointers for you, but for me, its just easier to think about with pointers, and I know what I'm getting into. My complaint about Java is pretty much subjective.

As CptPicard said, references in java are pretty much pointers already. They just automatically dereference for you and what they point to is cleaned up when it becomes unaccessable. Everything in java **except** primitive variables is a reference, and you can even make references to primitives if you need to.

On a side note, why is a lambda making CptPicard facepalm?

---

### Post by CptPicard on 2013-05-28
> **Leuchten said:**
> 
On a side note, why is a lambda making CptPicard facepalm?

That's a nice take on it. I always thought of it as CptPicard shading his eyes from the harsh glare of Truth, Beauty and Correctness... think Moses and God and so on.

---

### Post by prodigy_ on 2013-05-28
I thought Java was a travesty of a joke of a programming language - only good for writing useless and resource hungry "apps" for smartphones/tablets.

Oh, wait. It is!

---

### Post by snip3r8 on 2013-05-28
Because Linus Torvalds says this: [http://www.youtube.com/watch?v=Aa55RKWZxxI](http://www.youtube.com/watch?v=Aa55RKWZxxI)

---

### Post by Leuchten on 2013-05-28
> **prodigy_ said:**
> I thought Java was a travesty of a joke of a programming language - only good for writing useless and resource hungry "apps" for smartphones/tablets.

Oh, wait. It is!


Have to wonder what you think of python, or any language that's not c or c++ then.

> Because Linus Torvalds says this: [http://www.youtube.com/watch?v=Aa55RKWZxxI](http://www.youtube.com/watch?v=Aa55RKWZxxI)

Guess the linux community should stop writing apps in C++ then.[INDENT]
[/INDENT]

---

### Post by jnguyen on 2013-05-28
Guys and Gals,

After reading all the posts I would like to put in my 2 cents in if you don't mind:

There is a collection of huge Java Apps belong to Oracle (commercial). We have more than a hundred of Linux servers currently running using WebLogic as a front end to deploy java Apps and access the apps by the web browsers.. They work much better than deploy on Windows servers. In WebLogic you also can specify the min & max java memory use for your apps.

There is one thing I really don't like is the web browser needs a specific version of java plugin depend which apps you're running. The server will push down the right version of plugin for you nicely, but if you have more than two apps then your nightmare begins. You have to remove/reinstall plugins all day long when you switch apps or you have to have more than one computers or running VMs to accommodate this delimas like I do.

jd

---

### Post by Leuchten on 2013-05-28
> **prodigy_ said:**
> There's no language that can stop you from writing trash but "Java" and "screwup" are practically synonyms.

See, there are three categories of people:
A) Programmers. Mostly they don't care about how ugly their code is as long as it sort of works.
B) End users. Mostly they don't care the application they want to use is designed and implemented by a bunch of retarded monkeys.
C) Guys like me. Our job is to make sure that products devised by A somehow meet the expectations of B.

Personally I've been struggling with various garbage written in Java for over 15 years. Pardon me, but I don't have a single kind word to say about Java, its maintainers or those who employ it in their projects. Actually I hope they'll all die in terrible agonizing pain - for great justice.

How would another language fix this? I mean [hell is other people's code]("http://exodusdev.com/blog/mike/hell-is-other-peoples-code").

Anyway, there are plenty of non-java jvm languages, so no need to throw the baby out with the bathwater.

---

### Post by ofnuts on 2013-05-28
> **CptPicard said:**
> That's a nice take on it. I always thought of it as CptPicard shading his eyes from the harsh glare of Truth, Beauty and Correctness... think Moses and God and so on.
I always took that as CptPicard concentrating trying to figure out the misplaced parenthese in a Lisp program :)

---

### Post by ofnuts on 2013-05-28
> **jnguyen said:**
> There is one thing I really don't like is the web browser needs a specific version of java plugin depend which apps you're running. The server will push down the right version of plugin for you nicely, but if you have more than two apps then your nightmare begins. You have to remove/reinstall plugins all day long when you switch apps or you have to have more than one computers or running VMs to accommodate this delimas like I do
You are looking at the problem the wrong way. The browser isn't requiring different Java releases to run the apps, it's apps that won't run on later versions of the code because they aren't well written or are not maintained.  I have a photo manager written in the 1.2 days (on OS/2!) that still runs on 1.7 (Linux) (and I never updated the code...)

---

### Post by Some Penguin on 2013-05-28
> **jnguyen said:**
> Guys and Gals,
There is a collection of huge Java Apps belong to Oracle (commercial). We have more than a hundred of Linux servers currently running using WebLogic as a front end to deploy java Apps and access the apps by the web browsers.. They work much better than deploy on Windows servers. In WebLogic you also can specify the min & max java memory use for your apps.


This.  It's particularly well-suited for serious server work where high concurrency, high stability and the ability to easily introspect on live systems is important, and where having a JVM around isn't exactly a tough requirement to fill because you control the deployment environment.   This sort of work tends not to attract people interested in developing desktop applications,  and people who write things like back-end servers are highly likely to focus on building tools which make their lives easier (like database connectivity layers, stuff like Jersey which makes it trivial to write HTTP-based endpoints, or all kinds of test and debugging tools), and not on developing things like GUI toolkits to make it easier for application developers to switch.  If you're mostly into things like building systems which accept and handle millions of transactions a day and flagging transactions as fraudulent in real-time, it's probably not very high in your list of things to do to port GUI building tools in order to make some desktop developer's life easier especially when they probably cut their teeth on C++ and aren't looking for a reason to switch.

Also, users of desktop applications tend to be very tolerant of software that crashes with some frequency, let alone software that would have trouble running 72 hours w/o a serious memory leak.  The requirements usually permit more failure, and thus it's not necessarily a crisis if you have programmers who fail at memory management with some frequency.  It's not headline news when your word processor crashes once in a while, and it's practically *expected* that marquee games are broken at release and will probably frequently crash for a significant number of players all the way until the publisher starts selling the sequel.

---

### Post by 1clue on 2013-05-30
I'm a professional Java developer.

Swing IS hideous.  There are better options, but mostly I think Java is server-side and web interface, so that means nobody doing that uses swing.  The few real "applications" out there that use it put up with it as best they can, but there is also a semi-native toolkit available to better integrate with the native OS.  I've never used it and can't even remember the name.

I use groovy/grails mostly.  Groovy is a language that compiles to Java byte code, and grails is a framework for web applications for groovy.

Most of the disadvantages of Java (swing for example, and long start-up time for the JVM) are nullified by the way I use it.  If you use the server JVM, it takes longer to start the virtual machine but then the code runs at very near native speeds.  If you're running inside an app server (tomcat for example) the server stays up for days/months/whatever, and that startup cost is negated by uptime.  As well, since you're running a web application you're using HTML and CSS and JavaScript, and the web browser is your rendering engine.  In that sense the Java webapp is indistinguishable from PHP or any other language's webapp.

Keep in mind that one size does NOT fit all.  That's why we're not all using Windows.  There are things Java is good at, and things it's not good at.  Linux has a vast abundance of languages available and each has its strengths and weaknesses as well and the languages that run in the JVM are only a part of them.  The choice of the proper language is as important as any other aspect of a project.

---

### Post by r-senior on 2013-05-30
> **1clue said:**
> The few real "applications" out there that use it put up with it as best they can, but there is also a semi-native toolkit available to better integrate with the native OS.  I've never used it and can't even remember the name.
There's SWT, which is what Eclipse and XMind uses. There is also a Java GTK project around but it was an incomplete implementation of the toolkit last time I looked (probably about 2 years ago). The way forward for GTK is probably GObject introspection in the same way that PyGTK was deprecated.

Not tried it but there's a project ... [https://live.gnome.org/JGIR](https://live.gnome.org/JGIR)

---

### Post by 1clue on 2013-05-31
SWT is what I was thinking of, thanks.

---

### Post by diesch on 2013-06-01
> **r-senior said:**
> 
Not tried it but there's a project ... [https://live.gnome.org/JGIR](https://live.gnome.org/JGIR)

Last commit in the git repository is from 2010-02-09. I guess the project is dead.

---

