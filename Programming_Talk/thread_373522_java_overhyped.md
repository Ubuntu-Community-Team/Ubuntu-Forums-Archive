---
title: "java overhyped?"
date: 2007-03-01
forum: Programming Talk
---

### Post by dojo on 2007-03-01
Ive herd java is over hyped is this true?ive been using java and  I think its great so why do people say this?

---

### Post by Ramses de Norre on 2007-03-01
Because different people have different tastes... 
This thread has a very big potential to become and endless discussion like we've already got hundreds of.

---

### Post by pmasiar on 2007-03-01
Java is decent programming language designed to fill one particular niche: make programs independent from Microsoft chokehold. That was the reason why companies embraced it 12 years ago. It was rather significant improvement over C++ - automated memory allocation/deallocation saves a lot of problems, and object references are safer to handle for average programmer than pointers.

Computer field changed a lot since mid-'90: Windows has a strong competitor, Linux. Althogh Java did not invented automated memory allocation and virtual machine, it made it accepted - many languages use that approach now.

With success of open source operating system and applications, programmers started to expect programming tools be open source too. Eclipse is now very popular editor, and for many companies makes more sense to develop and sell eclipse plugins, than try to maintainf whole full-featured editor.

Very interesting judo-move is in action:  [commoditization](http://en.wikipedia.org/wiki/Commoditization) For any competitive company, it makes great sense to make commodity from what other companies do, and your product will be the distinguishing feature for which people pay extra. They buy commodity as cheap as you can, and add your special features they can afford.

Example: IBM was making PC hardware - but MS windows was able to run exactly as well on cheap PC clones, PC hardware became commodity, and IBM left PC hardware business, because it could not keep margin of profit it's investors demanded.

Free software makes excellent commodity: Apache, Firefox, GCC, are good enough and free, other companies have hard time to sell competing products. In database market MySQL is good enough to replace Oracle in many cases. OpenOffice, Gimp etc.

Why IBM promotes Linux? it makes their business consulting services the special extra factor when running Java apps in Linux on Dell servers :-)

Java became now the commodity application language, but the niche it was designed for is shrinking. Java's idea of being multiplatform was to move around compiled JAR files - but now we prefer sources. CPU speed increased significantly, runtime type-checking is not such a speed killer it was 15 years ago, and increase of programmer's productivity you can gain by using dynamically typed language from LAMP platform like Perl/Python/PHP/Ruby is significant, if compared with now cheap CPU cycles. Java applets in browsers do not look as such a great idea anymore. And for web application development, Java's text processing abilities are not  so great either. It is better than C/C++/Fortran :-) but no comparison with dynamic LAMP languages. Microsoft tried to "embrace, extend and choke" java, but was not allowed - so it created own improved Java, called C#.

Also, LAMP languages were open-source from very beginning, with no advertisement budget, no rich company was spending millions to promote them, and they have to earn popularity old-fashioned way: being easy to learn and solve problems fast. Java is harder to learn, even harder to become expert in using it's huge class library, and many solutions are optimized for huge projects. 

Ie. Stuts, Java's "standard" web application framework, explicitly says on front page is is overkill for simple websites with just couple dozens of pages. But couple dozens of pages is exactly what most people have (or start with). As they say, it scales up, but not down.

