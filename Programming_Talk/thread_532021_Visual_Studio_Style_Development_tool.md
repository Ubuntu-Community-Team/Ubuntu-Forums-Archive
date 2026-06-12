---
title: "Visual Studio Style Development tool?"
date: 2007-08-22
forum: Programming Talk
---

### Post by shavenlunatic on 2007-08-22
Hi,

I will start by saying that I am by no means a great programmer, but I began coding in BASIC, did a little pascal.. am fairly ok with coding in VB/VBA..  nothing special but I get the logic behind it and can usually manange to create something when I set my mind to it.

I haven't thought about coding anything in Linux before, I see lots kicking around about Python and C++/#/whatever..

Basically, what I was "hoping" is available is an equivalent of Visual Basic ...obviously not with basic as the language, but the same principle, form, create buttons, stick code/modules behind them and away you go..  I should be ok just learning the syntax of a new language but I was hoping to be able to create something visually and then throw code at it (a-la-Visual Studio)

Any advice on which I should start learning? (i don't want to start learning python and then find out its not what I was looking for)


Sorry if i seem ignorant on this matter, I haven't looked into it much until this moment and jusdt trying to gather as much information as I can while I'm still buzzing about the idea of coding :)

---

### Post by Wybiral on 2007-08-22
Like [Glade](http://glade.gnome.org/)?

---

### Post by shavenlunatic on 2007-08-22
cheers :) , yeah glade looks like the kind of thing I'm looking for

a mate of mine just suggested using Mono & C#.. any advantages/disadvantages of mono over glade?

Also, looks like both Mono & Glade both support pretty much any language.. would C# be a good place to start or should I be looking at Python or an alternative?

---

### Post by LaRoza on 2007-08-22
> **shavenlunatic said:**
> cheers :) , yeah glade looks like the kind of thing I'm looking for

a mate of mine just suggested using Mono & C#.. any advantages/disadvantages of mono over glade?

Also, looks like both Mono & Glade both support pretty much any language.. would C# be a good place to start or should I be looking at Python or an alternative?

I would look at Python over C#. Python has a clean syntax, easy to understand/read/learn, large library, and portable.

If you want tutorials/books/references, my wiki has many such things, first link in my sig.

---

### Post by shavenlunatic on 2007-08-22
nice wiki there, thanks for that (bookmarked) :)

so if at some point I decide to make a fairly simple game (would be 2D) mainly for my learning purposes, python would be a good choice for that? 

(I don't ask this because I'm planning on making a game, but I expect at some point I will decide I want to.. once I get bored of writing simple apps for me to use)

---

### Post by Soybean on 2007-08-22
> **shavenlunatic said:**
> so if at some point I decide to make a fairly simple game (would be 2D) mainly for my learning purposes, python would be a good choice for that? 

Yup! If you wanted to use fancy state-of-the-art 3d stuff, you'd probably need to do a fair bit of coding in a lower-level language like C or C++, but even in that case, Python could be a good choice for much of the program. I haven't used it myself, but I understand that the pygame library is quite good and should include most of what you'll need for a simple 2d game.

---

### Post by shavenlunatic on 2007-08-22
ok, so it seems python is the way forward for me...

Now the question remains/.. Mono vs  Glade?

---

### Post by LaRoza on 2007-08-22
> **shavenlunatic said:**
> ok, so it seems python is the way forward for me...

Now the question remains/.. Mono vs  Glade?

While learning, it is easier to hand code everything. I recommend GEdit, KWrite, VIM, or any text editor you like.

-EDIT 

I just restuctured the wiki, so everything for the Language is in one place.

---

### Post by shavenlunatic on 2007-08-22
so would i have to literally place every single object where I want it?  I struggle to visualise stuff like that.. i can write html but could I hell write a webpage that looked right just using a text editor.. i have the knowledge, just not the .... imagination i guess :)

the wiki looks good.. got a bit of work to do but I'm gonna spend some time this afternoon having a good read

---

### Post by LaRoza on 2007-08-22
> **shavenlunatic said:**
> so would i have to literally place every single object where I want it?  I struggle to visualise stuff like that.. i can write html but could I hell write a webpage that looked right just using a text editor.. i have the knowledge, just not the .... imagination i guess :)

