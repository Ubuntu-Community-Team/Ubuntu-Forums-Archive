---
title: "C Programming Language &amp; Java"
date: 2006-09-10
forum: Programming Talk
---

### Post by Brahman on 2006-09-10
I am currently learning C, but I want to know if its a good language to learn, as far as using linux and programming for linux and windows. Is it a nice language....its also my first I'm learning. I have a book called: Beginers Guide to C Programming, for those who've never programmed it teaches how to program in C and a lot of stuff. 

Also, I was told you need to learn Java if you want to do a lot with the graphical part of Ubuntu, that true? if so, where's a good place to learn Java after I accomplish C?

---

### Post by Grey on 2006-09-10
C is a nice language IMO.  And it's probably the most universally portable language out there, in that there's probably a compiler for it on whatever platform you choose.  If you master C, you will be powerful.

And no, you don't need Java for anything on Linux.  In fact, I might suggest staying as far away from Java as you possibly can, unless you are doing some web work that absolutely requires a Java applet, or programming something for a cell phone.

I have done a tiny bit of graphical stuff in Linux.  I have used OpenGL/C++, and GTK/C.  GTK is what I would recommend for graphical applications in the vein of Firefox, OpenOffice, The GIMP, or Gaim.  But Qt is also fairly popular.  OpenGL of course is for games and the like.

If you find that C is too hard... I might also suggest picking up Python instead.  The syntax is similar, but it's an interpreted language, and much easier to use.

---

### Post by X.Cyclop on 2006-09-11
> Is it a nice language
Yes. C and C++ (and Asm of course) are the best languages.

> Also, I was told you need to learn Java if you want to do a lot with the graphical part of Ubuntu, that true? if so, where's a good place to learn Java after I accomplish C?
It's not true. Graphical programs can be made with Python, Perl, C, C++, Java, PHP, Ruby, C# and more...

C# is better than Java, so, you may try this.;)

---

### Post by amo-ej1 on 2006-09-11
Yeah but C# finds it roots with you know who ...

I mainly played around in C/C++ and Java, but the last year I turned my back to Java. I haven't encountered anything yet that couldn't be accomplished in C/C++ ;-)

Depending on any prior programming experience it might be difficult too start  certainly when they start throwing pointers at your head but simply keep on learning once you'll fully master C/C++ you'll know the suffering (???) was worth it.

---

### Post by catanzag on 2006-09-11
Every language are nice or not, by IMO it depends only on usage and personal tastes. I use many of them. On my experience, C is of course the most portable one, but it must be recompiled for each platform (apart from the graphical library issues..); for linux/unix, a shell script (Python, TCL, bash,...) with some graphical GUI (PyGTK, Tk) in many case is the fastest way. I love Java, better than C#, from which, however, it got some important feature; it is no native but is TRULY portable (no recompilation needed among Windows, Linux and various Unix flavours), though it is slow and not fully graphically integrated.

However my suggestion is to concentrate only in one language, at your choice, and then take into accout its graphical library: on my experience I realize that it could generate confusion to study more than one

---

### Post by elettronicha on 2006-09-11
I agree with catanzag, so start learning C, which is very didactic, simple but powerful, low level, and suitable to learn managing pointers. Once you've learned it, there is the world of Object Orientation waiting for you (C++, Java, Python, ...). I think Java isn't suitable to desktop client applications, though has no rivals in server applications. In fact it dipends on what you want to do, there's no absolute best language: if you're writing a driver, probably C it's the best way to do it, if you're writing a >100,000 lines of code application and you want to use C, do the sign of the cross. :D

---

### Post by braveerudite on 2006-09-11
I am learning (or trying to learn) object oriented programing.  I know jack $h1t about C++.  Can anyone tell me what's the best program to use with Ubuntu to write simple C++ stuff?  

My school still using Visual Basic 6.0 and not the 2005 Express edition.

I recently donwnloaded the Visual 2005 Express Edition from MS and the simple example found on my college text book []("http://www.amazon.com/Object-Oriented-Programming-in-C%2b%2b-4th/dp/0672323087/sr=1-1/qid=1157152465/ref=sr_1_1/103-1303444-7188608?ie=UTF8&s=books")
dont work unless I try them on teh Vissual Basic 6.0 Why is this?  I though C++ is suppose to work no matter what program I use to write it with.

---

### Post by Brahman on 2006-09-11
Awesome. I'll stick with C and learn all I can with C!!!

---

### Post by Omnios on 2006-09-11
Highly rated newbie programmer books.

C++: [http://greenteapress.com/thinkcpp/](http://greenteapress.com/thinkcpp/)

Java: [http://greenteapress.com/thinkapjava/](http://greenteapress.com/thinkapjava/)[]("http://www.ibiblio.org/obp/thinkCSjav/")

Python: [http://greenteapress.com/thinkpython/](http://greenteapress.com/thinkpython/)

 G4 teckTV recomended this series of books called "How to think Like A Computer scientist" as one of the best book series for people new to programming.

---

### Post by catanzag on 2006-09-12
> **braveerudite said:**
> ...Can anyone tell me what's the best program to use with Ubuntu to write simple C++ stuff? ....

first, you need g++ and gdb; then, if you use qt (the base of KDE) you can use the *designer* IDE tool; I don't know if *Anjuta*, which is the same for gtk/gnome, can support C++ writing and debug.

---

### Post by amo-ej1 on 2006-09-12
Personally i'd suggest a good old text editor with some syntax highlighting for beginners you'll make more mistakes but you'll learn to understand the output of the compiler. 
And I still haven't seen any decent IDE which offers code completion the way i would want to use it, so personally I don't use an ide (emacs is so much more than an ide ;-) )

---

### Post by monktbd on 2006-09-12
i think starting with c is a very good albeit difficult choice.
but once you master c and c++ it wont take you long to grab the concept of other programming languages.

Another (graphical) framwork for c++ i would suggest is wxwidgets.
it works well (as far as i tested it, which ist gtk and windows) crossplatform and gives nice results in both.

---

