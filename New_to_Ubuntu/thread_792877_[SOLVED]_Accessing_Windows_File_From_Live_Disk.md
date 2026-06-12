---
title: "[SOLVED] Accessing Windows File From Live Disk"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Henrywantstobeapenguin on 2008-05-13
Hello there, 

My friends windows has broken(suprise) so I suggested he used my live disk, which he likes. Now we want to back up his personal data and install Ubuntu Properly.

He can access his external hardrive from Ubuntu, but cannot access his main windows drive. I have looked at this thread: - 

[http://ubuntuforums.org/showthread.php?t=791695&highlight=take+my+windows+files+off](http://ubuntuforums.org/showthread.php?t=791695&highlight=take+my+windows+files+off)

We tried using the terminal to input


sudo mkdir /mnt/windows, which was accepted

then
sudo mount -t ntfs /dev/hda1 /mnt/windows which said it can't access /dev/hda1 etc: no such file or directory. 

When we attempt to click on the drive we get the following error message: - 

$LogFile indicates unclean shutdown (0,0) Failed to mount 'dev/sda2' Operation not supported Mount is denied because Ntfs is marked to be in use. Choose one action: Choice one: If you have windows the disconnect the external drive then shut down windows cleanly (can't do this as windows is broken). Choice 2: Use the force option, but we don't know how to do this and it seems risky as we are trying to back up! 

Many thanks for any help, apologies if anything is unclear - will be checking frequently.

Best, Henry

---

### Post by Monicker on 2008-05-13
How badly is Windows broken?  Can you boot it into safe mode and then shut it right back down?  Or you might try the Recovery Console if you have the Windows CD.

---

### Post by Henrywantstobeapenguin on 2008-05-13
Thanks for replying, yeah - we have tried all the safe mode options for boot and its impossible to get to a windows screen. The diagnostics's test won't finish and says that there are several unrecoverable errors.

Unfortunately he has lost his recovery CD... (doh!) 

Thanks again,

Henry

---

### Post by tszanon on 2008-05-13
> **Henrywantstobeapenguin said:**
> sudo mount -t ntfs /dev/hda1 /mnt/windows which said it can't access /dev/hda1 etc: no such file or directory.

Henry, this may be happening because all drives in the computer are referenced as sd[x] (sda, sdb, sdc...)
So, the first hard drive should be sda, and its first partition should be sda1.

I suppose your external drive is referenced as sdb. So, this should work:

```
sudo su
mkdir /media/hd
mount /dev/sda1 /media/hd
```

If the external drive is not mounted automatically, do this too:
```
mkdir /media/external
mount /dev/sdb1 /media/external
```

Then just copy the wanted files from /media/hd to /media/external.

I didn't understand the second error message (that $LogFile thing). Where does sda2 come from? I didn't see it anywhere in the process you described.

---

### Post by bodhi.zazen on 2008-05-13
That error message also gives the answer, if you speak geek

First it appears your windows drive is sda2 (not sda1)

You can list your partitions with ```
sudo fdisk -l
```Second, looks like you need to force the mount.

```
sudo mount /dev/sda2 /media/windows -o force
```The mount will be ro, access the files with ```
gksu nautilus /media/windows
```

---

### Post by Henrywantstobeapenguin on 2008-05-13
Dear Bodi.hazen and tszanon

Many thanks for your help! It is working now, although I can't say which fix worked I'm afraid.  We did this first

sudo mout /dev/sda2 /media/windows -o force, which removed the drive mounting (I think)

then 

gksu nautilus /media/windows but that didn't seem to work and said that /media/windows wasn't valid or something.

Finally we did

sudo su
mkdir /media/hd
mount /dev/sda1 /media/hd

Which ran succesfully, but didn't tell us anything. After this we  accessed the drive via the file manager and are copying my documents to an external hardrive as we speak! Now we can install it properly and my friend will have a functioning PC for his finals.

Thanks so much.

Henry

---

