---
title: "Getch Help"
date: 2008-03-02
forum: Programming Talk
---

### Post by nerdpride on 2008-03-02
I know ncurses contains the function "getch()" but, because my linux computer is not connected to in the internet, i am having trouble installing it. There isn't any standard library that has it, right? I tried to use "getchar()" in stdio.h but it doesn't appear to be the same thing.

Help a programming idiot out,
nerdpride

---

### Post by Jessehk on 2008-03-02
**getchar()** in *stdio.h* will get a single character from stdin. By pressing enter, you can sort-of imitate **getch()**.

---

### Post by nerdpride on 2008-03-02
No, I use iostream's cin for stuff like that. is there anything that:
1. does not display the charecter
2.doesnot require that you do anything but press the key

---

### Post by jaddle on 2008-03-02
There isn't anything really straightforward, since this requires that the console be reconfigured somewhat, and this can't be done in a portable way. [http://c-faq.com/osdep/cbreak.html](http://c-faq.com/osdep/cbreak.html) has some more information about the issue.

I used the termio solution in a program I'm writing now, but used some #ifdefs to use getch instead when it's compiled for windows.

---

