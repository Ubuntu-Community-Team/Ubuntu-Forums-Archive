---
title: "Is Java really worth it?"
date: 2006-12-18
forum: Programming Talk
---

### Post by Verminox on 2006-12-18
I've been a web developer for some time and am pretty comfortable using C++ for command line applications or using SDL for a game-stuff.

Now, I wanted to give a try to programming applications with GUI. I use KDevelop on Kubuntu so it has a neat designer for KDE interfaces, but that will limit my application to KDE. Using the Windows SDK or GTK will create the same issues.

What I'm really looking for, is a way to to be able to make windowed programs not interacting with the system. I heard Java was good for such cross-platform development, as it only needs the JRE installed on the user's PC. 

Well, I was wondering if there was any way I can make windowed apps cross platform with C/C++ (maybe an API or somthing) or whether I should just learn Java and use that?

Does the cross-platform thing make Java worth it or not? Or should I stick to C/C++ now that I am comfortable with it. Will it be a big switchover from C/C++ or is it similar?

---

### Post by po0f on 2006-12-18
Verminox,

Java is great for cross-platform development IMO.  Source- and binary-compatible programs will be easier to develop if your target platforms have a Java RE available.  There's nothing like developing one application, creating a JAR out of it, and having Windows and Linux users (and others) able to use the same file.

Note: I really don't like Java, but it *is* the best solution for you if you want easy cross-platform development.

If games are your thing, you might want to look at link:[Lightweight Java Game Library](http://www.lwjgl.org/).  (I really don't know how "light" it is though, never got too into Java development myself.  :)

(Pointed out link, new forum colors don't distinguish links from text that well sometimes.)

---

### Post by Wybiral on 2006-12-18
I would avoid java, personally. GTK will work on windows and KDE (just look at GIMP, for instance). I would use either C++ with GTK, or if you are looking for a more portable language to use, python with GTK. Either will be better than java!

---

### Post by Verminox on 2006-12-18
For games I use C++ with SDL and OpenGL. That works fine cross-platform.

It's only when I want to make a window that I find I'm faced with multiple SDKs for multiple platforms and I don't want to make separate GUI classes for each platform in my app.... althogh that is an alternative none the less (mainly because I prefer the C/C++ programming to Java progamming, from the Java tutorials that I have read).

---

### Post by jblebrun on 2006-12-18
Java is not too different from C++. If you're interested in learning Java, I'd say go for it. It will certainly not hurt, and it will open your eyes to new patterns of development. 

That said, if you're interested in cross-platform development using C++, you should check out the [wxWidgets]("http://www.wxwidgets.org/") library. It's becoming quite popular, and it is being ported to other languages like Python, as well.

---

### Post by po0f on 2006-12-18
Wybiral,

I would tend to agree, but it also depends on what type of user the OP is targeting as well.  Most end users can't be bothered to install *additional* libraries on top of any development-related stuff (read: MinGW) in order to get the program working.  ("What? I have to install something else to get this to work?  Forget it!")

OTOH, Java is installed on a lot of people's computers, and most programs will work OOTB for them.

---

### Post by Wybiral on 2006-12-18
po0f: That's true, I've just never liked java. It isn't as fast as C++ (bytecode vs machinecode) and I don't really think most of the GUI's made in it look that great. I think C++ with gtk or as jblebrun mentioned, wxWidgets, is a much nicer approach than to use java. I would even recommend using python and gtk or tkinter over using java.

---

### Post by Verminox on 2006-12-18
I think I'll stick to C++ for now. I don't need Windows support anyway, since all my code is always open source and don't mind it confined to Linux.

Now comes the question, GTK or KDE :p

Do KDE applications work on GNOME by default? If so I'll just go ahead using KDevelop and its associated programs because it is really good.

---

### Post by po0f on 2006-12-18
Wybiral,

> **Wybiral]... I've just never liked java. ...[/quote]
Me neither.   said:**
> 

Verminox,

[quote=Verminox]Do KDE applications work on GNOME by default? ...
If "by default" you mean after installing Qt libs, then yes they do.  A default install of Ubuntu does not include these though, you should outline any specific dependencies your program needs in a README or something similar.

---

### Post by thesmartace on 2006-12-18
I like Java. I only started learning it when I got to uni a few years ago tho. The built-in GUI (with the metal L&F) isn't the prettiest thing ever but being able to make a Jar and distribute it to Windows or Linux with no additional files is really handy. 

If you do want to go one step further for Windows users, it is really easy to add a program icon and hide the Jar inside an .exe file with [**Launch4J**](launch4j.sourceforge.net).

I am moving more towards Mono and Python these days tho. I like using the GTK way more than the Java GUI classes. Plus, the Mono installer for Windows bundles GTK ;).

