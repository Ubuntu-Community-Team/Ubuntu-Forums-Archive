---
title: "How do I install a driver?"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by VetteGuy95 on 2012-01-09
Hi all.  I've installed a new graphics card (Zotac GT-430) which supports dual monitors.  It currently does not recognize the second monitor.  I've gone to the Zotac website and downloaded the latest driver for Linux.  Now the big question...

How do I install the new driver?

Talk about an incredibly stupid noob question!  I'm embarrassed just to ask it! :redface:

VetteGuy95

---

### Post by SlugSlug on 2012-01-09
Installation  instructions: Once you have downloaded the driver,   change to the  directory containing the driver package and install the driver by  running, as root, sh  ./NVIDIA-Linux-x86-256.53-pkg1.ru



--- its on the site ;) 

[http://www.nvidia.co.uk/object/linux-display-ia32-256.53-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-256.53-driver-uk.html)

---

### Post by VetteGuy95 on 2012-01-09
Gosh darn it!  I got the driver from the Zotac site, not nVidia!  I couldn't find the instructions there.  I should have known better..

Thank you VERY MUCH SlugSlug

---

### Post by Paqman on 2012-01-09
Actually I'd advise against manually installing the driver from the Nvidia site. Instead open up Additional Drivers and the one it offers you there.

Generally speaking on Linux you don't install anything direct from websites. You use your system's package manager. Doing so keeps your system stable and secure. Integrated package managers are probably the main reason why Linux has a better reputation for security and reliability than Windows.

---

### Post by SlugSlug on 2012-01-09
> **Paqman said:**
> Actually I'd advise against manually installing the driver from the Nvidia site. Instead open up Additional Drivers and the one it offers you there.

Generally speaking on Linux you don't install anything direct from websites. You use your system's package manager. Doing so keeps your system stable and secure. Integrated package managers are probably the main reason why Linux has a better reputation for security and reliability than Windows.
+1 this - sorry i didn't advise so

---

