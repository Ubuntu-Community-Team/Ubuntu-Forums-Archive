---
title: "Formatted IO"
date: 2008-10-17
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-10-17
How was printf (sscanf) implemented in C, because it uses dynamic arguments which isn't allow in C.

I read that it was done in Pike, but I doubt that Pike came before C. Maybe before Pike there wasn't formated io

---

### Post by WW on 2008-10-17
> **Mr.Macdonald said:**
> How was printf (sscanf) implemented in C, because it uses dynamic arguments which isn't allow in C.

Variable arguments *are* possible in C.  See, for example, [here](http://c-faq.com/varargs/varargs1.html) or [here](http://publications.gbdirect.co.uk/c_book/chapter9/stdarg.html).

---

### Post by Mr.Macdonald on 2008-10-17
I see, to bad that things like this aren't in most tutorials.

If you have a tutorial or guide that shows the quirks of C then I would like to see it

---

### Post by LaRoza on 2008-10-17
> **Mr.Macdonald said:**
> 
If you have a tutorial or guide that shows the quirks of C then I would like to see it

C shouldn't have quirks. Learn the standard C first.

---

### Post by Mr.Macdonald on 2008-10-17
A function that takes a variable number of arguments is a quirk while being standard C.

---

### Post by dwhitney67 on 2008-10-18
It is not a quirk.  If you ever wrote assembly language, you would understand clearly what is going on when passing a variable length of parameters to a function.  The additional parameters are stored on the stack.

When I used to program (in assembly) on the MC680x0 processors, only two parameters (sitting in registers D0 and D1) were readily available.  The other parameters (if any) were sitting there on the stack.

In C, you have something like:
[php]
void myFunc(const char* format, ...)
{
  va_list args;              // place holder for addt args
  va_start(args, format);    // collect the args on the stack after 'format'

  // ...
}
[/php]

As for C tutorials, these generally are directed towards beginners, not advanced users.  When I was in college, and into start of my professional career, I relied on this [book]("http://www.amazon.com/Programming-C-Stephen-G-Kochan/dp/B001EED1VG/ref=sr_1_9?ie=UTF8&s=books&qid=1224305168&sr=1-9"), albeit an earlier version, written by Stephen Kochan.

---

### Post by nvteighen on 2008-10-18
> **Mr.Macdonald said:**
> A function that takes a variable number of arguments is a quirk while being standard C.
Actually, Standard C has absolutely no quirks; maybe some third-party library could have one (I'm looking at you, ncurses), but not the Standard Library.

Std. C is one of the most coherent and clean programming language you may ever see. Everything is absolutely deduceable and the logic behind it is fairly easy; of course, you have to play around with it and also understand what was C designed for in order to learning and grasp the underlying design logic.

---

