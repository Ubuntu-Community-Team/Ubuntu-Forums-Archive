---
title: "[SOLVED] want to change screen resolution"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by kubes on 2008-11-13
I have just installed 8.04 and Ubuntu has detected my screen resolution as 800X600 automatically...
But on my screen 1024X768 looks better and 800X600 doesn't look good...
So when i change it to 1024X768...somehow my the screen starts doing weird things.:confused:.and i have to restart the Ubuntu..
Any suggestions how can i work around...or do i have to stay with this resolution forever..

---

### Post by bscbrit on 2008-11-13
Open a terminal and type the command:

sudo displayconfig-gtk

This will open a program which will allow you to set the correct monitor parameters.  You should then be able to set the screen resolution as you were trying to do before.  If that doesn't solve the problem, you could also try

sudo dpkg-reconfigure xserver-xorg

and input the desired data that way.  If you are not sure of an answer, accept the default.

If neither of those do the trick, come back and tell me what happened.  Good luck.

---

### Post by thunk77 on 2008-11-13
What kind of graphics card you have?

---

### Post by kubes on 2008-11-13
Thanks a million....
It worked...i dont why but when i changed last time ...there was always the problem....
but **sudo displayconfig-gtk** worked...

---

### Post by bscbrit on 2008-11-13
I'm pleased that you have a working system - I'll see you around the forums:-)

---

### Post by philinux on 2008-11-13
This may come as shock to some but in **Intrepid** displayconfig-gtk has been removed. Bullet proof x is supposed to sort it all out. If only. :lolflag:

---

### Post by bscbrit on 2008-11-13
Phil - I know that we have both seen the mistake in this move in this very forum over the last few weeks.  An automatic system is only any good if it ALWAYS works.  If no-one can guarantee that it will 100% of the time, then give us the tools to repair it please.

---

