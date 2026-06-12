---
title: "[SOLVED] Lost Menu labels; can't find SWAT"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Dr_Bop on 2008-06-27
I am new to Linux and have two problems:

1.  I have 8.04 running fine.  I must have clicked/dragged on my menu panel and lost the labels.  That is, out of the box on the menu you have:
Applications... System Firefox icon Evolution icon Help

I now have:
Firefox icon Evolution icon Help

I want the words back.  I did the RMB (right mouse button), add to the panel and got the icon for the words, but no words.  I did an Edit Panel, can't get words.  What am I missing?

2.  I have samba running (close anyway).  I saw that SWAT was a good utility. I loaded it with Synaptic but can't find it in any of the menus?
So, a) is SWAT the best? b) why is it not in a menu and how do I get it there.

Many thanks in advance

scott

---

### Post by bubba_169 on 2008-06-27
Try this:

- Right click on your panel
- Choose Add to panel
- In the list find 'Menu bar'
- Click and drag the 'Menu bar' item from the list onto your panel where you want it

---

### Post by cariboo on 2008-06-27
You have to access SWAT with a web browser. If it is running you can access it by typing in your browser address bar: 

```
http://localhost:901
```

To get to see if it is running in a terminal type:

```
ps ax | grep swat
```

if you get a result similar to this:

```
10596 pts/0    R+     0:00 grep swat
```

SWAT is not running

Jim

---

### Post by Dr_Bop on 2008-06-27
Thanks, bubba and Jim.

You both hit the target!  I appreciate your help...

scott

---

