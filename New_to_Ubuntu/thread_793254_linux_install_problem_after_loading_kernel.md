---
title: "linux install problem after loading kernel"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by benjo18 on 2008-05-13
Hi everybody, 
I am using kubuntu since one month, and I upgrade the previous version to kubuntu 8.04. Just notice that this computer has a partition for xp, and an other one for linux. I change something in the fstab file (in order to solve a problem with the cd drive) and then I could not run kubuntu anymore, it crash even on recovery mode, the error message is the following:

etc/init.d/ r : 137 :red .permision denied
init is enable to execute "init/sh" for rc default permission denied.

I decided to boot from the live cd, but now nothing happens... it stops after loading the kernel:

casper/vmlinuz.gz..........(etc)....
casper/initrd.gz...........(etc)....ready

and then I have a black screen with a black cursor, and nothing happens.
Is that normal, 
Is anyone can help me?
Thank for your time, 
Ben

---

### Post by ozorba on 2008-05-13
I hope you have a copy of the old and working fstab file.

Use live CD and mount the disk that has / directory. Then use sudo command to copy the old and working ftab as the new one. Here is the command used in the terminal window.

sudo cp /etc/fstab /etc/fstab.OLD2 ; cp /etc/fstab.OLD /etc/fstab

---

### Post by benjo18 on 2008-05-13
I'm sorry but I'm really new to that stuff; I'll try to be the more concentrate I can: I swear. But I don't understand how I can mount the disk that have /directoty.
When I put boot from the dvd, I just have some options like boot: (some options to put).

Thanks for you help
Ben

---

