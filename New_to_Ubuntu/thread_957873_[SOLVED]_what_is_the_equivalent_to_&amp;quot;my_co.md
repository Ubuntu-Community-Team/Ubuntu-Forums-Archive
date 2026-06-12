---
title: "[SOLVED] what is the equivalent to &amp;quot;my computer&amp;quot; of Windows"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by telltommy on 2008-10-24
In Ubuntu, how do i see my drives? I know i can see them in Gparted, but it there another way? HD, DVD and usb

---

### Post by SunnyRabbiera on 2008-10-24
Easy, go to places and then "computer" :D

---

### Post by mdpalow on 2008-10-24
You can always add those icon types to your desktop just like in Windows. There are a couple ways to do it.

Download QuickStart from my signature below and it will do it for you when selected.

Good luck...

mdpalow

---

### Post by link141 on 2008-10-24
One thing to note: on Linux systems, they aren't really seen as a separate hard drive.  Rather, partitions and file systems are mounted at a specific point on the main file system.  That is to say, a CD's and USB flash drive's file system is (temporarily) inserted into a specific folder branching off of the main (root) directory.  This means that applications see everything as one big filesystem as opposed to drive letters in Windows.

---

### Post by OneRingShort on 2008-10-24
Another way to view disk usage is the "Disk Usage Analyzer" in the Accessories menu.  For a terminal based command:
```
df -h
```

---

### Post by acidsolution on 2008-10-25
Open nautilius file browser and type 

```
 computer:/// 
```

this shows u similar to my computer in windows.

---

### Post by MrWES on 2008-10-25
> **telltommy said:**
> In Ubuntu, how do i see my drives? I know i can see them in Gparted, but it there another way? HD, DVD and usb

Right click on the Applications menu | Edit Menus | System Tools and put a check mark in Configuration Editor. Click close. 

Now you'll see the configuration editor in Applications | System Tools, click on it.

Navigate to apps | nautilus | desktop -- you'll see you can put check marks for which icons you want to show on your desktop.

Hope that helps. It's a tool that doesn't show by default when you first install HH.

Bill

---

### Post by telltommy on 2008-10-27
thanks all, every bit of info is useful.

---

