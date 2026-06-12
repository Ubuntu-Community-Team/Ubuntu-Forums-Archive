---
title: "Is there any Java expert here?"
date: 2010-11-27
forum: Programming Talk
---

### Post by zhaotianwu on 2010-11-27
Hi, I'm a programming fan, beginner though. I want to learn Java programming in Ubuntu environment. Now I have Ubuntu fresh installed, how and where can I download Java and start to write my own "helloworld" code from scratch? Any guide would be appreciated.

---

### Post by The Cog on 2010-11-27
Moved to programming talk. It won't get buried so quickly there, and it's more likely to get good answers.

I would suggests that you install packages **openjdk-6-jdk** and **openjdk-6-doc** for starters. This goves you the compiler, runtime and documentation.

You'll need an editor. gedit will do, but I prefer geany (also in synaptic).

The documentation package should give you a good introduction. I have also heard good words about an on-line book called "thinking in java" but it's a while since I played wiht java and there may be better references around now.

---

### Post by PaulM1985 on 2010-11-27
I would recommend going to the software centre:  Applications->Ubuntu Software Centre and downloading Netbeans.  I find this a really easy to use IDE (integrated desktop environment) which will allow you to write and develop your own software.

The Netbeans software is something that my university make us all use on my course and can be used to write standard software as well as web-based enterprise systems.

Other people may suggest Eclipse, which is a similar piece of software, but I personally prefer Netbeans.  It is up to you to see what you feel is the most intuitive.

Good luck with your learning.

Paul

---

### Post by Tcressy on 2010-11-27
Ahhhh, started with programming Java as a first language myself. It has its pros and cons. Just make sure you understand what a pointer is!!!! Many java programmers screw that up when finally transitioning into C/C++. Just remember that "=" does not translate to "equals to" in programming. I digress though :)

You definitely want to use Eclipse as an IDE, many people do use netbeans, and its good if your looking for the simpler approach. But i still recommend eclipse, simply because its well supported, has great addon features, and you can easily use it with other languages. Should at minimum check out their website for yourself [www.eclipse.org](www.eclipse.org)
Plus, if you really want to go for the simple approach you should just get dr. java! 
cheers!

---

### Post by ziekfiguur on 2010-11-27
I would recommend using a normal editor like gedit, kate or scite and using the terminal to compile, so you actually learn what is happening when you compile your code. You can always move on to an IDE after you get that.

---

### Post by trent.josephsen on 2010-11-27
I also recommend starting with a plain editor and compiling from a shell.  But then, I also recommend not starting with Java, so you've already broken the best advice I had to give.

---

### Post by zhaotianwu on 2010-11-28
> **trent.josephsen said:**
> I also recommend starting with a plain editor and compiling from a shell.  But then, I also recommend not starting with Java, so you've already broken the best advice I had to give.

  What would you suggest start with? I am quite determined to learn a USEFUL not a simple language, though.:p

And my work will relate to much of information visualization and object-oriented database. That's why I chose Java over some other simple languages, such as VB.

---

### Post by zhaotianwu on 2010-11-28
> **The Cog said:**
> Moved to programming talk. It won't get buried so quickly there, and it's more likely to get good answers.

I would suggests that you install packages **openjdk-6-jdk** and **openjdk-6-doc** for starters. This goves you the compiler, runtime and documentation.

You'll need an editor. gedit will do, but I prefer geany (also in synaptic).

The documentation package should give you a good introduction. I have also heard good words about an on-line book called "thinking in java" but it's a while since I played wiht java and there may be better references around now.

Thanks for this advice. What is the difference between "**openjdk-6-jdk**", "**openjdk-6-doc**" and "netbeans" or "eclipse"? Do I need both?

---

### Post by GregBrannon on 2010-11-28
The "-doc" file provides the documentation.

NetBeans and Eclipse are both Integrated Development Environments, or IDEs.  No, you don't need both - you don't NEED either, in fact - but you may want to try both to see which you prefer.  Both have similar capabilities with slightly different ways of doing things and both have relatively large resource requirements.

There are lighter weight (requiring less computing resources) IDEs. Geany is most often recommended in the lightweight division because of its full feature set and outstanding performance.

Others have given the advice to not use an IDE when learning how to program - a theme you'll see repeated often.  For that you just need a text editor.  The text editor options are many, including Vi/Vim, Emacs, gedit, kate, and on and on.  Some of those can be tailored to give some of the features typical to IDEs, like syntax highlighting.

