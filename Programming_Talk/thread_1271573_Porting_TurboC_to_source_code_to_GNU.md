---
title: "Porting TurboC to source code to GNU ?????"
date: 2009-09-21
forum: Programming Talk
---

### Post by NawafLol on 2009-09-21
sorry its : Porting Turbo C source code to GNU ?????


I have found an interesting  site [http://www.sandroid.org/TurboC/](http://www.sandroid.org/TurboC/)

but could not get around it every thing was about SuSE and FreeBSD

can anyone help me cause  i want to use turbo c header files in ubuntu  9.04

i like the GNU but i want the turbo c header files two !

---

### Post by dribeas on 2009-09-21
What are you missing from turbo C when you work in a modern linux environment? My advice is trying to find alternatives, as TurboC is basically dead, and all time invested in using the specifics will be worthless for real development.

---

### Post by dE_logics on 2009-09-21
What exactly are the headers which are causing the problem?

---

### Post by NawafLol on 2009-09-21
will conio.h and graphics.h 

and GNU is a bit hard to use i always get more errors than Turbo C

and most of the books i bought they talk about programming in the Turbo C Environment !

if anyone have a GNU compiler lesson or headstart that will be good two ..

---

### Post by NawafLol on 2009-09-21
so anyone !

---

### Post by lisati on 2009-09-21
Welcome to the world of GNU/Linux and portability. 

What I would suggest is that in the long run, looking for alternatives to the the routines that "require" the Turbo C headers would be a good move, as many of them are likely to be MS-DOS specific.

---

### Post by fct on 2009-09-22
> **NawafLol said:**
> will conio.h and graphics.h 

and GNU is a bit hard to use i always get more errors than Turbo C

and most of the books i bought they talk about programming in the Turbo C Environment !

if anyone have a GNU compiler lesson or headstart that will be good two ..

Those books sound quite outdated, since Turbo-C is a really outdated tool. I suggest that you install dosbox ( [http://dosbox.sf.net](http://dosbox.sf.net) ) so you can run Turbo-C there.

But just to learn by those books. You should move on to others that aren't tied to Borland's techonologies.

"The C Programming Language" by Kernighan & Ritchie was written by the authors of C and is UNIX-centric, so it should be easier to use what you learn in a linux environment.

---

### Post by NawafLol on 2009-09-26
thanks i'm already using dosbox is working but i want the conio.h header file in the gnu compiler !

i will look for this "The C Programming language" book !

---

### Post by tom66 on 2009-09-26
I believe tere exists a conio.h in GCC, but it's not common. It doesn't offer any of the advanced features that the DOS version did: no colors, for example. Only basic I/O was supported (getch, putch).

Take a look at ncurses for the kind of features you may be looking for.

Borland Turbo C... how old is that? It probably doesn't throw so many errors because it's too old to have all of the new features compilers have which can spot simple programming errors which cause crashes.

---

### Post by phrostbyte on 2009-09-26
Basically you run the code against the compiler and fix all the compiler errors one by one. It's much fun. :P

---

### Post by lisati on 2009-09-26
> **phrostbyte said:**
> Basically you run the code against the compiler and fix all the compiler errors one by one. It's much fun. :P

And potentially more time consuming if you work backwards from the last error or warning presented.....

---

### Post by NawafLol on 2009-09-27
Thanks every one, i must say programming at linux was alittle bit tricky for me !

but i like it ! and yet couldn't find the conio.h header file !

---