Is Java overhyped? It is decent language, but it certainly failed to be computing silver bullet - to be the only language to know. Couple languages failed in that goal before; Cobol, PL/1, Ada. Is java elegant language? certainly has flaws: [http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html) and [http://www.artima.com/weblogs/viewpost.jsp?thread=42242](http://www.artima.com/weblogs/viewpost.jsp?thread=42242) and 
[http://www.mindview.net/Etc/Discussions/CheckedExceptions](http://www.mindview.net/Etc/Discussions/CheckedExceptions) - and many more :-)

Sun maked it open-source not make friends - it was the only way to keep the developer's mindshare, it is a sign of failure (together with Sun's proprietary Unix, and proprietary servers - replaced slowly by Linux and Dell).

So we are back to the future: many languages, each good in it's own particular niche. Look around how your niche looks like, and learn couple of languages used around. Learn different classes of languages - if you are C/C++/C#/Java expert, learn Python or Ruby to know how dynamic languages may speed up development. If you know Python/Ruby, learn C to avoid speed bottleneck in your code. Try Lisp, XSLT, Prolog and Forth to expand your mind, to taste completely different approach to programming.

Nobody knows what future will be, but some smart people try to imagine how will be computing when CPU will be even more powerful than today:  [http://www.paulgraham.com/hundred.html](http://www.paulgraham.com/hundred.html)

IMHO, YMMV. I programmed in Algol, PL/1, assembler, Forth, C, VB, Perl and many other languages. I prefer Python now, but slowly learnig Java/Struts for simple websites - so i am biased :-)

---

### Post by dojo on 2007-03-01
hmm Intresting, True java does has its flaws,but does python not have flaws?Like its slow.But   I belive in about 50years computers will have such great cpu and memory power that people will no longer judge langaues by there speed.AND LINUX WIL RULE!

But anyway great reply pmasiar its very intresting,Its terribale how microsoft tried to convert java Bill Gates should be ashamed!Its true though how you said people should learn diffrent types of programing langauses,after java ill proberly go to PHP or maybe Ruby.

DOJO

---

### Post by pmasiar on 2007-03-01
> **dojo said:**
> does python not have flaws? Like its slow. 

I never said Python does not have flaws - I said that languages are optimized for niches they occupy. If Python does not aim for kernel-style performance, where speed is critical, it's somewhat slower speed does not matter AT ALL. It is not relevant in Python's niche.

Example: If you work on web front end for a database, and you know that on DB connection, couple of SQL queries, and browser request/response you spend 3 sec, how it is relevant that your code in python runs for 0.1 sec, while equivalent C code would run 20 times faster for total 0.005 sec? Response time is 3 sec either case. The difference is, Python code you can make over the weekend, and C will take you couple weeks. Why you would work couple weeks in C to finish only project only, if you can finish 5 such projects in Python and get paid 5 times as much? To maybe save 0.1 sec from browser response, which customer never notices? On a server which is idling at 20% anyway?

And if you just have something do quickly, rewrite is as C-library function, and call if from Python.

> Its terribale how microsoft tried to convert java Bill Gates should be ashamed!

Not at all. He was working hard to deliver the best value for the stockholders of Microsoft (so also for himself). Every company and every person should take care of their own interests - it is called free market.

Part of free market is that Microsoft tries beat competition - including methods like spreading FUD about free software like OpenOffice - and another part of free market should be that customer should consider if OpenOffice is good enough and switch if it makes sense. There is no shame in economy: there is self-interest, and government regulation to protect consumers and fair market.

---

### Post by lnostdal on 2007-03-01
> **dojo said:**
> Ive herd java is over hyped is this true?ive been using java and  I think its great so why do people say this?

Why don't you ask the authors of Java what they think? ;)

"We were not out to win over the Lisp programmers; we were after the C++ programmers. We managed to drag a lot of them about halfway to Lisp."

- Guy Steele, Java spec co-author

(actually; i don't consider languages like Java half-way to Lisp .. not even Python or Ruby is half-way ..   they are closer, but IMHO not yet half-way at all)

one of Javas greatest things, the GC-feature - is from Lisp:

> 
As one of the earliest programming languages, Lisp pioneered many ideas in computer science, including tree data structures, automatic storage management, dynamic typing, object-oriented programming, and the self-hosting compiler.
(from [http://en.wikipedia.org/wiki/Lisp_%28programming_language%29](http://en.wikipedia.org/wiki/Lisp_%28programming_language%29) )

edit: let the flaming begin

---

### Post by angryfirelord on 2007-03-01
Programming languages are like ice cream, they all depend on the user.

In terms of speed, C++ is still a little bit faster, but with the release of java 1.6, that gap is becoming pretty small now.

Plus, Java has established itself with the web, unlike C#.

One more thing I like about Java is how extensively cross-platform it is. As long as you have the JRE installed on a computer, you should never, never, ever have to edit any of your code (in general terms). Even the GUI is the same, whereas C++ doesn't really have that (you can't use a Windows GUI under Linux natively).

---

### Post by dojo on 2007-03-02
thx for clearing that up pmasiar im going through a nooby phase right know:)

By the way angryfirelord when you said
In terms of speed, C++ is still a little bit faster, but with the release of java 1.6, that gap is becoming pretty small now.

Does this mean java could take c++ over as the main langause for games in a few years?I mean why would people need low-level fetures for games?ANd it would also solve the problem for compatibility,like alot of the new games that are good run on mainly windows.Just a thought that crossed my mind if im wrong about when i claimed eg games dont need low-level fetures, please clear that up for me/
Dojo

ps:lnostdal ive got my falme throwe out muhahahahaha:twisted:

---

### Post by Wybiral on 2007-03-02
> **dojo said:**
> thx for clearing that up pmasiar im going through a nooby phase right know:)

By the way angryfirelord when you said
In terms of speed, C++ is still a little bit faster, but with the release of java 1.6, that gap is becoming pretty small now.

Does this mean java could take c++ over as the main langause for games in a few years?I mean why would people need low-level fetures for games?ANd it would also solve the problem for compatibility,like alot of the new games that are good run on mainly windows.Just a thought that crossed my mind if im wrong about when i claimed eg games dont need low-level fetures, please clear that up for me/
Dojo

ps:lnostdal ive got my falme throwe out muhahahahaha:twisted:

Well, modern games require a LOT of memory and calculations which explains the present day need for low level languages.

Java may very well become a good language for games if it continues to increase in efficiency, but as my personal opinion it is not quite there yet.

There are also several ways to make C/C++ programs capable of being compiled for different systems, so someone wanting to write a game to run on different platforms can simply write the code portable and cross compile it. SDL + OpenGL is a good example since code using those libraries can usually be compiled on a number of systems.

Naturally this is more work on the programmers end, but if it means utilizing the hardware to a greater extent, then it may very well be worth it.

But, I guess time will tell (I haven't seen too many games written in Java as of yet that compete with the larger games written in C and C++)

---

### Post by dojo on 2007-03-02
nice reply,Ive seen a few big games written in java like runescape and puzzle pirrates but when you said 

@There are also several ways to make C/C++ programs capable of being compiled for different systems, so someone wanting to write a game to run on different platforms can simply write the code portable and cross compile it. SDL + OpenGL is a good example since code using those libraries can usually be compiled on a number of systems."

So why dont people do this with comercial games like wow in the end wouldnt just increase there sales?Even if it more work for the programers,its there job:).I understand now why some big games reqiure low level langauses.But as you said Time will tell i hope java comes out on top:/.Oh yeah dont some comercial games use a mix of both java and c++?Im attuly planing to make a 3s or maybe 2d mmorpg when i finch learning java.

---

### Post by angryfirelord on 2007-03-02
> **dojo said:**
> Does this mean java could take c++ over as the main langause for games in a few years?I mean why would people need low-level fetures for games?ANd it would also solve the problem for compatibility,like alot of the new games that are good run on mainly windows.Just a thought that crossed my mind if im wrong about when i claimed eg games dont need low-level fetures, please clear that up for me/
Dojo

It's hard to tell because you never know what other languages will appear. C++ is still the major language in gaming, but I think that will change as more Java games are starting to appear. The reason C++ is used more is because there are more libraries for it. 

Remember, the whole reason Java was created was because of a person named James Gosling who didn't like C++. Now, there's another language starting to develop called the D programming language, which takes the best of C++ & Java. 

Low level features are better because they can make the system run faster & are more flexible. Think about it, try making a 3d game in Visual Basic. You can't.

---

### Post by Wybiral on 2007-03-02
> **dojo said:**
> nice reply,Ive seen a few big games written in java like runescape and puzzle pirrates but when you said 

@There are also several ways to make C/C++ programs capable of being compiled for different systems, so someone wanting to write a game to run on different platforms can simply write the code portable and cross compile it. SDL + OpenGL is a good example since code using those libraries can usually be compiled on a number of systems."

So why dont people do this with comercial games like wow in the end wouldnt just increase there sales?Even if it more work for the programers,its there job:).I understand now why some big games reqiure low level langauses.But as you said Time will tell i hope java comes out on top:/.Oh yeah dont some comercial games use a mix of both java and c++?Im attuly planing to make a 3s or maybe 2d mmorpg when i finch learning java.

