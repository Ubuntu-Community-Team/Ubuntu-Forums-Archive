---
title: "Best crossplatform programming language"
date: 2006-12-07
forum: Programming Talk
---

### Post by Thumper322 on 2006-12-07
Hello all,

I dabbled in programming under Windows (a bit of PHP, C++, and Java), and I was wondering: What programming language would be best for crossplatform coding? I'd like to write programs that *nix users and Windows users alike can run.

I've heard that Java, while crossplatform, is too slow, so is that a viable option? Also, I've heard of "compiling" Java code into native machine code--or something like that--using **gcj**; would this speed things up any, and would it work for Windows?

Finally, what GUI toolkit should I use? I'd like something that blends into the OS and isn't hideous--so, in the case of Java, Swing and AWT are definitely out. (Azureus looks pretty good and works across platforms; doesn't it use SWT or something?)

Thanks for any tips...

---

### Post by daniminas on 2006-12-07
i like python too ))

---

### Post by Ramses de Norre on 2006-12-07
I think Java is the best for your purpose, it's absolutely cross platform (I send my class files to windows users often) and the speed really isn't such an issue. (It's definitely faster than any cross platform scripting language like python or perl).

Compiling from Java into machine language would be pretty silly.. at first machine language is machine dependent and thus absolutely not cross platform compatible. And second: you'd loose a lot of the very useful concepts Java has, you'll notice when you dig a bit deeper into Java.

And there are several toolkits: swing, gtk, qt, wxwidgets.. I don't know much about them but most of them are platform independent (but some like gtk and qt require the toolkit to be installed on the user's pc).

---

### Post by meng on 2006-12-07
Yup, this question's never been asked before. :p

My vote would be for Python. I've become increasingly disillusioned with Java over the years. That said, I'll admit Java still has its strong points.

---

### Post by pmasiar on 2006-12-07
Crossplatform: if you require peak hardware performance, plan to hack on kernel, nothing can beat plain C. 

Every other use, especially if you value your own productivity, python is the winner. People claim being 10 times more productive in python than in java (I am at least 20 times :-) ). Google for java guru Bruce Eckel compaing java and python. You have even IronPython for .NET, no java will be ever ported for .NET, sorry.

---

### Post by Hendrixski on 2006-12-07
I haven't used python yet, but I would say Java based on my experience.

C is fading into obscurity, and I've used Object PASCAL, it only works on windows, and nobody uses it, it is obscure.  Don't use it.

C++ works everywhere too, but compared to java, and C#, it's not as effective.  I really have got to try python, I keep hearing good things about it.

---

### Post by sailingboarder on 2006-12-07
i use java (both when i was on windows and now on ubuntu), and have had no problems with it
then again, i don't make massive, system intensive programs
unless system performance is going 2 be crucial for you, then def go with java, for it is the best 100% platform independent language there is
plus, if u really do need the system performance, then u should make different versions tweaked for each platform

---

### Post by foxylad on 2006-12-07
As an old c hacker, I also vote Python. I tried it when it kept popping up in great applications, and fell in love. It is so intuitive that after writing the code for an application, most of my applications "just work". No debug cycles at all.

Another huge advantage is that it is so readable. You can give python code to pretty much anyone (I showed a sales person through some the other day) and they get it. So in terms of others (or yourself a month or two down the track) supporting your code, it wins hands down.

Cheers!
Foxylad.

---

### Post by pmasiar on 2006-12-07
> **Hendrixski said:**
> C is fading into obscurity.

C++ works everywhere too, but compared to java, and C#, it's not as effective.  

LOL! Language used to write Linux kernel fading into obscurity?

C++ is more effective than java, but harder to code in. Thats why they invented java: to make OO programming in C++ easier. C# is java from MS (by Stroustrup, author of C++). All are statically typed languages. Try dynamic language like python and feel the difference. 

Read [why hacker use python]("http://www2.linuxjournal.com/article/3882") [language for next 100 years]("http://www.paulgraham.com/hundred.html") [wikipedia entry for Python]("http://en.wikipedia.org/wiki/Python_%28programming_language%29") and [Comparison of programming languages]("http://en.wikipedia.org/wiki/Comparison_of_programming_languages#Expressiveness")

---

### Post by daniminas on 2006-12-07
python and c++ are in different levels... but, in crossplatrorm python wins :)

---

### Post by ghostdog74 on 2006-12-07
> **Ramses de Norre said:**
> ...
(It's definitely faster than any cross platform scripting language like python or perl)
...


Faster in terms of?? code development time?? execution? Any examples to prove this???

---

### Post by Thumper322 on 2006-12-08
Whoa... lots of responses. Quite a divisive topic.

I'll put up a poll later, when I have some time.

So, it's Java vs. Python?

---

### Post by hod139 on 2006-12-08
> **Thumper322 said:**
> 
So, it's Java vs. Python?

Not again...](*,)

---

### Post by pmasiar on 2006-12-08
This is more a meta-answer: how to select a language to learn and use.

Don't ask what we prefer, for *our* own purposes (or purposes of companies where we work): because we prefer different languages for our different goals, and want recruit you to worship our gods, of course. Everybody wants to prove that his decision is the right one. :-)

To make *your own* mind, check [wikipedia]("http://en.wikipedia.org/wiki/Comparison_of_programming_languages"). Compare [python ]("http://en.wikipedia.org/wiki/Python_%28programming_language%29")and [java]("http://en.wikipedia.org/wiki/Java_%28programming_language%29").

