---
title: "Several C++ Related Questions"
date: 2009-10-21
forum: Programming Talk
---

### Post by patrickaupperle on 2009-10-21
I am learning C++ out of a book that seems to be a couple (possibly several) years old, is this a problem?

What has changed in C++ in the last several years, that I should be aware of?

For #include statements, the book always does #include <file.h>, is this still acceptable? I read somewhere that something closer to #include <cfile> is better. Please guide me as to what to use.

How does the intel c++ compiler compare with g++?

I had some other questions, that I do not remember right now, so I will be either editing this post or posting them in a new post. :)

Thank you for the support.

Edit: I just remembered one of those questions!
Added above.

---

### Post by dwhitney67 on 2009-10-21
> **patrickaupperle said:**
> 
For #include statements, the book always does #include <file.h>, is this still acceptable? I read somewhere that something closer to #include <cfile> is better. Please guide me as to what to use.

This is correct; for example, in the past <iostream.h> was included; nowadays it is <iostream> and you must qualify objects such as cout and cin with the std:: namespace qualifier.  For certain C-library files, the "c" is prefixed in front of the header file name, and the trailing '.h' has been dropped.  For example, <ctime>, <cmath>, <cassert>.

> 
How does the intel c++ compiler compare with g++?

I've never used the latter; always used either Sun's compiler or Linux's g++ (GCC).

---

### Post by patrickaupperle on 2009-10-21
> **dwhitney67 said:**
> This is correct; for example, in the past <iostream.h> was included; nowadays it is <iostream> and you must qualify objects such as cout and cin with the std:: namespace qualifier.  For certain C-library files, the "c" is prefixed in front of the header file name, and the trailing '.h' has been dropped.  For example, <ctime>, <cmath>, <cassert>.


I've never used the latter; always used either Sun's compiler or Linux's g++ (GCC).

So, when all are options, should I use #include <cfile>, #include <file.h> or #include <file>?

Still looking for answers to the other questions, too!

edit: Wow, I think I misread your post earlier. So, you are saying I should use #include <cfile> when possible, #include <file> when there is no cfile, right?

---

### Post by TheStatsMan on 2009-10-21
> **patrickaupperle said:**
> 
How does the intel c++ compiler compare with g++?


For numerical work I have found the intel compiler to be quite a bit faster, particularly when using openmp. Some things are tough to get running with the intel compiler though and I have had the odd bug with it. The intel math kernel library is no where near as straight forward to link to and use as it should be.

---

### Post by patrickaupperle on 2009-10-21
> **TheStatsMan said:**
> For numerical work I have found the intel compiler to be quite a bit faster, particularly when using openmp. Some things are tough to get running with the intel compiler though and I have had the odd bug with it. The intel math kernel library is no where near as straight forward to link to and use as it should be.

So, you probably would not recommend it to learn on? You would, however, recommend it in a production environment? Am I correct in these assumptions?

Any want to tell me if the book I am learning out of is ok? 
Here is a link to the exact book: [C++ Without Fear: A Beginner's Guide That Makes You Feel Smart]("http://www.amazon.com/Without-Fear-Beginners-Guide-Makes/dp/0321246950/ref=sr_1_1?ie=UTF8&s=books&qid=1256134651&sr=8-1")

---

### Post by Simian Man on 2009-10-21
On include files:  The ones for the standard C++ library should be used as <file>.  For example <iostream> <string> <vector> and so on.  The ones for the standard C library should be used as <cfile>.  For example <cstdio> <cstdlib> and so on.  Sometimes there are filenames that sound similar, but are totally different.  <string> includes the C++ string class, while <cstring> includes C character array routines like strcat and strcmp.  For includes that are not part of either standard library, the names are the same as always and usually have a .h for example <GL/gl.h> for OpenGL routines.

The intel compiler is better for serious number crunching applications, but you probably shouldn't use it as a beginner for a few reasons.  First, gcc is much more commonly supported and easier to find references for.  Second, gcc is available everywhere so others will be able to compile and run your programs.  Also, you will not notice any speed improvements as a beginner anyway.

If you are writing an OpenMP weather simulation for a single machine, the Intel compiler would be a good choice though :).

---

### Post by jespdj on 2009-10-21
If you're just learning C++, then just use the default compiler that comes with Linux (which is g++). There's no reason to use something else, like Intel C++.

