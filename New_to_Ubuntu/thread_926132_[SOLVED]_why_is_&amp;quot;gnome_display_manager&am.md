---
title: "[SOLVED] why is &amp;quot;gnome display manager&amp;quot; running at start-up?"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by ferral-cat on 2008-09-21
Hi There I am using Xubuntu Hardy heron but I noticed during boot up as all the lines of code are scrolling by that "gnome display manager" is starting on my XFCE system.  

I executed this command:

```
sudo sysv-rc-conf
```

And I notice that gdm is set to start at runlevels 2,3,4,5

Should I remove it?

I had brasero and gedit installed but have since removed them.

---

### Post by Mornedhel on 2008-09-21
Because GDM is the display manager for XFCE.

Xubuntu has a *lot* of Gnome packages. A Xubuntu maintainer I know basically quit because of that...

---

### Post by Denestria on 2008-09-21
GDM is your graphical login window.  If you remove it you will boot up into a terminal and have to manually start X windows.

---

### Post by ferral-cat on 2008-09-21
Thanks guys.  I really appreciate your fast response and your donation of time to advance Linux.  

Im using my Linux partition about 80% of the time now and I love it!

---

