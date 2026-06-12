---
title: "What does pts/0 stand for"
date: 2009-05-26
forum: Programming Talk
---

### Post by H.om on 2009-05-26
who
hariom   tty1         2009-05-26 21:22
hariom   tty7         2009-05-26 20:37 (:0)
hariom   pts/0        2009-05-26 21:09 (:0.0)

---

### Post by simeon87 on 2009-05-26
For what it is worth (from [here](http://lists.opensuse.org/opensuse/2002-09/msg00641.html)):

> 
pts stands for pseudo terminal slave. A terminal (or console) is
traditionally a keyboard/screen combination you sit and type at. Old
UNIX boxes would have dozens of them hanging off the back, all
connected with miles of cable. A pseudo terminal provides just the same
facility only without the hardware. In other words, it's an xterm
window or a konsole window, or whatever utility you use. They pop into
life as you ask for them and get given sequential numbers: pts/0, then
pts/1 and so on. The physical console is the hardware which is actually
attached to your box - you probably only have one. That's labelled ":0"
and is refered to as the actual "console".


---

### Post by H.om on 2009-05-26
thanks
I got it

---

### Post by H.om on 2009-05-26
thanks
I got it

---

