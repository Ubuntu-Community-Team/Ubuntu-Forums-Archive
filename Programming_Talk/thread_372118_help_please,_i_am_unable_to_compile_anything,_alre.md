---
title: "help please, i am unable to compile anything, already got build-essential"
date: 2007-02-27
forum: Programming Talk
---

### Post by humbll on 2007-02-27
I have installed the build essential:
sudo apt-get install build-essential

i am using scite to program in, and when i try to compile i get the error 
studio.h no such file or directory

same error trying to compile from the terminal using either:
cc whatever.c
 or 
gcc whatever.c

a search of my filesystem confirms the library does not exist. I even redid the command on line 2 of this post to reinstall, still not there. Why am I having so much trouble with a function that any unix should have native support for (C programming)? Can someone please point out the hoops I need to jump through to get this functional? Thanks.

---

### Post by Tomosaur on 2007-02-27
I just answered this in the beginner section. It's not studio.h, it's stdio.h.

---

### Post by Wybiral on 2007-02-27
Yeah, I believe it means "standard in/out" thus the "std" "io"

No "u".

---

### Post by humbll on 2007-02-27
Ah, well i suppose that is the problem then. haven't slept in 38 hrs, i will fix it when i awake. thanks..

---

