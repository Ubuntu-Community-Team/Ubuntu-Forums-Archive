---
title: "How to set gcc 3.4 as default"
date: 2006-10-19
forum: Programming Talk
---

### Post by pagingmrherman on 2006-10-19
I had gcc 4.0 installed but I've got an app that needs to be compiled in gcc 3.4.  I did a 

sudo apt-get install gcc-3.4

and it installed ok but when I run gcc, it's still using ver. 4.0.  I tried running 'galternatives' but it doesn't give me a choice.

Thx

---

### Post by NPALeech on 2006-10-19
I'm not sure if this holds after a restart, but this is how to switch to 3.4

In a terminal:
CC=gcc-3.4
export cc

---

### Post by Arndt on 2006-10-20
> **NPALeech said:**
> I'm not sure if this holds after a restart, but this is how to switch to 3.4

In a terminal:
CC=gcc-3.4
export cc

You need to export CC, not cc, since it was CC you set.

This holds for the current shell, so it will need to be done in every command window you open, and it will not survive a restart. It will affect the default Makefile rules, but not if you type plain

```
gcc -c prog.c

```

If you have a Makefile, there will probably be a place in the beginning where it says

```
CC=gcc
```

or something similar. There you can write

```
CC=gcc-3.4
```

instead.

---

### Post by pagingmrherman on 2006-10-20
Works for me, thanks!

---

### Post by neilp85 on 2006-10-20
Just throw that at the end of your ~/.bashrc file so you never have to worry about it again.

---

