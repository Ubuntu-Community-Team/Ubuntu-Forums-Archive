---
title: "Any extra partitions which would speed up boot and overall performance?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by nkri on 2008-10-07
Hey, guys...

Ubuntu runs fast right now, but I want it to run faster!  I'm planning on doing a clean install when the final release of Intrepid comes out, and I've got a 5.21GB partition waiting to be used as /home and anything else necessary (right now, my Home Folder takes up a grand total of 300MB, so I'll have plenty of space for other partitions).  I want to know if there are any folders which would make the system boot or run faster if used as partition, or have any real importance as a partition instead of a regular system folder in /.

I've heard people suggest /usr, /var, and /boot, but don't know exactly why.

Thanks!
-nkri

---

### Post by talsemgeest on 2008-10-07
If you can make the partition on a separate hard drive, then it might speed it up, as it can access the files it needs to boot simultaneously. But I cant see any way that having a separate partition on the same hard drive could help out. In fact, I think it could eve degrade performance, as the read/write heads have to move to separate sections of the disk to access the files it needs.

---

### Post by nkri on 2008-10-08
Thanks, that helped a lot:)

btw, to what file system should I format?  ext2 or ext3?  Any advantages to either of them?

Thanks!
-nkri

---

### Post by handydan918 on 2008-10-08
> **nkri said:**
> Thanks, that helped a lot:)

btw, to what file system should I format?  ext2 or ext3?  Any advantages to either of them?

Thanks!
-nkri

ext3 is essentially a journalised version of ext2, so it will recover much more gracefully from unclean shutdowns, etc. You may take a slight performance hit using ext3 over ext2, but it is really the gold standard of file systems for Linux at the moment.

---

### Post by Paqman on 2008-10-08
Mounting different parts of the OS on separate partitions won't really improve your boot times. However, there is some worked roadmapped in for Ubuntu 9.04 on improving boot times. So basically sit tight for six months and you should see some improvement.

---

### Post by Archmage on 2008-10-08
Keep in mind that a swap-partition might speed up things.

---

### Post by PierreDeKat on 2008-10-08
Depending on how much hard drive you have, I would strongly caution against a 5GB /home/ partition. That's what I have n0w, and it only took  me a few days to see how much trouble it is.

Do you want to copy a CD or DVD by dropping an ISO someplace? You won't be able to put it in your /home/ folder or drop it on your desktop or anything. You'll have to drop it in your /tmp/ directory or on some other partition that you have read/write privileges for.

I'm going to be doing a fresh install when Intrepid's ready, and I'll either be setting up a 20 GB /home/ directory or one that allows me grow up to 20 GB if I want to.

---

### Post by talsemgeest on 2008-10-08
But that still depends on how much space you use. I couldnt live without at least 100GB for a home partition, but some could be running along nicely on a 1GB...

---

### Post by nkri on 2008-10-08
> **talsemgeest said:**
> But that still depends on how much space you use. I couldnt live without at least 100GB for a home partition, but some could be running along nicely on a 1GB...

Agreed...I've only used about 300MB in my home folder and have been using Ubuntu for six months.  I keep all of my pictures, music, and videos on a 500GB external hard drive, backed up to a 250GB drive.  I do a lot more work in the system folders than in my home folder (I install and use *a lot* of software), so 5GB is more than enough:)  Besides, I have limited space (100GB internal drive; 41GB Ubuntu, 
44GB Windows, 2GB swap, and 5GB Windows recovery to be used as /home) and the partition is already there, so why not use it?

Thanks!
-nkri

---