---

### Post by Patrick-Ruff on 2006-12-18
I think a programmer shouldn't limit himself to a language. I think a programmer should learn everything he can fluently and frequently use all that he/she knows.  from what I hear, Java is a little bit of C, and a little bit of C++, and it's own other stuff. so, just go for it. it'll be a good learning basis, probably will help you in learning other languages as well.  I am just now cracking into C for the first time (I'm 15 so I kinda wasn't very obligated to learn.) luckilly, I have a friend who is going to literally write a guide for me, and he also puts up with my crap when I don't understand stuff.

either way, go for it, you being good with C and C++, I don't think it will be much of a challenge.

---

### Post by slavik on 2006-12-18
> **po0f said:**
> Wybiral,

I would tend to agree, but it also depends on what type of user the OP is targeting as well.  Most end users can't be bothered to install *additional* libraries on top of any development-related stuff (read: MinGW) in order to get the program working.  ("What? I have to install something else to get this to work?  Forget it!")

OTOH, Java is installed on a lot of people's computers, and most programs will work OOTB for them.
Wasn't there a huge case where Microsoft was not allowed to bundle Java VM with Windows? chances are, Java VM does NOT come standard on Windows ...

Learn Java anyway. As for GTK, it will run under Windows, BSD, OS X, Linux (GNOME/KDE is irrelevant here).

---

### Post by Verminox on 2006-12-18
I agree with most posts here... and thanks... and yes I do know that Java is good for some things that C++ isn't good at, I've read the comparisions between them on several sites... but those are mostly for someone who has to choose to learn one of them.

My main question was whether it is worth learning a whole new language (Java) for a single purpose (GUI)... or will it be easier to get a library or learn multiple GUI APIs and just make 2-3 different GUI classes in a C++ program?

---

### Post by Wybiral on 2006-12-18
You should learn new languages for the fun of it (and for the experience) but it would be easier to use GTK or something in this case.

(Or create a wrapper for all of the API's you plan to use that way you only have to turn on/off some def's)

---

### Post by MadMan2k on 2006-12-18
> **Wybiral said:**
> po0f: That's true, I've just never liked java. It isn't as fast as C++ (bytecode vs machinecode) and I don't really think most of the GUI's made in it look that great.
sorry, but you dont have a clue what you are talking about.

Java is being JITed these days and actually languages using a VM, can be optimized much more than compiled languages.

