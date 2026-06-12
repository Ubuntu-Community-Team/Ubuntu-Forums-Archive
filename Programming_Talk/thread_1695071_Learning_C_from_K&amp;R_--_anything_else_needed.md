---
title: "Learning C from K&amp;R -- anything else needed?"
date: 2011-02-25
forum: Programming Talk
---

### Post by samalex on 2011-02-25
Hey Guys --

I used to have a copy of [K&R]("http://en.wikipedia.org/wiki/The_C_Programming_Language") but I lost it years ago (maybe lent it out and just never got it back -- not sure).  Then yesterday a co-worker was taking some books to Goodwill and asked if I was interested in checking them out.  What luck, out of the 15 or so books one was the K&R!  

I've been wanting to pickup C and/or C++ programming because I'd like to get into not only app development but working with the kernel as well.  I used to be rather proficient in C++ back in the DOS days, but I believe Borland C++ 3.5 for DOS was my last version to really use.

So would working through the K&R then reviewing snippets of the Linux kernel be sufficient to help get to know C and the kernel well enough to develop on that front?  What other resources would be suggested to go through?

Thanks --

Sam

---

### Post by johnl on 2011-02-25
From what I have heard K&R is a great C reference.  The only thing I would caution is that it is pretty old, and may teach you some outdated style.  Also I am fairly sure it won't cover anything from the C99 (or perhaps even C89) standards.

For example,  K&R writes functions like so:

```

int myfunction(foo, bar, baz) 
int foo;
int bar;
char* baz;
{


}

```

instead of the 'new' style:
```

int myfunction(int foo, int bar, char* baz)
{
}

```

which is important for a number of reasons (type checking, prototype-mismatches).


So while K&R is a great resource, I would recommend reading something more recent in addition to it.

---

### Post by Queue29 on 2011-02-25
> **johnl said:**
> From what I have heard K&R is a great C reference.  The only thing I would caution is that it is pretty old, and may teach you some outdated style.  Also I am fairly sure it won't cover anything from the C99 (or perhaps even C89) standards.

For example,  K&R writes functions like so:

```

int myfunction(foo, bar, baz) 
int foo;
int bar;
char* baz;
{


}

```

instead of the 'new' style:
```

int myfunction(int foo, int bar, char* baz)
{
}

```

which is important for a number of reasons (type checking, prototype-mismatches).


So while K&R is a great resource, I would recommend reading something more recent in addition to it.

The most recent version of the book ( published in 1988 ) covers ANSI complient C (C89), so everything is pretty much as up to date as it needs to be for writing useful C.

---

### Post by johnl on 2011-02-25
> **Queue29 said:**
> The most recent version of the book ( published in 1988 ) covers ANSI complient C (C89), so everything is pretty much as up to date as it needs to be for writing useful C.

Good to know, the OP might check which edition of the book he has and go from there :)

---

### Post by doas777 on 2011-02-25
the rkr is a great reference, but it is not a great source for initial learning. I would start with a book more geared to teaching than to documenting.

---

### Post by Vox754 on 2011-02-25
> **johnl said:**
> From what I have heard K&R is a great C reference.  The only thing I would caution is that it is pretty old, and may teach you some outdated style.  Also I am fairly sure it won't cover anything from the C99 (or perhaps even C89) standards.

For example,  K&R writes functions like so:

...
instead of the 'new' style:
...


You are wrong.

There are two editions of the K&R book. The first one (1978) is the one that has the "old" style. The second edition (1988) has the "new" style you mention, and it was basically written at the same time of the C89 standard.

Today, whenever someone mentions the "K&R book", they are assuming the second edition, because the first one is in fact completely and absolutely out of date. Many people keep a copy of the second edition for personal reasons, but only historians would keep a copy of the first one.

> 
So while K&R is a great resource, I would recommend reading something more recent in addition to it.

Now, this we can agree on.

K&R is too light, too simple for modern standards.

In order to learn C, you should read any other book, published in the 2000s, or even learn by websites. And then when you have the time, you may go back an read K&R just to get a feel of what was the language back in the 1980s. Also, you would be reading from the developers themselves, which adds a special nostalgic feeling.

Now, with this said, C is actually a pretty compact language. The core functionality of the language hasn't changed from 1988, so that's why the K&R book is still relevant today.

My suggestion of reading a newer book, or websites, is because newer materials build on years of teaching the language, and so they usually include more interesting algorithms and challenging exercises that greatly improve the learning experience.

Now, modern C++ is a completely different beast. It should not be regarded as a superset of C anymore. It should be considered a separate language, because it has its own standard libraries and standard "way of doing things". Learning from a dedicated C++ book is recommended.

Also, to start programming for the kernel. That is different matter. I assume you would need to know good C, then download the source, read on pages and pages of documentation, get acquainted with the most important macros and functions used, and just start hacking whatever you want, in C, not C++.

I believe the kernel still does not include any C++ code in it, only C, and some processor-specific code in assembly.

---

### Post by samalex on 2011-02-25
Hey guys ... 

