---
title: "ubuntu 13.04 not booting up even after boot-repair"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by salil2 on 2013-08-20
Hi,

I installed Ubuntu 13.04 on my Sony VAIO laptop. After 2 successful boots, it was not booting. Hence, after a preliminary search I ran Boot - repair, and now error keeps on coming during startup: ''ELF header smaller than expected.''

The log file after running Boot-repair can be seen at paste.ubuntu.com/6005483.

Appreciate the responses so that I might be able to get rid of Windows.

---

### Post by rai_shu2 on 2013-08-21
Maybe unplug the pendrive?

---

### Post by oldfred on 2013-08-21
Not sure if related or not.
Some BIOS have issues with large / (root) partitions where boot files get scattered all over. For those BIOS a smaller / (root) at beginning of drive or a /boot partition at beginning of drive solves that issue. Then use rest of drive as /home or /mnt/data.
On line 351 you have grub.cfg at 212GB and the rest of grub & kernel near beginning of drive.

One quick test, but it only has worked for about 50% of users I have suggested it to, is to just shrink your current / partition to under 100GB, repair grub and see if it works. Since you only have 2.6GB in your 290GB sda1 partition (line 8459) the shrink should go pretty quick.

---

