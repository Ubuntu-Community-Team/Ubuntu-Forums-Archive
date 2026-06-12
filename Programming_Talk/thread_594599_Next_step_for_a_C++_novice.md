---
title: "Next step for a C++ novice"
date: 2007-10-28
forum: Programming Talk
---

### Post by loza on 2007-10-28
Hi All

I wanted to start learning C++ so I've just completed  [C++ A Beginner's Guide by Herbert Schildt]("http://www.mhprofessional.com/product.php?cat=112&isbn=0072232153"). It was really go for a start. I have some pascal, delphi, C experience from years ago and a little Kylix from when it was first released.

I want to get into writing apps for the Linux desktop. Can anyone suggest a next step please?

Also I'm curious about embedded linux can anyone reccommend a good starting point on programming embedded please?

Thanks in advance

loza

---

### Post by LaRoza on 2007-10-28
For Linux programming, I suggest learning Python and Perl.

My wiki has C++ related links, that you may find interesting.

---

### Post by Compyx on 2007-10-28
> **loza said:**
> Hi All

I wanted to start learning C++ so I've just completed  [C++ A Beginner's Guide by Herbert Schildt]("http://www.mhprofessional.com/product.php?cat=112&isbn=0072232153"). 

Then you're off to a bad start, books by Herbert Schildt should be avoided like the plague. Look through some of the reviews of his books on [http://www.accu.org]("http://www.accu.org/") to see why, or check this out for a laugh: [http://www.lysator.liu.se/c/schildt.html]("http://www.lysator.liu.se/c/schildt.html")

If you're serious about learning C++, get your hands on "The C++ Programming Language, Third Edition" by Bjarne Stroustrup.

---

### Post by LaRoza on 2007-10-28
> **Compyx said:**
> 
If you're serious about learning C++, get your hands on "The C++ Programming Language, Third Edition" by Bjarne Stroustrup.

And [http://www.computer-books.us/cpp_0010.php](http://www.computer-books.us/cpp_0010.php) for GUI. I know, it is QT, but it is a free book.

---

### Post by dwhitney67 on 2007-10-28
The Stroustrup book is probably the worst candidate for a beginner to look at.  I cannot recall which edition I owned (I threw it away), but the book did not contain any complete coding examples... everything was just code snippets.

I forgot who said this (maybe Einstein?), but Stroustrup ought to take notice:  *If you can't explain something well enough for a six-year old to understand, then you don't understand it well enough yourself.*

Here is a list of books that I have found helpful (in order of simplicity):

Object-Oriented Programming in C++ (LaFore)
Design Patterns (Gamma-Helm-Johnson-Vlissides)
Object-Oriented Programming with C++ and OSF/Motif (Young)

If you are constantly forgetting the C++ STL API (like I am), here's a good reference:  [http://www.cplusplus.com/reference/stl](http://www.cplusplus.com/reference/stl)

There are other resources too; for instance the Boost Libraries:  [http://www.boost.org/](http://www.boost.org/).  I don't know if Ubuntu ships boost with their development package, but Fedora does.

---

### Post by loza on 2007-10-29
> **Compyx said:**
> Then you're off to a bad start, books by Herbert Schildt should be avoided like the plague. Look through some of the reviews of his books on [http://www.accu.org]("http://www.accu.org/") to see why, or check this out for a laugh: [http://www.lysator.liu.se/c/schildt.html]("http://www.lysator.liu.se/c/schildt.html")


That's a real shame because I found it really easy using that book. :D

[QUOTE=LaRoza]For Linux programming, I suggest learning Python and Perl.[/QUOTE]

I'm already doing some Python and seem to be picking that up quite easily. Funnily enough the other week we had a Sales Rep in telling us the next version of Tivoli was being written in Gyphon!

From what I have read about, "The C++ Programming Language, Third Edition" by Bjarne Stroustrup, I gather it is not really aimed at the beginner - however I shall give it a shot.

 
dwhitney67 - Thatnks for these I shall look these up!

Many thanks everyone for some direction - I know you probably get a lot of 'where to next' questions, but it seems like there are so many sources of information out there that it can be counter productive to a novice and getting opinions of more seasoned developers is worth weeks of fruitless searching! 

Thanks again

loza

---

### Post by pmasiar on 2007-10-29
"Thinking in C++" is good advanced book, explaining why's and consequances of design decisions.

Before you start on big projects, I would recommend (in this order): 

1) "Project euler" - math tasks with correct answers, to learn solving not-too-complicated tasks (and well defined - it's simple math).
2) learn about data structures. Wiki in my sig has links, also wikiversity.
3) Join some existing open source project using C++

