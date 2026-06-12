---
title: "Ubuntu screen resolution/size/position"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by hoochblues on 2008-06-27
I have an older Dell Latitude laptop that crashed. I didn't have the Windows disks. And had always wanted to try Linux. So I installed Ubuntu.

Install went fine. But when I rebooted I seem to be stuck with 800x600 screen resolution. 1024x768 worked fine on Windows.

I am completely new to Linux after years and years on Windows. 

Related to the above resolution problem, I am trying to configure Evolution Mail but having problems. The buttons (Forward etc.) themselves are not visible as that part of the screen extends beyond the visible portion I can view.

And for the live of me I can't figure out how to scroll down to get at the buttons. 

How do you do that in Ubuntu? My mouse scroll button works fine in Firefox. But not in other screens. 

Thanks!

---

### Post by Pjotr123 on 2008-06-27
Try this:
Applications - Accessories - Terminal
type:
```
gksudo displayconfig-gtk
```

Press Enter.

---

### Post by hoochblues on 2008-06-27
> **Pjotr123 said:**
> Try this:
Applications - Accessories - Terminal
type:
```
gksudo displayconfig-gtk
```

Press Enter.

Thanks. That took me to a screen where I can enter a driver. Now I think I need to research what the right driver is for this Dell Latitude. Because so far this screen still locks me into 800x600.

Thanks again.

---

### Post by Pjotr123 on 2008-06-27
OK... For the driver:

[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 )

---

### Post by hoochblues on 2008-06-27
> **Pjotr123 said:**
> Try this:
Applications - Accessories - Terminal
type:
```
gksudo displayconfig-gtk
```

Press Enter.

OK. Foolish boy. I made the mistake of actually trying to reset the driver to what I believed was correct. Now my screen is all messed up. It's basically showing 2 screens horizontal.

When I orginally set the driver there wasn't one specified under graphics card. Now I don't seem to be able to "delete" the graphics card setting I set.

How do I do that? In other words how to I reset it to what was originally installed?

Thanks!

---

