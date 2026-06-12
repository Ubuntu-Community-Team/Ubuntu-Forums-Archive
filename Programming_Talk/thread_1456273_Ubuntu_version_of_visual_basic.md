---
title: "Ubuntu version of visual basic"
date: 2010-04-16
forum: Programming Talk
---

### Post by cschamber on 2010-04-16
could some one point me in the right direction to find a program on Ubuntu that is the equivalint of Visual Basic so that i can start developing and giving back to the Ubuntu community

---

### Post by 3rdalbum on 2010-04-16
> **cschamber said:**
> could some one point me in the right direction to find a program on Ubuntu that is the equivalint of Visual Basic so that i can start developing and giving back to the Ubuntu community

The most useful language to Ubuntu is usually C or Python. Python is used for end-user programs and it's quite easy to learn. You can use the Quickly framework or something like Pythoncard to get a GUI designer like Visual Basic.

If you already know Basic and want to stick with that, you can check out Gambas, which is similar to VB but not a clone.

---

### Post by Serpher on 2010-04-17
TBH, BASIC should really only be used to learn basic programming stuff. Second of all the .NET stuff VB uses is the worst framework in the world. If I were you I'd replace the BASIC with C, and the .NET with GTK+.

CodeBlocks (sp?) is an IDE that can do VB though IIRC. Been a while since I've done any application programming.

---

### Post by HermanAB on 2010-04-17
Howdy,

You use one of Perl, Python or PHP with Glade for GUI development.

The secret is Glade.

---

### Post by kalaharix on 2010-04-17
Hi

'BASIC should really only be used to learn basic programming stuff' What condescending drivel! You use the language that suits you. I agree that .Net is a bit of a dogs breakfast but Gambas is an object oriented programming environment that has been properly designed from the start (not grown like topsy aka VB).

It is debatable what the TIOBE charts indicate but you can conclude that the BASIC language is still well up there in COMMERCIAL use and some 50% more active than Python ([http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)).

I finish with a quote from a visitor to my blog: 'Well, I’m creating a mmorpg game, linux client made in gambas and windows/mac client in python. And i have to say that gambas is 100 times faster than python. Linux client works around 900 frames per second and python at 20 frames per second, and its a big perfomance problem. Sad that gambas doesnt work on windows.

---

### Post by lisati on 2010-04-17
Moved to "Programming Talk"

---

### Post by soltanis on 2010-04-17
With the aforementioned performance problems aside, performance is rarely the limiting factor in many programs and you are better off developing in Python, whose draconian rules on how complex you are allowed to make your statements and indentation rules are sure to keep your programs readable.

Until you discover list comprehensions. Thank God someone in the Python community loves functional programming...

---

### Post by nvteighen on 2010-04-17
The issue is not BASIC. Remember that BASIC is the predecessor of Python in a lot of things. IMO QuickBASIC 4.5 was really great.

The issue is *Microsoft(tm) VisualBasic(tm)*, be it pre-.NET or .NET. It's a framework that leads people to program exactly the opposite way common sense tells you to do: adapting the code to the UI. Of course you can do things right in VB, but it's really much harder. Not only that, the language itself is full of awkward oddities, even though I'm told that VB.NET has improved a lot on this.

In the Free Software community people use "traditional" programming: writing code in a text editor using a programming language and something that interprets it. IDEs have become popular in the Free Software community just these last recent years but they essentially do the same... they just integrate both tools I referred above into one single program and add features specially designed for "code editing" (not "text editing"). Gambas, Squeak and similar solutions are very rare and used just for educational purposes.

---

### Post by kalaharix on 2010-04-17
Hi

'...and used just for educational purposes.'.

What utter nonsense.

Gambas has just been used to create a web-centric GIS for the management of all traffic signs in Paris. [www.guygle.net](www.guygle.net).  You can see a slightly dated synopsis in English at [http://gambasdoc.org/help/app/guygle?view](http://gambasdoc.org/help/app/guygle?view).

Also have a look at [www.domotiga.nl](www.domotiga.nl) for Open Source Home Automation software written in Gambas.

---

### Post by nvteighen on 2010-04-17
> **kalaharix said:**
> Hi

'...and used just for educational purposes.'.

What utter nonsense.

Gambas has just been used to create a web-centric GIS for the management of all traffic signs in Paris. [www.guygle.net](www.guygle.net).  You can see a slightly dated synopsis in English at [http://gambasdoc.org/help/app/guygle?view](http://gambasdoc.org/help/app/guygle?view).

Also have a look at [www.domotiga.nl](www.domotiga.nl) for Open Source Home Automation software written in Gambas.

Seems I was misinformed. Thanks! :)

---

### Post by phrostbyte on 2010-04-17
Mono supports VB.NET, you should download this [package]("apt:mono-vbnc"). It's worth noting that Mono's C# support is far better at this point.

[Gambas]("apt:gambas") is similar to VB6, if you are used to VB6 you should feel at home.

---

