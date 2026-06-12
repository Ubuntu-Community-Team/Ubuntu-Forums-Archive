---
title: "Worth it to learn C?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by bbqsandwich on 2008-07-24
Hello,

I'd like to learn a desktop programming language. I like the idea of being able to write a simple program, compile it myself with gcc or whatever, and use it right away (however basic the program may be). I also hope to better be able to understand the programs I use in Linux by looking at the source code. It seems to fit with the spirit of Ubuntu.

All that said, is it best to learn C? Should I learn something else, like Python? I know some Javascript, basic (very basic) Ruby, etc., so I am somewhat familiar with the logic/structure of programming languages...

Thanks!

---

### Post by PGScooter on 2008-07-24
Hi,

I am not an expert on programming languages, but for your purposes, I might think about Perl. Perl is an excellent complement to linux. You can do absolutely anything you need to with text files.

---

### Post by KIAaze on 2008-07-24
Of course it's worth it!

As to what language to choose...:
[ Learning Computer Programming FAQ  ]("http://ubuntuforums.org/showthread.php?t=667422")

Sticky from programming section:
[http://ubuntuforums.org/showthread.php?t=832449](http://ubuntuforums.org/showthread.php?t=832449)

If you need any more help, here's a good forum section:
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

edit:
Concerning above response:
Yes, Perl is very good if you want to work on text files.
But so is Python, and personally, I think it's a lot easier than Perl for this purpose.

I'm no professional programmer, but here's my personal opinion:
-If you want to write simple games: Python
-If you want to write complex games (FPS, RTS, 3D stuff): C++ (but Python and Java are apparently also 3D capable, altough I haven't been convinced by their speed in this domain yet)
-If you want to create GUIs: C or C++ with GTK+, wxwidgets or QT, Python+PyGTK

-If you want to do something cross-platform easily, use Python or Java. (in C and C++, you'll often need some bits of platform specific code and you'll need to get it to compile on each platform)

---

### Post by o.besner on 2008-07-24
I'm not much of a programmer but I hang with some, and they all disagree on what you should learn :

- My Windows pal is a big fan of C# (.Net framework) which is called "Mono" in the Linux world. He says it's the most powerful, rather simple and the best way to get rich.
- I like Python. It's powerful, easy, you don't have to compile it, and you can write the program with half the command line of C. Lots of Ubuntu apps are in Python (For example Exaile, Deluge)
- My open-source programming pal (much much better than me) is a Perl adept. He says Perl is as fast as Python to write and learn but there's more subtlety and choice in it.

So basically, choose one and stick with it. If you persevere it'll rock.

---

### Post by Yannick Le Saint kyncani on 2008-07-24
> **bbqsandwich said:**
> I'd like to learn a desktop programming language.

A language to automate desktop tasks ? If you're using unix/linux, you will need to learn bash basics at some point.

Also, a more functionnal language like python (or perl) would be my choice.

---

### Post by king.pest on 2008-07-24
ok, I'm not an educated programmer with a CS major, but since I'm getting paid for programming, I'll share my views:)

- if you want to learn something useful on linux, try Perl. it's very easy to learn, yet it's powerful and... gives a lot of fun:)
- if you want to be able to create GUI programs for linux, try Python. it's very easy as well, and with PyGTK of PyKDE you can do actually everything; 
- if you want to get rich easily, try Java or .NET; they're both quite easy and its good to know them if you want to work as a programmer; 

about C: in my opinion every programmer should know it. it's a bit difficult, it takes a long time to create a big project using it, and it's also harder maintaining the code written in C, but knowing this language gives you a huge insight into computer programming in general. I remember that C was the first programming language I tried to learn, and it was a bit of a mistake, because it's difficult and a bit... discouraging I'd say. once you master some other programming language though, learn C and learn it well.

---

### Post by CarlosNYB on 2008-07-24
> **Yannick Le Saint kyncani said:**
> A language to automate desktop tasks ? If you're using unix/linux, you will need to learn bash basics at some point.

Also, a more functionnal language like python (or perl) would be my choice.

I was going to say, yes, if you want to automate desktop tasks and work with text files, bash and a scripting language like Perl is a sensible and powerful combination.  For gui stuff and GTK, QT with C++ is very good, and C++ is very efficient for things like high-powered games.  I don't know anything about Python.  For dynamic web development with databases, learn some sort of web server script and SQL.

---

### Post by bbqsandwich on 2008-07-24
> **CarlosNYB said:**
> I was going to say, yes, if you want to automate desktop tasks and work with text files, bash and a scripting language like Perl is a sensible and powerful combination.  For gui stuff and GTK, QT with C++ is very good, and C++ is very efficient for things like high-powered games.  I don't know anything about Python.  For dynamic web development with databases, learn some sort of web server script and SQL.

Oh, sorry, I meant desktop language as opposed to a Web-based language like PHP, ASP.NET, etc. :-)

