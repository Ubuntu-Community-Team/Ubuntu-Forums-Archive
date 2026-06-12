---
title: "Access to mouse events"
date: 2009-08-19
forum: Programming Talk
---

### Post by ruru on 2009-08-19
I would like to get hold of mouse movements and dump them to disc. I will be using more than one mouse (I plan to use these as cheap data capture devices) and some research has suggested that mouse movement data is streamed to /dev/input/mouseXXX, but I am not sure how to access this info. 
```
sudo cat /dev/input/mouse2
``` doesn't show anything at all.

I have USB mice (they all work fine) and am working on Ubuntu Intrepid (AMD64).

Can anyone point me in the right direction? I would really appreciate your help!

---

### Post by jeffathehutt on 2009-08-19
I don't use Ubuntu, so this may not apply to you...

On my system the mouse events are sent to /dev/input/mice and using
```
sudo cat /dev/input/mice
```
does show data whenever I move the mouse.  Maybe your system is set up in a similar way?  Hope that helps a bit. :)

---

### Post by ruru on 2009-08-20
This is what I have been reading, but I don't get those results. cat /dev/input/mice (and all of the other input devices, mouseXXX, eventXXX) just gives blank output. 

I can identify the correct input device by hotplugging it and seeing which files are changed. 

Anyone know why /dev/input/mice would not return anything for a functioning USB mouse?

---