What features are more important to you? Is for you more important language easy to learn , where you can quickly write working code? Use python. Want to learn language to get a job in a bank? Learn java or C#. Language to program device drivers? C. Web applications? ruby or python are the hottest, and of course javascript (using AJAX). Hack on kernel? C and nothing else. Contribute do KDE? C++ only, please. Want language what mark Shuttleworth prefers to use for Ubuntu? It's python. :-)

Try it. First language inplemented on every platform is C. But it is used to port these crossplatform tools and systems (like linux kernel, GNU, gcc, python, etc), to make platform usable.

Python is already installed in ubuntu, java is not hard to install either. Try to write a program which reads file and looks for a string, like analyzing log for suspicious activities.
 
Languages change. COBOL was *the* language 30 years ago. Would anyone want to learn it now? Read  [The hundred-year language]("http://www.paulgraham.com/hundred.html") about what future language might look like.
If you want to be programmer, you cannot restrict yourself to single language only, even if java people will try to trick you into believeing it :-)

And if you ask subquestion: what should be my first language? Then answer is easy: learn python first. It is much simpler and forgiving to beginner that almost anything else, and when you understand what programming is about, you can learn java, C++, C# or whatever.

---

### Post by Thumper322 on 2006-12-08
> **pmasiar said:**
> This is more a meta-answer: how to select a language to learn and use.

Don't ask what we prefer, for *our* own purposes (or purposes of companies where we work): because we prefer different languages for our different goals, and want recruit you to worship our gods, of course. Everybody wants to prove that his decision is the right one. :-)

To make *your own* mind, check [wikipedia]("http://en.wikipedia.org/wiki/Comparison_of_programming_languages"). Compare [python ]("http://en.wikipedia.org/wiki/Python_%28programming_language%29")and [java]("http://en.wikipedia.org/wiki/Java_%28programming_language%29").

What features are more important to you? Is for you more important language easy to learn , where you can quickly write working code? Use python. Want to learn language to get a job in a bank? Learn java or C#. Language to program device drivers? C. Web applications? ruby or python are the hottest, and of course javascript (using AJAX). Hack on kernel? C and nothing else. Contribute do KDE? C++ only, please. Want language what mark Shuttleworth prefers to use for Ubuntu? It's python. :-)

Try it. First language inplemented on every platform is C. But it is used to port these crossplatform tools and systems (like linux kernel, GNU, gcc, python, etc), to make platform usable.

Python is already installed in ubuntu, java is not hard to install either. Try to write a program which reads file and looks for a string, like analyzing log for suspicious activities.
 
Languages change. COBOL was *the* language 30 years ago. Would anyone want to learn it now? Read  [The hundred-year language]("http://www.paulgraham.com/hundred.html") about what future language might look like.
If you want to be programmer, you cannot restrict yourself to single language only, even if java people will try to trick you into believeing it :-)

And if you ask subquestion: what should be my first language? Then answer is easy: learn python first. It is much simpler and forgiving to beginner that almost anything else, and when you understand what programming is about, you can learn java, C++, C# or whatever.

Thanks! This is a perfect answer. :-D

I'll start out with Python, then, and see how well it goes... What do I do about setting up a GUI in Python?

My program isn't supposed to be rock-solid or anything; it needs to be relatively fast and crossplatform, as I'm making this to run on my box (Ubuntu) and a few friends' (WinXP :-#).

Is wxPython any good? I've heard about it, but don't know much. In any case, native controls are a must.

---

### Post by pmasiar on 2006-12-08
> **Thumper322 said:**
> it needs to be relatively fast and crossplatform, as I'm making this to run on my box (Ubuntu) and a few friends' (WinXP :-#).

what your program will do? Is GUI requirement, or nice-to-have? Command-line is so much simpler, and wxPython is not in universe - need to install by yourself. Ask experts, not me :-)

> Is wxPython any good? I've heard about it, but don't know much. In any case, native controls are a must.

wxWidgets is as good as it gets - and does have native controls. I don't use it tho - web frontend for database apps is my area.

---

### Post by Thumper322 on 2006-12-08
> **pmasiar said:**
> what your program will do? Is GUI requirement, or nice-to-have? Command-line is so much simpler, and wxPython is not in universe - need to install by yourself. Ask experts, not me :-)



wxWidgets is as good as it gets - and does have native controls. I don't use it tho - web frontend for database apps is my area.

GUI is a requirement. What's the difference between wxPython and wxWidgets? Can you point me to a good tutorial on how to get started?

---

### Post by pmasiar on 2006-12-09
WxPython is python binding (= wrapper) for library wxWidgets (written I guess in C++). wxWidgets is a wrapper around native GUI libraries for each platform. So you need to install both wx thingies, matching versions.

To start, find wxPython homepage, they have FAQ, tutorials etc. Google is your friend - I never used wxWidgets, sry. I usually start my learning of any new area from a relevant wikipedia page, in your case it would be  [wxWidgets]("http://en.wikipedia.org/wiki/Wxwidgets") page. I can see links to wxPython (with tutorial screencasts) and wxGlade GUI designer. Good stuff.

---

### Post by jan247 on 2006-12-09
Java - for everything - including full blown servers and its own database, but high learning curve and not so speedy development

Python - for smaller applications or applets - desktop and some web only, but development time is really shorter compared to java

---

