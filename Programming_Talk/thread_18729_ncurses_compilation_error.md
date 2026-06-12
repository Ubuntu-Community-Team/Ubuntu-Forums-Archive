---
title: "ncurses compilation error"
date: 2005-03-08
forum: Programming Talk
---

### Post by Kimm on 2005-03-08
ok, I just installed ncurses libraries on my computer, I need them for a project for school... when I try to compile this program (just made it to test if g++ found the libraries):

```

#include <ncurses.h>

int main()
{
       getch();

return 0;
}

```

g++ gives me this error:

> 
/tmp/cclgZLIU.o(.test+0x11): In function 'main':
: undefined reference to 'stdscr'
/tmp/cclgZLIU.o(.test+0x19); In function 'main':
: undefined reference to 'wgetch'
collect2: ld returned 1 exit status


can anyone tell me whats wrong? ](*,)

---

### Post by goatnuts on 2005-03-30
> **Kimm]ok, I just installed ncurses libraries on my computer, I need them for a project for school... when I try to compile this program (just made it to test if g++ found the libraries):

```

#include <ncurses.h>

int main()
{
       getch() said:**
> (*,)


You need to add the  compiler flag "-lcurses"  to tell the compiler to use the curses library. My compiler call looks like this

g++ -o foo/bar foo/c.o foo/main.o -pthread -lwx_gtk2-2.4 -lcurses

Hope this helps.

-goatnuts

---

### Post by ben-g on 2006-09-19
All the other code besides "g++ -o -pthread -lcurses" doesn't work but when I do run that it gives me this error.

"/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o: In function `_start':../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status"

I really need to figure this out because it's in my c++ class, so if any of you know how to do this please respond.

---

### Post by po0f on 2006-09-19
How exactly are you calling the compiler?  The "-o" flag takes one argument, the target binary, or *output*.  And if you are using ncurses, you need to tell the linker what libraries to link the binary with, namely curses.  Something like this should work:
```
$ gcc -Wall -o mybinary mysource.c -lcurses
```

The above might not work.  If you get linker errors, try substituting "-lncurses" in that case.  I don't know if you should be calling initscr() for so simple a program, but that might help too.  Also, it'd be a good idea to get used to adding "-Wall" to all your compiler commands, it lets you know when you made a boo-boo.

---

### Post by ben-g on 2006-09-19
I'm rather new to all of this, so if you could tell me what initscr() is that would help. I tried the code you gave me but it says that mysource.c doesn't exist. Do I have some missing files that I should download?

Thank you for helping me I really appreciate it.

---

### Post by po0f on 2006-09-20
If you need some curses help, [this](http://www.tldp.org/HOWTO/NCURSES-Programming-HOWTO/index.html) is what I started to learn.  [TLDP](http://www.tldp.org/) is a pretty good starting point for almost any Linux-related question, just for future reference.

---