regarding the GUI:
[http://ensode.net/java_swing_mustang_screenshots_gtk.html](http://ensode.net/java_swing_mustang_screenshots_gtk.html)

my personal view:
I never liked Java either, but after having to write a GUI usign C++, I must say I just love it. C++ is just a big miss with its header files and unclear syntax.

And to say something useful OnTopic:
use whatever language you want with Glade:
[http://glade.gnome.org/](http://glade.gnome.org/)

it looks great on Linux, kinda messy on Windows and hardly works on Mac, but this way you are integrated in at least one platform - if you use wxWidgets they wont fit in anywhere...

---

### Post by Wybiral on 2006-12-18
I don't want to disagree with you, but I've been dabbling in compiler design and VM design lately and I can tell you for a fact, that machines being interpreted or running from a VM will NOT be as fast as machine compiled programs. If you understand the processes involved, then you realize that VM's are running from a machine code program... So how a program running on a machine code program will ever be faster than the straight machine code is beyond me... VM's have to translate the VM opcodes into commands that get acted out on the actual machine... Machine code sends the opcodes directly to the machine... It doesn't take a genius to figure out which one will be faster.

Now that I'm done bashing VM languages (which is actually funny because if you click the link on my sig, you'll see that one of my main projects right now is a VM'd language) I will say this... They are faster than straight interpreted code, like HTML or something... And they are very portable because the VM can be compiled on every system which makes it's source, and it's bytecode, able to run on any system that the VM can be compile on. And... The VM can act as an abstraction over the machine that allows for things like dynamic variable allocation and type conversion that wouldn't be as simple to integrate into a compiled program.

But, VM's aren't as fast and optimized compiled code (like c/c++)

---

### Post by slavik on 2006-12-18
Java, C#, Perl, Python will never be faster than C/C++. At best they will be as fast.

As for the VM languages being better optimised better than C/C++, I have to say 'go read the gcc/g++ man page, u n00b.' Because the java VM is written in C++ ... if C++ cannot be optimised then how can you say that Java can be better optimised than C++ VM it runs on?

As for glade ... it's a GUI designer that generates its own XML type descriptions files which it then translates to C, or C++, or Perl, or Python, or whatever else you want as long as there is a module for it. In retrospect, Visual Studio works on Windows and not anywhere else.

My rant is done.

---

### Post by Tomosaur on 2006-12-18
> **Wybiral said:**
> I don't want to disagree with you, but I've been dabbling in compiler design and VM design lately and I can tell you for a fact, that machines being interpreted or running from a VM will NOT be as fast as machine compiled programs.

You cannot state this as a fact. Java's speed is always improving, and, in most cases, it's speed is indistuingishable from that of say, C or C++  (when you consider that most software is not commercial, ie - never released to the general public). Sloppy code is what makes Java 'noticeably' slow, and general bad programming practices. In most other situations, Java is simply not the best tool for the job anyway, which is where this 'Java is slow' thinking comes from.

---

### Post by Keffin on 2006-12-18
First to add something nobody has mentioned into the mix - Qt 4 works on linux, windows, and mac. KDE 4 will be built on Qt 4, and should also be able to run on linux, windows, and mac. Since the original poster seems to like KDevelop, perhaps this is the way forward - either just using Qt 4 and being immediately able to work everywhere, or using KDE libraries and porting to KDE 4 when the time comes.

And just a few Java points:
1) Java 6 GUIs are no longer ugly, Swing now uses native widgets, as has SWT for ages (note how eclipse/azureus never looked like ugly Java apps).
2) Java may be "slow", but frankly most GUI apps sit around idle anyway. Try telling me which of the apps in GNOME are python/mono based without prior knowledge. You can't because for all intents and purposes they are just as fast. I am very aware that this is not true in all cases.
3) KDevelop has next to no support for Java, at least until version 4 (I hear they have something in the works here). Just something to think about for the OP. You have the choice of eclipse or netbeans.
4) I like Java.
5) > VM's have to translate the VM opcodes into commands that get acted out on the actual machine... Machine code sends the opcodes directly to the machine... It doesn't take a genius to figure out which one will be faster.
That's lovely. However, if your computer constantly sits at 100% CPU you either need to use lighter programs or buy a new computer. Otherwise the VM has 90% of the CPU time to compile your code to the exact specs of your machine, and do a little profiling to discover exactly what is best to keep closer to the processor.
Which brings us to > As for the VM languages being better optimised better than C/C++, I have to say 'go read the gcc/g++ man page, u n00b.' Because the java VM is written in C++ ... if C++ cannot be optimised then how can you say that Java can be better optimised than C++ VM it runs on?
I have to say go read [http://java.sun.com/products/hotspot/docs/whitepaper/Java_Hotspot_v1.4.1/Java_HSpot_WP_v1.4.1_1002_4.html](http://java.sun.com/products/hotspot/docs/whitepaper/Java_Hotspot_v1.4.1/Java_HSpot_WP_v1.4.1_1002_4.html) "u n00b", which states several optimisation techniques that rely on gaining information at runtime and using that to further optimise the program (you can start reading about half way down), this optimisation can't be done on a C++ program. Not to mention that everything you're using now is compiled for a 386 processor, but the JVM (or g++) can still optimise the code it's running (or compiling) to e.g. a core 2 duo or whatever. Congratulations for having a self-confessed rant based on no information what-so-ever.

Please note that I do believe from my own experience that Java is slower than C++. I am not arguing that it is faster now, I'm just arguing that it won't "always be slower because man gcc". If you can point me at anything in the gcc man page that says it isn't possible to optimize Java more than C++ then please let me know, because I've never read that bit.

---

### Post by firebadger on 2006-12-18
Actually, because of the VM nature of Java, optimization decisions can be made at runtime where you have more information about the architecture of the system running it, and exactly how the program is being run.  This results in roughly equivalent performance in the real world between Java and compiled languages.
Have a look at this... [http://www.javaperformancetuning.com/news/qotm042.shtml](http://www.javaperformancetuning.com/news/qotm042.shtml)

Java does have a bad reputation for performance and it is not entirely unfair.  However, I think this is largely to do with desktop apps and the overhead at startup of initialising the JVM.  Also, the JVM tends to grab memory and not give it back irrespective of how much the program actually needs.  I think that these are the issues that really need to be addressed for Java on the desktop.

---

### Post by Wybiral on 2006-12-18
You must not understand the concept of a virtual machine... It isn't compiling it as it runs it, or converting it to equivalent opcodes... If you think that it is going to "compile your code to the exact specs of your machine..." then you were lied to somewhere because thats not how the java VM works at all.

---

### Post by Keffin on 2006-12-18
> **Wybiral said:**
> You must not understand the concept of a virtual machine... It isn't compiling it as it runs it, or converting it to equivalent opcodes... If you think that it is going to "compile your code to the exact specs of your machine..." then you were lied to somewhere because thats not how the java VM works at all.

The Java JVM is a **J**ust **I**n **T**ime **compiler**. "Compiling as it runs it" is exactly what it does (to within a few milliseconds at least). So I'm left either thinking Sun is lying to me (obviously you didn't read my link as it proves you wrong), or you are just trolling. Lets see, which shall I believe.....

Let me link to the Java SE HotSpot VM (JVM) main page this time. [http://java.sun.com/javase/technologies/hotspot/index.jsp](http://java.sun.com/javase/technologies/hotspot/index.jsp)

In particular I'll quote this:
**It includes dynamic compilers that adaptively compile Java bytecodes into optimized machine instructions**

Sorry, I'll believe Sun on this one, especially since they're well on the way to GPLing Java now. GO LOOK AT THE CODE!

---

### Post by Wybiral on 2006-12-18
Yes, but there is a difference between the java VM and the java JIT. Not all code can be ran through the JIT from what I've read, and especially not on every system. So then you have speed vs compatibility. Another thing to mention is the loading time... Java is always going to take longer than a precompiled language if it is using the JIT. Another point to bring up is that people do not always want to install the java runtime environment which is a factor when releasing a big project.

You are right though, I was wrong, I was doing all of my research on the JVM and neglected the JIT. But, it still is not a sure-fire approach because not every system is compatible with the JIT, and none of them produce standartize executable machine code because they are essentially being compiled by different programs. Now, dynamically compiled java definitely reaches C++ worthy speeds, but at the cost of it's prized portability and a very slow loading time... And I have yet to see any statistics to show it going above C++ speed. Equal yes, but not above.

(I do believe java was made on C, so even if it were faster than C... It would just be an example of how fast C is, lol)

Thank you for pointing out the JIT, that did enlighten me as to why people would use java over C++

---

### Post by firebadger on 2006-12-18
What code can't be run from it and what commonly used system isn't supported by the Sun Hotspot JVM (the most common)?  And how does "dynamically compiled java" lose its portability?

The JIT compiler is a component of the JVM so not really as seperate as you think.  

This all sounds like a lot of F.U.D.

---

### Post by pmasiar on 2006-12-18
> **Verminox said:**
> Now, I wanted to give a try to programming applications with GUI. ....  make windowed apps cross platform with C/C++ 

Does the cross-platform thing make Java worth it or not? Or should I stick to C/C++ now that I am comfortable with it. Will it be a big switchover from C/C++ or is it similar?

Learning new library and become expert in it is big time committment, bigger than learning new language. Java is very close to C++ and you will learn it fast - but it will take you months and years to become expert in java objects.  They are different for no good reason - just incompatible for marketing reasons. 

To get better return of investment of your time I would suggest to learn different language: python. Dynamic typing and memory management will open new horizons to you, new levels of pruductivity, and you learn new tricks, like runtime introspection (if you care about it). With python, you would be able to create a prototype of your system in 10% of time it would take in C++. Of course it would be 50% slower than C version, but you can find bottlenecks and reimplement them in C, or rewrite whole thing in C - but you will have experience (and user feedback) from python version. Also, python will allow you to build non-critical parts of your infrastructure, like unit-test pipeline, developer suppert website etc much faster.

Python supports wxWidgets, popular library that looks native in all environments.

---

### Post by Wybiral on 2006-12-18
Actually pmasiar, I know we've had our share of python vs C conversations (if you will...) but I would give python a lot more credit than 50% slower... It is definitely better than that. Just not AS fast as C++ (I say C++ because C isn't really relevant, C++ has more in common with python). And I agree with pmasiar, python is a really good language to have under your belt, especially since you can embed it in your C++ programs for user scripting, create modules for python using C++, or just use python to orchestrate your C++ programs. It is very useful an easy to learn.

---

### Post by Verminox on 2006-12-18
Hmmm... I've never really thought of Python... not really heard much about it to tell you the truth.... don't even know what it can do actually.

I'll try giving Python a try then.... something new will be fun to learn... and whatever I am doing is as a hobby only anyawy, not professionally.... so I can deviate to whatever is more suitable and more fun.

---

### Post by MadMan2k on 2006-12-18
> **Wybiral said:**
> You are right though, I was wrong, I was doing all of my research on the JVM and neglected the JIT. But, it still is not a sure-fire approach because not every system is compatible with the JIT, and none of them produce standartize executable machine code because they are essentially being compiled by different programs. Now, dynamically compiled java definitely reaches C++ worthy speeds, but at the cost of it's prized portability and a very slow loading time... And I have yet to see any statistics to show it going above C++ speed. Equal yes, but not above.

(I do believe java was made on C, so even if it were faster than C... It would just be an example of how fast C is, lol)
puh, you indeed read a lot about java, the VM and JITing, but sadly you have only poorly understood it.

points which come to my mind:
* what does the language a compiler is written in got to do with the execution speed of the output?
* JIT is not gjc
* compile caches?

---

### Post by Erunno on 2006-12-18
What kind of application does the the OP intend to create ? If it isn't any kind of real-time application (for which there are actually modified libraries, but that's beside the point) stop caring about machine code vs. byte code. I'm sure your users won't really notice if your application is idling a bit faster while they are tying or hovering with the mouse to find a button ;) . It's much more likely that runtime the behavior will be affected by bad choice of data structures or algorithms with with quadratic or worse complexity.

