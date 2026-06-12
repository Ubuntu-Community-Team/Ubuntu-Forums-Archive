---
title: "why like this?"
date: 2010-12-11
forum: Programming Talk
---

### Post by munna.cheyur on 2010-12-11
conio.h , string.h header files are not at all working in gcc compiler. First i was used gedit+terminal to run c progs. Now i'm using geany editor in this also these file all not working. Pls solve my prob.

---

### Post by bodhi.zazen on 2010-12-11
*Thread moved to **Programming Talk**.*

---

### Post by unknownPoster on 2010-12-12
conio.h is a MS-DOS header file, as such it won't run on Linux. A Linux library with similar functionality is Ncurses.

---

### Post by nvteighen on 2010-12-12
string.h should be there, though. Have you installed the build-essentials package from the repos? That package will install the basic development environment for C and C++.

---

### Post by trent.josephsen on 2010-12-12
Your problem is that you're using a bad tutorial.  I can't fix that for you.

---

### Post by CptPicard on 2010-12-12
> **trent.josephsen said:**
> Your problem is that you're using a bad tutorial.  I can't fix that for you.

For some reason it appears that Turbo C is still alive and well in education in India; we get these "my *editor *won't compile conio.h" questions over and over again :)

---

### Post by StephenF on 2010-12-12
Freedos is free and so is Borland Turbo C++ which appears to be the target platform of your tutorial.

---

### Post by trent.josephsen on 2010-12-12
> **CptPicard said:**
> For some reason it appears that Turbo C is still alive and well in education in India; we get these "my *editor *won't compile conio.h" questions over and over again :)
No question about that.  It's still alive in education here in the US, in some of the places where they haven't all switched to Java.  But conio.h is still archaic and nonstandard, and it has no place in programs that have been written since... oh, 2000 maybe, to be exceptionally generous.  Sheesh, you'd think people would catch on quicker.

---

### Post by Vox754 on 2010-12-12
> **trent.josephsen said:**
> No question about that.  It's still alive in education here in the US, in some of the places where they haven't all switched to Java.  But conio.h is still archaic and nonstandard, and it has no place in programs that have been written since... oh, 2000 maybe, to be exceptionally generous.  Sheesh, you'd think people would catch on quicker.

I believe this is because many people have "unauthorized copies" of old software. So, as long as it works, they (schools?) don't bother to upgrade.

I also know people who use Microsoft Visual C++ 6.0, which was released in 1997 or something. Of course, they don't use it beyond simple exercises, but conio.h and friends are still present.

It's surprising, as nowadays a simple mingw environment with a tiny IDE would cover most needs of these students.

---

### Post by worksofcraft on 2010-12-12
Lol - I wanted to try get a programming qualification recently. The course I enrolled in were teaching with a Dos version of Turbo Pascal :shock:

I didn't complete the course. Perhaps I would have seen it thru had they been using Borland C++ :D

I'm wondering how hard it would be to implement all the functions of conio.h I think all it needs is some "glue" logic to ncurses and that would truly solve the conio.h issue... :popcorn:

---

### Post by Vox754 on 2010-12-12
> **worksofcraft said:**
> ...
I'm wondering how hard it would be to implement all the functions of conio.h I think all it needs is some "glue" logic to ncurses and that would truly solve the conio.h issue... :popcorn:

I think it has been attempted already, several times.

I won't bother searching for more options, just this example: [http://sourceforge.net/projects/linux-conioh/](http://sourceforge.net/projects/linux-conioh/)

As far as I can tell, most people do not need conio.h or ncurses at all. It's just that the old Windows IDEs include it automatically whenever you start a new "project".

A template like this is common
```

#include <stdio.h>
#include <conio.h>

main()
{
// code in here
    return 0 ;
}

```

Obviously, when they move their project to Linux, it doesn't work.

In most cases, the solution is as simple as removing conio.h, and getch().

I would expect that people who make use of all of conio's capabilities would also know about ncurses, and prefer this one instead. It's the completely clueless people that ones that usually have this problem.

---

### Post by trent.josephsen on 2010-12-12
> **worksofcraft said:**
> Lol - I wanted to try get a programming qualification recently. The course I enrolled in were teaching with a Dos version of Turbo Pascal :shock:

I didn't complete the course. Perhaps I would have seen it thru had they been using Borland C++ :D

I'm wondering how hard it would be to implement all the functions of conio.h I think all it needs is some "glue" logic to ncurses and that would truly solve the conio.h issue... :popcorn:
A solution that encourages bad practice is no solution at all...

---

### Post by worksofcraft on 2010-12-12
> **trent.josephsen said:**
> A solution that encourages bad practice is no solution at all...

IMO it depends what the solution is for.

If you just want to compile and run some old legacy code without having to redesign it then a conio.h substitute makes perfect sense TBH

---

### Post by trent.josephsen on 2010-12-12
> **worksofcraft said:**
> IMO it depends what the solution is for.

If you just want to compile and run some old legacy code without having to redesign it then a conio.h substitute makes perfect sense TBH
A fair point.

But of the 1,001 times I've encountered a reference to conio.h, not a single one of them has been in legacy C code, and every last one has been in an outdated tutorial or a forum post like this one.

---

### Post by worksofcraft on 2010-12-12
> **trent.josephsen said:**
> A fair point.

But of the 1,001 times I've encountered a reference to conio.h, not a single one of them has been in legacy C code, and every last one has been in an outdated tutorial or a forum post like this one.

Oh well... both times I have encountered conio.h in the last 15 years, 100% have been in ancient command line programs that said "press any key to continue" and then had a loop like..
[php]
     while (!kbhit());
[/php]

I'll fully grant you that it is **abominable** practice to dissipate processing time like that on an idle loop and also I think it's real *sucky* to put a semicolon on while statements, but none of that is down to a problem in conio AFIK :shock:

---

