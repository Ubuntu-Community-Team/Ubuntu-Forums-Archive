---
title: "Compiz"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Benbow on 2008-05-20
Any ideas what this means?
benbow@benbow-desktop:~$ compiz fusion
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by overdrank on 2008-05-20
> **Benbow said:**
> Any ideas what this means?
benbow@benbow-desktop:~$ compiz fusion
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

HI and this thread may help
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by bumanie on 2008-05-20
It looks as though you have not installed the restricted graphics driver and are still on the linux 'vesa' driver that does not provide 3d acceleration. Go to System --> Administration --> Hardware Drivers and install the driver. If you have already done this, you will likely have to try one from the manufacturer's site.

---