Java and C# are nice that you don't have to deal with the memory management. Unless you are an experienced C/C++ programmer you will probably run into memory leaks and weird pointer behavior and you gain very few (see above). Additionally it makes your applications more stable.

I haven't worked with the new Java 1.6 but Swing ( the GUI toolkit ) in 1.5 was very tiresome to work with. Best get an IDE with a GUI builder like NetBeans which will yield good results in a short time.

Just for some clarification, the just in time compiler compiles classes dynamically for the native architecture if they are accessed on a frequent basis. JIT compilation is also a lot faster from byte code as some of the intermediate steps which are required to compile from source are already being finished in byte code.

Plus, Java is still one of the leading enterprise programming languages.

---

### Post by pmasiar on 2006-12-18
> **Verminox said:**
> Hmmm... I've never really thought of Python... not really heard much about it to tell you the truth.... don't even know what it can do actually.

I'll try giving Python a try then.... something new will be fun to learn... and whatever I am doing is as a hobby only anywy, not professionally.... so I can deviate to whatever is more suitable and more fun.

Python has all java features, except static typing (python uses dynamic typing). So when making collections, you get all objects in and out intact - without recasting. Python also has operation overloading and multiple inheritance (java lacks both). 

I also prefer python's dynamic exceptions compared with java's static ones - for pilot project, I handle only really annoying and/or easy to handle exceptions, so I can avoid 50% of the really nasty and boring error-handling code (for pilot).

