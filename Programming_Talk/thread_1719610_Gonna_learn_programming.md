---
title: "Gonna learn programming"
date: 2011-04-02
forum: Programming Talk
---

### Post by nkae100 on 2011-04-02
I am very frustrated with most software developed and up to my ears experiencing bull ****.

I have had enough of this flawed 'user knows everything' mentality of most software developers and decided to take up programming.

I am 26 years old and jobless. I party and I drink allot. I love computers but I love partying and woman more. This is why I have never taken up programming, because I just don't have the time for it.

What I've decided is I'm gonna tap into into it, but not full on, so in other words when I have nothing else to do.

I have decided to choose learning the C programming language because it is the most wide spreed language used (according to Wikipedia) and its open sourced.
Computers are a passion for me. I don't care about making money off them. I guess you can say I am a computer philantropist.


I've established that the official website for C found at is:

[http://www.open-std.org/JTC1/SC22/WG14/](http://www.open-std.org/JTC1/SC22/WG14/)

I've also established that the current standard is ISO/IEC 9899:1999.
The problem I face is that this website suffers the 'user knows all' mentality. I have no fuckin idea what is going on!

What I am after is a Specification page, where I can go in and learn from the fundamentals.

To give an example, I am pretty good at HTML. I learn't HTML from the official specification website at:

[http://www.w3.org/TR/1999/REC-html401-19991224](http://www.w3.org/TR/1999/REC-html401-19991224)

... this is the type of page I am looking for, but for C. So I can start off at the start and learn the basics, if you know what I mean??..

Can anyone give me a direction?

---

### Post by nkae100 on 2011-04-02
I just saw at:

[http://www.open-std.org/JTC1/SC22/WG14/www/standards](http://www.open-std.org/JTC1/SC22/WG14/www/standards)

"Published ISO and IEC standards can be purchased from a member body of ISO or IEC."

Does this mean I have to buy the Specification thing?

---

### Post by Phenax on 2011-04-02
Good primer to the language:
[http://www.cprogramming.com/tutorial/c/lesson1.html](http://www.cprogramming.com/tutorial/c/lesson1.html)

C compilers are reasonably complex these days, so it might take a little while to learn how to fully use them. On Ubuntu, most people use GCC (GNU Compiler Collection).

Extreme basics:
gcc source.c -o executable
Compile source.c (C source code) to a file named executable (executable file).

There are also a lot of other tools you should eventually become acquainted with along the way. Like using a linker, using a build system (like GNU Make/CMake), using third-party libraries (like SDL/GMP), a debugger (like GDB)

Edit: Here's a draft of the standard, but it's mostly technical writing that probably isn't suitable from learning the basics from. [http://www.open-std.org/JTC1/SC22/WG14/www/docs/n1256.pdf](http://www.open-std.org/JTC1/SC22/WG14/www/docs/n1256.pdf)

---

### Post by 23dornot23d on 2011-04-02
I have just started too ... and want to get straight into it ......

I have many books on C and have done the hello world thing .......

But here is where I am trying to bring things together to make them useful

If you want to have a look I sort of keep a log as I go through things ,,,,,

Might Help you a little  ,,,,,, if not hope someone else can help out

Here is a LINK to what[ I am doing and learning on linux]("https://sites.google.com/site/programminglearnc/assignments")

Looking at Qtcreator Project 1 - it has lots of demo files ..... to look at too and to try out

Enter this below or look in synaptic package manager for it ......

sudo apt-get install qtcreator

---

### Post by nkae100 on 2011-04-02
Phenax:

I would like to learn from the official bodies documentation.

I have used GCC successfully.

I won't be using third party libraries or anyone elses stuff. Only my own. I have never found someone elses software that I am completely happy with.


23dornot23d:

haha yeah I have done the hello world thing aswell. It was an exciting milestone for me.

Your sites confusing man.

---

### Post by 23dornot23d on 2011-04-02
Sorry if my sites confusing ... just do it as I go ..... each time I think of something to do I add to it ....... and if it works I post it ..... if it fails I post it ......

But I keep a record of what is available at the time and what I am trying to achieve ....

There are loads of sites set up to go step by step ....... QTcreator is pretty good though and I tried the examples and they work ok ...

Just alter them and see what happens ....... 

I learn by trying things out .....

---

### Post by nkae100 on 2011-04-02
I am turned off C. They charge money.

---

### Post by Phenax on 2011-04-02
> **nkae100 said:**
> I am turned off C. They charge money.

You can find the current draft for the C99 standard here: [http://www.open-std.org/JTC1/SC22/WG14/www/docs/n1256.pdf](http://www.open-std.org/JTC1/SC22/WG14/www/docs/n1256.pdf)

---

### Post by 23dornot23d on 2011-04-02
Who charges money the programs are all free on Linux anyway !!

---

### Post by nkae100 on 2011-04-02
I am on the python website. This looks like something I will enjoy. They speak on my level. Its also probably going to be faster to achieve something I will be happy with.

---

### Post by nkae100 on 2011-04-02
HAHA on their beginers page:

[http://wiki.python.org/moin/BeginnersGuide/NonProgrammers](http://wiki.python.org/moin/BeginnersGuide/NonProgrammers)

Check it out:

"If you've never programmed before, the tutorials on this page are recommended for you; they don't assume that you have previous experience."

---

### Post by juancarlospaco on 2011-04-02
Python *?*

---

### Post by 23dornot23d on 2011-04-02
Python is good - quicker to achieve results too ..... what are you going to try to do ?

Most what I do is based a round 3D so scripts in Blender are Python .....

Also 2D like Gimp the Plugins there are written in Python .....

QT4 also outputs forms in Python ...... using Python tools

---

### Post by Learning Linux 2011 on 2011-04-02
I personally think you are starting off on the wrong foot with that C standards web site.  That is way too complex for a beginner.  Sites like those are for people who are masters of C.

I would recommend getting a book like "The C Programming Language" by Kernighan and Ritchie.  They literally invented the language, and that book is pretty decent for learning it.

You may want to look into other beginning programming books too.

Learning Python might be a good idea too.  A good book for learning it is called "Think Python".  You can either get a PDF or buy a paper copy at [http://greenteapress.com/](http://greenteapress.com/)**thinkpython**/**thinkpython**.html

---

### Post by nkae100 on 2011-04-02
Right now I am reading "How To Think Like A Computer Scientist".

I'm on this page:

[http://openbookproject.net/thinkcs/python/english2e/preface.html](http://openbookproject.net/thinkcs/python/english2e/preface.html)

This guy's mentality is EXACTLY what I am after. This guy needs a reward!

This book is officially endorsed.

---

### Post by CptPicard on 2011-04-02
You know, learning programming takes lots of effort and dedication. Just deciding to fix everything using only your own code(!) and doing it on the side when you're otherwise drinking and partying doesn't sound like a realistic proposition.

But, you are on the right track with Python. It's an excellent start for a beginner, and a really nice language overall even after you're no longer a beginner.

---

### Post by simeon87 on 2011-04-02
You seem to think you can rush into the programming field and make improvements to existing software quickly. It's not that simple, in particular when you're learning the basics.

I would also suggest to start with Python rather than C.

---

### Post by dazman19 on 2011-04-04
> **Phenax said:**
> Good primer to the language:
[http://www.cprogramming.com/tutorial/c/lesson1.html](http://www.cprogramming.com/tutorial/c/lesson1.html)



aiii,

C to start off with. Understanding passing by value/reference is very important. C++ is a nightmare if you don't understand pointers because you wont know what you are doing.

---

### Post by 102jon on 2011-04-04
> **dazman19 said:**
> aiii,

C to start off with. Understanding passing by value/reference is very important. C++ is a nightmare if you don't understand pointers because you wont know what you are doing.

Yeah, but it's way more important to learn the fundamentals of programming first (basic logic, standard variable declarations, input/output, conditional statements, loops, etc.) before getting closer to the hardware. Yes, pointers are important. They are by no means the first thing a new programmer should learn however.

---

### Post by Segaman on 2011-04-04
you also could look at microsoft (yes,microsoft) education web-portal [http://dreamspark.com](http://dreamspark.com) , you can find useful links there. If you`d be a student,you could download that soft for free :)
P.S. Perhaps you shiould try to code something on pascal? Then,in a couple of months, get into c++.
P.P.S If you got money or you`re student, visit [http://www.pluralsight-training.net/microsoft/](http://www.pluralsight-training.net/microsoft/)

Dont blame me for "microsoft" lol :D

---

### Post by dazman19 on 2011-04-04
> **102jon said:**
> Yeah, but it's way more important to learn the fundamentals of programming first (basic logic, standard variable declarations, input/output, conditional statements, loops, etc.) before getting closer to the hardware. Yes, pointers are important. They are by no means the first thing a new programmer should learn however.

Yeh

I started with towers of hanoi, functions, understanding them how and what they return. And basic Types int/char/float. Move onto
Loops (for/while/do) and arrays of basic types. Then onto data structures, pointers(*) and references(&).

Finally recursion / malloc and free.

Once you got this you are ready for C++.

---

### Post by andrew1992 on 2011-04-04
C is not a prerequisite to learning C++, if that's what you're suggesting. Besides, OP has already said he's going with Python.

---

