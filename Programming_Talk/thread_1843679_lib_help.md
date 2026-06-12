---
title: "lib help"
date: 2011-09-13
forum: Programming Talk
---

### Post by Jakemurray on 2011-09-13
im going through the book "Hacking:The art of exploitation 2nd edition" (no i havent any intention of being a hacker nor cracker) but im having a small problem. in the beginning it gives a few C examples but the libs arent included with the dvd.......

is there any way to download the specific libraries or if there is anyone else who has used the book, am i just not finding them?

---

### Post by Bachstelze on 2011-09-13
How about you tell us what those libraries are? ;)

---

### Post by Jakemurray on 2011-09-13
well throughout the book it uses many many different ones, but the most common are 
stdio.h 
stdlib.h
string.h
fcntl.h
sys/stat.h
hacking.h
is there a terminal command to search for a file?

---

### Post by Bachstelze on 2011-09-13
Those are standard headers. It seems you are not very familiar with C yet so I'd suggest you get familiar with it first before trying to follow that book. The stickies at the top of this forum probably have some resource to get you started.

---

### Post by Jakemurray on 2011-09-13
well im going through the book for some networking tutorials but they use it alot so ill probably do that thanks, but in any case those should be on the cd somewhere right?

---

### Post by Senesence on 2011-09-13
> **Jakemurray said:**
> well im going through the book for some networking tutorials but they use it alot so ill probably do that thanks, but in any case those should be on the cd somewhere right?

The standard libraries would probably not be included, because they are standard, and should therefore already be present in your build environment.

On Linux, these files are usually found is /usr/lib, the include files (.h) in /usr/include. To find any one file, you can use the locate command.

Except for hacking.h, those all seem like standard C headers, which you should already have on your system, along with the relevant libraries.

---

### Post by Jakemurray on 2011-09-13
> **Senesence said:**
> The standard libraries would probably not be included, because they are standard, and should therefore already be present in your build environment.

On Linux, these files are usually found is /usr/lib, the include files (.h) in /usr/include. To find any one file, you can use the locate command.

Except for hacking.h, those all seem like standard C headers, which you should already have on your system, along with the relevant libraries.


thank you i really appreciate it

---

