---
title: "programming langueges"
date: 2007-08-06
forum: Programming Talk
---

### Post by bribaetz on 2007-08-06
willing to learn any language im pretty experienced in programming 
never taken a college course on it tho i would like to know a good languege for like a swiss army knife to do graphic and text based programing language if you know of something like this please provide me with a tutorial link and a compiler as  i have found lists with hundreds of languages and if its not main stream or older it is quite difficult to find tutorials and compilers.thank you for any help you may provide and just out of curiosity what language(s) is Ubuntu feisty fawn in

---

### Post by slavik on 2007-08-06
to answer 1 of your questions, ubuntu is written in C ... ALL OF IT!

as for which language is mainstream, I'm surprised nobody has said python yet (seems to be the latest rage). I am a perl nut :P

---

### Post by bribaetz on 2007-08-06
thanks what compiler do you use for perl and what would be a good place to learn it

---

### Post by smartbei on 2007-08-06
The linux kernel is in C. However, the programs that are included with python are not all c. For example, Exaile and Listen, two good music players, are written in Python, and available from the repositories. Etc.

I believe you can just use synaptic to install perl. And try googling 'perl tutorials', or for that matter 'python tutorials'.

---

### Post by xtacocorex on 2007-08-06
> **bribaetz said:**
> thanks what compiler do you use for perl and what would be a good place to learn it
Perl is an interpreted language; here is a list of tutorials from a google search of "perl tutorials".
[http://www.google.com/search?client=safari&rls=en&q=perl+tutorials&ie=UTF-8&oe=UTF-8](http://www.google.com/search?client=safari&rls=en&q=perl+tutorials&ie=UTF-8&oe=UTF-8)

---

### Post by LaRoza on 2007-08-06
I recommend Python, but Perl is nice, my wiki is a very good place to start, if I do say so myself.

See the link in my sig.

---

### Post by Wybiral on 2007-08-06
> **smartbei said:**
> The linux kernel is in C. However, the programs that are included with python are not all c. For example, Exaile and Listen, two good music players, are written in Python, and available from the repositories. Etc.

I believe you can just use synaptic to install perl. And try googling 'perl tutorials', or for that matter 'python tutorials'.

But, all of the python modules were written in C. I'm sure the media library used for Exaile and Listen was written in C.

Not that Python isn't a good language, because it is, but it's heavily dependent on C and C-written modules.

I recommend: C, C++, or Python.

---

### Post by Ramses de Norre on 2007-08-06
> **slavik said:**
> to answer 1 of your questions, ubuntu is written in C ... ALL OF IT!

All KDE stuff is written in C++, many GUI front ends are written in python, many scripts and little applications are written in perl or bash, and the repos contain quite a lot of applications in java, xul, php, ... Ubuntu certainly isn't written entirely in C.

---

### Post by slavik on 2007-08-06
GNOME, GTK, kernel, ls/cd/grep and such ....

perl is installed by default.

---

### Post by Ramses de Norre on 2007-08-06
> **slavik said:**
> GNOME, GTK, kernel, ls/cd/grep and such ....

perl is installed by default.

That's probably not even half of ubuntu's code base.

---

### Post by pmasiar on 2007-08-06
> **Wybiral said:**
> But, all of the python modules were written in C. 

Not all - just many :-)

Python is *the* best language for beginner, especially self-learner. It is not only With C/C++ you will get bogged down with boring details from very beginning -- details with Python will take care for you, like variable types, etc.

