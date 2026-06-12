---
title: "Lost enthusiasm."
date: 2005-12-31
forum: Programming Talk
---

### Post by Jimmey on 2005-12-31
I've mentioned this in a reply I posted to a thread earlier in this forum, but, this time I'd love some help.

The problem is, as the title suggests, I've lost enthusiasm for programming.
I've started with the languages C++ and Python, and know some Pascal due to college, but as it's ( in my opinion ) an ugly looking language, Pascal's not top of my list. 

I know more of Python than I do C++, but, let's face it, that's easily done.

I've learned the basics - Loops, selection, functions, structures(?) and classes ( You either get them, or you don't. I don't, but have never needed to. ) I've even written a pretty smart file lister ( Basically does the same as 'ls' would, in the terminal ). But now what?

I'm a little stuck for projects to work on, I don't know what to learn next, and I've got some major problems with GUI programming. 

I'd LOVE to be able to write my own GUIs, and I'm not to keen on RAD programs ( Damn college's force-fed me Delphi :( ), but GUI programming seems ALOT more specific than the actual program programming (lol), and, with GUI programming, I'm facing a truck load of new keywords, without a truck load of explanation. The final GUI downer in the list is - Classes aren't my friend. They just...Don't seem to want to play.

So, basically, I figure - I'm not yet ready for GUI programming. If not that, then what..?

Any suggestions ( even those telling me to zip it, because I know many will think that :P ) are welcomed :)

Thanks..

Jimmey

---

### Post by pharcyde on 2005-12-31
Programming does not come easy to most people.  There are several schools of though when learning to program.  I am a strong believer of learning low-level practices and techniques before learning more complex algorithms.  The best way to learn about this stuff is how to model real world tangible object in a coding language.  This is the purpose of class containers and structures.

Now for GUI applications the biggest thing is learning to turn a simple usually console based need and translating it into a pretty interface for users.  The biggest thing about GUI apps is providing a layer between the core of the application and the interface for the user.  In other words your application should be able to work fairly well by itself with or without a gui.  Once you have developed a program that works as such putting a GUI on top of it to control it is fairly simple.  This eliminates the need for extraneous work when u want to upgrade the interface or application.  By sepperating the two you make maintainability and upgradability much easier than if they were tightly coupled.

In summary the biggest thing about programming is learning how to model the real world and translating it into simple structures that can be modeled by software.

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=Jimmey]I've mentioned this in a reply I posted to a thread earlier in this forum, but, this time I'd love some help.

The problem is, as the title suggests, I've lost enthusiasm for programming.
I've started with the languages C++ and Python, and know some Pascal due to college, but as it's ( in my opinion ) an ugly looking language, Pascal's not top of my list. 

I know more of Python than I do C++, but, let's face it, that's easily done.

I've learned the basics - Loops, selection, functions, structures(?) and classes ( You either get them, or you don't. I don't, but have never needed to. ) I've even written a pretty smart file lister ( Basically does the same as 'ls' would, in the terminal ). But now what?

I'm a little stuck for projects to work on, I don't know what to learn next, and I've got some major problems with GUI programming. 

I'd LOVE to be able to write my own GUIs, and I'm not to keen on RAD programs ( Damn college's force-fed me Delphi :( ), but GUI programming seems ALOT more specific than the actual program programming (lol), and, with GUI programming, I'm facing a truck load of new keywords, without a truck load of explanation. The final GUI downer in the list is - Classes aren't my friend. They just...Don't seem to want to play.

So, basically, I figure - I'm not yet ready for GUI programming. If not that, then what..?

Any suggestions ( even those telling me to zip it, because I know many will think that :P ) are welcomed :)

Thanks..

Jimmey[/QUOTE]
Maybe you could start with something simple like Tk.  It is not the prettiest GUI toolkit, in my opinion, but it is not that hard to throw something together with it.  I don't find that I generally have to create new classes with it, either.

You can experiment with it from python by importing the "Tkinter" package.  I learned how to use it from the big GUI section in "Programming Python" (by Lutz, I think).

I generally don't like to create big GUIs, but sometimes I like to create graphical dialogs as front ends to my command line programs.

---

### Post by coredump on 2006-01-01
I'm not sure if this'll help, but I'll suggest it anyway...