Thanks everyone for your responses so far!

---

### Post by WRDN on 2008-07-24
C is a brilliant language to learn if you want to do GUI programming. Combined with GTK, its great! Also, C is useful if you want to change some parts of the Linux kernel, as most of it is written in C.

---

### Post by estyles on 2008-07-24
I hate to say it, but don't learn C if you want to be able to do something useful quickly.  C (and by extenstion C++) is a great programming language, very versatile, extremely powerful, and is the basis for a lot of other programming languages.  If you learn C, you'll have a great start on learning quite a few other languages, and IMHO, the way C makes you think is helpful in just knowing how to program in general.  Note, of course, that doing something in LISP, Perl (I think... you could fit what I know about Perl in a thimble), or a bunch of other languages will require completely different thinking, completely alien to C.  But Java, Python, C#, and some others, use such similar structure that you will pick them up very easily after learning C.

But if you want to be able to, say, write a small GUI application in the next month, I don't suggest using C for that.  Not that it's impossible, but there's just so much going on with C that trying to learn it quickly is pretty overwhelming.

---

### Post by ibuclaw on 2008-07-24
Here's my 2p.

[Teach Yourself Programming in Ten Years.]("http://norvig.com/21-days.html")

It is a very enticing read. And will help you decide on your best choice of action.

Although, in my personal opinion, it's best to work your way up:
from a basic, high level scripting language.
then learn a more advanced, lower level one,
then have your go at C/C++.
if your still couragious after that, then perhaps ASM, or an ancient language such as Fortran or Cobol...

ie:
```

Bash
Ruby --> Perl
         Python --> C
                    C++ --> ASM
                            Fortran
                            Cobol

```

[EDIT]
Forgot to note, Sed and Awk are two very good Languages to learn too :)

Regards
Iain

---

### Post by Sydius on 2008-07-24
C++ is my favorite language, but I have to admit, developing with it can be slow, and learning it took a few years for me.  It's not that it has to be hard--it's just so flexible that it's difficult to decide how to do something, and almost everyone decides differently, which can make things messy for a newbie trying to do something and getting partial (and valid but incompatible) solutions from a number of sources.  If you decide to go with C++, get a book on STL and visit the BOOST web site often--it'll make your life a lot easier.

I learned QuickBASIC first... that was a horrible mistake for me, as it taught me to think in ways that are fundamentally conflicting with C++ and most other languages (at least in my eyes).  I think learning BASIC first made learning C++ much more difficult.

There's so many tutorials out there, though, that you should be able to figure out how to make something from scratch in any language within a few hours of Googling.

---

### Post by estyles on 2008-07-24
> **tinivole said:**
> 
ie:
```

Bash
Ruby --> Perl
         Python --> C
                    C++ --> ASM
                            Fortran
                            Cobol

```


