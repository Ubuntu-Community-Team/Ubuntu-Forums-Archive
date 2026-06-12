---
title: "C++ in 21 days? Really?"
date: 2008-12-19
forum: Programming Talk
---

### Post by xarte on 2008-12-19
So it seems like C++ is a good place to start.

[http://newdata.box.sk/bx/c/](http://newdata.box.sk/bx/c/)

I'm a bit dubious about the 21 day bit - I assume it's really a crash course that gives me a bit of a kick-start, but it certainly makes it look achievable. 

I found this nice list of C++ resources
[http://www1.epinions.com/book-review-25E8-9A58F3F-392BE424-prod1](http://www1.epinions.com/book-review-25E8-9A58F3F-392BE424-prod1)

the only downer is... it's Microsoft. WAAAAAHHHHH. *sob* *sob*

Does this mean I'm going to have to *gulp* make space for an XP partition on my (not so spacious) hard drive? Or will virtualboxing do the trick?

---

### Post by namegame on 2008-12-19
> **xarte said:**
> 
the only downer is... it's Microsoft. WAAAAAHHHHH. *sob* *sob*

Does this mean I'm going to have to *gulp* make space for an XP partition on my (not so spacious) hard drive? Or will virtualboxing do the trick?

Where does it say you need windows? It says you need a FREE compiler, that's all.

assuming you are on Ubuntu:

[php]
sudo apt-get install build-essential
[/php]



This command will give you the arguably best free compiler in existence.

To invoke the compiler for C++:

[php]
g++ sourcefile.cpp
[/php]
where sourcefile is the name of your source file...




**Also look at the stickies in this forum. They should answer a lot of your questions.**

---

### Post by mssever on 2008-12-19
Be wary of 21-day claims: [http://www.norvig.com/21-days.html](http://www.norvig.com/21-days.html)

---

### Post by xarte on 2008-12-19
> **namegame said:**
> Where does it say you need windows? It says you need a FREE compiler, that's all.




The extent of my ignorance is frightening! I wonder where I'd gotten the impression that it was a Microsoft thing... *duh*

I did install the linux compiler yesterday, yay!

It does seem slightly barmy taking on something like this at the age of 40something and already working too hard. But it's way more interesting than Oprah.

---

### Post by xarte on 2008-12-19
> **mssever said:**
> Be wary of 21-day claims: [http://www.norvig.com/21-days.html](http://www.norvig.com/21-days.html)

Very, very good advice - thanks for that link, mssever.

Funnily enough I've blogged on this very topic though in regard to a different skill (art) as I'd similarly noted the plethora of "Painting Made Easy" and "Sew a Widget in an Hour" etc books and magazines. We all want everything easy and instant.

The thing I'm up against is age and time: I've got a job and kids and I'm well into middle age. So while I do take the '21' days with a grain of salt - I figured it would be a good condensed introduction to the important principles - and don't expect to ever be great, I do wonder whether I'll be able to get at least a degree of competence.

I think it's worthwhile having a look, in part because my son wants to be a game designer, so if I've got a bit of an idea 'what's out there' and can help him get started, it will be time well spent. I'm checking out the Programming with Alice site and we also have a Lego Mindstorms set that I'll drag out after Christmas.

Having read that page, I think I'd better have a good look at Python before I make up my mind. I've seen a lengthy debate about it on this forum.

---

### Post by CptPicard on 2008-12-19
> **xarte said:**
> So it seems like C++ is a good place to start.

No, it is not. In particular, if you are a general programming beginner, check out Python. You really want to get started on the right foot. Do not get distracted by language specifics, but learn to actually solve problems.

---

### Post by xarte on 2008-12-19
Cptpicard, I think you might be right. It sounds like I might actually be able to DO some thing with python. It looks pretty versatile too.

I suspect I'd never get much past tinkering with the lower-level languages.

Righto then. Python it is! Good. Decision made.

---

### Post by Lux Perpetua on 2008-12-19
> **xarte said:**
> I'm a bit dubious about the 21 day bit - I assume it's really a crash course that gives me a bit of a kick-start, but it certainly makes it look achievable. There are languages that can be essentially learned in a couple weeks or less (of course, I'm not claiming you would become a good programmer in that amount of time). C can easily be learned in a few leisurely weeks. The most commonly used subset of Python can be learned in just a few *days*. Does C++ fall into this category? I don't really know, but I'd be surprised. Don't get me wrong: I like C++, and I use it all the time, but it's rather complicated, and its many features can interact in unobvious ways.

---

### Post by ankursethi on 2008-12-19
> **xarte said:**
> Righto then. Python it is! Good. Decision made.

Whoa. I wish I could make decisions like that :(

Righto then! Pizza it is. No! Wait! I don't want pizza at this time of the day. What about a sandwich instead? But I'll have to make a sandwitch myself. Nope. Can't have that. Some fruit might do me good. Wait ... I only have one apple, and if I eat this now I'll have to go hungry tomorrow evening. I *could* technically buy more, but that involves going *out*. Oh God, I'm such a retard ...

---

### Post by Maratonda on 2008-12-19
If I can give a fresh experience starting from level 0 in computer science you should definitely check out [stanford engineering everywhere]("http://see.stanford.edu/SEE/courseinfo.aspx?coll=824a47e1-135f-4508-a5aa-866adcae1111").

It uses Java and Eclipse, you have all the material they actually use, and I've watched all 28 classes and it's really helpful and also light hearted sometimes.
The professor is very funny and keeps interest alive...

This course is very important if you want to understand what it really means to be a good computer programmer before you start coding like crazy without the correct mindset. In fact you could end up coding programs that work, but are really poor in terms of style and usability.

---

### Post by xarte on 2008-12-19
thanks for that link, Maratonda - great resource. Java would be an obvious choice for me as it would be at least vaguely familiar - I've cut-and-pasted other people's code when playing about with web pages. For some reason I think of Java as just web apps, though I suppose it's much broader than that.

I get the idea of clean and elegant code from writing HTML (still don't like WYSIWIG editors) though how this actually applies to programming is something I'll need to learn.

Ankursethi - yours is pretty much my decision making process about most things -  trying to choose an icecream flavour is torture. The prospect of upgrading my computer has meant months of googling reviews!

But I'm itching to get started with this! 

Python does sound rather promising - if I can at least start to feel like I can find my way around in it, and look at a simple program and have a rough idea of what is going on - that will be a great start.

I think I'll go and google the sorts of apps that people have created in various languages.

---

### Post by mssever on 2008-12-19
> **xarte said:**
> thanks for that link, Maratonda - great resource. Java would be an obvious choice for me as it would be at least vaguely familiar - I've cut-and-pasted other people's code when playing about with web pagesI think you're confusing Java with JavaScript. However, they're completely separate and unrelated languages. JavaScript has a syntax that's vaguely reminiscent of Java, but that's where the similarities stop. The name JavaScript was merely chosen as a marketing ploy to try to capitalize on Java's popularity.

> Python does sound rather promising - if I can at least start to feel like I can find my way around in it
Python is definitely a great starting point. Don't let the fact that its syntax is a bit different from JavaScript throw you off. Once you get started, you'll realize that syntax is a very small part of a language.

---

### Post by bibleman on 2008-12-19
I switched from C++ to Python. I already know C++ and how to use it but I have found that Python is easier to use and many of the major applications for linux are written using Python. 

I have been going through this resource here [http://diveintopython.org/]("http://diveintopython.org/"). It seems to be a good resource and I have learned quite a bit by going through it.

I want to do a GUI program though and I am still researching how I should go about that with Python.

---

### Post by mssever on 2008-12-19
> **bibleman said:**
> I switched from C++ to Python. I already know C++ and how to use it but I have found that Python is easier to use and many of the major applications for linux are written using Python. 

I have been going through this resource here [http://diveintopython.org/](http://diveintopython.org/). It seems to be a good resource and I have learned quite a bit by going through it.

I want to do a GUI program though and I am still researching how I should go about that with Python.
Just to clarify. *Dive into Python* is a great book, but it's written for experienced programmers. It isn't for newbies.

---

### Post by pmasiar on 2008-12-19
> **xarte said:**
> Java would be an obvious choice for me as it would be at least vaguely familiar - ... I think of Java as just web apps, though I suppose it's much broader than that.

In fact, Java is quite bad for web apps - it is quite weak in text processing and list processing. Of course it is used for web apps - any turing-complete language could - but it was designed to program GUIs for appliances, and it shows. Today, Java is best used for huge enterprisey apps. But I am not sure why you mention web apps - you started with C++, which is **really overkill** for web apps...

See wiki in my sig for Python links.

---

### Post by xarte on 2008-12-19
my ignorance showing again. I don't actually know what languages are used for what purpose - it's just that C++ sounded like the place to start learning any sort of programming.

Let's see. If I could program anything, what would it be?

An author's writing tool like Scrivener for Linux
 A wireless networking interface that actually makes sense when you don't know anything about wireless networking.

A linux driver for my webcam that works. easily.

My son wants to make a kids game/chat website where you create your own 3-D avatar with lego pieces and use it to play games with.

I'd love a program that can access my bank accounts and manage my money and bills for me. Slight problem there with bank security I guess.

Shoehorn mini linux onto my old PDA.

I'd love to be able to contribute to Gimp or a variation, since I'm an artist. That'd be cool.

---

### Post by Maratonda on 2008-12-19
Yeah, I meant Java, but in my opinion, if you want to learn programming and/or computer science, it's not about the particular language, it is about concepts.

In my opinion, in fact, before you investigate how to program something specific in a specific language, you should become familiar with the most important concepts that are  peculiar to modern computer science, i.e. you need to know which purpose OOP, methods, hashmaps, recursions, classes, etc. serve and then start coding. Because when you become familiar with those basic concepts, you can master whatever language you want...because at this point, you are kind of naked, and if you run into a particular concept which represents a hurdle to you, then you're gonna need to become familiar with the concept regardless of the language you're coding in.

On the other side, I agree Python is a better choice than C++!

---

### Post by mssever on 2008-12-19
> **xarte said:**
> Let's see. If I could program anything, what would it be?
Those projects are worthy goals, but it will be quite some time before you're able to effectively tackle any of them. They're all fairly involved. You're best off starting by simply learning how to program, and eventually you'll get to where you can do something like what you mentioned. Python is probably the most pain-free way to get started.

You mentioned earlier that you didn't know of good Python resources. pmasiar has a bunch of relevant stuff linked in his signature. Just find one of his posts and you're good to go.

---

### Post by xarte on 2008-12-19
yes, I've found his links now. The Learn Python Wiki is excellent.

I do realize those are pretty advanced things I've written there - just brainstorming ideas to try and get an idea of a general direction to go in.

If I can ever do something useful and creative with it, I'll be really chuffed. Short term goals - something simple - I don't know, a little widget of some sort... something I can show and say "look what I made!"

Checking out Game-Baker!

---

### Post by Sorivenul on 2008-12-20
> **xarte said:**
> If I can ever do something useful and creative with it, I'll be really chuffed. Short term goals - something simple - I don't know, a little widget of some sort... something I can show and say "look what I made!"
It doesn't take much to do something useful, especially for yourself.  You know your own needs better than any professional programmer out there.  When I started Python I made simple applications for myself and my wife (password generator, script to archive music and pictures, a script to parse recipe contents and catalogue them, etc.).  

Things may seem advanced or difficult at first, but Python is really quite easy to pick up, especially with the great help available from the Python lovers on these Forums.

Good luck to you!

---

