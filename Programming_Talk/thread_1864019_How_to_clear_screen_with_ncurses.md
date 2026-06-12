---
title: "How to clear screen with ncurses?"
date: 2011-10-18
forum: Programming Talk
---

### Post by googleye on 2011-10-18
Downloaded ncurses to be able to use clrscr() in my console applications but I have never installed a 3rd party header before and I have no idea how to do it. Help?

---

### Post by karlson on 2011-10-18
> **googleye said:**
> Downloaded ncurses to be able to use clrscr() in my console applications but I have never installed a 3rd party header before and I have no idea how to do it. Help?

Why not install it from the repository?  More importantly what does ```

locate ncurses.h

```

show?

---

### Post by googleye on 2011-10-18
Couldn't find a package name so don't know how to install through terminal :p

Searching for ncurses.h and curses.h because curses.h is the header name:


***@ubuntu:~$ locate ncurses.h
/usr/include/ncurses.h
***@ubuntu:~$ locate curses.h
/home/***/.local/share/Trash/files/ncurses-5.9/include/curses.h
/home/***/.local/share/Trash/files/ncurses-5.9/include/curses.h.in
/home/***/.local/share/Trash/files/ncurses-5.9/include/curses.head
/usr/include/curses.h
/usr/include/ncurses.h

---

### Post by karlson on 2011-10-18
> **googleye said:**
> Couldn't find a package name so don't know how to install through terminal :p

Searching for ncurses.h and curses.h because curses.h is the header name:


***@ubuntu:~$ locate ncurses.h
/usr/include/ncurses.h
***@ubuntu:~$ locate curses.h
/home/***/.local/share/Trash/files/ncurses-5.9/include/curses.h
/home/***/.local/share/Trash/files/ncurses-5.9/include/curses.h.in
/home/***/.local/share/Trash/files/ncurses-5.9/include/curses.head
/usr/include/curses.h
/usr/include/ncurses.h

Looks like ncurses is already installed.

---

### Post by googleye on 2011-10-18
Well, still says clrscr() was not declared in this scope, and yes I've included the header file :D

Is clrscr() wrong? Or do I need to link the header to the install directory? I don't know how to do that :/

---

### Post by karlson on 2011-10-18
> **googleye said:**
> Well, still says clrscr() was not declared in this scope, and yes I've included the header file :D

Is clrscr() wrong? Or do I need to link the header to the install directory? I don't know how to do that :/

It's actually clear().

---

### Post by googleye on 2011-10-18
Now i got undefine reference to clear().

However code::blocks detected clear(it showed up in a list when i started typing it).

---

### Post by karlson on 2011-10-18
> **googleye said:**
> Now i got undefine reference to clear().

However code::blocks detected clear(it showed up in a list when i started typing it).

Are you linking -lncurses to your project?

---

### Post by googleye on 2011-10-18
Well no thats the thing, if I were compiling in the terminal I would know how. But in code blocks I'm lost.

---

### Post by Meghnaad on 2011-10-19
If doing it with ncurses is not a compulsion,
you can use **system()** function from **stdlib.h**

Something Like this:
```
system("clear");
```

---

### Post by googleye on 2011-10-19
Well I've read about it quite a few times and supposedly it's a major security risk to let system control your console or something like that. Even though my apps will never have any practical use and are only built to learn I want to get it in my system to never use that to clear the screen. 

I have tried the simplest method i know of, Lots of endl's in a loop, but the downside is that afterwards the text prints out at the bottom of the screen. Looks really ugly :/

---

### Post by MeduZa on 2011-10-19
> **Meghnaad said:**
> 
Something Like this:
```
system("clear");
```

never do something like this, is a bad programing way!

also system("pause"); is really bad, only use that just for testing, but a cin or scan is better to pause the program.

I'm start using ncurses 1  mount ago but I really easy (like old way programing xD )

there a lot of help out there about ncurses, and the library is really easy to use:

```
//creating main window
initscr();
//clear screen, send cursor to position (0,0)
clear();


```

---

### Post by MeduZa on 2011-10-19
dupe (delete me)

---

### Post by googleye on 2011-10-19
Well my issue is that I don't know how to link -lncurses when compiling with code blocks, thanks for clarifying though :)

---

### Post by denago on 2011-10-20
> **googleye said:**
> Well my issue is that I don't know how to link -lncurses when compiling with code blocks, thanks for clarifying though :)

[http://stackoverflow.com/questions/5862757/how-do-i-link-to-a-library-with-codeblocks](http://stackoverflow.com/questions/5862757/how-do-i-link-to-a-library-with-codeblocks)

---

