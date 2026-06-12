---
title: "Ubuntu sees second Software RAID is two drives"
date: 2015-08-26
forum: New to Ubuntu
---

### Post by iscariot on 2015-08-26
I have two raid1 arrays that are I guess softraid off my mobo.  It's an ASRock 970 EXTREME3.  In windows, it sees the raid as a single drive.  I've got ubuntu also installed on a raid and it sees that raid as a single drive but not the other raid.  Is there a way to fix this?

---

### Post by sandyd on 2015-08-26
The softraid off the motherboard is not software raid. In Linux, it is called 'fakeraid', and is completely different than Ubuntu's Software RAID. 

Normally, if you are just running Ubuntu, I would recommend Ubuntu's software raid as it is much more versatile than fakeraid. However, Windows does not support Ubuntu's software raid.

Here are some instructions on how to install Ubuntu with fakeraid: [http://askubuntu.com/questions/455511/dual-boot-ubuntu-14-04-and-windows-7-on-fakeraid-installation-error-question-m](http://askubuntu.com/questions/455511/dual-boot-ubuntu-14-04-and-windows-7-on-fakeraid-installation-error-question-m)

---

### Post by iscariot on 2016-02-09
Ubuntu is runnning on a fakeraid fine, it's not seeing the other fakeraid drive, it's seeing two 1tb volumes.  How doI fix that?

---

