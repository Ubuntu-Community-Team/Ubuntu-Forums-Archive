---
title: "Monitor is unstable"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by bob525 on 2012-11-21
I am new to ubuntu. This is the closest I have got to actually using the OS. The installation went well on my ASUS computer.
But the monitor ViewSonic has been detected by ubuntu - the image flashes like a strobe light, parts of the information fade in and out as the mouse is moved around ad sometimes the screen has lines all over it!
I am not sure what to do next!
Help

---

### Post by papibe on 2012-11-21
Hi bob525. Welcome to the forums ):P

Could you post the result of these commands?
```
lshw -C display

lspci -nnk | grep -iA2 vga
```
Regards.

---

