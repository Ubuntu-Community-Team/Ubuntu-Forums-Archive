---
title: "Cscope Help"
date: 2006-08-13
forum: Programming Talk
---

### Post by snaggletooth on 2006-08-13
Hey everyone, I am having a problem compiling cscope, I'm getting this error:

> 
build.c:51:20: error: curses.h: No such file or directory
make[1]: *** [build.o] Error 1
make[1]: Leaving directory `/tmp/cscope-15.5/src'
make: *** [install-recursive] Error 1


I have been using Ubuntu during my internship at IBM this summer to ssh to a
server in the lab with SLES with cscope. It's been so convenient and useful
I decided to install it my Ubuntu box but it's failing because of some curses.h
file. Has anyone successfully installed it? What do you guys program and browse
through C/C++ code?

Thanks
&#1092; §&#325;&#258;&#290;&#286;&#321;&#282;&#358;&#510;&#510;&#358;&#294; &#1092;

---

### Post by NewWithoutClue on 2006-08-14
curses.h ?

I suspect installing ncurses-dev and/or libncurses-dev should permit your compile to continue past the current block.

Regards,
Paul

---

### Post by snaggletooth on 2006-08-15
Wow, thanks a lot for helping me with that.
It works beautifully now, I appreciate the help.

I have one last question.
How do you guys know if it's a library that's missing, 
and what's even more puzzling, how do you know the name
of it?

I searched google for 'curses.h cscope' and other 
variants but I couldn't find anything about a library.

How do you know where to look for help?

Thanks again,
&#1092; §&#325;&#258;&#290;&#286;&#321;&#282;&#358;&#510;&#510;&#358;&#294; &#1092;

---