the wiki looks good.. got a bit of work to do but I'm gonna spend some time this afternoon having a good read

When learning a language, you should start using GUI's and other libraries, until you have the language learned.

Hand coding a small GUI is easy, in Python, you can use EasyGUI, which is a very simple tool kit, for getting user input, and doing simple tasks. wxPython and Tkinter are more powerful, and are easy to learn, then you might want to look into the above mentioned gaming module.

---

### Post by pmasiar on 2007-08-22
> **shavenlunatic said:**
> equivalent of Visual Basic ...obviously not with basic as the language, but the same principle, form, create buttons, stick code/modules behind them and away you go.. 

Python is good overall language - and LaRoza stole all my good lines to promote it! :-) But my wiki is better :-)

At the start, don't focus on GUI, do commandline training tasks, like pythonchallenge (and my wiki has some too). Pygames is good library for games if you fancy that.

SPE is good IDE, but you can start with IDLE - it is very simple, but not too simple, and good enough.

Python syntax is so simple that you don't need constant help from IDE to "generate" code - and good editor helps you not only "generate" code but also refactor it.

Programmer's productivity should be emasured not in lines **written**, but in lines **spent**. The less lines you have for same task, the easier it will be enhance/maintain it later (up to some limit of course, when code is too terse to be comprehended).

---

### Post by LaRoza on 2007-08-22
> **pmasiar said:**
>  But my wiki is better :-)


Careful, my wiki changed, might want to look at where beginners are sent :-)

---

### Post by samjh on 2007-08-22
> **shavenlunatic said:**
> so would i have to literally place every single object where I want it?  I struggle to visualise stuff like that.. i can write html but could I hell write a webpage that looked right just using a text editor.. i have the knowledge, just not the .... imagination i guess :)

A piece of paper and pencil can do wonders.  I used to (and occasionally still do) draw my GUIs on paper before coding them.

---

### Post by pmasiar on 2007-08-23
> **shavenlunatic said:**
> equivalent of Visual Basic ...obviously not with basic as the language, but the same principle, form, create buttons, stick code/modules behind them and away you go..  I should be ok just learning the syntax of a new language but I was hoping to be able to create something visually and then throw code at it (a-la-Visual Studio)

What you are looking for is not language but [http://en.wikipedia.org/wiki/Integrated_development_environment](http://en.wikipedia.org/wiki/Integrated_development_environment).

There are some, even many of them. But many of the smartest programmers don't use IDE, but use really smart universal editor, like vim/emacs (1337 hackers), or gedit/SciTe/kate (hackers in training). And you know why? Several reasons (I use vim, but it applies to any of popular "generic" editors mentioned above):

- IDE aren't available for new cutting edge languages - the languages which are most fun and most attractive to gurus
- vim works work for any language the same, so you don't have to fight with quirks of any IDE
- many programmers don't care about GUI, prefer fast keyboard shortcuts
- many programmers like to write own macros and enhancements to editors: traditional editors like vim/emacs are known to be highly customizable (as a result of **decades** of gradual improvements be generations of hackers. emacs is in like version 22?
- many (possibly most) programs are written to be used **not** in GUI environment: web based apps, compilers, databases, all the services and what not. 
- after 10 years of using same editor, you know all the shortcuts, and probably even added own macros/features customized to what **you** prefer.

Additionally, vim (only) is installed on any (Linux) computer, so even if you log to remote computer, vim is there.

So there are IDEs, but they are not as important as in Windows world. Hackers prefer open sourced tools (to modify it to own needs), not many are interested to spend time on GUI which their peers will not use: many of them learned editors years ago and stick with it (to solve more urgent problems).

For Python, I recommend you to use very simple IDE, called IDLE. There are couple more IDEs: Eric (of course :-) ) and SPE are free, Komodo has free teaser version, Eclipse has plugin...

I use IDLE and SPE for Python, and SciTe for everything else. Sometimes also cooledit directly from Midnight commander. Yes, [http://en.wikipedia.org/wiki/Midnight_commander](http://en.wikipedia.org/wiki/Midnight_commander) is something you should look into: **really** simplifies your like in terminal window.

For links to learn Python, see wiki in my sig.

---

### Post by fct on 2007-08-23
A working Visual Basic-like environment is Gambas:

[http://gambas.sourceforge.net/](http://gambas.sourceforge.net/)

Python is really nice too, and probably more portable. I think Gambas is not available for MacOS or Windows.

---

### Post by pmasiar on 2007-08-23
... and gambas is not widely used - I do not think you can get paid job in Gambas, but if you are good Python hacker, Google might be interested! :-)

BASIC is a dead end language. Don't waste your time.

---

### Post by shavenlunatic on 2007-08-28
> **pmasiar said:**
> ... and gambas is not widely used - I do not think you can get paid job in Gambas, but if you are good Python hacker, Google might be interested! :-)

BASIC is a dead end language. Don't waste your time.

aah, but it was my first true love.. so I can never discard it completely :) (even if I keep an old spectrum emulator running, it gives me that warm fuzzy feeling!)

