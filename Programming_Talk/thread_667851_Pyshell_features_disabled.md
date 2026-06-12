---
title: "Pyshell features disabled?"
date: 2008-01-14
forum: Programming Talk
---

### Post by Bionic Apple on 2008-01-14
I wanted to get started into Python, but the tutorials required me to do things in the menu which PyShell grayed out. I can't even open a new window and I can't even open a file!  I reasoned it is because I am missing a package, but I downloaded the python-dev package (I have no clue what that does) and nothing happened.  What should I do, or is there a better program to write Python with?

---

### Post by Bionic Apple on 2008-01-15
I know the question may be simple, but I need help!

---

### Post by dwblas on 2008-01-15
Many use their favorite text editor and run the program file from the terminal.  There is also Idle, which comes with Python.  I am a text editor + terminal person so I can't comment on how good it is.  BTW, why are you using pyshell instead of bash?  In case you didn't see it, here is the link to the programming tutorials from the posts at the top of this forum if you are looking for additional refs.  [http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867) and this is the link from that link to getting started with Idle which also covers saving a program to a file and running it  [http://hkn.eecs.berkeley.edu/~dyoo/python/idle_intro/](http://hkn.eecs.berkeley.edu/~dyoo/python/idle_intro/)  and  [http://ubuntuforums.org/showthread.php?t=666668](http://ubuntuforums.org/showthread.php?t=666668)

---

### Post by Bionic Apple on 2008-01-15
Well, I started with Pyshell because it was already on my computer (it must come with Ubuntu) and I wanted to get into Python.  However, it looked a lot like the Idle, which I thought would be great (plus the added features).  But, why shouldn't I use Pyshell? Also, apparently I downloaded WxWidgets through the repositories, but I only have PyCrust and PyShell (as far as I can tell).  Do all the wxPython programs come in that package and if not how can I get them (if there is now downside to them)?

---

### Post by pmasiar on 2008-01-15
Maybe you can start with plain IDLE? See wiki in my sig day of idle toying" is very beginner level intro to IDLE. Or check showmedo.com website, they have plenty of screencasts about Python, so you will see how stuff is done.

---

### Post by Bionic Apple on 2008-01-17
How would I get to the IDLE?  If the IDLE is "Applications -> Programming -> Python Interpreter (2.5)", then that does not help me at all.  In the tutorials, they show you how to save your file and open up a non-interpreter window for editing.  The Python Interpreter that I just mentioned just opens up a interpreter in the terminal, not allowing any saving to be done.  Also, (for the third time) why is PyShell so unpopular?

---

### Post by Compyx on 2008-01-18
In IDLE you just select File->New Window and you're good to go.
PyShell is probably not very popular because IDLE already has everything you need. And most people don't even use IDLE, just a decent text-editor and a terminal-window will do perfectly fine.

I myself use VIM for all my editing needs and a simple xterm for running my apps. If for some reason I need an interactive python shell, I'll just fire up python without arguments on the command line.

---

### Post by pmasiar on 2008-01-18
> How would I get to the IDLE?

What is your platform? IDLE is not installed by default in Ubuntu, get it using synaptic.

---

### Post by Bionic Apple on 2008-01-18
Thanks, those last two posts helped a lot.  I thought the IDLE was already installed in Ubuntu.  Well, I got the "idle" package and that did it for me.  However, I wanna smack myself for not realizing that sooner!

However, I think the question (thread title) should still be answered for anyone who needs it later.  So this thread is still marked as unsolved.

---

### Post by dwblas on 2008-01-18
> However, I think the question (thread title) should still be answered for anyone who needs it later.>  I can't even open a new window and I can't even open a file!It's not that pyshell is bad, it's that it doesn't do what you want it to do, and there are many other tools that will.  You are not trying to learn pyshell, you want to learn Python.

---

### Post by Reactor5 on 2008-05-27
I'm trying to use pycrust/shell and I've got the file actions disabled to, except for save.  Are there any workarounds?  I know python and I'm exploring different editors/IDEs and I'd really like to get this working.  Any tips?

---

