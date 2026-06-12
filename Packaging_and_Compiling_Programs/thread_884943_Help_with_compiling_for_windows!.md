---
title: "Help with compiling for windows!"
date: 2008-08-09
forum: Packaging and Compiling Programs
---

### Post by Anbog on 2008-08-09
Hi,

I'm I user - not a programmer, hacker, or in any other way used to handling code. However, I would like to know how much work it would take, for me to be able to compile a program for windows from source code?

More specifically, I would like to also use PyMol on my WinXP install, and not just on my Ubuntu install. The program is open source and available at [SourceForge]("http://pymol.svn.sourceforge.net/viewvc/pymol/branches/b11/pymol/"), but since the program moved from version 0.99rc6 to 1+ (currently at 1.1) they no longer provide free windows builds.

So, would an absolute beginner like me be able to compile it for use in windows (like follow a simple guide or something), or would I have to spend a lot of time reading to figure this out?

Andreas

---

### Post by Steveway on 2008-08-09
> **Anbog said:**
> Hi,

I'm I user - not a programmer, hacker, or in any other way used to handling code. However, I would like to know how much work it would take, for me to be able to compile a program for windows from source code?

More specifically, I would like to also use PyMol on my WinXP install, and not just on my Ubuntu install. The program is open source and available at [SourceForge]("http://pymol.svn.sourceforge.net/viewvc/pymol/branches/b11/pymol/"), but since the program moved from version 0.99rc6 to 1+ (currently at 1.1) they no longer provide free windows builds.

So, would an absolute beginner like me be able to compile it for use in windows (like follow a simple guide or something), or would I have to spend a lot of time reading to figure this out?

Andreas

Since that seems to be written in Python it doesn't need to be compiled. Just install Python and you should be able to run it.

---

### Post by oneporter on 2008-08-09
Can't you just use [the old build]("http://delsci.com/rel/099/")?

---

### Post by Anbog on 2008-08-09
Sure I can use the old one and that is what I do currently - but I would like the newest version to get the new features and all :)
I'll try getting it to work by installing Python..

Still, anyone care to take a guess on how much work it would be to compile?

---

### Post by Anbog on 2008-08-09
The install-python-and-run-it method seems to have failed, but maybe I'm doing somthing wrong?

All .py-files are now 'clickable' but nothing happens. I've tried "setup.py" and "setup2.py" from the main directory and "launch_pymol.py" from the \modules\ directory. If I chose to open them in IDLE and run them from there, I see a lot of error messages I don't understand.

---

### Post by Steveway on 2008-08-09
I guess that you propably are missing some libraries. Launch it from a terminal (python /path/to/file.py) and post the output.
Don't forget to put the output in [ code] [/ code] tags.

---