been in London having some fun and frollics recently.. so not had time to test the water with any of these.. will look into everyones advice and see which suits me best..

:)

---

### Post by Dragonbite on 2007-08-28
> **pmasiar said:**
> ... and gambas is not widely used - I do not think you can get paid job in Gambas, but if you are good Python hacker, Google might be interested! :-)

BASIC is a dead end language. Don't waste your time.It's a dead-end in the Linux world.  Actually, it's practically a no-show (I've been looking to use my VB in Linux for a long time).

I'm using VB.NET and ASP.NET here at work (Windows). At home I've got Monodevelop and am going through a C# book to teach myself C# (via Mono).

Since both utilize the .NET framework I'm hoping to be able to cross-pollinate my experiences (home and work).

---

### Post by pmasiar on 2007-08-28
> **Dragonbite said:**
> It's a dead-end in the Linux world. Actually, it's practically a no-show 

It is "no-show" because in Linux program space, BASIC has plenty of competition as a language easy to pick for beginners, and powerful enough to call most libraries: Perl, Python and Ruby are all in that niche, and either one kicks VB. So no many Linux hackers are willing to invest time in inferior language, just to make some Windows converts happy. It is not that much fun, unless you are paid for it like Mono project.

> I'm using VB.NET and ASP.NET here at work (Windows).

VB.NET is **quite** a different animal from old BASIC. I never said I liked it (I tried it, and tried to like it: very smart team here is doing rather interesting project in it, but I got disgusted), but it has all the libraries MSFT can unleash on a programmer.

I never understood why it is so hard for people to pick another language - maybe what is hard is to pick **second** language :-) - but for me the pain was always in libraries. And I had the luxury of not having to learn .NET libraries, and choose not to :-)

So yes, VB.NET is frankensteinish monster with new features grafted over old BASIC body (just count reserved keywords), but it does have own place in MSFT universe: to be simpler C# (and access .NET) for people too lazy to learn C# -- or too brain-damaged by using BASIC for too long :-) 

However, that reason does not extend to Linux, so neither does BASIC :-)

---

### Post by kknd on 2007-08-28
Please, stay away from BASIC.

I think Python is a good alternative for you. Python + Glade = true RAD.

---

### Post by aitorcalero on 2007-08-29
> **shavenlunatic said:**
> 
Basically, what I was "hoping" is available is an equivalent of Visual Basic ...obviously not with basic as the language, but the same principle, form, create buttons, stick code/modules behind them and away you go..  I should be ok just learning the syntax of a new language but I was hoping to be able to create something visually and then throw code at it (a-la-Visual Studio)


Maybe you could take a look to [Gambas]("http://gambas.sourceforge.net/").

---

### Post by Dragonbite on 2007-08-29
> **shavenlunatic said:**
> Basically, what I was "hoping" is available is an equivalent of Visual Basic ...obviously not with basic as the language, but the same principle, form, create buttons, stick code/modules behind them and away you go..  I should be ok just learning the syntax of a new language but I was hoping to be able to create something visually and then throw code at it (a-la-Visual Studio)Oh, I must have missed this point.

So you are looking for a Visual design tool (for any language) IDE.

[[COLOR="Blue"]NetBeans [/COLOR]]("http://www.netbeans.org/")(Java) looks like a pretty good IDE with visual forms.  You can download it or order a free CD they will ship.

To run it you do need to download the Java SDK and some other stuff. The site includes some pretty good (visual) tutorials to get you started.

---