Well, Java is great for networked games and online games. Especially lower graphics quality.

When I said big, I was referring to codesize and level of graphical detail, not just userbase. There have been a number of Java games to get a big userbase (RuneScape is a good example as you mentioned)

I mostly mean the newer, more graphically intensive games like:
Doom 3 (available on: Mac, Linux, Windows, Xbox)
Quake 3 (available on: Dreamcast, IRIX, Macintosh, Linux, Windows, PlayStation 2)
Half-life 2 (available on: Windows, PlayStation 3, Xbox, Xbox 360)
Halo: Combat Evolved (available: Xbox, Windows, Apple)

These are all written in either C or C++ and as you can see, were able to support multiple platforms.

And their graphics were all pretty good.

Thats the thing that worries me about Java. I know it's capable of OpenGL now, but I have yet to see any substantial demos to show that it can handle higher quality games. I've seen the small JoGL demos and they look nice... But they prove nothing about it's ability to handle a full featured high quality 3d game.

If anyone knows of any Java programs that can show off a BSP level, some models, and special effects like lighting/bumpmapping/etc... I would love to see them. But I just don't think Java has reached those speeds yet.

---

### Post by RedSquirrel on 2007-03-02
> **angryfirelord said:**
> 
One more thing I like about Java is how extensively cross-platform it is. As long as you have the JRE installed on a computer, you should never, never, ever have to edit any of your code (in general terms). Even the GUI is the same, whereas C++ doesn't really have that (you can't use a Windows GUI under Linux natively).

