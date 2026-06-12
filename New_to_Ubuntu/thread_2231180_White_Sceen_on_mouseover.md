---
title: "White Sceen on mouseover"
date: 2014-06-23
forum: New to Ubuntu
---

### Post by Michael_Belanger on 2014-06-23
Whenever I pull up a menu or go to look at files, and mouse-over them, they turn white, almost as if I was pulling a curtain over them, to the point where[/FONT] I can't see them without getting _really_ close to the screen (even on a 32" TV) and even then, it's still hard to read what's there.  Scrolling down a list is agonizing!
Is there a "workaround" or fix for this?
Using Lubuntu 14.0 on a Dell tower, 1.6GHz Intel processor, 512MB RAM, 20 GB HDD.  I wiped the drive (it originally had Win XP Pro) before installing Lubuntu.

---

### Post by Michael_Belanger on 2014-06-27
I guess either there's no workaround, or no one has an answer.

---

### Post by Vladlenin5000 on 2014-06-27
I guess if you posted the info regarding the graphics card/chip there would be some replies...

---

### Post by Michael_Belanger on 2014-06-27
Being new to Ubuntu (or in my case, Lubuntu), I'm not sure where on that system to look for the graphics card.  When I go to the "System Profiler & Benchmark" window, I don't see a graphics card anywhere on there.  I'm _guessing_ (possibly incorrectly) that that's where I need to look for it, but I could easily be wrong.  If you (or whoever) could/would guide me here, I'd be appreciative.

Under the "Summary" it shows:

**Computer**
Processor:  Intel Pentium 4 CPU 1.60 GHz
Memory:  506 MB (216 MB used)
Operating System:  Ubuntu 14.04 LTS
User name:  owner (Owner)
Date/Time:  Fri 27 Jun 2014 <and the current time>

**Display**
Resolution:  1024x768 pixels
OpenGL Renderer:  unknown
X11 Vendor:  The X Org Foundation

**Multimedia**
Audio Adapter:  ICH-Intel 82801BA-ICH2

**Input Devices**
Power Button
Power Button
AT Translated Set 2 Keyboard
B16_b_02 USB PS/2 Optical Mouse

**Printers**
No printers found <there aren't any>

**SCSI Disks**
ATA Maxtor 6L040L2
HL-DT-ST CD-RW GCE 8160B

---

### Post by Rob Sayer on 2014-06-27
Why don't you just try searching for "ubuntu show graphics card" in your search engine?

---

### Post by Michael_Belanger on 2014-06-27
If the graphics card is the same as originally installed, it's an integrated AGP 4X card/chip.

---

### Post by Vladlenin5000 on 2014-06-27
The following command should output all the relevant information: ```
glxinfo | grep OpenGL
```
Please post back the results for further troubleshooting.

---

