---
title: "AMD Proprietary Drivers"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by clementchiew on 2013-08-01
The typical method to install AMD's proprietary drivers is from the Additional Drivers tab in System Settings. Mine, however, says that I do not have any proprietary drivers that need installing. So, I installed the AMD Fan Club Install Manager ([http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html](http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html)) but it gave me a problem and stopped installing the drivers. I have a old AMD card (Radeon 4570) and I could use some extra frames in Dota 2 or visual quality. What should I do to get those drivers now?

---

### Post by mastablasta on 2013-08-01
you need to install 12.04.1 or lower to get the kernel, xserver etc. that supports your card. Then you can install the additional drivers. it is possible to downgrade those but is not advised as it can cause issues. 

that card was unfortunatelly moved into legacy support. but at least they could have made the drivers available as it's understandable they won't add any new features.

another option is to get latest kernel and latest opensource drivers. which were improved a lot by AMD iv'e read (but not tried myself).

---

### Post by su:bhatta on 2013-08-01
> **mastablasta said:**
> 

another option is to get latest kernel and latest opensource drivers. which were improved a lot by AMD iv'e read (but not tried myself).

This i have also recently learned both Fedora and Chakra forums! Fresh 3.11 kernel supposedly is more suited or works better with AMD! have not tried though!

---