Reminds me of something I read the other day:

** Bjarne Stroustrup:**
>  Java isn't platform independent; it is a platform.:)

Source: [http://www.research.att.com/~bs/bs_faq.html]("http://www.research.att.com/%7Ebs/bs_faq.html")

---

### Post by phossal on 2007-03-02
> **angryfirelord said:**
> **Low level features are better because they can make the system run faster** & are more flexible.

My impression is that *this* is the reason behind the C's dominance in game programming. I've often read that good game programmers are really just hardware experts, especially since games have been marketed for nearly two decades by pushing the "wow" factor - usually anchored by visual improvements.

By the way, I *hate* Java.

---

### Post by Wybiral on 2007-03-02
> **phossal said:**
> My impression is that *this* is the reason behind the C's dominance in game programming. I've often read that good game programmers are really just hardware experts, especially since games have been marketed for nearly two decades by pushing the "wow" factor - usually anchored by visual improvements.

Yeah, if you look at the source code for all of the big, long standing, games written in C, you will find a TON of assembly. Doom and quake are prime examples. I'm looking at the source for quake right now and the files in the source folder are about 40% ".s" with the rest being ".c" and ".h"

I believe John Carmack prefers C over C++ for this reason, because it's easier to integrate with raw assembly. (That's not a quote, just speculation... I would also assume the lack of C++ overhead was a motivation as well)

But, unfortunately Java will never be graced with this ability... It goes against everything Java was built on (which had a lot to do with platform independence). Java's good for many applications, but not cutting edge games.

Actually, some quotes from John Carmack (a legend in the game development industry) from his blog:

> ...The biggest problem is that Java is really slow. On a pure cpu / memory / display / communications level, most modern cell phones should be considerably better gaming platforms than a Game Boy Advanced. With Java, on most phones you are left with about the CPU power of an original 4.77 mhz IBM PC, and lousy control over everything...

> ...Even compiled to completely native code, Java semantic requirements like range checking on every array access hobble it. One of the phones (Motorola i730) has an option that does some load time compiling to improve performance, which does help a lot, but you have no idea what it is doing, and innocuous code changes can cause the compilable heuristic to fail. 

Write-once-run-anywhere. Ha. Hahahahaha. We are only testing on four platforms right now, and not a single pair has the exact same quirks. All the commercial games are tweaked and compiled individually for each (often 100+) platform. Portability is not a justification for the awful performance.

