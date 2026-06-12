---
title: "NetBeans hogging more than 500MB of memory."
date: 2009-11-27
forum: Programming Talk
---

### Post by Repgahroll on 2009-11-27
Hello.

I'm using netbeans for web development because it kicks-asses :D

However, after some little time, the thing consumes more than 500MB of memory and begin to behave choppy.

I think it has something to do with the number of undos on memory or something because just after launch it consumes less than 40MB and if i let it open it stay as is, but when i open a file (the file i'm working has <3k lines) and begin to work, after some time it's hogging more than 500MB and i'm forced to restart the application.

I've tried several versions starting from 6 up to the latest nightly and the same thing happens.

I'm on Ubuntu 9.10 updatath.

Thanks in advance.

---

### Post by froggyswamp on 2009-11-27
It's because you're running a 64bit distro and hence a 64bit Java. 64bit Java takes about 2x more RAM than the 32bit one and Sun didn't fix this "problem" yet.

---

### Post by infestor on 2009-11-27
i have the same problem but stopped using netbeans because of its unbearable speed. i am trying to use eclipse.

---

### Post by Repgahroll on 2009-11-27
Nope, I'm using 32-bit kernel :D.

Eclipse is just "okay", NetBeans is simply amazing. It has superior autocompletion, on-the-fly debugging, styles preview, good auto format, etc., etc., etc. ...

Also, NetBeans is the best IDE for a bunch of languages, including C/C++ (only MSVC+VA is better) and Ruby (IMHO of course). I don't program in Java so i can't say about features for this language.

Thanks.

---

### Post by Can+~ on 2009-11-27
I remember having that problem very frequently, that was the main reason I never liked netbeans.

But, there's a simple workaround. If I remember correctly, you can add a "memory check" widget to the toolbar on netbeans, and if you click it, it forces garbage collection, at least that worked for me.

> Also, NetBeans is the best IDE for a bunch of languages, including C/C++ (only MSVC+VA is better) and Ruby (IMHO of course). I don't program in Java so i can't say about features for this language.

Eclipse has a C/C++ that works fine too. Dunno about ruby.

---

### Post by Repgahroll on 2009-11-27
Thanks man, i use such widget but never knew it was clickable :D... I'll give it a try.

---

### Post by froggyswamp on 2009-11-28
Forcing GC collection doesn't work for me. NetBeans (6.7.1 on x64) with no project loaded takes 438MB, after I click on GC it only goes slightly down to 417MB, not a big deal.. For comparison my Gnome/Ubuntu OS takes only about 290MB.
And yes, NetBeans is "da best" but it's also the slowest one (especially for Java web and C/C++ apps) and wins hands-down the world contest of "hugest memory hog ever created".

---

### Post by TheBuzzSaw on 2009-11-28
Every C++ IDE in existence has things I hate. Maybe we ought to rally together to form a godly GPL C++ IDE. ^_^

---

### Post by Repgahroll on 2009-11-28
Force garbage collection doesn't completely solve the problem... but it's usable now... so far it's consuming 200MB of memory, and i clicked a lot of times to force GC.

@TheBuzzSaw: I used to love Code::Blocks, however, NetBeans is far better. It has no RAD support, but it has QT Designer integration (QT integration/QT Creator aren't RAD imho).
Although, Code::Blocks + wxsmith is a true RAD platform, just like Lazarus/Delphi. Just "design-click-code"... QT Designer is cool, but has no click-and-code feature like wxsmith, you have to call the objects coding by hand, very boring, very slow, and if you have a complex gui you need elephant memory to remember the objects names etc.

The only GUI that has almost everything i need/want is NetBeans, and the only problem it has is it's almost unusable... looks like it never "relases" memory.

Otherwise i would consider it an opensourced "Visual Studio" ;).

---

### Post by TheBuzzSaw on 2009-11-28
I hate how NetBeans requires a Makefile.

---

### Post by slavik on 2009-11-29
> **froggyswamp said:**
> It's because you're running a 64bit distro and hence a 64bit Java. 64bit Java takes about 2x more RAM than the 32bit one and Sun didn't fix this "problem" yet.
Please elaborate.

---

### Post by BenAshton24 on 2009-11-29
Geany = Best IDE ever IMHO... It's simple, lightweight and it works great... also it's not written in java :)

---

### Post by Repgahroll on 2009-11-29
Okay, collect garbage doesn't work after 2k lines.

