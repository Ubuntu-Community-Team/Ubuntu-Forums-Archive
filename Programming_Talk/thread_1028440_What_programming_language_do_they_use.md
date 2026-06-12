---
title: "What programming language do they use ????"
date: 2009-01-02
forum: Programming Talk
---

### Post by hoboy on 2009-01-02
I am a java guy, I am curious about what type of programming langages they use in place like NASA, Rokett-Technologies, Aeronautic like fighter plan.
Is it c,c++, python, lisp  or something else ?

---

### Post by dexter on 2009-01-02
Most military projects use a very strict language like ada: [http://en.wikipedia.org/wiki/Ada_(programming_language](http://en.wikipedia.org/wiki/Ada_(programming_language))

---

### Post by aranke on 2009-01-02
I don't know about the others, but NASA uses Python.

---

### Post by creek23 on 2009-01-02
> **aranke said:**
> I don't know about the others, but NASA uses Python.

And I thought Java was used into one of NASA's vehicle that landed (or orbited) Mars.

---

### Post by ZuLuuuuuu on 2009-01-02
> **aranke said:**
> I don't know about the others, but NASA uses Python.

On Python web page it says "NASA uses Python" but that does not mean "NASA *only* uses Python". Python is just one of the programming languages they use.

---

### Post by Cracauer on 2009-01-02
> **hoboy said:**
> I am a java guy, I am curious about what type of programming langages they use in place like NASA, Rokett-Technologies, Aeronautic like fighter plan.
Is it c,c++, python, lisp  or something else ?

Most of these places use several languages. Even if management cracked down on the language zoo you need one high-performance language such as C++ and most shops (including google as a prominent example) realize that the most common programmer is most productive in a language like Python.

Plus space and aero people use a lot of Fortran. If you have an existing simulation in Fortran you are going to maintain it.

NASA has quite a bit of Lisp code. Systems to find solutions for very complex problems such as packing a Space Shuttle are often initially implemented at universities and then used there.

The on-board systems are all microcontroller like systems that have a preferred language and if you are lucky it's C.

The military use of ADA is overrated. They switched "completely" to ADA just as the United Stated switched to the metric measurement system.

---

### Post by tinny on 2009-01-02
> **creek23 said:**
> And I thought Java was used into one of NASA's vehicle that landed (or orbited) Mars.

Java was used on the ground for remote control.

[http://www.sun.com/aboutsun/media/features/mars.html](http://www.sun.com/aboutsun/media/features/mars.html)

Future missions plan on using real time Java in the rover itself.

[http://www.linuxdevices.com/news/NS3674252711.html](http://www.linuxdevices.com/news/NS3674252711.html)

---

### Post by slavik on 2009-01-02
> **Cracauer said:**
> Most of these places use several languages. Even if management cracked down on the language zoo you need one high-performance language such as C++ and most shops (including google as a prominent example) realize that the most common programmer is most productive in a language like Python.

Plus space and aero people use a lot of Fortran. If you have an existing simulation in Fortran you are going to maintain it.

NASA has quite a bit of Lisp code. Systems to find solutions for very complex problems such as packing a Space Shuttle are often initially implemented at universities and then used there.

The on-board systems are all microcontroller like systems that have a preferred language and if you are lucky it's C.

The military use of ADA is overrated. They switched "completely" to ADA just as the United Stated switched to the metric measurement system.
all civilian avionic equipment runs ADA code, land (control towers) or air (critical airplane systems).

---

### Post by dwhitney67 on 2009-01-02
NASA is such a huge organization, that it depends on the platform and the application at hand to decide which language to use.  I know that in the past, NASA used Assembly, C, C++, Java, Ada, Lisp, Fortran, Shell scripting, and presumably Python as well.  Ada has fallen out of favor with many organizations; its day in the sun is for the most part, over.

---

### Post by Cracauer on 2009-01-02
> **slavik said:**
> all civilian avionic equipment runs ADA code, land (control towers) or air (critical airplane systems).

Also see:
[http://en.wikipedia.org/wiki/DO-178B](http://en.wikipedia.org/wiki/DO-178B)

[http://www.gcn.com/print/27_8/46116-1.html](http://www.gcn.com/print/27_8/46116-1.html)

---

### Post by kjohansen on 2009-01-02
i have a few friends at boeing who do work in fortran...

---

### Post by hoboy on 2009-01-03
Thanks all of you for your very informative answers.

---

### Post by slavik on 2009-01-03
> **kjohansen said:**
> i have a few friends at boeing who do work in fortran...
what do they use their fortran code for? I would guess for physics related problems when making a plane.

---

### Post by imdano on 2009-01-03
I interviewed with Raytheon, which does a lot of contract work for the US Government, and they told me I'd probably be doing C/C++ if I ended up working there.  They also menitioned GUI work that was done in Java.

---

### Post by kjohansen on 2009-01-03
> **slavik said:**
> what do they use their fortran code for? I would guess for physics related problems when making a plane.

One works with navigation systems, and one makes sure the wings dont fall off...

---

### Post by jespdj on 2009-01-03
The programming language [Ada](http://en.wikipedia.org/wiki/Ada_(programming_language)) is, as far as I know, used a lot in the US DoD for things like airplanes and other military equipment.

Probably C is also used as a low-level systems programming language.

The NASA also uses Java; for example the software that NASA uses to plan the missions of the Spirit and Opportunity rovers on Mars, and for uploading commands to those rovers, is written in Java (in fact, it's an Eclipse Rich Client Platform application). See this: [Java Technology and the Mission to Mars](http://www.sun.com/aboutsun/media/features/mars.html).

Java programs are also used at CERN for the Large Hadron Collider: [Cern demos Java apps for giant 3D digital camera](http://news.zdnet.co.uk/software/0,1000000121,39418106,00.htm)

I love science, space and technology, I would love to work on such a project someday.

*edit*: Oh, I see I was not the first one posting those links...

---

### Post by samjh on 2009-01-03
> **hoboy said:**
> I am a java guy, I am curious about what type of programming langages they use in place like NASA, Rokett-Technologies, Aeronautic like fighter plan.
Is it c,c++, python, lisp  or something else ?

NASA is a huge organisation and they use many programming languages, including Ada, C, C++, Java, Python, and many more.  Python is generally restricted to data-centre and project coordination roles, Java is used for control UI (Mars rover, Hubble, and others) and some embedded systems.  The majority of "hard" programming (ie. on the spacecraft) are done in Ada, C, and C++.

The ESA (European Space Agency) is a heavy use of Ada for flight software.  C and C++ are also prevalent.

In the avionics industry, Assembly, Ada, C, and C++ are the staple languages.  You'll rarely find anything else.  Ada is extremely popular in air traffic control across North America and Europe, as well as rail networks.  There is a trend toward using "safe" subsets of those languages like SPARK, MISRA-C guidelines, Embedded C++, and associated tools.

The Ada mandate was a political flop, unfortunately.  Mismanagement by the US government killed Ada, and resulted in the mandate being lifted in 1997.  Mandating the use of a language without proper compilers or development tools just doesn't work.  Interestingly, after the mandate was lifted, its popularity expanded and better tools became available.  But it's still a dying language these days (much like COBOL and Fortran - good in its niche, not much else).

---