LaRoza is right, learning python is useful also for hardcore C++ hackers. many times you have only a simple task, where CPU time  efficiency is not important, and in Python you often can solve it 10 times faster. Tasks like build scripts, testing data generation and parsing, little bits here and there. See also [How learning Python made me a better C++ programmer](http://www.ginstrom.com/scribbles/2007/10/05/learning-python-made-me-a-better-cpp-programmer/)

For Python links, see wiki in my sig

---

### Post by loza on 2007-10-29
Thanks for the pointers pmasiar. I think perhaps I'll be better off learning Python first!

Kind regards

loza

---

### Post by meatpan on 2007-10-29
> **loza said:**
> 
I want to get into writing apps for the Linux desktop. Can anyone suggest a next step please?

Also I'm curious about embedded linux can anyone reccommend a good starting point on programming embedded please?


Consider 'Beginning Linux Programming', by Stones and Matthew.  The book covers fundamental technologies related to unix/linux, such as processes, filesystems, virtual memory, SysV tools (shared mem, message queues, semaphores),  sockets, and concurrent programming (threads, etc...).

C++ is a good choice, and I recommend getting a recent compiler, like icc 9+, or gcc 4+.  I strongly disagree with the above post that claims 'The c++ programming language' by Stroustrop, is a bad choice.  The book is terse, but accurate and comprehensive.  I have yet to meet a good c++ dev that doesn't have at least 1 copy of this book.

---

### Post by loza on 2007-10-30
> **meatpan said:**
> Consider 'Beginning Linux Programming', by Stones and Matthew.  The book covers fundamental technologies related to unix/linux, such as processes, filesystems, virtual memory, SysV tools (shared mem, message queues, semaphores),  sockets, and concurrent programming (threads, etc...).

I have had a look at this book today and it looks really good and 'pitched' at my level so I think I may invest in this book to give me a 'shove' in the right direction as well as looking up all the free stuff on the internet. Thanks for the suggestion.

> C++ is a good choice, and I recommend getting a recent compiler, like icc 9+, or gcc 4+.

I have never heard of icc 9+, I shall look it up but I have gcc.

Thanks again

loza

---

### Post by loza on 2007-11-16
I got the 'Beginning Linux Programming', by Stones and Matthew and think its a very good recommendation! 

I now know what icc is and prefer gcc instead! (I read that version 10 is slower than the version 9...) :)

kind regards

loza

---

### Post by samjh on 2007-11-17
> **loza said:**
> From what I have read about, "The C++ Programming Language, Third Edition" by Bjarne Stroustrup, I gather it is not really aimed at the beginner - however I shall give it a shot.Don't do it.  Stroustrup's book is for experienced C++ programmers.  It will be a waste of money and most of the content will go over your head.

When someone asks me about C++ books, I always recommend these two books, in this order:
[list=1][*][Accelerated C++]("http://www.amazon.com/Accelerated-C-Practical-Programming-Example/dp/020170353X/ref=pd_sim_b_img_3/104-7548612-8867112") by Koenig and Moo.
This is a great book for C++ beginners.  You can actually write non-trivial applications effectively after finishing this book, and it is very short for the amount of content it covers.  In fact, most C++ hobbyists will not need to learn much more about C++ than what is presented in this book.

[*][C++ Primer]("http://www.amazon.com/C%2B%2B-Primer-4th-Stanley-Lippman/dp/0201721481/ref=pd_bbs_sr_1/104-7548612-8867112?ie=UTF8&s=books&qid=1195293364&sr=1-1") by Lippman, Lajoie, and Moo.
This is a great book for fortifying your basic C++ knowledge and learning the more advanced language features and applications.  If you have a sharp mind, you can even use this as your introductory book.  It covers 99% of C++ you'll ever need to use.[/list]
After you have gone through both books, should you then try Stroustrup's book.


> Also I'm curious about embedded linux can anyone reccommend a good starting point on programming embedded please?You'll need to learn C first.  With your knowledge of C++, learning C should only take a few days.

This is the definitive book on standard C:
[C Programming Language]("http://www.amazon.com/C-Programming-Language-2nd-Ed/dp/0131103709/ref=pd_bbs_sr_3/103-3436644-7271848?ie=UTF8&s=books&qid=1195294135&sr=1-3") by Kernighan and Ritchie (the inventors of C).

---

### Post by Paul820 on 2007-11-17
> When someone asks me about C++ books, I always recommend these two books, in this order:

   1. Accelerated C++ by Koenig and Moo.
      This is a great book for C++ beginners. You can actually write non-trivial applications effectively after finishing this book, and it is very short for the amount of content it covers. In fact, most C++ hobbyists will not need to learn much more about C++ than what is presented in this book.
   2. C++ Primer by Lippman, Lajoie, and Moo.
      This is a great book for fortifying your basic C++ knowledge and learning the more advanced language features and applications. If you have a sharp mind, you can even use this as your introductory book. It covers 99% of C++ you'll ever need to use.

+1 I have both of these, they are really excellent books.

---

### Post by Smygis on 2007-11-17
Also learn the boost library.

[http://www.boost.org/](http://www.boost.org/)

Great stuff.

---

### Post by pmasiar on 2007-11-17
> **samjh said:**
> 
When someone asks me about C++ books, I always recommend these two books, in this order:.

You should add this to sticky post about C++ (or ask the author of C++ post to add it, or create new post about C++ and ask Wybiral to link it too). Lots of people ask for C++ books, and "experts" recommend advanced books all the time (instead of intro books).

Not that i expect someone to actually **read** that sticky ... :-/

---

### Post by samjh on 2007-11-17
Thanks for the suggestion, I've added it to the thread.

---