If you're happy with the conventional procedural programming stuff (loops, conditionals, selection, etc) then have you had a look at lower-level programming like assembler?  Not necessarily for the i386 under Linux with, say, 'gas', but maybe 8-bit programming on the 6502.  Or the 6809 or 16-bit programming on the 68000.  All these CPUs are available as emulators nowadays, and there's a growing retrocomputing movement that keeps the old systems alive.

Or, you could start by coding your own assembler or emulator in C.  I've written 6502 emulators in Ratfor, 68000 assembler, C and 8086 assembler.  One of my goals with Ubuntu is to run my C-coded 6502 emulator on the Mac/PowerPC.

What do you think?

---

### Post by stimpack on 2006-01-01
68000 hmmm!, is it wrong to have erotic feelings about an instruction set?

---

### Post by Jimmey on 2006-01-01
Hahaha, lol...
*refuses to comment*
I am going to start assembler, or some of it, in college next year, and so I'll start taking a look at it.
Thanks.

---

### Post by thumper on 2006-01-01
I must admit to not "getting" objects while I was at uni.  Oh I knew the theory, but never really understood the practice.  That was until I got my first real job and started using C++.

Some things you just have to do in order to understand.

Follow what you love.  Pick something you would like to automate and look to write a program to do it.  It doesn't have to be original, 'cause you are just using it to learn.

---

### Post by guttley on 2006-01-01
And why do you believe delphi is a bad thing? 

I program with delphi for a living with GUI and non GUI applications and it is excelent at what it does, i personally favor it over C++ for RAD and imho looks much cleaner than C, but this is probably down the style of whoever wrote the code.
I also use a lot of C++ for CORBA work so i am very familier with delphi and C++ and the only thing i really think delphi is missing is the meta programming capability of C++ with templates.

Anyway back to the point, i think you need a project, a goal to acheive.
Thats a big factor for me, the satisfaction of realising a spec or concept into a live system and seeing it work.

---

### Post by Jimmey on 2006-01-01
I don't believe Delphi's bad. Infact, I believe the opposite.

I was saying that I don't much like it. I wasn't a fan of Pascal to begin with, and I'd much rather learn GUI programming than do it in Delphi, or any other RAD tools.

The next project I'm going to try is a Python script that updates a HTML. I need a new homepage for Firefox.

---

### Post by stimpack on 2006-01-01
While your still new it may be worth giving classes another crack, either in python or c++ as you know both. As someone who grew up with assembler and C in the 80s classes are so alien and unatural to me, I find GUI programming rather troublesome now.

---

### Post by Jimmey on 2006-01-01
I shall do, and I should probably look into learning some ruby - I hear OOP's nice on that side of the fence.

With Python, I've no idea what __init__ and self are, nor what purpose they serve, and find it hard to include those in my class declarations. Which's the Python disadvantage. The Python advantage is that is allows declaration of member functions within the declaration of the class ( keeps everything nice, and tidy ) - Where C++ doesn't. That's why I'd only ever use classes in C++ for a large project...And I've not the inspiration nor skill to do. I'll stop complaining and start fiddling though - Maybe I'll get somewhere.

Thanks :)

---

### Post by thumper on 2006-01-01
C++ does allow the definition of class members within the class, it is just that you don't normally want to do it in order to hide the implementation.

__init__ in python is used to initialise an object into a known state, similar to a constructor in C++.

---

### Post by pharcyde on 2006-01-01
> C++ does allow the definition of class members within the class, it is just that you don't normally want to do it in order to hide the implementation.

Functions declared in this way cause the compiler to treat them as inline functions which you may or may not wish to do.  Like thumper said you normally don't want to do this as it is usually bad coding practice and makes code hard to maintain.

---

### Post by thumper on 2006-01-01
[QUOTE=pharcyde]Functions declared in this way cause the compiler to treat them as inline functions which you may or may not wish to do.  Like thumper said you normally don't want to do this as it is usually bad coding practice and makes code hard to maintain.[/QUOTE]
If you want to get pedantic, the compiler may choose to treat them as inline functions :)

---

### Post by DeniseDD on 2006-01-02
Here is something no one seems to mention that may excite some enthusiasm-

[http://www.pythonchallenge.com/](http://www.pythonchallenge.com/) 

I am not sure how easy or difficult these challenges are but they may be worth your while for some fun. Also you can google "programming challenges" or something to that effect and find other challenges in different languages-

---