Whichever path you choose, get started and good luck!

---

### Post by trent.josephsen on 2010-11-28
> **zhaotianwu said:**
> What would you suggest start with? I am quite determined to learn a USEFUL not a simple language, though.:p

And my work will relate to much of information visualization and object-oriented database.

That may be.  My job will probably involve writing lots of assembly code and VHDL, but I am really, **really** glad that I didn't use either of those as a first language; it probably would have scared me off permanently.

You may very well end up using Java eventually, but it really doesn't offer much to beginners.  Java would be my first choice for a 10,000 line GUI program that had to run exactly the same on every deployed system in a large enterprise.  The problem is that to make good use of the good features it offers, you really need to know how to program already, and understand OOP, design patterns, memory models, and a host of other things.

So in answer to your question, I say start with Python.  It's well-designed, simple to learn and powerful.  A lot of people will recommend "A Byte of Python"; it seems like a good tutorial.

I wouldn't suggest learning Java until you're comfortable with C.  A lot of the design decisions of Java will make far more sense with some background in pointers and memory management.

The standard disclaimer applies.

---

### Post by CptPicard on 2010-11-28
> **trent.josephsen said:**
> 
I wouldn't suggest learning Java until you're comfortable with C.  A lot of the design decisions of Java will make far more sense with some background in pointers and memory management.


I'm in complete agreeement with the rest of the post, but I'm not sure C is that helpful... the basic control structures that are common are just as well learned from Java itself, and the interesting bits that make Java what it is are not present in C. That is, it's all about learning to make use of classes and programming in object-oriented terms...

I guess what you're referring to with memory management and pointers is getting the idea of object on the heap vs. reference to object on the stack. Even that is quite understandable within Java's own rules... no malloc required :)

---

### Post by zhaotianwu on 2010-11-28
> **trent.josephsen said:**
> 
So in answer to your question, I say start with Python.  It's well-designed, simple to learn and powerful.  A lot of people will recommend "A Byte of Python"; it seems like a good tutorial.


Thanks for this piece of advice. I've checked a bit about Python, it does seem very attractive for beginners. However I have one concern. Since within the open source community a lot of code are written in Java, if I use Python does it mean I will lose a lot of opportunity to take advantage of those open source code out there? If Java is the ultimate choice, then what is the point wasting time learning a different language? Considering that I have a little background knowledge about C and pointer back in high school, I think with effort I will learn Java very well.;)

I also want to ask another practical question here. If I want to use Netbeans, on their webpage: Java SE, JavaFX and Java, which one should I download?
[http://netbeans.org/downloads/index.html?pagelang=](http://netbeans.org/downloads/index.html?pagelang=)

I don't need to use it to design any web-based applications. I use it totally for my desktop.

Many thanks.

---

### Post by trent.josephsen on 2010-11-28
> **CptPicard said:**
> I'm in complete agreeement with the rest of the post, but I'm not sure C is that helpful... the basic control structures that are common are just as well learned from Java itself, and the interesting bits that make Java what it is are not present in C. That is, it's all about learning to make use of classes and programming in object-oriented terms...

I guess what you're referring to with memory management and pointers is getting the idea of object on the heap vs. reference to object on the stack. Even that is quite understandable within Java's own rules... no malloc required :)

Eh, I wasn't trying to put much stress on C in particular; the main point was to become a competent programmer before using Java.  C is IMO a good stepping stone.  Without a good understanding of how to write programs, Java's design makes very little sense.  (In fact, sometimes it just doesn't make much sense at all... but that's another topic.)

As for the interesting bits of Java not being present in C, that's kind of the point of learning C first.  You won't be able to make the best use of Java's special features unless you understand what it's really doing and what the motivation behind the design is.

And there's quite a bit more to memory management than you mention, although I'm sure you're already aware of that.

---

