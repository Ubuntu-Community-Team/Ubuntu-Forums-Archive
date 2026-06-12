---
title: "speed"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Navane on 2008-08-18
In win 95 when you started netscape you had to wait a few seconds before it actually came up. In my current ubuntu I still have to wait a full second before firefox comes up. Back in the days I ran a pentium 1 133 mhz. No i have 2 ghz core 2 duo. Why can't it be instantanous?

To clearify; it's not that it's loading a website. Gedit still takes a full second to load as well.

---

### Post by sstusick on 2008-08-18
It must be your system. My system is as instantaneous as can be running 1 GB of RAM, 1.6 GHz core duo processor and Ubuntu 8.04.

---

### Post by nicedude on 2008-08-18
You should check all the services that are running by default and disable any you don't use for a start. Like maybe bluetooth or cups if you don't use them. You can google this and there are guides to what Ubuntu services are bad idea to turn off so you don't goof.

Hope that helps speed it up.

---

### Post by amo-ej1 on 2008-08-18
Well you test isn't very representative, to make a true comparison you should in fact launch netscape on your current system.

Software people tend to take full advantage of the system and try to add as many things as possible when given some extra room. You system/software is now filled with all additional extra features and enhancements, all this comes with a cost.

---

### Post by pro003 on 2008-08-18
Nah, this got nothing to do with your system, it's simply mozzila's fault... It does not matter where you run it, it always takes a few sec to load... Tell me when you open up a second window of firefox - does it still get too long...

p.s. and about pentium 1 stuff and mswin95, nah!

---

### Post by sdennie on 2008-08-18
Much of the delay you see is simply from reading an application from disk.  You'll notice that the second time an application starts it's basically instantaneous if you've recently started it.  You can use a utility called preload that, after it learns what applications you use, can make your common applications generally behave like this all the time by, well, preloading them.  It's as easy to install as:

```

sudo apt-get install preload

```

You can look at /etc/preload.conf to get a better understanding of how the software works.

---

