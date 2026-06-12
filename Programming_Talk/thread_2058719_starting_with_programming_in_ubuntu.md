---
title: "starting with programming in ubuntu"
date: 2012-09-16
forum: Programming Talk
---

### Post by ajdinm on 2012-09-16
I'm starting with engineering university (computer science) and we're starting with programming. First semester is programming in C, and rest 4+ years is c++. They are using Code::Blocks. 
My question is, will I be able to follow and do same stuff as others via Ubuntu. I've installed Code::Blocks on Ubuntu, and it **seems** it's working fine from now. I wasn't writing any actual code yet, so will it have same functionality and everything as I'd be doing it on windows. (which is not problem, i have win7, and every freshman gets  license for win8 and some other ms stuff).
Thanks in advance.
P.S. Since I'm complete newbie to programming, would You mind posting helpful links. tutorials or tips for programming.  Since it will become my main tool for job, i really want to get as good as possible in it.

---

### Post by KdotJ on 2012-09-16
Programming in C will have some dependencies depending on which platform you are working on. 

However, I would strongly guess that for your first year (if not your whole course) and an introduction to programming that you would just be doing generic stuff in which it would not matter if you were using Windows, Linux or OSX. 

I'm sure you'll be fine, good luck!

---

### Post by ajdinm on 2012-09-16
> **KdotJ said:**
> Programming in C will have some dependencies depending on which platform you are working on. 

However, I would strongly guess that for your first year (if not your whole course) and an introduction to programming that you would just be doing generic stuff in which it would not matter if you were using Windows, Linux or OSX. 

I'm sure you'll be fine, good luck!

Thanks, I plan extensively learning and spending hours coding. Last thing I want is to stop every minute because it isn't same as tutors work or something like this. Thanks.

---

### Post by EnexOD on 2012-09-16
I am a beginner in programming too (only been coding for a year now) but am still in highschool. Currently we are learning Python 2.7 on Windows.

---

### Post by Petro Dawg on 2012-09-16
I'm by no means an expert programmer, and I haven't tried too hard to find a solution, but it has been my experience that the C++ programs I've compiled in Windows will not run on Linux and vice-versa.  There may be ways around this (perhaps a setting in Code-Blocks) but be careful when submitting an assigned complied program (if that ever happens) to be sure it is compiled for the correct environment.

However, a program written using Code-Blocks in Linux can easily be compiled in Windows and runs just fine in Windows and vice-versa.  Just be careful about including Windows or Linux specific libraries and such.

I'm quite surprised you would spend your entire education learning only c (or a c variant), wouldn't you also be taught java, html, vb, or python?

---

### Post by Galdov on 2012-09-16
I use for school jobs Borland under Wine because of some issues in programs under different compilators, but i would prefer to use a native program

In what im studying (3 years) is year 1 and 2 C++ and year VB, not Java or Phyton :/ (but when i finish i'll be looking for something else)

---

### Post by ajdinm on 2012-09-17
> **Petro Dawg said:**
> 
I'm quite surprised you would spend your entire education learning only c (or a c variant), wouldn't you also be taught java, html, vb, or python?
In first semester it's c, rest is c++. If i get good at those I plan extending my knowledge by probably php, java or something like that.

---

### Post by trent.josephsen on 2012-09-17
Sheesh, is two languages all they teach in a bachelor's CS program? That's ridiculous. I studied Java, 2 or 3 assembly languages, MATLAB, and LabVIEW just to pass my classes (not counting the C, Lua, and VHDL I used in projects). And that was in Engineering, not CS (in case that wasn't obvious).

Storing information for my rant on CS education... perhaps the situation is worse than I realized.

---

### Post by Petro Dawg on 2012-09-17
PUBLIC FUNCTION good_post(reader AS VARIANT) AS BOOLEAN

> **trent.josephsen said:**
> Sheesh, is two languages all they teach in a bachelor's CS program? That's ridiculous. I studied Java, 2 or 3 assembly languages, MATLAB, and LabVIEW just to pass my classes (not counting the C, Lua, and VHDL I used in projects). And that was in Engineering, not CS (in case that wasn't obvious).

Storing information for my rant on CS education... perhaps the situation is worse than I realized.

DIM interested AS BOOLEAN
interested = get_interested(reader)

IF interested = TRUE THEN

Petroleum Engineering major here, had to learn the basics of C, the entirety of VBA, a small amount of HTML, and some Mathematica thus far to get through my Junior year, still another year to see what else I'll need.  Oh yeah, almost forgot my TI calculator programming (I'm counting that too ;)).  GOTO 2  

LABEL 2
I've always considered my self a rather low level programmer, but perhaps I'm further ahead than what I thought when considering what's being taught in CS programs. 

I think the best way to learn the stuff is to edit existing code.  Programming your own games helps too.

good_post = true

ELSE

good_post = false

END IF

END FUNCTION

---

### Post by Glencore on 2012-09-19
We really need to liberate schools from Windows :)

Mostly it will all be the same except for OS commands, some libraries can help with the basic stuff though. 

Good luck \o/

---

### Post by ofnuts on 2012-09-19
> **trent.josephsen said:**
> Sheesh, is two languages all they teach in a bachelor's CS program? That's ridiculous. I studied Java, 2 or 3 assembly languages, MATLAB, and LabVIEW just to pass my classes (not counting the C, Lua, and VHDL I used in projects). And that was in Engineering, not CS (in case that wasn't obvious).

Storing information for my rant on CS education... perhaps the situation is worse than I realized.
One assembly language is enough. However, if getting familiar quickly with a new  language is the hallmark of the decent programmer, I'm not convinced that proper CS education is measured by the number of languages they teach you. Looking at my freshly graduated colleagues, I wish they taught them less languages but more theory and good programming practices. Language fashion changes, my "main" programming language changes every 3-4 years.

Ah, and  the use of shell scripts and the command line.

---

### Post by trent.josephsen on 2012-09-19
> **ofnuts said:**
> One assembly language is enough.
I concur. I took a computer engineering concentration, so my core requirements included 3 assembly languages most of the engineering students would not be exposed to (ARM, x86, m68k), in addition to the machine language programming we did in the fundamentals-of-engineering class... some kind of Atmel processor, I think? But I'm not advocating teaching every student assembly; it's not useful.

> However, if getting familiar quickly with a new  language is the hallmark of the decent programmer, I'm not convinced that proper CS education is measured by the number of languages they teach you. Looking at my freshly graduated colleagues, I wish they taught them less languages but more theory and good programming practices. Language fashion changes, my "main" programming language changes every 3-4 years.
Which is exactly why it's important that new graduates have experience with multiple languages, so they can apply what they know to learning whatever *new* languages they need in the workforce. Real programmers can write FORTRAN in any language; I imagine you could say the same thing about inexperienced programmers and C++.

But I can agree with you about good programming practices. I had a programming internship during school and that's really where I learned about stuff like documentation, revision control, SQL, and putting code in a real-world environment. My university's CS students didn't have an industry-sponsored senior design project like the engineers did, so I'd bet quite a few of them were less well prepared for industry than they might have been if they'd been taught, you know, practical stuff.

</rant>

---

### Post by satsujinka on 2012-09-19
@trent
Some schools just have a really poor CS curriculum.

Where I went we learned 2 languages in the intro class (Scheme and Python.) Other classes had a variety of languages (ASM, C, C++, Java, Perl, C#, and FORTRAN.)

A friend of mine's school only taught Python, Java, and C. And another's only taught in C++ (well, they had a tour of languages class, but that hardly counts.)

---

