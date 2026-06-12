---
title: "JAVA Question"
date: 2007-06-26
forum: Programming Talk
---

### Post by LaRoza on 2007-06-26
*This is not a post to spark any debates, flames, or international conflicts.*


I have a delicate question and am not sure how to say it. I am just beginning learning JAVA, I have already studied C++ and Python, among others and am wondering what the use of JAVA is.

The book I have says it is OO, platform independent, portable, has garbage collection, etc, but I can find no reason to use it except for applets. I know Java is more useful than that.

The question is, Python can be compiled into byte code, is very portable, has good graphics modules, and is much easier to write and read, and has other features that Java also has, so in what situation would Java be the answer?

I am NOT trying to belittle Java, I just want an experienced Java programmer to tell me what Java is good at.

This question comes out of my IGNORANCE of Java and my knowledge of other languages.

Please eductate me.

---

### Post by samjh on 2007-06-26
I don't have enough all-round experience in Java to answer your question definitively.  My Java experience is in desktop applications and hardware-desktop interfacing using Java.  I have no experience using Java in a web environment except in purely academic exercises.

So, given that background, and given also my knowledge of Java usage in related industries, I can give one example where Java has stood out, and continues to gain acceptance...

Java is useful in situation where you need a single platform that can tie together desktops and servers across multiple architectures or operating systems, especially as part of a critical information system.  One of the most common - yet unexpected - uses of Java in this manner is in the aerospace and defence industries.  Companies such as Raytheon (missiles and radars) and Thales (radars and sonars) use Java to interface with mission-critical hardware, which are normally controlled by Ada or C++ software.  Java provides the glue and the user interface to control those systems.

Why is Java good for this?

Firstly, Java is widely adopted in portable devices, such as mobile phones and palm-top computers, so there is a lot of industry experience in porting the Java runtime to such machines.  These are the very types of devices that are frequently used in so-called mission-critical industries.

Secondly, Java is a strongly-typed language, and provides very strong facilities for runtime error checking and exception handling.  These are features that are often criticised for making Java programming difficult.  But critical systems industries has experienced over many years that strong typing, runtime checks, and error handling, are necessary for safe software.  This is why languages like Ada are still routinely chosen over more flexible languages like C and C++, and other arguably suitable alternatives like Forth.

Thirdly, Java has a comprehensive built-in standard API.  This is both a blessing and a curse.  The API is complicated and some programmers get frustrated by it.  But if you're working in an industry where plugging in add-on libraries from third-parties introduce safety risks in your code, having a comprehensive standard API by the language's de facto implementers is a very good feature.

As yet, no programming language has been proven to be widely successful at balancing time-to-market, maintainability reliability, safety, and portability across devices, as Java has.

Those same features that make Java attractive to aerospace and defence, also make Java useful for other companies that rely on safe software.  Banks and Financial institutions have been traditionally heavy users of Java.  At first it was because of its web capabilities, but as time progressed, Java has found its way more into the back end for important data processing.  With computing power (and litigation) continually on the rise, the need for performance has given way to the need for more safety.


As for web applications and applets, well Java is still very strong in those areas.  But I actually think languages like Ruby, Python, and PHP are better suited for most of that stuff.  The only time when Java could be better is if there is a requirement to read from proprietary databases across platforms.  Java is interoperable with MS .NET-based infrastructure.  I'm not sure if Ruby, Python, and PHP offer the same level of interoperability unless they use something like Iron-Python (almost unheard of in mainstream usage).

---

### Post by LaRoza on 2007-06-26
Thanks for your answer!

---

### Post by pmasiar on 2007-06-26
To learn java, try "head-first" book series - they are really good. OODesign and Design Patterns are from same series, you get discount if you order more books, and all of them are really good.

Java is popular in big companies (Fortune 500 etc), where big teams of average coders crank loads of average code, and bosses like it because with java standards, they can pick 5 more coders off the street and plug them in, or fire some and be safe that later people will be able to pick pieces up.

Java can get you a job, but it is probably boring job (but with pay :-) ). Java coders, disilusioned by horrendous text precessing capabilities and over-complicated web app frameworks, in hordes left for Ruby. If you ever tried web app like Struts, you will understand why they left. Struts can easily handle 10K pages enterprise website - but to write simple hello-world app, you have to define most of the config like for big app. Struts scales up, but not down.