### Post by Sammi on 2010-11-30
I'm just finishing up my first semester studying software development. We've been using this book for our basic introduction to Java, and programming as a whole: 
[http://www.amazon.com/Objects-First-Java-Practical-Introduction/dp/013197629X](http://www.amazon.com/Objects-First-Java-Practical-Introduction/dp/013197629X)

You can see that the user reviews on Amazon are good.

I don't want to sound like an ad, but I just have to give this book a shout, because I can so strongly and honestly recommend it. It has thought me a lot about Java, basic types and methods, and basic object oriented programming. It really was the best book I've read for any course ever.

There's is one caveat, and that is that this book might be hard to follow without a support system of some sort. It is supposed to be used in a school setting, where teachers and other students can help each other get through the exercises, which get quite hard in the middle of the book.

---

### Post by PaulM1985 on 2010-11-30
> **zhaotianwu said:**
> 
I also want to ask another practical question here. If I want to use Netbeans, on their webpage: Java SE, JavaFX and Java, which one should I download?
[http://netbeans.org/downloads/index.html?pagelang=](http://netbeans.org/downloads/index.html?pagelang=)

I don't need to use it to design any web-based applications. I use it totally for my desktop.

You probably only want Java SE (Java Standard Edition) if you are only planning on writing desktop applications.  If this is what you want, I would recommend installing Netbeans from the Software Centre in Ubuntu, rather than downloading from the Netbeans website.

Paul

---

### Post by ziekfiguur on 2010-11-30
> **zhaotianwu said:**
> Since within the open source community a lot of code are written in Java, if I use Python does it mean I will lose a lot of opportunity to take advantage of those open source code out there? If Java is the ultimate choice, then what is the point wasting time learning a different language? Considering that I have a little background knowledge about C and pointer back in high school, I think with effort I will learn Java very well.;)
\

As far as I have seen, there is at least as much open-source Python code as java. I think even more, seeing that Python is part of the default ubuntu distribution, but Java isn't. In my opinion, Java certainly is not the ultimate choice.
Also, you won't waste time learning a programming language, learning a new programming language will likely improve your programming skills in the languages you already know. Although I would recommend starting with Python, once you know your first language you should start looking at some others anyway.

---

### Post by zhaotianwu on 2010-11-30
> **ziekfiguur said:**
> As far as I have seen, there is at least as much open-source Python code as java. I think even more, seeing that Python is part of the default ubuntu distribution, but Java isn't. In my opinion, Java certainly is not the ultimate choice.
Also, you won't waste time learning a programming language, learning a new programming language will likely improve your programming skills in the languages you already know. Although I would recommend starting with Python, once you know your first language you should start looking at some others anyway.

Thank you. I find your advice most convincing. I will start with Python. Can you recommend a forum (preferably as newbie-friendly as this Ubuntu one), where I can get real-time communication with some advanced users?
By the way, do you think jython is a good choice if one wants to learn both Java and Python? If so, how to install it to Netbeans?

---

### Post by PaulM1985 on 2010-11-30
I would recommend learning one or the other.  Jython can be installed as a plugin of Netbeans once Netbeans is installed.

Paul

---

### Post by lucasart on 2010-11-30
> **zhaotianwu said:**
> What would you suggest start with? I am quite determined to learn a USEFUL not a simple language, though.:p

And my work will relate to much of information visualization and object-oriented database. That's why I chose Java over some other simple languages, such as VB.

Depends what you want. If you really want to understand programming deep down inside, and write code that is very fast, then begin with C, and then C++. But don't start with C++ direct, or you'll forever remain a newbie who doesn't understand the low-level issues, such as using pointers, understand how a call stack works, how exceptions unwind through the stack, why non-trivial objects should be passed as reference etc.

Otherwise, Python is very easy for beginners, and very trendy nowadays. It's quite slow, but very powerful and useful in practice. But do not touch VB, it's a proprietary Microsoft language, and you surely don't want to become dependant on them, nor to encourage their monopoly...

I don't like Java, so my biaised advice is not to touch it ;)

So to summarize, if you want to really go hardcode then C/C++, or if you want to program highlevel then Python.

---

### Post by trent.josephsen on 2010-11-30
While it's true that C will probably give you a deeper understanding of the machine, I still wouldn't recommend it for newbies.  Programming well is more than just learning the right languages in the right order; your skill reflects how much effort you put into understanding what you are doing.  I would still (and always) suggest Python first, just to become comfortable with the tools and terminology under a language with simple syntax and significant hand-holding.  (I also wouldn't describe it as "quite slow", but I suppose that depends on what you're doing and how you measure it.)

After you're comfortable with Python, you might try going straight to C, or you might try Perl first.  Perl is expressive and practical, with the well-earned moniker of "Swiss Army chainsaw of programming languages", and it's quite a bit sloppier than Python, but the syntax is more in the fashion of a C-like programming language.

... at this point I'm just going to point you to [ESR's advice on learning to program](http://www.catb.org/~esr/faqs/hacker-howto.html#skills1), because if I continue I'm just going to sound like I'm parroting him.

---

### Post by lucasart on 2010-11-30
> **trent.josephsen said:**
> While it's true that C will probably give you a deeper understanding of the machine, I still wouldn't recommend it for newbies.  Programming well is more than just learning the right languages in the right order; your skill reflects how much effort you put into understanding what you are doing.  I would still (and always) suggest Python first, just to become comfortable with the tools and terminology under a language with simple syntax and significant hand-holding.  (I also wouldn't describe it as "quite slow", but I suppose that depends on what you're doing and how you measure it.)

After you're comfortable with Python, you might try going straight to C, or you might try Perl first.  Perl is expressive and practical, with the well-earned moniker of "Swiss Army chainsaw of programming languages", and it's quite a bit sloppier than Python, but the syntax is more in the fashion of a C-like programming language.

... at this point I'm just going to point you to [ESR's advice on learning to program]("http://www.catb.org/%7Eesr/faqs/hacker-howto.html#skills1"), because if I continue I'm just going to sound like I'm parroting him.

