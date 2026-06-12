---
title: "How to install dev c++"
date: 2010-03-29
forum: Programming Talk
---

### Post by sinhanikhil.5 on 2010-03-29
I want to install dev c++ compiler in my machine??? How can I Load it in Ubuntu?
I want to do it using Terminal, also want to know how to un-install it, incase have to do in future.
Feedback welcomed.



[COLOR=White].[/COLOR]

---

### Post by fly-by-night on 2010-03-29
[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

Check here (to post your question).  More than likely Programming Talk.

---

### Post by Simian Man on 2010-03-29
Don't install Dev-C++.  It is horribly buggy and hasn't been developed in a long time.  Try Code::Blocks.

---

### Post by cariboo on 2010-03-30
A bump for the move

---

### Post by Can+~ on 2010-03-30
Oh, I also started with Devcpp in windows, and tried desperately to run it on ubuntu on my first days.

Move on, ubuntu has better tools, and devcpp is dead old. If you want a simple "click and compile" alternative, install geany.

```
sudo apt-get install build-essential geany
```

(build-essential is for compiling C/C++).

---

### Post by deer dance on 2010-03-31
I wrote a tutorial on installing Dev-C++ on Linux on the CrunchBang forum.

Though it's meant for Openbox, nothing really changes in GNOME.

[http://crunchbanglinux.org/forums/topic/6129/install-devc-on-linux-wine/](http://crunchbanglinux.org/forums/topic/6129/install-devc-on-linux-wine/)

---

### Post by sinhanikhil.5 on 2010-04-01
> **Can+~ said:**
> Oh, I also started with Devcpp in windows, and tried desperately to run it on ubuntu on my first days.

Move on, ubuntu has better tools, and devcpp is dead old. If you want a simple "click and compile" alternative, install geany.

```
sudo apt-get install build-essential geany
```

(build-essential is for compiling C/C++).
Thanks to all, 
Can+~ thanks for the alternative I installed geany in my machine and its working perfectly perfect.
:)




[COLOR=White].[/COLOR]

---

### Post by sinhanikhil.5 on 2010-04-01
Well actually its not so perfect.

I wrote a simple program to add two numbers and compiled, till here its fine.i have saved it as sum.c on my desktop, but when ever I run the program its giving an error msg:
./geany_run_script.sh: 5: ./sum: not found.
also 1 more problem(as related so putting in same thread.)


i can only access geany through terminal and when ever i close terminal it closes. How to access geany directly.

---