It seems that John isn't too fond of Java.

---

### Post by pmasiar on 2007-03-02
> **RedSquirrel said:**
> Bjarne Stroustrup: Java isn't platform independent; it is a platform.

That's exactly the problem with java, in one sentence, from the guy who knows. Java is a solution (independent application platform) for non-existing problem: we already have platform, and it is GNU/Linux. C is not platform-independent, but is easy enough to port - rest is C libraries, and GNU has all of them, and free.

Java is popular now and because there are many millions lines of existing code, it will be used and maintained for many years - it will be used extensively in big companies, enhanced, even appreciated - but it only rarely it will be loved passionately, used for your hobby pet projects you work on weekends for fun: you will use Python, Ruby, C or Lisp for that. Java is OK for day job, but even people using it daily often use something else for hobby project because coding in Java is too tedious and not exciting and fun.

Even 20 years from now people will be using Java like we still use Cobol, but like Cobol, java is dead branch in evolution of languages. New languages will focus on being fast like C/C++, dynamic like Python/Ruby, or incredibly flexible like Lisp and Forth: but as Linux will take over, being platform-independent C++ with garbage collection will  make less and less sense. All the reinvented wheels, all the incompatible APIs to master.... If you want generics and extensive introspection, you may as well switch to Python - at least in Python it is coded in C and it is fast.

Java feels perfect to people who learned it as the only language and never knew any better. Many people who know other languages, even if they use java daily, but hate it anyway.

IMHO, YMMV, I am not a time traveler.

---

### Post by angryfirelord on 2007-03-03
> **pmasiar said:**
> That's exactly the problem with java, in one sentence, from the guy who knows. Java is a solution (independent application platform) for non-existing problem: we already have platform, and it is GNU/Linux. C is not platform-independent, but is easy enough to port - rest is C libraries, and GNU has all of them, and free.

Java is popular now and because there are many millions lines of existing code, it will be used and maintained for many years - it will be used extensively in big companies, enhanced, even appreciated - but it only rarely it will be loved passionately, used for your hobby pet projects you work on weekends for fun: you will use Python, Ruby, C or Lisp for that. Java is OK for day job, but even people using it daily often use something else for hobby project because coding in Java is too tedious and not exciting and fun.

Even 20 years from now people will be using Java like we still use Cobol, but like Cobol, java is dead branch in evolution of languages. New languages will focus on being fast like C/C++, dynamic like Python/Ruby, or incredibly flexible like Lisp and Forth: but as Linux will take over, being platform-independent C++ with garbage collection will  make less and less sense. All the reinvented wheels, all the incompatible APIs to master.... If you want generics and extensive introspection, you may as well switch to Python - at least in Python it is coded in C and it is fast.

Java feels perfect to people who learned it as the only language and never knew any better. Many people who know other languages, even if they use java daily, but hate it anyway.

IMHO, YMMV, I am not a time traveler.

So, what you're saying is that it doesn't really matter what language you learn because it will be obsolete in 20 years? ;) lol C has been around since the 60's. (although most programming jobs require you to know either VB, C++, and/or Java).

The one key advantage that Java has is using Object-Oriented Programming. C++ somewhat uses it, but Java _requires_ you to use it.

I'm not saying that Java is the best language in the whole wide world (I'm still writing console based programs for my high school course). It's just that I know it's going to be used extensively for a while.

I'm surprised that no one programs directly in binary anymore. :-D

---

### Post by Tomosaur on 2007-03-03
Like many people, I would say that D is going to be the next big thing. I like Java - once you get past the initial WTF, it's actually very easy to throw together a decent application. It won't be the fastest program on the planet, and lord knows it'll probably be ugly as hell before you go tweaking, but it will work, and it will work pretty damn well. It just makes things a lot easier IMO.

However - D takes all of the best bits from C, C++, Java, and fits them all together into something which reads like C++, runs like C, and has the ease of development of Java. You can create purely OO applications with ease, because it retains classes - but you can create standalone functions too, so there's no need to waste time instantiating objects which you're not going to use later on. You have all of the low level functionality of C, garbage collection as standard, and other excellent features. The only drawback is that D is still undergoing heavy design, and as such, doesn't have the extensive libraries that C or C++ have, but it's pretty easy to convert C/C++ code into D code.