You're right. Python is the best choice for a beginner. It will allow you to teach yourself and experiment in algorithmics, and do things that actually are practical and cool.

But it depends what you're looking for in programming: do you want results ? or do you want understanding ? Personally I am not a proffessional programmer only a hobbist, and I only ever sought understand which is why I started with assembly first, then C, then C++. I also do some VB and Python for practical reasons, but I don't enjoy it as much as C/C++.

But once you master it, and *if* want to learn what is really behind all these highlevel languages and how the machine works, you should read the Kerninghan & Ritchie (ebook pdf just google it). Just remember that C is the grale, here are many reasons why:
* this very system you're using is made up of millions of lines of C code. even the horrible Windows you were probably using before also is written in C and C++.
* It's the only language that has been around and almost never changed since the early 1970's.
* if a programming genious like Linus Torvaldes only codes in C, there is a reason

---

### Post by trent.josephsen on 2010-11-30
@lucasart:  I think you're distorting the issue by introducing a false choice between programming for results or programming for understanding.  Lest you misinterpret my previous statements, let me say for the record that I strongly advise the OP to learn C, but not as a first language.  I believe that it's possible to reach a deeper understanding quicker by learning the basics with a hand-holding language like Python, and then moving down to the lower level of C.

> **lucasart said:**
> * this very system you're using is made up of millions of lines of C code. even the horrible Windows you were probably using before also is written in C and C++.
* It's the only language that has been around and almost never changed since the early 1970's.
* if a programming genious like Linus Torvaldes only codes in C, there is a reason
All this is totally irrelevant and questionably true.

---

### Post by zhaotianwu on 2010-12-02
> **lucasart said:**
> 

But do not touch VB, it's a proprietary Microsoft language, and you surely don't want to become dependant on them, nor to encourage their monopoly...


Thank you lucasart, and everybody who gave me precious advice here! 
I have a question concerning VB. I know it's a proprietary language and I don't like it in this regard either. But is it safe to say that ANYTHING in VB you can do it in Python? Is Python as good in GUI WYSIWYG design as VB is?
I currently mainly use Linux, but I do have quite a lot of Microsoft Outlook .PST files that I will have to process (and maybe convert to something that I can use in Ubuntu later). What do you think of it?

---

### Post by ziekfiguur on 2010-12-02
> **zhaotianwu said:**
> Thank you lucasart, and everybody who gave me precious advice here! 
I have a question concerning VB. I know it's a proprietary language and I don't like it in this regard either. But is it safe to say that ANYTHING in VB you can do it in Python? Is Python as good in GUI WYSIWYG design as VB is?
I currently mainly use Linux, but I do have quite a lot of Microsoft Outlook .PST files that I will have to process (and maybe convert to something that I can use in Ubuntu later). What do you think of it?
As long as you're talking about stand-alone programs, yes, you can do anything thats possible in VB in Python. 
However if you want to write plugins, some programs might only accept plugins written for .NET (VB or C#)
But, the reverse is also true, there are also programs that only accept Python plugins.

---