Java was once seen as defence against total domination on Microsoft platform - as guarantor of platform independence. Those big companies mentioned by samjh so far used only 3 languages: COBOL, ADA, and now java. And they will not upgrade anytime soon... They do not care much about productivity of developer - all thay care is process management, maintaining legacy code over decades.

I worked once in company maintaining 40MB of source code (with a group of experts of course). Fixing a bug took couple days (1-3): couple hours to learn part of the GUI used for it (learning from appropriate QA person - hardly anyone knew whole system functionality) and duplicate the error, couple hours to find the bug, and couple boring hours of researching 40MB sources if changes will break anything. I averaged about 1 changed line per day, which was OK. This is world of programming for big companies. This is java. It pays well :-)

---

### Post by LaRoza on 2007-06-26
> **pmasiar said:**
> To learn java, try "head-first" book series - they are really good. 

I'm spooked, the only Java book I have is a "head-first" book.

Thanks for your reply, I am only learning Java to for the sake of knowledge, I can't see my self using it for much.

---

### Post by pmasiar on 2007-06-26
Yes, but to be able to talk to java programmers you need to talk in Patterns :-) I mean use patters in your code :-) 

Java community would love to have code as readable as Python is, but because language is so verbode and API libraries are so byzantine and names are so long and so standard, they use [Design Patterns](http://en.wikipedia.org/wiki/Design_patterns) to add yet little more bondage and discipline into everyday Java coding. They obviously love pain :-)

Seriously, head-first Pattern book is great. 

For the sake of knowledge, better learn TurboGears! :-)

---

### Post by blah blah blah on 2007-06-26
Try groovy, it's sort of like python but it's for the java platform.

---

### Post by meman63 on 2007-06-26
I actually use JAVA for some custom tools of my own.It is really quite simple to use the same tool on a number of different platforms.(Yea,yea,yea...the old joke,notwithstanding).

To ME,it is easier because that's what I know to work,and work well.

For ME!I know JAVA better than I know C++,so it is easier to me.

Just my 2cents worth,
Meman63

---

### Post by LaRoza on 2007-06-26
> **meman63 said:**
> 
For ME!I know JAVA better than I know C++,so it is easier to me.
Just my 2cents worth,
Meman63

Amazing how often it comes down to personal preferences.:D

I am enjoying the study of JAVA, so that alone makes it worth it.

---

### Post by kknd on 2007-06-26
Java is also much faster than plain Python (I know, you can compile you modules in C and etc, but it will take portability away and introduce another language. And, Java can do that too =) ).

By the way, I like Python too.

---

### Post by steve.horsley on 2007-06-27
Don't underestimate the safety aspect of java. For long-running processes, server processes etc. it is far more reliable (and far faster) than python in my opinion. Python is fine for many things, but if I were to write something that must run for months or years reliably, I would choose java. Also, java's object oriented-ness helps keep things compartmentaised in large projects. 

And java is very well documented, which again helps in writing reliable software. I have found many times that python's handling of errors and edge cases is not documented, leaving the programmer to manually test all the edge cases they can think of, and then still not be sure the code will behave under all circumstances. Yesterday I caught a piece of python code printing a floating point value as "-1.#IND", which the recipient machine took an objection to. That kind of thing just doesn't seem to happen in java - it's just more trustworthy. Not that I want to put python down of course - python is a good language. But java excels at reliability, interoperability and is pretty good at speed (after a slowish startup).

---

### Post by LaRoza on 2007-06-27
Thanks, is it no wonder I could not find a specific use for my own purposes? I am learning it, and am probably going to stick to applets with Swing and AWT, as I am most interested in Web programming.

---

### Post by steve.horsley on 2007-06-28
Hmm. I'm rather less of a fan of swing and AWT than I am of java in general. The words slow and ugly come to mind. If you want to make a GUI, I wuld suggest looking at alternatives to swing. I have played with eclipse recently, and that looks pretty good, and it uses its own GUI toolkit called SWT. You might also find GTK2 or WX toolkits for java. I can't recommend specific ones, I've only ever done swing GUIS (very few), and they have never felt slick to me.

---

