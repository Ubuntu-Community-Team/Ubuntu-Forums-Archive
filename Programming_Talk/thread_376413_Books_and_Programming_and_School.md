---
title: "Books and Programming and School"
date: 2007-03-04
forum: Programming Talk
---

### Post by Dylnuge on 2007-03-04
DISCLAMER: This is not the average "Which Programming Language is the Best."

I have been programming since I was 8-sort of. (Liked computers, bought a C++ book, got freaked out by the word Exponentiation under Basic Math).

I have been actually programming since I was 11. I started with a programing language called DarkBASIC. I have used VisualBasic and more.

I purchased a book on C++, and was going to start reading it. However, this year I took Computer Science at my High School, and they teach Java. Personally, I don't love java-the cross platform is nice, but its not open source (the platform).

Now, I am at a crossroads. I have a book on Visual Basic that I never read and due to my crossover to Ubuntu never will read, a book on C++ that I want to read but never have time to because of Java, and a class that teaches Java. I have heard some good things about C# (that's said C-Sharp, right?), and Microsoft makes it possible to program Xbox 360 games using it now (they need to be made in Windows, though), and heard that Python was really good for teaching, and I will get to that in a minute.

I don't want these expensive books to go to waste, but I am still unsure what language to learn. The problem is that me and a few friends recently started a small company. We all know computers-but I am the only one with programming experience. I am expected to tell them what language to use, since we can't all use different languages.

So here are my thoughts on each language:
Java-Cross Platform and thought at my school, which two of my friends in the business also go to.
C++-Versatile and popular but hard.
Python-Supposedly easy, I don't know anything about it-most likely out.
C#-Nice Features, easy to use, no experiance
VB, etc-No

We are developing games and web-based applications (Using Flash and PHP for the web apps though, so we already know that).

What are your thoughts on which language my company should use, and do you know of any good training resources-preferably good, teach-yourself and free, although thats a dream more then a reality. Also, since they are my friends, does anyone know of a simple test, maybe 50 questions or so, that tells if people are good enough at computers to program, so I can screen them? Thanks.

---

### Post by lnostdal on 2007-03-04
Sun is open sourcing Java this year. By mid 2007 it will be open source.

Games often use more than one language.

I'd probably go for..

* C: Well, it's C. Low-level, not flexible - but good performance for low-level "static parts" that you'd want to optimization in the first place.
* Common Lisp: High-level flexibility like nothing else while still having native compilation for good performance.

..in almost all cases. You get a strong left, and a strong right arm -- covering a lot of area with little overlap.