Yes, sorry I do have the second edition. My main goal is two fold: to get into kernel programming and to also write stand alone applications.  I know C is pretty much all that's used in the kernel, so hopefully the K&R will get me somewhat prepared to start reading through the kernel source.  Also using ncurses hopefully I can also do some GUI coding with C as well though I'd like to learn C++ for more of those projects.  

I remember years ago someone saying C++ was just an OOP spin of C, but I can see how this is no longer the case with the evolution of C++ over the years. 

But for now I'll probably start focusing on C and see how far that takes me.

Thanks for all the great info --

Sam

---

### Post by trent.josephsen on 2011-02-25
> **Vox754 said:**
> K&R is too light, too simple for modern standards.
Fair enough, although I wouldn't put it that way.  It's simply that the standards have outgrown the book.  Ballpark, 98% of the book still applies and is relevant to modern C programming, and the remaining 2% is not central.

> In order to learn C, you should read any other book, published in the 2000s, or even learn by websites. And then when you have the time, you may go back an read K&R just to get a feel of what was the language back in the 1980s.
I disagree.  K&R is still a great way to learn C.  Not a great way to learn programming, but a good way for programmers to pick up C.  It has all the qualities of a good introductory text, as indeed it was written.  What it does not have is "this is what a variable is, this is what a string is, this is how the + operator works, this is what it means to take an address,"  fundamental things that programmers should already have some handle on.

> My suggestion of reading a newer book, or websites, is because newer materials build on years of teaching the language, and so they usually include more interesting algorithms and challenging exercises that greatly improve the learning experience.
True, maybe.  Most of the Web tutorials out there are written by comparative novices.  Some of the books, even the popular ones (*coughSchildtcough*), are just as bad or worse.  If you have good ones to recommend, please do.

> <snip>
I believe the kernel still does not include any C++ code in it, only C, and some processor-specific code in assembly.
Yep.

---

### Post by samalex on 2011-02-25
I've heard that K&R is definitely a book to help programmers (not beginner) learn C, and given I've been coding for over 20 years in some form or fashion it should work in my case.  It's just over the last 10 years or so my focus has moved more from app development to web development and now my forte is working with databases and data warehousing.  For this I've gotten out of the coding scene but really want to break back into it.  

Personally though I've been a Linux user for about 15 years now and having touched most parts of my system except the kernel I figured learning C would be a fun way to get back into coding and maybe learn something that'll let me give back to the community.  I don't see myself becoming a master C developer anytime soon, but if I can at least learn enough to start parsing through some of the code behind the Linux kernel maybe I can at least learn more about how my own system works under the hood.

---

### Post by Vox754 on 2011-02-26
> **trent.josephsen said:**
> Fair enough, although I wouldn't put it that way.  It's simply that the standards have outgrown the book.  Ballpark, 98% of the book still applies and is relevant to modern C programming, and the remaining 2% is not central.


Well, I did mention that the 1988 book is still relevant today.

> 
I disagree.  K&R is still a great way to learn C.  Not a great way to learn programming, but a good way for programmers to pick up C.  It has all the qualities of a good introductory text, as indeed it was written.  What it does not have is "this is what a variable is, this is what a string is, this is how the + operator works, this is what it means to take an address,"  fundamental things that programmers should already have some handle on.


You are right. I was immediately thinking in absolute beginners.

Any competent programmer wouldn't have a problem reading K&R. But then again, what competent programmer doesn't already know a bit of C? A bootstrap paradox!

> 
True, maybe.  Most of the Web tutorials out there are written by comparative novices.  Some of the books, even the popular ones (*coughSchildtcough*), are just as bad or worse.  If you have good ones to recommend, please do.


Segmentation fault.

---

### Post by Vox754 on 2011-02-26
> **samalex said:**
> I've heard that K&R is definitely a book to help programmers (not beginner) learn C, and given I've been coding for over 20 years in some form or fashion it should work in my case.  It's just over the last 10 years or so my focus has moved more from app development to web development and now my forte is working with databases and data warehousing.  For this I've gotten out of the coding scene but really want to break back into it.  


Then K&R should be fine for you. But I also recommend some other modern resource. Really, anything modern will help. Just to have a different perspective.

> 
Personally though I've been a Linux user for about 15 years now and having touched most parts of my system except the kernel I figured learning C would be a fun way to get **back into coding and maybe learn something that'll let me give back to the community.**  I don't see myself becoming a master C developer anytime soon, but if I can at least learn enough to start parsing through some of the code behind the Linux kernel maybe I can at least learn more about how my own system works under the hood.

If your objective is to help the community, I would stay away from the kernel. Really, the vast majority of users, who are not programmers, would be most interested in user applications.

With your interests I would suggest getting better at C, then learning GTK+ and using it to create graphical programs, and contribute patches to existing ones. With that knowledge you wouldn't have problem to transition to C++ and Qt, which is the other major combo of programming language and GUI toolkit.

But hey, perhaps you are one of those people who actually like to mess with the low level aspects of hardware interaction, so perhaps your contributions are actually valuable in the dark areas of kernel development.

I have the impression that kernel development is much less glamorous than regular GUI and user-space applications programming. That is, your contributions are only noted by the other kernel hackers in the mailing list, and then your code goes to this giant git repository regular users know nothing about.

---