Just compare simple task, like printing song "99 bottles on the wall" in:
[C](http://99-bottles-of-beer.net/language-c-820.html) (kernel module style - like C should be used), 
[Java](http://99-bottles-of-beer.net/language-java-3.html)  (with all the object obsession as standard Java uses all the time), 
[C++](http://99-bottles-of-beer.net/language-c++-111.html)
[Python](http://99-bottles-of-beer.net/language-python-808.html) and 
( very idiomatic) [Perl](http://99-bottles-of-beer.net/language-perl-539.html)

Each language has other version, but I tried to link most idiomatic solution (as the language is used in real life)

---

### Post by Wybiral on 2007-08-06
> **pmasiar said:**
> Each language has other version, but I tried to link most idiomatic solution (as the language is used in real life)

That C example was grossly over complicated.

It was intended as a kernel module, not a simple application.

To be fair you have to show a python version that's intended to be loaded as a kernel module :)

---

### Post by pmasiar on 2007-08-06
Not so. Would *you* use C or Python for kernel module? C or Python for simple script to massage data a little?

My goal was to show how languages are used - what code learner might encounter when reading real-life code.

---

### Post by Wybiral on 2007-08-06
When you're comparing these programs in terms of complexity, the code should be the typical way a C programmer would do it. Not what YOU think C is always meant to be used for.

I get your point, Python is meant for tiny scripts :)

But that doesn't mean every C program is going to be a kernel module.

EDIT:

Do *you* think a beginner should be blogged down with the complexity of large object oriented structures? Well... Python supports it. And C supports writing kernel modules... But both languages are flexible.

---

### Post by pmasiar on 2007-08-06
> **Wybiral said:**
> I get your point, Python is meant for tiny scripts :)

like [TinyERP](http://www.tinyerp.org/), complete enterprice system including shopping cart? :-)


> Do *you* think a beginner should be blogged down with the complexity of large object oriented structures? Well... Python supports it. And C supports writing kernel modules... But both languages are flexible.

after re-reading OP, she claims she knows programming pretty well, so... question is, what kind of programming you want to learn? 

Hacking on OpenOffice? Kernel? Drivers? Gnome/KDE GUI? Dynamic web applications (web2.0)? Programs for OLPC - famous $100 laptop? help with ubuntu own development? maintain some specific package you know or like to know better?

For every use case, there would be some most optimal language - and different for every case.

First ask "where you want to go" and then "how I will get there" and start looking for a map. Map of Chicago is useless in NYC... :-)

---

### Post by Wybiral on 2007-08-06
> **pmasiar said:**
> like [TinyERP](http://www.tinyerp.org/), complete enterprice system including shopping cart? :-)


> Do *you* think a beginner should be blogged down with the complexity of large object oriented structures? Well... Python supports it. And C supports writing kernel modules... But both languages are flexible.

after re-reading OP, she claims she knows programming pretty well, so... question is, what kind of programming you want to learn? 

Hacking on OpenOffice? Kernel? Drivers? Gnome/KDE GUI? Dynamic web applications (web2.0)? Programs for OLPC - famous $100 laptop? help with ubuntu own development? maintain some specific package you know or like to know better?

For every use case, there would be some most optimal language - and different for every case.

First ask "where you want to go" and then "how I will get there" and start looking for a map. Map of Chicago is useless in NYC... :-)

My script comment was a joke, I've seen some nice stuff written in Python.

I also think you hit the nail on the head... The OP needs to clarify what they want to do before asking how to do it.

---

### Post by pmasiar on 2007-08-06
> **Wybiral said:**
> My script comment was a joke, I've seen some nice stuff written in Python.
.

I know that you know it was a joke but some people might thought you said is seriously, and then repeat it somewhere and confuse more people - and TinyERP is pretty cool system I found recently :-)

---

### Post by bribaetz on 2007-08-06
thanks for  all the help i will check some of this stuff out i will probably  
still need a little more help though thanks very much
none of this works um im trying python using pype python interiter how do i make the code run

---

### Post by bribaetz on 2007-08-06
> **pmasiar said:**
> like [TinyERP](http://www.tinyerp.org/), complete enterprice system including shopping cart? :-)


> Do *you* think a beginner should be blogged down with the complexity of large object oriented structures? Well... Python supports it. And C supports writing kernel modules... But both languages are flexible.

after re-reading OP, she claims she knows programming pretty well, so... question is, what kind of programming you want to learn? 

Hacking on OpenOffice? Kernel? Drivers? Gnome/KDE GUI? Dynamic web applications (web2.0)? Programs for OLPC - famous $100 laptop? help with ubuntu own development? maintain some specific package you know or like to know better?

For every use case, there would be some most optimal language - and different for every case.

First ask "where you want to go" and then "how I will get there" and start looking for a map. Map of Chicago is useless in NYC... :-)

any widely used and widely available language is good for me i dont want crappy text based applications even once im expert at it.i have done C++ i love it but some stuff syntax otherwise i am inexpierianced at and find it hard to learn becasue i have not learned all i need to learn form other scipts but C++ is still cool i want to learn something a bit eisier for now

---

### Post by bribaetz on 2007-08-06
> **pmasiar said:**
> Not all - just many :-)

Python is *the* best language for beginner, especially self-learner. It is not only With C/C++ you will get bogged down with boring details from very beginning -- details with Python will take care for you, like variable types, etc.

Just compare simple task, like printing song "99 bottles on the wall" in:
[C](http://99-bottles-of-beer.net/language-c-820.html) (kernel module style - like C should be used), 
[Java](http://99-bottles-of-beer.net/language-java-3.html)  (with all the object obsession as standard Java uses all the time), 
[C++](http://99-bottles-of-beer.net/language-c++-111.html)
[Python](http://99-bottles-of-beer.net/language-python-808.html) and 
( very idiomatic) [Perl](http://99-bottles-of-beer.net/language-perl-539.html)

Each language has other version, but I tried to link most idiomatic solution (as the language is used in real life)

i read it python and perl a very similar in the syntax etc
basic is so old but look its cool  10 REM Basic version of 99 bottles of beer
 20 REM Modified by M. Eric Carr (eric@carrnet.net)
 30 REM from prior version found on this site.
 40 REM (Modified to correct "1 bottle" grammar)
 50 FOR X=99 TO 1 STEP -1
 60 PRINT X;"bottle";
 70 IF X<>1 THEN PRINT "s";
 80 PRINT " of beer on the wall,";X;"bottle";
 90 IF X<>1 THEN PRINT "s";
100 PRINT " of beer"
110 PRINT "Take one down and pass it around,"
120 PRINT X-1;"bottle";
130 IF X<>1 THEN PRINT "s";
140 PRINT " of beer on the wall"
150 NEXT

---

