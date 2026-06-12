---
title: "Calendar app, where to start??"
date: 2008-02-06
forum: Programming Talk
---

### Post by mattgaunt on 2008-02-06
Hey everyone

I am interested in attempting to write my own calendar app, Ive been programming for about yr and a half at uni (Studying computer science) and i largely want to see if I can achieve this.

I have alot of hurdles to overcome and I know this but anyway, All the programming I've done has been very much command line based implementing algorithms for certain tasks.

Basically what I'm trying to ask is, what is the best language to write a program to use on ubuntu with GUI and just everything working. Ive only touched C, Java, Haskell before as well as other random languages like occam, verilog and assembler code.

To cut things short any guidance would be awesome, this is more of a personal challenge than anything to any help would greatly appreciated

Gaunt

---

### Post by lnostdal on 2008-02-06
there is no definite answer

but of those you mention java seems most likely your best bet: [http://java.sun.com/docs/books/tutorial/uiswing/index.html](http://java.sun.com/docs/books/tutorial/uiswing/index.html)

c always has always gui libraries of course:
[http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)

something that you do not mention - but many here probably will, is python and pygtk:
[http://www.pygtk.org/](http://www.pygtk.org/) (check the tutorial)

python and java is in this case easier to deal with than c, and probably the more suitalbe choices

check the stickies for more links to books, tutorials and reference guides for each language

---

### Post by mattgaunt on 2008-02-06
Kool thanks Inostdal Ill have a look into it, at least now i have a bit of a starting point

Gaunt

---

### Post by pmasiar on 2008-02-06
In Python you will be more productive that in Java, especially if you are not expert in java's byzantine libraries and there is no expert guide at hand.

And Python is easy to learn: for someone like you, it is as Tim Berners-Lee famousle said: "a language you can learn in one flight on one set of batteries".

"Dive Into Python" is your book. See wiki in my sig for more links and training tasks - or you can reimplement tasks you already did in other languages.

---

### Post by mattgaunt on 2008-02-06
One question I forgot to ask in the original post, does anyone have any bright ideas on the best way to store the information for the calendar??

I was thinkin possibly using a database to store the information and my program act as a front end for it, but i would need a database that is pretty flexible I imagine.

Any ideas??

Thanks for the help so far guys

Gaunt

---

### Post by pmasiar on 2008-02-06
What kind of database store? 
Single user? SQLite is fine
Multiuser calendar? That is more interesting, but also much bigger can of worms to open, google for "project chandler" :-)

---

### Post by mattgaunt on 2008-02-06
Yeah it was jus a single user, i just tried having a lil play around with SQLite but was stopped instantly since the compiler isn't finding the library sqlite3.h, any ideas how to fix this??

Gaunt

---

### Post by pmasiar on 2008-02-06
> **mattgaunt said:**
> any ideas how to fix this??

Use Python, 2.5 comes with pysqlite included :-)

Motto of Python is "batteries included"

---

### Post by lnostdal on 2008-02-06
mh, wait a second .. sqlite is in the ubuntu repositories (like most other things) - no need to download and compile the software "manually" .. just do:

```

root@ibmr52:~# aptitude search sqlite | grep python
p   python-pysqlite1.1              - python interface to SQLite 3              
p   python-pysqlite2                - python interface to SQLite 3              
p   python-pysqlite2-dbg            - python interface to SQLite 3 (debug extens
p   python-sqlite                   - python interface to SQLite 2              
p   python-sqlite-dbg               - python interface to SQLite 2 (debug extens
v   python2.4-pysqlite1.1           -                                           
v   python2.4-pysqlite2             -                                           
v   python2.4-sqlite                -                                           
v   python2.5-pysqlite1.1           -                                           
v   python2.5-pysqlite2             -                                           
v   python2.5-sqlite                - 

```

i believe *python-pysqlite2* is the package you are after .. (someone please correct me if i am wrong here)

---

### Post by stevescripts on 2008-02-06
Re: SQLite - the latest precompiled binaries are always available 
from:  [http://www.sqlite.org/](http://www.sqlite.org/)

The source is available there as well.

Steve

---

### Post by mattgaunt on 2008-02-07
Yeah i downloaded sqlite3 from the repo's but the gcc compiler cant find sqlite3.h, any idea on fixes, if i get time tonight at work ill play arnd on my laptop to try out python, but if anyone does have a solution to the problem regarding C would be gd to know

Thanks guys

Gaunt

---

### Post by lnostdal on 2008-02-07
..you did not mention C previously ... x)

but in that case:

```

sudo aptitude install libsqlite3-dev

```

there is a pattern here for similar things: *lib<name-of-software>-dev* .. i use *aptitude search* and *grep* to find what i'm after usually

---

### Post by mattgaunt on 2008-02-07
Cheers man i jus worked it out before i read your post, i didnt really that the -dev files included all the header files.

Gaunt

---

