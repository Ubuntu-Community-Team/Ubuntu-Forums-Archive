---
title: "Adding a registry key for wine ?"
date: 2010-06-12
forum: Programming Talk
---

### Post by WitchCraft on 2010-06-12
Hi, question:

I'm writing an installer that installs a program that can convert AutoCAD drawings to Flash .swf files. That conversion program I use for a website, which can do floor-planning.

The converter program is for windows, but I got it working under Linux via wine, I just needed to copy some mfc dll's over.

My question now is: The program has a license key, which it stores in the registry. 
My installer program should thus write a windows registry key to wine's registry into section HKLM/Software. How do I do that on Wine ? 
Via script, or C/C++, or is there a way with mono ?

I need some way to write the registry key from a .deb package.

---

### Post by geirha on 2010-06-12
I guess you pass it as a file to wine's regedit.
```
wine regedit /\?
```

---