edit:
some resources for Common Lisp is mentioned here: [http://nostdal.org/~lars/writings/common-lisp-getting-started.xhtml](http://nostdal.org/~lars/writings/common-lisp-getting-started.xhtml) (the book "Practical Common Lisp" (it's free) and the Hyperspec)

for C you want the book "The C Programming Language": [http://www.amazon.com/dp/0131103628](http://www.amazon.com/dp/0131103628) (even if it's old its still the best IMHO)

..but there are also many resources out there for learning game development .. some free and some not so free .. for 3D graphics you probably want OpenGL .. see: [http://nehe.gamedev.net/](http://nehe.gamedev.net/) and [http://www.opengl.org/documentation/](http://www.opengl.org/documentation/) .. for audio you probably want openal and/or fmod .. everything is portable

---

### Post by daniel of sarnia on 2007-03-04
> **lnostdal said:**
> Sun is open sourcing Java this year. By mid 2007 it will be open source.

* Common Lisp: High-level flexibility like nothing else while still having native compilation available for good performance.

..in almost all cases. You get a strong left, and a strong right arm.

Don't mean to hijack the thread, but I've never looked at lisp, I am more of a c and python kind of guy also starting to like how mono and C# are looking.

I'm just wondering why you like lisp over python or purl. Keep in mind I'm saying this not knowing anything about lisp other than using emacs a little.

---

### Post by tbodine on 2007-03-04
My first language was Python, and I highly recommend it.
C#(yes, See-Sharp) is, I believe, a Windows programming language (I haven't read much into it, but when I was using it a long time ago I read something like that).
Donate your BASIC book(s) to a library!

---

### Post by lnostdal on 2007-03-04
daniel of sarnia:
hm .. way too much to mention here(#1) .. try it, spend a year on it .. getting past the initial bumps/thresholds can be quite hard but it's definitively worth the effort

#1: see instead: [http://wiki.alu.org/The_Road_To_Lisp_Survey](http://wiki.alu.org/The_Road_To_Lisp_Survey)

---

### Post by Dylnuge on 2007-03-04
You are not hijacking the thread by any means-I am open to suggestion.

Not too sure yet, but I know that I need to find some good training material. School and trying to start a business are hard enough-no way am I throwing teaching into that.

The main difference between C and C++ is OOP, right? I have heard that C++ is harder/worse, and that C is harder/worse.

No huge games planned yet. I started out the year with a discussion on why design team requests for MMOs constantly get rejected-pointing out that there was a lack of 3D graphic experiance and the most advanced program we had written was a 2D tanks clone with a collision glitch.

Also, I enforced the idea of the GPL. I think that there is very little chance we would actually sell anything-better to get people interested in our company.

So, here are some choices I have already made (please note I am looking for as much cross platform as possible, because I use Linux and I am the only one):
1. We start with Web Design. Everyone learns XHTML 1 Transitional from W3Schools. Everyone learns PHP from W3 Schools. Everyone learns XML from W3Schools. Everyone learns CSS from W3 Schools.

2. Advanced Website Design-Macromedia Studio. Since it is not free, and only I own a copy, most people will be hand coding or desiging while I make the finishing touches. One select person works with me on this.

3. Basic Programming-Need a Language. Hence my Post. Tired of buying $50 books I don't read-I may have what was recommended to me as "the greatest book ever on VB" but I don't want to learn VB.

4. Game Programming-Resources exist for Python. C/C++, and Java. If Java is going open source, these are my top three languages.

5. 3D-OpenGL and Blender.

6. Cross Platform-The further I go, the more likely one platform will start to stand out. I like Linux, Raffi likes Mac, everyone else has Windows (I won't say likes-None of them ever tried Linux/Mac). It looks like Cross Platform will be an issue, but both me and Raffi have learned to get around the common lack of games for our platforms.

7. Finally getting products out there-2008. :-).

Also, does anyone know of a good IDE for C/C++ in Linux? I use NetBeans for Java and Kate for Python.

Thanks
Dylan

---

### Post by Mr. C. on 2007-03-04
No offense to lnostdal's predilection for the language, LISP is an interesting language to be sure, and certainly has a cult following.  However, it has had only marginal or fringe success.  Probably the most ubiquitous usage of the language is Emacs.

It frightens me to think that I studied and programmed LISP...gasp... 27 years ago!  I don't want to start thinking about how many languages I've learned.. and how many I've forgotten!

From an academic standpoint, it along with yesterday's and today's languages and programming environments should be studied and understood; each brings strengths and weaknesses.  Some argued that Snobol was the killer language, Others Algol 68, then C++, then Java, then ...

One of the key problems with Computer "Science" is that it is very little science, and a whole lot of hearsay and NIH syndrome.

So, my opinion, don't toss any of your books - they all have good information, and historic value.

Learn that languages that seem appropriate to you, for the tasks that you choose to undertake.  Consider personal interest, and long term "marketability" - these are all very important.

Enjoy the persuit,
MrC

---

### Post by Dylnuge on 2007-03-04
Thanks Mr. C. Those are some great suggestions, and I think that I am going to go with Java-it's platform will be Open Source soon, and it is a nice language with cross-platform in mind, although I will still take a look at Python and C++.

Anyone know of a good computer skills assesment. Something that could help me tell if people were good enough to learn programming would be preferred, but anything is nice.

---

### Post by lnostdal on 2007-03-04
Just note that Common Lisp is not LISP. Especially not 27-year-old-LISP. :) Some of the most significant things where added way after the original LISP.

When people say "LISP" they usually mean the old dialect(s). Stuff way back from 1959. "Lisp" is sometimes used when "Common Lisp" is meant however.

..but "Lisp" is also a whole family of languages; Scheme and Common Lisp are the ones most used today though. So what is meant when one say "Lisp" is often clear from context:

* Common Lisp (for instance comp.lang.lisp is for Common Lisp)
* One particular Lisp; like Scheme (for instance comp.lang.scheme is for the Scheme-dialect of Lisp)
* The whole family of Lisp-like languages
* ..or the old original Lisp called "LISP"

---

### Post by Mr. C. on 2007-03-04
Our views are not in disagreement.

---

### Post by daniel of sarnia on 2007-03-04
> **tbodine said:**
> My first language was Python, and I highly recommend it.
C#(yes, See-Sharp) is, I believe, a Windows programming language (I haven't read much into it, but when I was using it a long time ago I read something like that).
Donate your BASIC book(s) to a library!

C# is a ecma and iso spec that works on linux and mac though mono, I here it is good for fast (as in execution speed as well as development time) for gui apps. But I personally have yet to really look into it yet.

---

### Post by Ozitraveller on 2007-03-04
My 2 cents... I hope nobody minds if I add my thoughts here?

I've been writing/designing software for around 30 years, and my first programming now no longer exists. And I have learnt many other languages since then. And one thing I have learned along the way is the most languages have many of the basic things in common, e.g. looping, branching, variable declaration and assignment… Once you get to the point where you can see the common things it’s easier to learn a new language. In your situation I go with a language that a few of you know (you said that you and a couple of the other were doing the same java course as school), it’ll make it easier if you can work together. Also java is a c-like language and quite similar to C#. So it’s not that big a jumper to go to c# if you want to. And both java and c# are both sort after commercial languages. And I’m pretty sure that games can be developed in both java and c#. And the big advantage to doing java is that there are a bunch of people at school to talk to about it. In my experience it’s very hard to learn a language and not have anybody to ask questions of.

---

### Post by pmasiar on 2007-03-04
> **Dylnuge said:**
> The main difference between C and C++ is OOP, right? I have heard that C++ is harder/worse, and that C is harder/worse.

OOP or not is not the only difference between languages. Other big differences are: 
(1) memory allocation: Java, Python, Perl, PHP are garbage collected (although using different approaches - Python way IMHO gives little more predictable response time, but I am open to deeper explanation)
(2) type binding. Statically typed languages, Like, C, C++, C# and Java force you to set types at compile time. Dynamically typed languages, like Python, Perl, Ruby, PHP, postpone checking type info (existence of proper methods) to runtime, taking some time but adding whole lot of flexibility.
(3) Exception handling. Static exception handling which Java has makes sure all exceptions are accounted for, but makes harder to write first draft version of the code. Dynamic exception handling allows for much faster  development of pilot prototype - so you can explore couple different designs and check which one suits your needs better.

> Also, I enforced the idea of the GPL. I think that there is very little chance we would actually sell anything-better to get people interested in our company.

Not necessarily. Ie Python is under "artistic license", you can release proprietary code, if you make sure you do not link any GPL libraries - but most libraries are under Python license too. [galcon]("http://renesd.blogspot.com/2006/12/galcon-released.html") is pretty addictive proprietary game written in Python using pygames library.

> 1. We start with Web Design. Everyone learns XHTML (...)
2. Advanced Website Design-Macromedia Studio. (...)
3. Basic Programming-Need a Language. (...)
4. Game Programming-Resources exist for Python. C/C++, and Java. If Java is going open source, these are my top three languages.
5. 3D-OpenGL and Blender.
6. Cross Platform-(...)
7. Finally getting products out there-2008. :-).


Looks like your selection was driven not by needs, but by the price.

IMHO it is fools errand to teach good designer to program, and rely on programmer to pick matching colors. And if you reject paying for tool which helps you to increase your productivity and make more money - you are losing money, not making it.

Why you need both web and desktop programming skills? Web apps are inherently cross-platform (browser compatibility is separate issue). Looks like you did not decide yet what you want to focus on? For web apps, you forgot to mention AJAX - it is all the rage now.

I would recommend to go for Python - wxPython for desktop, or Turbogears/Django/Pylons for web framework. Twisted makes very ... twisted :-) backend server if needed. If Python code is not fast enough, profile it and reimplement bottleneck in C. And with Python, you have better chance that Google would buy you. :-)

