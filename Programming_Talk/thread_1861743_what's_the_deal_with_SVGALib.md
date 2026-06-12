---
title: "what's the deal with SVGALib?"
date: 2011-10-16
forum: Programming Talk
---

### Post by littleknowledge on 2011-10-16
Good day, I have been a C programmer for a while but mostly for backend  stuff like cgi, but i have been wanting to get into GUI programming. I  found a library called SVGALib which seems to be a library that is still  being used. I notice a lot of low level software uses it, I like the  fact that it does not rely on any other technology like X. But it seems  like the SVGALib community is dormant. 

I bought a book on amazon but turned out to be VERY outdated, i tried  installing the pre-compiled svgalib binaries using apt-get which  installs but it doesnt seem to work (basic programs wont compile). My  question is does anyone know what happened to this project and is there a  modern substitute preferably one that is low level as svgalib but that  has an active community...

---

### Post by Bachstelze on 2011-10-16
Do yourself a favor and use a GUI toolkit like GTK or Qt. No one who doesn't have X is going to run your program.

---

### Post by littleknowledge on 2011-10-16
> **Bachstelze said:**
> Do yourself a favor and use a GUI toolkit like GTK or Qt. No one who doesn't have X is going to run your program.

I don't deny you are right. Does anyone know what happened to the community though? Ubuntu still provides the pre-compiled packages for it.... which means there is support for it SOMEWHERE.... I didn't want to learn this library to make a career out of it, rather to provide an interface for my networking tools straight from boot bypassing the overhead of such a sophisticated system that is X. ncurses isnt cutting it any more.

---

### Post by kerryhall on 2012-03-21
AFAIK it still works, I've been playing around with it a bit (and it's awesome!) There are some cool examples here:

[ftp://sunsite.unc.edu/pub/linux/apps/graphics/hacks/svgalib/!INDEX.html](ftp://sunsite.unc.edu/pub/linux/apps/graphics/hacks/svgalib/!INDEX.html)

BTW if you manage to get a super thin window manager going, let me know, I would love to use it haha. I actually wrote something like this awhile ago on a Pentium 1 but alas it was lost while moving to a new house.

If you write it in C maybe I'll try porting it to x86 assembly for the hell of it heh.

What would be cool too is having hardware accelerated OpenGL drawing without X, I think this might actually be in the works.

---

### Post by ysangkok on 2013-02-26
it is indeed in the works, see [https://github.com/dvdhrm/kmscon](https://github.com/dvdhrm/kmscon)

---

