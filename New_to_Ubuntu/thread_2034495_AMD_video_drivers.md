---
title: "AMD video drivers"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by h2z on 2012-07-28
What is the best driver to use for gaming and general use? I have used the driver from AMD's site and the one the comes with "restricted drivers" but I'm not sure which works best. Using 12.04.

---

### Post by QIII on 2012-07-28
The driver you install from the Precise repo is the AMD/ATI 12.4 Catalyst Driver.

From the AMD/ATI website, you get the 12.6 (or perhaps 12.7 by now) driver.  There may be some very minor improvements.

However, installing the driver from the AMD/ATI website requires that you reinstall every time the kernel is updated when you do your normal Ubuntu updates.

For that reason, I recommend that newer users install from the repo.  

The fglrx-updates (Post Release Updates) version has been troublesome for many users, so I recommend against that one for the time being.

Also, using the graphical "Additional Drivers" method may also be troublesome.

If the "Additional Drivers" method fails, please refer to the ATI driver wiki in my signature.  In the table of contents, select "Using the Ubuntu repositories (alternate command line method, including hardware acceleration)" and follow the instructions.

---

### Post by h2z on 2012-08-06
In that case I think staying with the one from AMD is best for me. Is there a way to know exaclty when to reinstall it? When I get more than 15 update I rarely bother checking them one by one...

---

### Post by verymadpip on 2012-08-06
I run a (an?) HD4870 & I've always used the default drivers in the kernel without issue.

---

