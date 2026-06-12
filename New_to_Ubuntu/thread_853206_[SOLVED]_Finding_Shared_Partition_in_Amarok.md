---
title: "[SOLVED] Finding Shared Partition in Amarok"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by andrewt522 on 2008-07-08
As per the forum, I am brand new to Ubuntu.  I set up a dual boot and what I hoped would be a shared partition between Windows XP & Ubuntu.  The partition is formatted NTFS and contains all of my media.  I downloaded the KDE desktop so I can use Amarok.  After I startup Amarok, the import wizard opens up but I can't find my shared drive as an import option.  I do see the drive listed as "Media 90.8 GB" listed under "Places" and have mounted it.  How do I add this drive to the list of import options in Amarok?

Apologies in advance if this answer is easily found elsewhere.  It's quite possible I am not searching under the right terms.

---

### Post by wolfen69 on 2008-07-08
you did not have to download the kde desktop to run amarok. a simple: ```
sudo apt-get install amarok
``` would have sufficed. you can run kde based apps within gnome, no problem. 

you will need to navigate to the partition to import anything. if you are not familiar with the linux file system, and how it works, this may be difficult. basically, go to root (/) then media, then your partition.

---

### Post by andrewt522 on 2008-07-09
Thank you, Wolfen 69.  Per your advice, I did some reading on linux file systems and was able to find the partition.

Thanks again!

---

