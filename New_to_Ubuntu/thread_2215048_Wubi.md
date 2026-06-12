---
title: "Wubi"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by james120 on 2014-04-04
Hey, I'm new to linux.  I downloaded and installed ubuntu 12.04 using the windows installer route.  C:\ubuntu.  Everything looks good so far.  It'll dual boot and I choose generic.  I think that's right.  Anyway,  I tried to replace my desktop with a picture from another internal drive I use for photos.  It worked fine, but I logged out, rebooted and logged back in later and the photo that I chose was missing from the desktop, but was still in the appearence section.  My question is:  how do I save this so when I get back in it'll come up as it was when I logged off.  Thanks

---

### Post by Impavidus on 2014-04-04
The cause of your problem is that the photo is not stored on your virtual Ubuntu partition, nor on the Windows C partition. It is stored on a partition that is not automatically mounted before you login. The easiest solution is to copy the photo you want as background to your home directory. Saving disk space you can also automount the photo partition using [fstab]("https://help.ubuntu.com/community/Fstab").

Note that the Windows installer ("wubi") method is deprecated. It doesn't work with the latest Windows versions. You can continue using it for some months to try Ubuntu, but if you like it I recommend that you later install Ubuntu 14.04 as a real dual boot.

---

### Post by elliotn on 2014-04-04
> **Impavidus said:**
> The cause of your problem is that the photo is not stored on your virtual Ubuntu partition, nor on the Windows C partition. It is stored on a partition that is not automatically mounted before you login. The easiest solution is to copy the photo you want as background to your home directory. Saving disk space you can also automount the photo partition using [fstab]("https://help.ubuntu.com/community/Fstab").

Note that the Windows installer ("wubi") method is deprecated. It doesn't work with the latest Windows versions. You can continue using it for some months to try Ubuntu, but if you like it I recommend that you later install Ubuntu 14.04 as a real dual boot.

+1 I concur

---

### Post by newb85 on 2014-04-04
The issue with Wubi is more than just nit working with newer Windows. Canonical is dropping support for Wubi altogether.

---

### Post by PaulW2U on 2014-04-04
> **newb85 said:**
> Canonical is dropping support for Wubi altogether.

I think it was dropped some time ago - [http://www.omgubuntu.co.uk/2013/04/wubi-advice](http://www.omgubuntu.co.uk/2013/04/wubi-advice)

---

