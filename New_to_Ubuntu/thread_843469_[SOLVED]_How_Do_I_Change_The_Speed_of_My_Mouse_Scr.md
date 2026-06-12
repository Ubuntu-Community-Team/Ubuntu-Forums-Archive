---
title: "[SOLVED] How Do I Change The Speed of My Mouse Scrolling?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Eric Qel-Droma on 2008-06-28
For some reason, my MS Wireless mouse is scrolling SUPER FAST in 8.04.  I've checked System --> Prefs --> Mouse, but I see no scroll wheel options there.  How do I change the scrolling speed?

Thanks!

Eric

---

### Post by unutbu on 2008-06-28
```
xset m 3 4
```
Make the 3 smaller if it is still too fast.

---

### Post by cmike2 on 2008-06-29
Does this command actually change the mouse wheel scroll speed? I don't notice a difference in scroll speed when I use "xset m 3 4" or "xset 1/2 4". The man page says that it affects mouse acceleration.

---

### Post by unutbu on 2008-06-29
The "xset m accel threshold" command only affects mouse pointer movement. The mouse wheel clicks and each click forward or backward is actually recorded as a mouse button press/release event, which is a different thing entirely. 

It appears that how the mouse wheel clicks are handled is done on an application-by-application basis. Here are instructions for controlling mouse wheel speed in Firefox: [http://ubuntuforums.org/showthread.php?t=59815](http://ubuntuforums.org/showthread.php?t=59815)

---