Overall, you see that python's fun factor is higher, line count is lower. Java is more 'enterprisey' bacause suits like java more: there is more java programmers, and they are more predictable. Genius python hacker can make in a week alone what java team struggled for half a year. You cannot build nice rigid enterprise with people like that. :-)

---

### Post by Ben Sprinkle on 2006-12-19
I hate bloody Java now, while being really fun, it is emulated thru bytecode and cannot be run on it's own which just plain sucks.
I don't want to type java everytime and not be able run it by double clicking or ./

---

### Post by hod139 on 2006-12-19
> **Goat Spirit said:**
> I hate bloody Java now, while being really fun, it is emulated thru bytecode and cannot be run on it's own which just plain sucks.
I don't want to type java everytime and not be able run it by double clicking or ./

What are you talking about?  You can create jar files that a user can double click to run.  You can even use Java Web start to launch your application with a single click over a network.   Good luck getting a compiled language to do that.  What do you mean "cannot be run on its own?".  You need a JVM sure, but if you want to run C/C++ code you need the C/C++ libraries installed as well.  No difference.

---

### Post by lnostdal on 2006-12-19
> **Goat Spirit said:**
> I hate bloody Java now, while being really fun, it is emulated thru bytecode and cannot be run on it's own which just plain sucks.
I don't want to type java everytime and not be able run it by double clicking or ./

