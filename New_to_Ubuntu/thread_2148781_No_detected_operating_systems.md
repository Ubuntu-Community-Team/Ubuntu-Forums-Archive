---
title: "No detected operating systems"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by Rowanem on 2013-05-26
Hi, I'm not exactly a computer genius or whatever, so if you find a solution to this, use simple terms please :)
I'm trying to install Ubuntu alongside Windows 7 from a USB stick, and I can boot from it fine, but when I try and install it I get this message: 
"This computer currently has no detected operating systems. What would you like to do?
I'm not sure what's happening :(

---

### Post by Mark Phelps on 2013-05-26
It's very likely that you have a PC with UEFI -- which I personally don't debug.  My suggestion is NOT to try to force an installation as, if you do, you could possible trash Win7 in the process.

Someone will be along who better understands the issues related to UEFI and will help.

---

### Post by Rowanem on 2013-05-27
bump

---

### Post by newb85 on 2013-05-27
I second Mark Phelps' recommendation that you not force an installation.  I've done that once on a friend's computer, and it wiped out Windows.  (Fortunately, he had recently purchased a new computer, and didn't need anything on that old one anymore.)

Does your computer have a special HDD setup?

---

### Post by fantab on 2013-05-27
> **Rowanem said:**
> 
"This computer currently has no detected operating systems. What would you like to do?


What version of Ubuntu do you have?
Can you post the screenshot of your Windows partitions?

If a system has uefi then the installer will give you options in the BIOS/UEFI Boot Menu when you go there to boot your USB. They will be 'PMAP' and 'UEFI/EFI'. Do you see such options?

What machine is this laptop? what are the specs?

Did you do anything with your Hard Disk Partitions before you tried to install Ubuntu?

---

### Post by squakie on 2013-05-27
And - if uefi you must install the 64 bit version.

---

