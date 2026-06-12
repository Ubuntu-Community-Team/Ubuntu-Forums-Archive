---
title: "Basic programming language"
date: 2010-01-25
forum: Programming Talk
---

### Post by kpsg25690 on 2010-01-25
Hey!
I wanted to get a head start on learning BASIC as i have use for it later in my curriculum for programing micro-controllers..

I wanted to know a good and easy application(or IDE) to start..

I have some experience with C and C++..

I have tried using Basic-256 but it seems to be buggy for Ubuntu..

I am using karmic...
any help is appreciated..
:D

---

### Post by saif_held on 2010-01-25
I heard **Kbasic **is good, I never tried it though but it might work out for you.

---

### Post by kpsg25690 on 2010-01-26
I'll try it out and get back..
downloading it now...
meanwhile any other suggestions would be appreciated..

---

### Post by Tony Flury on 2010-01-26
I would be very careful with BASIC.

Unlike C, C++, Python, JAVA etc which are more or less governed by as set of international standards, and which most implementation abide by, BASIC (although it does in theory have an international Standard) there are many fundamentally different dialects - for instance BBC Basic and Microsoft Visual BASIC - both dialects of the simple language but with very different features, and learning BBC Basic does not actually help really when you try to learn Visual Basic.

If I were you I would try to discover which dialect of Basic you will be using, and if you can get an implementation of that dialect, if you don't you could end up learning features of a dialect which don't exist (or even worse work in a different way) in the dialect which you need to use later on during your study.

---

### Post by lisati on 2010-01-26
There's also [FreeBASIC]("http://www.freebasic.net/")

---

### Post by underquark on 2010-01-26
OP - which micro-controller?  It's likely got its own requirements for a subset of BASIC or a BASIC with proprietary features.  To get the most out of the micro-controller will probably mean using every trick available for that device.

---

### Post by kpsg25690 on 2010-01-27
first of all,
thank you for replying..

@Tony Flury
I know that much that i have no real use for visual basic for what i am looking to learn..

@lisati
I tried Freebasic,i installed it only to discover nothing new..
i think it only adds the compilers,libraries for basic but isn't like an IDE i guess,if so i couldn't get it to work that way..


@underquark
i am not looking for anything specific right now, i know most microcontrollers have their own subset of basic for making and burning the programs on that,but i want to learn basic in general so its easier to learn and implement that.

i actually am quite familiar with both C and C++,and i know that C is used to make programs for microcontrollers,
but i was lead to believe that it's easier in BASIC..

if there's no program like that that's easy and simple to use, i guess i should just use wine..
wanted to stay away from it but ..


any replies would be appreciated
:D

---

### Post by mikejonesey on 2010-01-27
i use [http://www.cipherlab.com/catalog.asp?CatID=9&ProdID=31&SubcatID=13](http://www.cipherlab.com/catalog.asp?CatID=9&ProdID=31&SubcatID=13)

which i believe is a derived from quickbasic, its the best basic compiler i have used. 

ps i hate basic, you can consume zillions of lines of code to achieve very little.

---

### Post by kpsg25690 on 2010-01-28
couldn't find anything on the link you gave..
thanks anyway..

---

### Post by dmb1122 on 2010-01-28
Have you tried REALbasic?  It's a cross-platform development environment, so you can compile for Mac, Windows and Linux from any platform.  It's a modern implementation of BASIC, and it's easy to learn.

[http://www.realsoftware.com](http://www.realsoftware.com)

They have a free 30-day trial too.

---

### Post by RLWurdack on 2010-01-28
The Parallax development software (For their STAMPS, SXs, and PROPELLER boards) is available for download free on their site, parallax.com.
 
You can get cheap development systems there as well.
 
Microchip has a wealth of free downloads also for their PIC and PICDSP stuff.
 
I'd bet Freescale and Ardino have similar offerings.
 
I have no connection to any of the above companies. I'm retired so now I only tinker 18 hours per day.
 
Dick

---

### Post by lisati on 2010-01-28
> **dmb1122 said:**
> Have you tried REALbasic?  It's a cross-platform development environment, so you can compile for Mac, Windows and Linux from any platform.  It's a modern implementation of BASIC, and it's easy to learn.

[http://www.realsoftware.com](http://www.realsoftware.com)

They have a free 30-day trial too.

Very nice in the video, but (a) non-free, and (b) it didn't play nice with Firefox on my laptop for some reason.

---

### Post by ve3tru on 2010-01-29
GAMBAS all the way, its similar to Visual Basic (windows) but tweaked for Linux.
I'm a complete novice and now I'm making simple programs. yay 
That reminds me I have to post a question, I'm a little stumped now.
Oh ya its free unlike Visual Basic, they want lots of $$$ for that one.

---

### Post by ferty on 2010-01-30
Hi,Take a look at this [http://www.purebasic.com/]("http://www.purebasic.com/")

A fab,fast,language with great linux support great runtime speed and tiny program size,as well as Windows,MacOS X.

Try the demo version Here=[http://www.purebasic.com/download.php]("http://www.purebasic.com/download.php")

Best of luck.

---

### Post by Superpelican12 on 2011-01-07
So KBasic, isn' t anything? I'm a beginning programmer. And I like the clear interface of it. It' s a great IDE. And if you don't like it or can't use it, I've one tip: only look at RAD programs. RAD means: Rapid Application Development, in case you didn't no. No RAD means a waste of time.

---

### Post by skullmunky on 2011-01-07
If it's for microcontrollers I bet we're talking about the BASIC Stamp; if you already know some C/C++ you'll be best served by just starting with that, or the version of BASIC for whichever micro you're going to be working with.   

My own inclination would be to just skip all that and use Arduino or straight C on an AVR - more modern, better cross-platform support, open-source ...

---

### Post by worksofcraft on 2011-01-07
> **kpsg25690 said:**
> Hey!
I wanted to get a head start on learning BASIC as i have use for it later in my curriculum for programing micro-controllers..


You can't be serious :shock:

---

### Post by Tony Flury on 2011-01-08
> **kpsg25690 said:**
> first of all,
thank you for replying..

@Tony Flury
I know that much that i have no real use for visual basic for what i am looking to learn..


I did not say you needed VB - i was using it as a example of the very big differences between the dialects of Basic. To be honest no-one needs VB, it is a mess of a language.

---