I have a relatively powerful PC and NetBeans doesn't allow me to edit a single 2k lines file. It's using "only" 350MB of memory, but every key takes seconds to process.

If the developers actually use NetBeans to develop it, i wonder what kind of PC they have... a 5k-cores server?

Geany is good but has no code-completion, on-the-fly debugging, and all those productivity features that actually decrease the development time.

I'm gonna test Zend Studio.

I'm a beginner programmer, so i really need those silly features.

Thanks everyone.

---

### Post by slavik on 2009-11-29
tell JVM to allocate a 1GB non-resizable heap when running Netbeans. Use concurrent garbage collector as well.

---

### Post by Repgahroll on 2009-11-29
Thanks man, but i tried it and doesn't work also.

Just after opening the (2k lines) file the memory applet shows 96MB/1016MB (i set to 1024, have no idea why the app show 1016) but when i try to type a simple "$array = Array(a,b,c);" line, the thing takes too much seconds after the "$", the "=", the "A" (from Array) and the "(". And i think it takes one minute to type the entire line, so it's actually unusable.

I tried both official jre6 and openjdk with the same result (openjdk consumes little bit more memory though).

I don't think memory is the problem.

BTW... Zend is too much expensive, are there another "free/at least cheap" alternative?

---

### Post by froggyswamp on 2009-11-30
> **slavik said:**
> Please elaborate.

> 
Compressed 64-bit object pointers (afaik scheduled to be default for JDK7):
A technique for compressing 64-bit pointers to fit into 32 bits, which decreases memory and memory-bandwidth consumption and thereby improves performance (VM-level feature)

However with JDK7 the whole picture still ain't gonna look rosy enough, please Google for more info, there's lots.

edit: sorry forgotten to put the link:
[http://openjdk.java.net/projects/jdk7/features/#f603](http://openjdk.java.net/projects/jdk7/features/#f603)

---

### Post by Repgahroll on 2009-12-01
I tried eclipse pdt and it ran pretty faster, also, it has the same debugging (xdebug) features and it's an important feature, however, it doesn't have intelligent completion, independent javascript/php/html/css completion and highlighting on the same file, handy documentation pop-up (this feature multiplies my productivity by 2), CSS preview (netbeans is the best CSS editor i've seen), intelligent and clean autoformatting, handy virtual buttons, decent macro, easy html objects insertion, "preview" feature, decent database connection, etc. etc. etc..

So i'm using eclipse for big files and netbeans for everything else. Running together netbeans+eclipse consumes 2GB of memory, fortunately i have 4 (of course, on a 32-bit os i have 3.2 actually). That's the price to have some silly help from a IDE. If netbeans was programmed on C++ i think it would consume less than 40MB and would run many times faster, i think. That's why i never wanted to learn java ;).

---

### Post by escapee on 2009-12-02
Have you tried searching through Eclipse's many plugins to supplement anything lacking in the core program?  They should probably be able to match up with NetBeans.  Couldn't tell you for sure - I used to run NetBeans, but I never really gave Eclipse a chance.

---

### Post by Repgahroll on 2009-12-02
@ escapee: Which IDE are you using right now?

If there's a kind of app that we (Linux users) really need are IDEs. Almost every Linux user programs a little and lots are programmers in some level.

Even if you aren't a programmer, IDEs like those commercial ones for Windows will allow people to program complex things many times faster than on a text-editor and many times easier, after some time the user feels comfortable with the language itself and doesn't need much programming help.

An example is, here in my country, people who study in Universities that teaches C++ using Visual Studio, are able to program C++ (pass on a C++ advanced test) after 1 year, and those who study in Universities that uses Dev-Cpp or another simple IDE only are able to pass on the same test after 2 years, and some just aren't able to pass, not even after the graduation (4 yr on computer science).

Maybe the Universities are just too bad in my Country, but at least a little bit of truth does exit on these statistics i think.

---

### Post by escapee on 2009-12-08
Sorry for late reply, forgot to check back.

I don't currently use any IDE aside from Xcode on Mac when doing Objective-C work.  I'm primarily using TextMate and VIM on Mac these days.  On Linux I use VIM, gedit, or KATE for editing.  I don't find much of a need for full-blown IDE's - they normally just get in my way.

There are a bunch of IDEs available for Linux.  To name a few:

NetBeans
Eclipse
Aptana
Code::Blocks
Geany
KDevelop
Anjuta

That is not to say that the perfect IDE exists yet, but most seem to find Eclipse does what they need.

---

