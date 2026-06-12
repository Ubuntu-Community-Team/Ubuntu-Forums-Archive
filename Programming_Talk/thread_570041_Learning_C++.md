---
title: "Learning C++"
date: 2007-10-07
forum: Programming Talk
---

### Post by #Reistlehr- on 2007-10-07
I've been programming in PHP for the past 7 years now, from php4-php5, and ive been checking out the repo for php6 about every week.

I want to learn C, C#, C++ or D. but i dont know what one. My goal is to program desktop applications that can lets say, go fullscreen, and edit files. I know the whole OO and singleton methods and such, but i just dont know where to start. Main use will probably be on linux, but maybe if it's good i can code it for windows.

I dont want to get my feet wet, iwant to dive right in. I'm a good graphical learner. I like to disect code to see how things work.

Any pointers, links or anything else would be greatly appreciated.

---

### Post by gnuman on 2007-10-07
Read the stickies above for resources and discussions of languages.

C++ is C with OOP added, more or less.  Also consider Python for rapid development capabilities.

Good luck.

---

### Post by ryno519 on 2007-10-07
> **gnuman said:**
> C++ is C with OOP added, more or less.

Don't forget the standard template library. :)

If you want to learn about design patterns I'd say C++ is the way to go. It's a powerful language and you will find a lot of support on GNU/Linux for it. Look into gtkmm for a widget toolset for C++ developers. I like it a lot. Another plus is you can easily use C libraries with your C++ application, so you're not limited by the availability of third party libraries.

Python is alright, but I never learned more than the very basics of the language, so I can't add much.

---

### Post by Auria on 2007-10-07
> **#Reistlehr- said:**
> 
I want to learn C, C#, C++ or D.

My opininon:

C : Old and proven. Simple and clean. Lacks more advanced features, people often use awful hacks to fake OOP.
C++ : And evolution over C. Many more features, no need to fake them anymore. But the language is extremely complex and some parts a bit messy.
C# : no opninion, it's very microsoft-based and mono doesnt have much of the libs i need
D : A cleanup over C++. IMO this is the best for the future but i think it's not yet fully ready. The langauge is stable but it doesn't have many stable libraries or IDEs.

Final word : when you know C++ you know them all. So i'd learn C++. Unless you don't need that power, of course. If you find it too hard, you can start with C# or D (works very well for learning with terminal programs) and use them as stepping stones. But in the end when you master the basic idea it's only syntaxic changes. Only C has less features, but as i said people often fake them anyway.

Little difference though : C and C++ have no garbage colelction and involve you manipulate pointer directly, so it's a bit lower-level.

---

### Post by ryno519 on 2007-10-07
> **Auria said:**
> 
C++ : And evolution over C. Many more features, no need to fake them anymore. But the language is extremely complex and some parts a bit messy.
.

Which parts of the language do you think are messy? I've always found C++ to be rather intuitive.

---

### Post by pmasiar on 2007-10-07
If you don't require low-level efficiency of C or C++ (which I believe you don't), Python can do everything you need, but you code it much, much faster. In weeks instead of months. Still, would be useful to learn C too, in case some of your functions are too slow, and recode them in C (after yo measured where the bottleneck is, and only if you really need it).

---

### Post by ryno519 on 2007-10-07
> **pmasiar said:**
> If you don't require low-level efficiency of C or C++ (which I believe you don't), Python can do everything you need, but you code it much, much faster. In weeks instead of months. Still, would be useful to learn C too, in case some of your functions are too slow, and recode them in C (after yo measured where the bottleneck is, and only if you really need it).

2,066 posts and they're all recommending python. :P

That has to be some kind of record.

---

### Post by Auria on 2007-10-07
> **ryno519 said:**
> Which parts of the language do you think are messy? I've always found C++ to be rather intuitive.

Actually i'm just quoting other people. I myself never had that much problems with C++. But some people do, see [http://en.wikipedia.org/wiki/C++#Problems_and_controversies](http://en.wikipedia.org/wiki/C++#Problems_and_controversies)

Well i made my personal opinion clear anyway, my personnal choice is D as much as possible, C++ otherwise. :)

