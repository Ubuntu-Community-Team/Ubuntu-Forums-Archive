---
title: "Problem Changing the screen resolution down to 800x600."
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Dead Angel on 2008-10-15
Problem is I cannot, and when I try the screen starts this very rapid rotation I cannot change I can modify by movin the mouse. I cannot stp this however. I have this problem continously and it is limiting my usage of Ubuntu.

---

### Post by cmnorton on 2008-10-16
Will your graphics processor support 800x600? It probably should.

First examine /etc/X11/XF86Config and go to the screen section. Make sure your resolution is there. If it isn't, add it using sudo in front of your favorite editor.

Else, you may need to boot into recovery mode and run 

dpkg-reconfigre xserver-xorg

take all the defaults, except add 800x600 as your resolution.

---