Nothing except the most trivial of things "runs on its own". If you want to distribute your (I assume C-based .. *shrug*) software under Ubuntu (or any OS) you have to package it in .debs (or installers) that specify and handle dependencies - or you need to link in external libraries statically.

For an example of how to distribute a Java-app take a look at the Frostwire-site. When I click on the "Ubuntu"-link (pointing to a .deb) it is installed directly from the site and it adds menu-icons etc. automatically which enables me to start the application by clicking on it as you wanted.

Java isn't emulated - it is JIT-compiled to native code which runs fast considering what you get in return; GC .. no dangling pointer hell .. etc. .. These are good things; Python, Java, Lisp, Ruby is popular because of this. It is worth it 99% of the time; simply rewrite that small 1% of your app that needs it in C when you're done (optimize last). Almost all languages can interface with C-libraries so there is no need to write everything in C just because some small part of your app needs it.

```

lars@ibmr52:~/Desktop$ cat blah
#!/bin/sh
iagno
lars@ibmr52:~/Desktop$ chmod +x blah

```

typing ./blah will now start a game of othello ..  dragging it to one of your panels will create a launcher .. or right-clicking on your "Applications" main menu will enable you to edit and add `blah' to the menus .. I assume you're able to figure out that you can use something similar to start your java-apps also.

---

### Post by pmasiar on 2006-12-20
Some advice after trying to use java for web application - setup tomcat web server.

[LIST]
[*]Tomcat is not Apache. All you learned for Apache is irrelevant. Strart learning from beginning.
[*]Tomcat is hard to set up - it is designed to be enterprise application, dozens on programmers adding apps for hundreds of users. With appropriate level of complexity. 
[*]Administering is not simple. You are supposed to have pro admin. If you are not pro admins, sux to be you.
[*]Sample application in java is hard to set up.
[*]Java experts are not here (in ubuntu forums) or just too damn busy to help you. 
[/LIST]

Compare: 

Setup LAMP: standard 6 lines config file to enable CGI in your directory and set ScriptAlias. 3 line python test script: 

```
#!/usr/bin/python
import cgi
cgi.test()
```

I still don't know how to do it in java - and no answers to my question [http://ubuntuforums.org/showthread.php?t=321885](http://ubuntuforums.org/showthread.php?t=321885) - not a single one!

---

### Post by firebadger on 2006-12-20
Hmm, Java webapps aren't really that much harder than LAMP stuff.  It's mainly the illusion that what you are familiar with is simpler than what you are not.

I think there are a few Java experts around here including myself who answer questions from time to time.  I'll have a look at your post just now...

---

### Post by Game_Ender on 2006-12-20
If you want to get into cross platform GUI programming and don't want to use Java, but want something simpler that C++ try PyQT and wxPython.  Both are python wrappers around C++ GUI toolkits.  QT applications should look pretty native, and wxWidgets uses native widgets so it will definitely fit in with what ever platform you run it on.

pyQT: [http://www.riverbankcomputing.co.uk/pyqt/](http://www.riverbankcomputing.co.uk/pyqt/)
wxPython: [http://www.wxpython.org](http://www.wxpython.org)

Python has virtual machine and a JIT(through Psyco) but it still starts up several times faster than Java.  Although you will never get the same performance with Pyhon that you will with Java you will develop with it much faster.  Be sure to check out cool applications like PyCrust.

---