While Assembly is still extremely useful (although insanely difficult to learn: if anyone is interested in a nice ASM website, this one is the best, IMHO: [http://www.azillionmonkeys.com/qed/asm.html](http://www.azillionmonkeys.com/qed/asm.html), though I must admit I'm not an ASM programmer and mostly used it for a few examples that I needed in a VC++ program, and also as just very interesting reading all around), I can't imagine that there's any point to learning Fortran and Cobol these days.  Legacy maintenance jobs, though once plentiful if not glamorous, aren't that big anymore AFAIK, and no one seriously codes in Fortran or Cobol any more than they do in Pascal.  (or SHOULD in BASIC, though that doesn't stop people...)

---

### Post by Frenske on 2008-07-24
As kid I had an MSX (remember those) and programmed in Basics. Later as geophysicist I have been taught Fortran and I have programmed it for years. Working for the next company, I had to learn C++ (basic level).
Now I am in a research position and basically I am given carte blanche and I am learning myself Python. If I need to do heavy calculations I simply plug some Fortran code in the Python code.

I think for basic programing Python is great and it has a very active community. Therefore I would strongly recommend it over C/Fortran.

---

### Post by ibuclaw on 2008-07-25
> **estyles said:**
> While Assembly is still extremely useful (although insanely difficult to learn: if anyone is interested in a nice ASM website, this one is the best, IMHO: [http://www.azillionmonkeys.com/qed/asm.html](http://www.azillionmonkeys.com/qed/asm.html), though I must admit I'm not an ASM programmer and mostly used it for a few examples that I needed in a VC++ program, and also as just very interesting reading all around), I can't imagine that there's any point to learning Fortran and Cobol these days.  Legacy maintenance jobs, though once plentiful if not glamorous, aren't that big anymore AFAIK, and no one seriously codes in Fortran or Cobol any more than they do in Pascal.  (or SHOULD in BASIC, though that doesn't stop people...)

Yeah, well, the problem with legacy languages is that around 60% of business' codebase still run on them (ie: if it's Unix/a Windows VT session to a Unix computer and the interface looks like curses, then you are most probably looking at a COBOL application), and maintainers are usually hard to find for reasons you just mentioned.

I seriously don't think that most companies will want to change their systems any time soon (if it has worked for 10-20 years, why change?) so I doubt Cobol or Fortran will disappear quite as quick as you misleadingly perceive...

As I stated in my (quick and painless) diagram, it s at the bottom of the list of languages, at least I, would like to try out. I recommend it to be only necessary if you want a quick side job that pays very good value for money. ;)

Regards
Iain

---

### Post by LowSky on 2008-07-25
My College made us learn Cobol before we could even take a Java or C/C++ class. IBM was our contributer of a Cobol Server. Until they took it down in 2006, now the new student learn it in Virtualization, which isn't the same.

Old languages are great to learn for some job like archiving and preserving but the newer languages is where the new exciting jobs are.

---

### Post by estyles on 2008-07-25
> **tinivole said:**
> ...I doubt Cobol or Fortran will disappear quite as quick as you misleadingly perceive...

As I stated in my (quick and painless) diagram, it s at the bottom of the list of languages, at least I, would like to try out. I recommend it to be only necessary if you want a quick side job that pays very good value for money. ;)

Okay, you're probably right, and I'm probably wrong on this one.  For one thing, I wasn't really aware of the proliferation of FORTRAN use in the scientific community.  But I still don't really think it's worth putting on a list of languages to learn (not that I'm saying your list is "wrong", it's just my opinion).  Maybe if it was the first thing you learned, you could try to get a quick side job for some cash.  But if you're going to learn all those other languages first, and actually delve into them rather than just superficially learn the syntax, why bother learning old mostly-dead languages at the end of it all?  

ASM on the other hand... not many people use it any more, but it's *so* powerful, *so* useful for the right type of things...  I mean, it's practically suicide to code an entire application in ASM these days, with all the GUI's and how complicated most programs have become, especially with all the nice high-level languages and application authoring tools.  But for a few CPU-intensive routines, the amount of speed you can gain is impressive.  One of the articles on the assembly page I linked earlier in the thread is about how much speed gain you can get compared to the strlen() commmand which is still used in the standard libraries - very interesting.

And some things are just so hard to do in some languages (I remember trying to do injected .dlls in C++, and realized I could do in about 10 lines of ASM (even without fully understanding the ASM code) what I never fully figured out how to do any other way), that learning ASM can be really useful for an already accomplished programmer.  Not that I'm there yet - which is why I don't really know ASM... :)

---

### Post by CarlosNYB on 2008-07-25
Three important things, IMO:

1) Personal 'fit':  Research the different IDE's and programming libraries which are available in various languages, some of them involve more text editing than others, some are more GUI, some have better widgets available, more support for drag and drop, etc.  You may discover from researching this that you really are impressed with or like a certain option, or that one of them seems to 'fit' you or your project, or would be inspiring to play with.  What impresses or inspires you, what do you want to tinker with, what might you enjoy tinkering with?  That's a very personal thing, people have different temperaments.

2) Practical considerations:  Consider whether a given language is suited for what you want to accomplish.  Perhaps you want to do 3D matrix calculations for a game and therefore a C++ environment involving the GTK makes sense, or perhaps you want to launch applications and Perl or Bash scripting makes more sense, perhaps you have a lot of time or don't have a lot of time to work on any given project, etc.

3) Considering the long term:  Think of the benefit a given language/system/environment may give you after you spend some time using and learning.  Perhaps one will be very flexible/powerful in the long run for you.  Perhaps in the long term mastery of a scripting language is most flexible/powerful for you, perhaps in the long term knowing C and the details of the kernel is most flexible powerful for you, etc.

---

