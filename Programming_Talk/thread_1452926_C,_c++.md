---
title: "C, c++"
date: 2010-04-12
forum: Programming Talk
---

### Post by duke.tim on 2010-04-12
Okay I know this is mainly for linux and ubuntu, but since linux users have been much more helpful than windows and such I hope you can help. :) okay so I have started some tutorials on c++ and I have come across cin verses scanf; and cout verses printf. What is the Diffrence they seem to do the exact same thing :/ 

P.S. I am running ubuntu 64bit if that makes any diffrence to which command I should use

---

### Post by lisati on 2010-04-12
Moved to "Programming Talk"

Perhaps someone more experienced in C & C++ than myself can elaborate but here goes with my $0.02

scanf and printf are traditional C functions. cin and cout are specific to C++, and are better suited to the OOP programming style that C++ lends itself to.

---

### Post by azagaros on 2010-04-12
The C language:

stdio.h -- 

scanf(inVar)
printf(OutVar)

The C++ language

oistream(.h)

std::cin << inVar;
std::cout >> outVar >> std::endl;

if you understand the evolution of the two languages, c++ is an extension of C and now has evolved a little further than that.

Most of the C++ out there is a perversion of an implementation in c.

if you hit the STL part of c++ you see a lot of C references in it.

---

### Post by PaulM1985 on 2010-04-12
I am pretty sure, almost certain, that cin and cout are only available in c++ and not in c.

I would generally as a rule use cin and cout for input and output in c++ and use scanf and printf in c.  I have a feeling, but again not definite, that some of the Windows compilers are deprecating scanf and printf for c++ and these functions used in c++ code flag up as deprecation warnings.

Paul

---

### Post by MadCow108 on 2010-04-12
yes they do very similar things
printf is the cout of C
cout is the printf of C++

they are both just the mean of the language to perform input output
printf is available in C++ is just to keep compatibility with C code
it does not mean you should use it in new code

---

### Post by nvteighen on 2010-04-13
> **duke.tim said:**
> Okay I know this is mainly for linux and ubuntu, but since linux users have been much more helpful than windows and such I hope you can help. :) okay so I have started some tutorials on c++ and I have come across cin verses scanf; and cout verses printf. What is the Diffrence they seem to do the exact same thing :/ 

P.S. I am running ubuntu 64bit if that makes any diffrence to which command I should use

Hm... This is the best C++ tutorial I know of and it clearly avoids "C-like C++": [http://cplusplus.com/doc/tutorial/](http://cplusplus.com/doc/tutorial/)

And btw, if interested on learning the differences, this is the best C tutorial I know of: [http://crasseux.com/books/ctutorial/](http://crasseux.com/books/ctutorial/)

---