---

### Post by Frak on 2007-10-07
> **ryno519 said:**
> 2,066 posts and they're all recommending python. :P

That has to be some kind of record.
I see 7, but I also recommend Python, then C++, then C. Take a look at D sometime, it'll do ya some good.

---

### Post by ryno519 on 2007-10-07
> **Auria said:**
> Actually i'm just quoting other people. I myself never had that much problems with C++. But some people do, see [http://en.wikipedia.org/wiki/C++#Problems_and_controversies](http://en.wikipedia.org/wiki/C++#Problems_and_controversies)

Well i made my personal opinion clear anyway, my personnal choice is D as much as possible, C++ otherwise. :)

A lot of those critiques could be considered invalid. The standards compliance one even states that it's not much of an issue anymore. I really don't consider C++ or the STL to be exceedingly complicated. Take containers for instance. How many types of containers do you have? Vectors, lists, deques, strings, queues, priority queues, etc. You don't really have to have intimate knowledge of every single one of these classes, because they all function the same. An iterator for a vector works just like an iterator for a list or a queue (not internally, of course).

Another complaint was that C++ isn't pure OOP. Well, as a language designed to be compatible with C code it really can't be an OOP language without breaking that C compatibility. That being said, it's not hard to make a C++ application purely object oriented if you like, excluding the entry point.

The incompatibility with some C code is the only real issue I see here. It can be a bit of a pain once in a while, but you don't run into incompatibility issues too much and when you do they're pretty easy to fix. Also, most C library maintainers will be more than happy to accept a minor patch which will make their code C++ compatible. The reserved keywords in C++ that don't exist in C doesn't seem to come up much either and is also a very easy fix.

I haven't used D, but I hear good things. I'll have to disagree with you about D having more of a future than C++ though. C++/C/C# aren't going anywhere anytime soon and D developers are going to have to work very hard to get their language into the mainstream. I wish them luck.

---

### Post by LaRoza on 2007-10-07
You can learn a lot on the web, I have made a wiki attempting to make this process easier. The links are in my sig. I have many languages there.

---

### Post by pmasiar on 2007-10-07
> **ryno519 said:**
> 2,066 posts and they're all recommending python. :P

That has to be some kind of record.

Of course every one of us have preferences, and would like influence other people to have same preferences, to guarantee growth of community of each language. 

Yes, I prefer Python, and I would like to Python community to grow.

Yes, if I see situation where Python is good choice, or better choice, I mention it.

You are not correct with your claim that ALL my post recommend Python. Just big majority of them. It has two reasons: 
1) - Python is very good language, widely used, and good fit for most task posted here (mostly by beginners)
2) - If Python is not good choice, and someone already recommended something other, I don't bother to post.

I have no problems with C or C++, I used it when it was best available choice for some project back them when it was. I STILL would advice to everyone to learn C, but as SECOND LANGUAGE, because I strongly believe that for most tasks (including the one OP is facing), Python is the best. Do you want me to put bias disclosure in my sig, so it is 3 pages long? I do it, when you do it. 

so, what is YOUR bias? :-)

---

### Post by engla on 2007-10-08
> **ryno519 said:**
> 
Another complaint was that C++ isn't pure OOP. Well, as a language designed to be compatible with C code it really can't be an OOP language without breaking that C compatibility.

Except: Objective-C. Objective C is a superset of C and totally compatible. It is very object oriented. Not as efficient as C++, but very useful in its very dynamic model. The only users of Objective-C are on the OS X platform though.

---

### Post by Yz85Racer on 2007-10-08
Learn Java. It is much more better - bar CPP.

---

### Post by ryno519 on 2007-10-08
> **pmasiar said:**
> You are not correct with your claim that ALL my post recommend Python.

Well, I was joking so I wasn't expecting to be 100% correct in my exaggerated statement. ;)

> so, what is YOUR bias? :-)

Socialist politics, Canadian beer and the clear superiority of the structuring of OO code vs procedural. :)

---

### Post by LaRoza on 2007-10-08
> **ryno519 said:**
> Well, I was joking so I wasn't expecting to be 100% correct in my exaggerated statement. ;)