Intel C++ might be interesting if you're working on a project for high-performance software. For almost everything, GNU g++ is more than good enough. As far as I know, (almost?) all software for Ubuntu is compiled with g++.

Note that Intel C++ is not free, you'd have to buy it from Intel for several hundred $. (Although I think you can use it for free for non-commercial purposes or for evaluation; check Intel's website for details).

In other words, you most likely don't have to worry about Intel C++ at this point.

---

### Post by patrickaupperle on 2009-10-21
Ok, so:
#include <library>
use g++
Is the book I am following good enough to learn out of?
What types of things are now incorrect, due to C++ changing over time, in that book (2004 Publish date, I think)?

---

### Post by noerrorsfound on 2009-10-21
I think you should just get a newer book. Nobody can tell you everything to look out for and you'll end up learning some bad C++.

---

### Post by MadCow108 on 2009-10-21
you should check for which C++ standard it was written.
if it is for c++98 its probably ok.
Make sure it has a chapter on the STL, Standard Template Library or Standard Library.
Without using this you'll basically be learning C with a syntactic sugar in form of object orientation support.
C++ is a lot more than that.

---

### Post by patrickaupperle on 2009-10-21
In the front of the book, under the header ***What Is Not Covered?*** is a sub header that says **Templates and STL (Standard Template Library)** Under that it explains why the author did not include them. It reads > This is another good topic for an advanced book. A temlate is a way of creating a gereralized data structure in which an absrtract mechanism can be combined with any number of specific data types. The template-defining capablity was not originally in the c++ specification, although it is now standard.

Does this mean that the book is OK, but it just does not get advanced enough to start teaching templates, or does it mean I should get a different book? I'll attach a few code sample from fairly late in the book, so you all might be able to determine if the syntax is up to date enough. I had to change the extension to .txt, but other than that they are straight off the cd.

---

### Post by hessiess on 2009-10-21
> **patrickaupperle said:**
> In the front of the book, under the header ***What Is Not Covered?*** is a sub header that says **Templates and STL (Standard Template Library)** Under that it explains why the author did not include them. It reads 

Does this mean that the book is OK, but it just does not get advanced enough to start teaching templates, or does it mean I should get a different book? I'll attach a few code sample from fairly late in the book, so you all might be able to determine if the syntax is up to date enough. I had to change the extension to .txt, but other than that they are straight off the cd.

The STL makes common tasks a *LOT* easier, for example std::vector, which is a dynamic array class. Without this you have to manually relocate memory at runtime which can get complicated and lead to buffer overruns.

---

### Post by patrickaupperle on 2009-10-21
> **hessiess said:**
> The STL makes common tasks a *LOT* easier, for example std::vector, which is a dynamic array class. Without this you have to manually relocate memory at runtime which can get complicated and lead to buffer overruns.

I guess my questions are:
Is it really important to know the STL at such an early level? 
Should I worry about all that at this level? 
Do most books teach the use of STL fairly early on? 
Is it ok to not know that until a later time? 
Is this book OK to learn the basics out of?
If not, what book is?

---

### Post by MadCow108 on 2009-10-21
If the book is a good introduction to the basics, use it as an introduction. The basics are essential for learning the more advanced subjects.
But don't stop learning after you finished the book, get a more advanced book.

---

### Post by patrickaupperle on 2009-10-21
> **MadCow108 said:**
> If the book is a good introduction to the basics, use it as an introduction. The basics are essential for learning the more advanced subjects.
But don't stop learning after you finished the book, get a more advanced book.

:) That was the respose I was hoping for. Thank you. 

Anybody disagree with this statement?

---

### Post by dwhitney67 on 2009-10-21
> **patrickaupperle said:**
> :) That was the respose I was hoping for. Thank you. 

Anybody disagree with this statement?

You should forget about C++ or any related books.  Just read the Bible, and don't forget your daily prayer session.



Just kidding... In the time it took for this thread to go through it's motions, you could have been half-way through any typical C++ programming book.

---

### Post by patrickaupperle on 2009-10-21
> **dwhitney67 said:**
> You should forget about C++ or any related books.  Just read the Bible, and don't forget your daily prayer session.



Just kidding... In the time it took for this thread to go through it's motions, you could have been half-way through any typical C++ programming book.

I could have been, but I wanted to learn correct and proper C++. I was making sure there were not any drastic changes since that book that would have thrown me off. :) Anyway, thank you all. When I finish this book, I will probably be back here asking you all what a good next step is.

---

