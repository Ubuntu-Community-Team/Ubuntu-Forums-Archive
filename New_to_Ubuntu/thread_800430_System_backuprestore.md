---
title: "System backup/restore"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Metal Mick on 2008-05-19
Hi all,

I have Ubuntu pretty much as a fresh install (with a driver or two and the multimedia codecs in place) and would like to back up the entire system, so that if there's a catastrophe, I can recover without too much trouble.

In any event, it's not a bad thing to have an image (on DVD) to restore from. Can someone make a recommendation or two regarding this?

I have a Wubi install, with WinXP as my other OS. Ubuntu is on a second hard drive, in a 50GB partition.

My data is stored on a partition on the Ubuntu drive and I back this up separately.

It would be nice if I could make a bootable DVD and restore this to the hard drive it was removed from.

Still, any and all advice would be gratefully received.

Regards,

Michael P

---

### Post by SunnyRabbiera on 2008-05-19
well one thing I suggest is to invest in a external hard drive, they are usually fair priced these days.
one app I can suggest you try is simple backup, simple backup provides a pretty decent way to back up your files

---

### Post by Metal Mick on 2008-05-20
Hi SunnyR,

many thanks for the suggestion. I'm looking into the software after I finish this.

As for the hardware, I would normally have done this, but I have a spare HD in my machine that I want to burns images of both OSs to.

Regards,

Michael P

---

### Post by Ryadt on 2008-05-20
hi..check this tutorial [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
hope it helps.

---

### Post by mapes12 on 2008-05-20
Hi

I found this website accompanlished exactly what you may be looking to do. Worked for me:

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by philinux on 2008-05-20
Specifically for ubuntu.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by avtolle on 2008-05-20
If I understood the OP correctly, Wubi was used to install. It would seem to me that if this will work, as Ubuntu is located in a separate folder under XP, he should back up that folder from his/her XP side. While one may do many things "the same" under a Wubi install as one would do them under a "true" dual boot XP/Ubuntu install on separate partitions, I'm not sure that the traditional backup routines we use for such install will work when the installation was done under Wubi. I guess any of the suggestions made above may be tried, but I wonder as to their eventual efficacy.

---

### Post by gmrishel on 2008-05-20
I have used 'dd' in the past with great results, but it can be dangerous.  
Really read up on this and study it.  You can wipe a hard drive easily if not done properly.  I wont try to give details on how to do it, I would feel bad if something went wrong.

Never mind, I don't think discussions about 'dd' is appropriate for this section.  Some people say 'dd' stands for Disk Destroyer...

---