Socialist politics, Canadian beer and the clear superiority of the structuring of OO code vs procedural. :)

You were part correct, Forth and Python, not just Python. (Joking here)

Do you like Java or Ruby? I am partial to procedural code, and like Fortran and C.

---

### Post by ryno519 on 2007-10-08
> **LaRoza said:**
> Do you like Java or Ruby? I am partial to procedural code, and like Fortran and C.

I don't enjoy coding in Java, no, but if you're paying me then I'll code as many Java apps as you want.

I've never tried Ruby. I'm more of a PHP5 guy when it comes to web development.

---

### Post by LaRoza on 2007-10-08
> **ryno519 said:**
> I don't enjoy coding in Java, no, but if you're paying me then I'll code as many Java apps as you want.

I've never tried Ruby. I'm more of a PHP5 guy when it comes to web development.

PHP5 all the way! I use PHP5 also for web development. However, my host uses PHP4, and I learned my lesson by coding a site using all the new OO features and having it fail in real life.

Ruby is very OO, you might like it. I can't imagine anyone enjoying coding in java.

---

### Post by ryno519 on 2007-10-08
> **LaRoza said:**
> PHP5 all the way! I use PHP5 also for web development. However, my host uses PHP4, and I learned my lesson by coding a site using all the new OO features and having it fail in real life.

Ruby is very OO, you might like it. I can't imagine anyone enjoying coding in java.

I don't see the point in me learning Ruby at this point in time. I can't foresee myself using it in the conceivable future. Maybe when/if it becomes more mainstream in industry I'll give it a shot.

---

### Post by LaRoza on 2007-10-08
> **ryno519 said:**
> I don't see the point in me learning Ruby at this point in time. I can't foresee myself using it in the conceivable future. Maybe when/if it becomes more mainstream in industry I'll give it a shot.

I don't like Ruby, for several reasons, but I enjoy learning new languages, even I don't use them.

---

### Post by aks44 on 2007-10-08
> **ryno519 said:**
> Which parts of the language do you think are messy?

The "plain old C" part... ;)

---

### Post by ryno519 on 2007-10-08
> **aks44 said:**
> The "plain old C" part... ;)

*rimshot*

What are you going to say next? That GObject is is a mess and scanf is insecure? :P

---

### Post by aks44 on 2007-10-08
> **ryno519 said:**
> What are you going to say next? That GObject is is a mess and scanf is insecure? :P

Are they? :-\"

FWIW I had old C casts in mind (that's the worst IMHO, both design-wise and security-wise)...

---

### Post by ryno519 on 2007-10-08
> **aks44 said:**
> Are they? :-\"

FWIW I had old C casts in mind (that's the worst IMHO, both design-wise and security-wise)...

Tell me about it. I still see people doing C style casts in C++ code all the time. It drives me up the wall. Just because it saves you three seconds doesn't mean it's a good idea!

---

### Post by #Reistlehr- on 2007-10-14
What are the limitations surrounding Python, and likewise with C-Style

---

### Post by Wybiral on 2007-10-14
> **#Reistlehr- said:**
> What are the limitations surrounding Python, and likewise with C-Style

Python: Can't be used for low level stuff like drivers/kernel development.

C: Terrible string handling, manual memory management, lack of exceptions, less portability then HLLs like ruby/perl/python.

But the two can work together really well (embedding Python in C when user scriptability may be needed, or writing modules for Python in C when low level code is needed)

---

### Post by #Reistlehr- on 2007-10-14
Well my honest to god goal, is to make my own IDE, that supports linux/windows (But who cares about windows, i use linux anyway).

I want to add SVN nad FTP support, with Syntax Highlighting. I don't want to go as extreme as like a functions list, but i want to have a file browser and such.

Is this possible with python?

---

### Post by Wybiral on 2007-10-14
> **#Reistlehr- said:**
> Is this possible with python?

Yes, and Python is definitely a better tool for a project of that nature then C.

---

### Post by #Reistlehr- on 2007-10-15
Thank you! I have a little python knowledge, but not enough to make a little project, so time to get reading.

---