and free books? there are plenty. [http://learnpydia.pbwiki.com/HowToStart](http://learnpydia.pbwiki.com/HowToStart) will point you in right directions.

---

### Post by Dylnuge on 2007-03-04
Thanks. What I meant by enforced GPL was not that we would use GPL software, but that we would release our software under GPL. I know I have options, I like the GPL.

My choices are somewhat determined by price. We don't have an office or any money-buying Studio and Maya for everyone was not in my top 10 list. Also, I happen to like Blender, and Cross-Platform, and OpenGL is good for Cross-Platform.

Thanks for all the help. I think each programming language sounds good-I will experiment a little and see what works best. After all, I know that every company must use different languages-getting hired by a company that uses C++ is hard if you use Java, and vice versa.

Popularity of the language is somewhat important to me. I am going to try these langauges and decide which works best:
1. Java
2. C++
3. Python

Other suggestions sounded good, but I think I will stick with these.

---

### Post by daniel of sarnia on 2007-03-04
> **tbodine said:**
> Donate your BASIC book(s) to a library!

Please don't, library's are not dumping grounds for garbage!! lol, ahh BASIC was the first language I learned, I was 7 and twelve years latter I almost have it purged from my head completely.

When that garbage is the first thing you learn from such a young age you outlook on reality is so distorted. Like taking LSD, it just messes with your mind.  Lucky for me when I was ten I found out quake was written in c along with most other games and that's what I originally wanted to do was make games, that's when c became my language of choice.

---

### Post by dancavs on 2007-03-05
hi if your serious about games programming and the gpl, c and/or c++ is the way to go, 3d games are system resource hogs, and java apps are simply too slow. id start with c, opengl and freeglut (a window interface library). once comfortable with opengl and freeglut, id recommend migrating to c++. c++ is not hard if you are comfortable with OOP from using java. 

an ide? if you want to code in linux id recommend a text editor to begin with - (gedit is fine) and start to learn how to use make files. its a pretty steep learning curve all in all - im about a year into it. good luck :)

