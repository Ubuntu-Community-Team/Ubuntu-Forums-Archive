---
title: "[SOLVED] Partitioning the /home directory on a fresh install (not looking for a how-t"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by rideburton56 on 2008-11-01
I am planning on doing a fresh install of 8.10, and it seems like there are a lot of benefits to doing a separate partition of the home directory.  I know that there are a multitude of howtos on the subject.  I am just curious if it is a good decision based on my hardware.  Right now, my home folder is about 2.8 gb, and i believe i have ~28 gb free.  Will seperate partitions put additional stress on my already dated HD, and slow down my system?  For someone who plans on doing fresh installs for all new verisions, is it worth it?

---

### Post by PoopyTheJ on 2008-11-01
I've run a separate home partition for a while now and never had a problem, through 710 to 8.10 and reinstalls in-between. The first time I reinstalled and found my background wallpaper the same as before the reinstall I wasn't sure if the OS actually re-installed! Having seperate partitions should not slow down or otherwise tax your harddrive any more than a single partition, AFAIK it may help with performance a bit as it gives it a better structure for finding files and such. For my two cents it's definitely worth it as I've done my reinstalls without worrying about data loss and can get to my files right after a reinstall unlike when I was using Windows.

---

### Post by rideburton56 on 2008-11-01
Great, thanks!  Does anyone have any input on how I should allocate my harddrive?  for example, would 10gb be enough for the ubuntu main partition (the non home partition)?

---

### Post by RequinB4 on 2008-11-01
> **rideburton56 said:**
> Great, thanks!  Does anyone have any input on how I should allocate my harddrive?  for example, would 10gb be enough for the ubuntu main partition (the non home partition)?

Yep, 10GB is perfect for / minus /home

---

### Post by Idefix82 on 2008-11-01
10 GB for your / partition should do. If you want to minimise the risk of the main partition getting cluttered up and halting your system, you could allocate, say, 1GB to /tmp and 2GB to /var. This way your system will not be hampered by old log files and/or Synaptic temporary data.

Actually, since I am guessing that with a small HD you will not use your computer as the main storage for music and pictures, your /home partition probably needn't be overly big either. So I would probably do something like
/ 10GB
/tmp 1GB
/var 2GB
/SWAP 1-2GB depending on your RAM and needs
/home everything else

---

### Post by rideburton56 on 2008-11-02
Thanks for the replies everyone, I am sure I will be back when I take on the task of partitioning my home directory

---

