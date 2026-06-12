---
title: "Network Card Not Recognized After Upgrading to 11.10"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by iswear on 2011-10-15
I recently upgraded from Ubuntu 11.04 to 11.10 using the Update Manager and now my wireless network card isn't recognized anymore. I have a Trendnet TWE-644UB wireless USB card. Any help in getting this thing working would be appreciated, but really I would much rather get an explanation of why my card worked in the previous version of Ubuntu but doesn't work now that I upgraded to a newer version. Don't they keep the drivers in the kernal from the previous releases of Linux?

---

### Post by mörgæs on 2011-10-15
There is a number of things which can break in an upgrade. Drivers for wirefree cards is only one of them. 

Do you have wired internet access?

---

### Post by wildmanne39 on 2011-10-15
Hi, no they do not always keep the same drivers sometimes they upgrade them.

Anytime you install a newer version you have to install the drivers again because of legal reasons they are not included and activated automatically on install.

Also with each new release there are some kinks that have to be worked out to get wireless working on some computers it is easy and others not so much.
Thank you

---

### Post by Allavona on 2011-10-15
Your old kernel should still be there unless you purged it. Update grub and reboot and see if 'previous linux version' appears in the grub menu.

---

### Post by wildmanne39 on 2011-10-15
Hi, please post the results of:
```
lsusb
```
Thank you

---