checkout: 
[http://nehe.gamedev.net/](http://nehe.gamedev.net/)
[http://freeglut.sourceforge.net/](http://freeglut.sourceforge.net/)
[http://fly.cc.fer.hr/~unreal/theredbook/](http://fly.cc.fer.hr/~unreal/theredbook/)

---

### Post by lnostdal on 2007-03-05
> **dancavs said:**
> 
an ide? if you want to code in linux id recommend a text editor to begin with - (gedit is fine) and start to learn how to use make files.

i strongly recommend scons over makefiles .. the `ubuntu-programming' files [here]("http://nostdal.org/~lars/writings/") show how to use scons from emacs .. but other editors should also handle this (simply call scons -u from them)

---

### Post by Ramses de Norre on 2007-03-05
> **Dylnuge said:**
> So here are my thoughts on each language:
Java-Cross Platform and thought at my school, which two of my friends in the business also go to.
C++-Versatile and popular but hard.
Python-Supposedly easy, I don't know anything about it-most likely out.
C#-Nice Features, easy to use, no experiance
VB, etc-No

It seems java is the only language for which you didn't list any disadvantages? I'm taking my second programming course in college now and both courses use java. I think the language is pretty decent as first (and overall) language. Despite all the bad things people here like to tell about it.

---

### Post by pmasiar on 2007-03-05
> **Ramses de Norre said:**
> I'm taking my second programming course in college now and both courses use java. I think the language is pretty decent as first (and overall) language. Despite all the bad things people here like to tell about it.

Looks like java is the only language you have any experience so far, right? I am curious why you think Java is decent compared to something what you never tried.

Java is definitely not good as first programming language - ie. Python does not confuse beginner with strong types and need of typecasting, and does not force beginner to define everything as objects. You just put your values to the list and get them out - no typecasting, no confusing differences between arrays, list, arrayLists, and other kinds of collections, between int and Integer, and other java abominations. All this does not exist in Python, so you can start solving problems - even before you grok OO.

Later, if so desired, you can go to Java, C++, C or whatever, but why to start with such a confusing language? It is decent average production language, used a lot in big companies, and CS teachers teach it because it can land you a job - but C, VB, C++ or C# can do same. If they cared about their students, they should teach basics in simple language (like Python), and then show them what have other popular languages (C/C++/C#/Java, and also PHP/Perl/Ruby) common and different. Wiring their brains in Java makes future programmers disservice - it will be hard for them to even recognize concepts existing in other languages which java is missing.

back to original topic:
IMHO Java is decent (average but not spectacular) programming language, popular in big companies because it allows them to pluck avarage trained coder from the street and put them to any existing java project and in short time expect about average predictable results. So programmers are easily replacable resources, like cogs, to keep market share and average industry performance without rocking the boat.

Startup is in very different position. Your market share is zero, and your only chance to change it is to find couple of above-average hackers, who can rapidly create above-average product to steal market share from your competitors. Graham wrotearticle about why his startup used Lisp to [beat the average competitors](http://www.paulgraham.com/avg.html), how Java is halfway between C++ and Lisp, and why you  [need nerds in startup](http://www.paulgraham.com/icad.html) (and nerds language like Lisp or Python)  to win big, and why [great hackers hate java](http://www.paulgraham.com/gh.html)

[Joel Spolsky](http://www.joelonsoftware.com/Archive.html) has couple good articles how to hire good programmers like [this one](http://www.joelonsoftware.com/articles/fog0000000073.html)- and how to keep them happy.

IMHO, YMMV. Have fun.

---

### Post by Dylnuge on 2007-03-05
> **Ramses de Norre said:**
> It seems java is the only language for which you didn't list any disadvantages? I'm taking my second programming course in college now and both courses use java. I think the language is pretty decent as first (and overall) language. Despite all the bad things people here like to tell about it.

True. Java Disadvantages: Need Runtime Environment installed, JRE can be a resource hog, files are .jar which can be confusing for people used to .exe. Nothing for the programmer, but user problems seem to be a bit high.

> **pmasiar said:**
> Looks like java is the only language you have any experience so far, right? I am curious why you think Java is decent compared to something what you never tried. 

I have C/C++ experience, but only enough to write console programs-Java is easy enough to write GUIs in, especially with an IDE.

> Java is definitely not good as first programming language - ie. Python does not confuse beginner with strong types and need of typecasting, and does not force beginner to define everything as objects. You just put your values to the list and get them out - no typecasting, no confusing differences between arrays, list, arrayLists, and other kinds of collections, between int and Integer, and other java abominations. All this does not exist in Python, so you can start solving problems - even before you grok OO.

Java was not my first-Basic was (DarkBASIC, its like BlitzBASIC in that it is designed for basic Game Programming). However, Python sounds better for people who will have their first language.

> Later, if so desired, you can go to Java, C++, C or whatever, but why to start with such a confusing language? It is decent average production language, used a lot in big companies, and CS teachers teach it because it can land you a job - but C, VB, C++ or C# can do same. If they cared about their students, they should teach basics in simple language (like Python), and then show them what have other popular languages (C/C++/C#/Java, and also PHP/Perl/Ruby) common and different. Wiring their brains in Java makes future programmers disservice - it will be hard for them to even recognize concepts existing in other languages which java is missing.

If a public high school finds enough money to hire teachers experienced in all languages they would. The school teaches Java because they know it-also, I don't think any language is "too hard" to learn from. You can operate in Java without even knowing what typecasting and pardigams are-most students in my class do.

> back to original topic:
IMHO Java is decent (average but not spectacular) programming language, popular in big companies because it allows them to pluck avarage trained coder from the street and put them to any existing java project and in short time expect about average predictable results. So programmers are easily replacable resources, like cogs, to keep market share and average industry performance without rocking the boat. 

I don't care about the popularity of the language for me or my friends. I want to run a company when I grow up, not work for one. Strike that-I want to run a company now. :-)

> Startup is in very different position. Your market share is zero, and your only chance to change it is to find couple of above-average hackers, who can rapidly create above-average product to steal market share from your competitors. Graham wrotearticle about why his startup used Lisp to [beat the average competitors](http://www.paulgraham.com/avg.html), how Java is halfway between C++ and Lisp, and why you  [need nerds in startup](http://www.paulgraham.com/icad.html) (and nerds language like Lisp or Python)  to win big, and why [great hackers hate java](http://www.paulgraham.com/gh.html)

Of course I need nerds/hackers/coders to startup. I sometimes hate myself for choosing friends who I know will work hard but don't know how to code, then I hate myself for even thinking I should not choose friends. I do have friends who know how to code, maybe I should open up and invite them in.

Thanks for the advice.

I finally have made my decision. I will learn Python, find a good resource for it, and tell my friends to learn from it too. If they can't, they can't work with me.

---

### Post by pmasiar on 2007-03-05
> **Dylnuge said:**
> If a public high school finds enough money to hire teachers experienced in all languages they would. The school teaches Java because they know it
For teachers, learning Python good enought to be able to teach beginner students should be easier than learn java. Also, teachers do not have to be experts in all these other languages - just capable enough to point out differences.

But then again it would expect district's Bored By Education :-) to competent enough to hire competent people - iow hard task.

You know this old saying: if you can code -- you go and code. If you cannot code, you manage coders. If you cannot even manage coders, you go teach them. And if you cannot even teach, you go to government to control, regulate and oversee the industry. :-)

> I finally have made my decision. I will learn Python, find a good resource for it, and tell my friends to learn from it too. If they can't, they can't work with me.

Every competent coder can learn Python (or any other new language) in couple weeks. If she cannot, she was not competent to start. Harder part than learning syntax is learning libraries you need in your problem area. And learning competent methods to test, debug and deploy application is separate matter - good thing you need only one QA process for whole company. :-)

---

