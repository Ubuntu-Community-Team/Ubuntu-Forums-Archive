---
title: "Routine Disk Check Fails"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by metasolaris on 2008-10-09
Hi

Each time I fire up ubuntu I am told that a routine disc check is progress. If I leave it, it fails and I get a >. If I esc, I get ubuntu and its working fine except several times recently I have had errors when attempting to download updates - the problem clears up eventually.

I have a amd 4400+ X2 64 running ubuntu hardy on one drive and windows XP on another. Ive had some crashing problems with XP also.

Any help would be great!

Thanks

---

### Post by cmnorton on 2008-10-09
I think you are being asked to run fsck, before the drive is mounted. Offhand, I do not know the syntax you should use at that boot prompt. 

You could try just typing fsck and then answer the prompts yes.

I wouldn't keep using your system if you're getting a check each time and it's failing.

---

### Post by PocketDog on 2008-10-09
It's failing because it runs at boot using user access. If he does what you say and types fsck when it drops to the root prompt instead of rebooting it should sort things out

---

### Post by oldos2er on 2008-10-09
Don't run fsck on a mounted partition. If you have an Ubuntu LiveCD, run it from there.

---

### Post by cmnorton on 2008-10-10
I believe metasolaris is being prompted to recover at the point in the boot before the partition is mounted, and you are absolutely correct not to run fsck on a mounted partition.

---

### Post by philinux on 2008-10-10
> **metasolaris said:**
> Hi

Each time I fire up ubuntu I am told that a routine disc check is progress. If I leave it, it fails and I get a >. If I esc, I get ubuntu and its working fine except several times recently I have had errors when attempting to download updates - the problem clears up eventually.

I have a amd 4400+ X2 64 running ubuntu hardy on one drive and windows XP on another. Ive had some crashing problems with XP also.

Any help would be great!

Thanks

Have a look through your messages log. System>Admin>System Log

It could be the hard drive. Scroll though messages.log and see if there are any read/write errors. 
When it drops you to the command prompt use 
fsck -v
if it asks to repair anything answer Y.
This can also happen if you had a power failure or a hard reboot.

---

### Post by G-Dub on 2008-11-18
i am having this same problem
this is what it records in the log:
```
Log of fsck -C3 -R -A -a 
Tue Nov 18 13:23:55 2008

fsck 1.41.3 (12-Oct-2008)
/dev/sdb1: recovering journal
/dev/sdb1: clean, 117/12214272 files, 8384500/48839600 blocks
fsck.ext3: Unable to resolve 'UUID=23547649-06b5-42cd-b0ae-d7e3d1e2c70b'
fsck died with exit status 8

Tue Nov 18 13:23:56 2008
----------------
```

This has only started after repartitioning my hard drive to make room for xp. On top of that, i cannot access my xp partition through linux.

tried the fsck -v and it gave me this

```
*******@*******:~$ fsck -v
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.

```

---

### Post by cariboo on 2008-11-18
The first thing you should do is run:

```
sudo blkid
```

as the device id of the drive in question is out of date. Then reboot and see if you still get the same message.

If the drive still has a problem, boot up using the LiveCD and run:

```
sudo fsck /dev/sda1
```

from a terminal.

Jim

---