[Check it out](http://www.digitalmars.com/d/index.html).

I often just write a short little program to tinker with D, it's just a nice language to write in.

---

### Post by laxmanb on 2007-03-03
Java's had static functions and static imports for a long time... you really don't need to instantiate an object to use functions...

and please, there is a Java platform & the Java language...

The platform will live on forever...Java, JRuby, Jython, Groovy (the JCP's very own dynamic language) and 300 other languages can be run using the JVM. The JVM is really, really suited to server side code( a fault in a Java web app makes the app exit gracefully...) With Vista's 1GB+ RAM req., it's not like C++ or C code equals fast... OpenOffice 1.1 took as much time as Netbeans to load...

The language was built with a set requirement list... it is similar to the C++ language, which was the most widely used language (now Java is), and it was built to promote good programming skills( no goto, etc. etc...)

I have no problem with Java. I LOVE Java. I find programming in Java fun. It has the best IDEs in the market, and they're free... that's just me tho...

PS: Let the flaming continue!!!

---

### Post by Achetar on 2007-03-03
In a way Java is over-hyped. It is much slower than C++ (I can program in Java and C++). But it is platform independent and can be used for web apps. So i guess it is  just not generally capable of say, a graphics intesive game on the desktop. But it can be useful for web stuff, much more so than C++.


I have tried to write this unbiased.

---

### Post by Tomosaur on 2007-03-03
> **laxmanb said:**
> Java's had static functions and static imports for a long time... you really don't need to instantiate an object to use functions...


Except for those ones where, you know, you do. 

Besides, a standalone function to print to standard output is much more sensible than an Outstream.print() function imo.

---

### Post by Achetar on 2007-03-03
> **phossal said:**
> My impression is that *this* is the reason behind the C's dominance in game programming. I've often read that good game programmers are really just hardware experts, especially since games have been marketed for nearly two decades by pushing the "wow" factor - usually anchored by visual improvements.

By the way, I *hate* Java.

good game programmers are NOT just hardware experts. There is a ton of that in there, but there are more than one programming side to it
there is Graphics, Hardware, and Engine programming. And each doesnt require that you know a thing about the other.

(By the way i agree on your view of Java)

---

### Post by elmerfud on 2007-03-03
I'm not a game developer, but I do develop applications for commercial use. 

These days you never know what platform the customer has, so Java or something that runs on QT are about the only choices.  Maybe VB if one wants to start playing with mono on Linux. (It now has a built in VB compiler !)

Of these, I like Java or QT.  If you want to use C/C++, get kdevelop and the QT builder plugins and you've got a pretty nice development platform.

I like Java.  I have Eclispe with visual editor (ve) installed and its great.  Its like a supercharged VB environment without the overhead and Microsoft dependency. 

Is Java overhyped ?  I dunno.  I thought all the Java hype had subsided.  Java is a darn good system as far as I am concerned, especially now that Sun has open sourced the Java virtual machines !  If they would have done that 5 years ago, .Net would have never gotten started. 

I actually think that Java is a bit underhyped.  There was an article on Slashdot a few months back and most developers think its only good for writing browser applets.    Truth is that the modern Java frameworks (Swing, AWT, SWT) are really good.  Eclipse itself is written in Java and its great, although a little bloated.  But then look at everything it does !

My favorite rapid development application, by far, is C++ Builder, by Borland, but it isn't multi platform.  They released Kylix, but it wasn't a good product and it has died.  

Anyway, Java is pretty darn good.

For the record, I am a pretty good C/C++ programmer.  The problem with C/C++ is the lack of a multi platform library except Qt.   If someone came out with a good multi platform library for C/C++, I'd pick it over Java.

---

### Post by Wybiral on 2007-03-03
> **elmerfud said:**
> I'm not a game developer, but I do develop applications for commercial use. 

These days you never know what platform the customer has, so Java or something that runs on QT are about the only choices.  Maybe VB if one wants to start playing with mono on Linux. (It now has a built in VB compiler !)

Of these, I like Java or QT.  If you want to use C/C++, get kdevelop and the QT builder plugins and you've got a pretty nice development platform.

I like Java.  I have Eclispe with visual editor (ve) installed and its great.  Its like a supercharged VB environment without the overhead and Microsoft dependency. 

Is Java overhyped ?  I dunno.  I thought all the Java hype had subsided.  Java is a darn good system as far as I am concerned, especially now that Sun has open sourced the Java virtual machines !  If they would have done that 5 years ago, .Net would have never gotten started. 

I actually think that Java is a bit underhyped.  There was an article on Slashdot a few months back and most developers think its only good for writing browser applets.    Truth is that the modern Java frameworks (Swing, AWT, SWT) are really good.  Eclipse itself is written in Java and its great, although a little bloated.  But then look at everything it does !

My favorite rapid development application, by far, is C++ Builder, by Borland, but it isn't multi platform.  They released Kylix, but it wasn't a good product and it has died.  

Anyway, Java is pretty darn good.

For the record, I am a pretty good C/C++ programmer.  The problem with C/C++ is the lack of a multi platform library except Qt.   If someone came out with a good multi platform library for C/C++, I'd pick it over Java.

Well, in the defense of C/C++ game programmers, mostly all you need is OpenGL. It isn't like a lot of software that requires risking portability when selecting a GUI toolkit, OpenGL is basically the API of choice in 3d games these days (it battles with Microsoft's DirectX/D3D but people who use those are the ones restricting their portability, OpenGL works on almost everything)

You can design your own "GUI" for the game in OpenGL and you never have to question the portability.

When you couple OpenGL with another highly portable library like SDL, the result is easy to use, high quality portability.

Game programmers generally do not need to worry about native windowing API's the way the average software developers do.

So in this area, Java doesn't hold much ground in terms of portability, and when you can lose the extra overhead that makes Java so safe in trade for speed which makes games capable of the graphical eye-candy that they are known for... Most game developers will make that trade.

Java may be great for a lot of applications, but certainly not games. Sure, 2d games and simplistic 3d games should work (RPG's shouldn't be too hard) but I don't see it being able to support the recent wave of graphically intensive FPS and strategy games... It just totes around way too much overhead for that.

---

### Post by phossal on 2007-03-03
> **Achetar said:**
> good game programmers are NOT just hardware experts. There is a ton of that in there, but there are more than one programming side to it: there is Graphics, Hardware, and Engine programming. And each doesnt require that you know a thing about the other.

I'm opinion-free at the moment. I believe I read the bit about game programmers being hardware experts in Irvine's book on Assembly Language. However, after minimal consideration, I think I would agree with him. Breaking game programming into *components* sounds like a management task. Not everyone is a hardware expert afterall. Graphics, hardware and engine programming though? It strikes me as being all *hardware* in the end. No need to convince me though. I don't really care. ;)

---

### Post by Wybiral on 2007-03-03
> **phossal said:**
> I'm opinion-free at the moment. I believe I read the bit about game programmers being hardware experts in Irvine's book on Assembly Language. However, after minimal consideration, I think I would agree with him. Breaking game programming into *components* sounds like a management task. Not everyone is a hardware expert afterall. Graphics, hardware and engine programming though? It strikes me as being all *hardware* in the end. No need to convince me though. I don't really care. ;)

Well... When you distill the modern 3d video game, what you are left with is speed. That is almost always the goal. The more speed you can win, the most intense you can make the graphics (it's like having to work harder for a bigger graphics budget in terms of CPU)

Most of the time, the only way you will reach those levels is through manual work... You do have to have a pretty good understanding of the underlying hardware, otherwise you're not going to get too far in the optimization stage.

Modern engines are littered with assembly. The reason is simple... A generic language like C or C++ is only going to optimize the compiled result so far, it has no idea what is best for a 3d game. The developers however do... And they need to know how to manually squeeze as much power out of that CPU as possible so they can lace their games with all the pretty little graphics that the industry is becoming known for.

> **Achetar said:**
> good game programmers are NOT just hardware experts. There is a ton of that in there, but there are more than one programming side to it
there is Graphics, Hardware, and Engine programming. And each doesnt require that you know a thing about the other.

(By the way i agree on your view of Java)

I disagree... The engine basically encompasses graphics and hardware... Actually, since most modern games use hardware accelerated graphics, you might even say that a large portion of the graphics can be tucked under the hardware category.

Regardless, the engine must bind all of these together in a seamless and synchronized way... Anyone developing one of these parts has to know enough about the other parts for the engine to seamlessly run.

And in almost every corner of a modern game engine you will find... ???

Inline/manual assembly.

---

### Post by phossal on 2007-03-03
A few days ago I made a post about serializing an object into MySQL. I wanted to store a data structure for processing a few days later. Is this something that gives Java an advantage, or is it possible to do effectively the same thing with C and C++? It seems like you could just as easily create a byte array out of a file structure (or just the binary file) and store it for reading later. Having never done it with the C's, would it be necessary to actually write a file to disk or can you turn the data structure into a byte array in memory? I assume Java has the advantage because you can do those things without having to write all of the helper code.

---

### Post by pmasiar on 2007-03-03
> **angryfirelord said:**
> lol C has been around since the 60's. 

lol hardly from 60 - [C]("http://en.wikipedia.org/wiki/C_%28programming_language%29") was developed in 72, "Big Blue C" book published in 78. But I agree that C is ancient - and also C is just a thin layer on top of good assembler. :-) And until CPU will use the kind of opcodes we have now, C will stay with us. I am hoping since mid-80 for a [Forth]("http://en.wikipedia.org/wiki/Forth_%28programming_language%29")-based CPU. Maybe 10-15 years from now, one of 32 CPU cores will be hardwired Forth - and new revolution might begin. And maybe not :-(

> The one key advantage that Java has is using Object-Oriented Programming. C++ somewhat uses it, but Java _requires_ you to use it.

... or java *forces* you to use OOP regardless of your problem? IMHO for beginners and simple problems, procedural approach (with optional using of existing objects) is just fine. Beginners might include ie. expert biologists who want solve some problem simple and quickly - without creating layers of objects to worship OO gods. For funny rant about Java's OO obsession, read [Execution in the kingdom of nouns]("http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html")

> I'm not saying that Java is the best language in the whole wide world (...)  It's just that I know it's going to be used extensively for a while.

and I agreed with you 100% in my previous post - do you understand it differently?

> So, what you're saying is that it doesn't really matter what language you learn because it will be obsolete in 20 years? ;)

Not at all. As best explained in Graham's article [http://www.paulgraham.com/hundred.html](http://www.paulgraham.com/hundred.html) about evolution of languages, IMHO 100 (and even 20) years from now we will have different priorities - and different processors to run our code on. But we can feel now features of language of the future, and try avoid misfeatures which are evolutionary dead ends. Static typing and static exception handling for mainstream application language is one of them, IMHO. We will need to learn new languages without a doubt, but some existing languages are more "future-proof" than other.

Of course C will still be used 20 years from now - kernel, compilers and other deep infrastructure needs be fast and it makes sense to use programmer's time to do it right. But even now nobody thinks doing it in assembler. C share will shrink even more.

Dynamically typed, late binding, garbage collected languages like Python, Ruby and their descendants will be mainstream to allow us create apps quickly, use programmer's time efficiently and burn CPU cycles inefficiently.

Java 9 :-) will still be around like Cobol++, running zillions of lines of statically typed  code in big corporations with layers of byzantine API. People will be still making living of it, and hate it even more passionately than they do now. Java code will be slower than C, and development will be slower than dynamic languages - Java in the "sour" spot.

New more dynamic ways of programming will be mainstream - dynamic exception handling, dynamic memory management (garbage collection), dynamic typing, multiple inheritance, dynamic compiling (according to type information inferred dynamically from running code). Using test-driven development, first tests you will write for your modules will be checking for type information, duck-typing way: does object has all the methods I need? Quick and easy - check type safety dynamic way, but before runtime. Many new ideas: assert? Multiple cores will require parallel processing - what features of Erlang will become mainstream?

IMHO, YMMV. I have no time machine, but booking forward to it.

---

