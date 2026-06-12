---
title: "[SOLVED] Power outage. RAID Lost???"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by talking_walnut on 2008-06-09
Hi,

Set up a RAID0 array a while back (see [here]("http://ubuntuforums.org/showthread.php?t=807962") for the help I got on that). Everything was working fine till one day the power went and the computer went down :( 
When I started up the computer again the RAID didn't wouldn't mount and I got a "mount: wrong fs type, bad option, bad superblock on /dev/md1," error when I tried to do it manually. 

Have I lost all the stuff I had on the discs? I tried stopping the array (mdadm -S) which worked but I don't know what I could do from there to assemble it again :confused: 

Anybody got any ideas??

---

### Post by ukripper on 2008-06-09
> **talking_walnut said:**
> Hi,

Set up a RAID0 array a while back (see [here]("http://ubuntuforums.org/showthread.php?t=807962") for the help I got on that). Everything was working fine till one day the power went and the computer went down :( 
When I started up the computer again the RAID didn't wouldn't mount and I got a "mount: wrong fs type, bad option, bad superblock on /dev/md1," error when I tried to do it manually. 

Have I lost all the stuff I had on the discs? I tried stopping the array (mdadm -S) which worked but I don't know what I could do from there to assemble it again :confused: 

Anybody got any ideas??

use live cd to boot and then do fsck on the drives.

---

### Post by talking_walnut on 2008-06-09
Do I need to use the live cd? I don't think I've any handy and I've no blank cds :p The RAID didn't have the operating system on it. Was just file storage.

When you say "run fsck" do you mean run it on the RAID partition (/dev/mda1) or on the actual drives (/dev/sdc  /dev/sdb)? 

Sorry if these are stupid questions. Never worked with this kind of thing before.

---

### Post by ukripper on 2008-06-09
> **talking_walnut said:**
> Do I need to use the live cd? I don't think I've any handy and I've no blank cds :p The RAID didn't have the operating system on it. Was just file storage.

When you say "run fsck" do you mean run it on the RAID partition (/dev/mda1) or on the actual drives (/dev/sdc  /dev/sdb)? 

Sorry if these are stupid questions. Never worked with this kind of thing before.

i would do it for partitions and use live cd as it is not recommended to run fsck on the mounted partition you are currently working on. use recovery mode to do fsck for other partions except the one you working on.

---

### Post by talking_walnut on 2008-06-11
Sorry for the delay in getting back but had some other stuff to deal with. 

I booted to the Live CD and tried running fsck, but each time I tried I got "fsck.mdraid: not found" and the program fails. I've tried to fsck.mdraid but I can't find it. Anyone know what's wrong?

---

### Post by alienexplorers on 2008-06-11
I thought raid was a redundant system.  Are you sure your raid controller did not take a hit.

---

### Post by talking_walnut on 2008-06-11
It's software RAID0 so there's no redundancy and no controller :)

---

### Post by ukripper on 2008-06-11
> **talking_walnut said:**
> Sorry for the delay in getting back but had some other stuff to deal with. 

I booted to the Live CD and tried running fsck, but each time I tried I got "fsck.mdraid: not found" and the program fails. I've tried to fsck.mdraid but I can't find it. Anyone know what's wrong?

did you try ```
fsck /dev/mda1
```?

---

### Post by talking_walnut on 2008-06-11
Got it!!!

/dev/md1 had disappeared because I had stopped the RAID but restarting (and messing about with the boot cd) made it reappear. Then I ran 

```
sudo fsck /dev/md1
```

and it fixed it. Thanks for taking the time to help guys!

---

### Post by ukripper on 2008-06-12
> **talking_walnut said:**
> Got it!!!

/dev/md1 had disappeared because I had stopped the RAID but restarting (and messing about with the boot cd) made it reappear. Then I ran 

```
sudo fsck /dev/md1
```

and it fixed it. Thanks for taking the time to help guys!

Great. Could you mark this thread as solve in your title, users looking for answers may spot that?

cheers.
ukripper

---

### Post by greco8523 on 2008-08-03
I know this problem has been solved but I thought I would post some advice for anyone else that has lost there RAID. 

If your RAID does fail and the data is so important that you can't live without it. The first thing is to take images of the drives and keep them in a safe place. Therefore any strange configurations that you do to try and get the RAID back won't make things worst. 

If the testing of different configuration doesn't work. You can try getting the data back with Data recovery Software and mouting the images. The link below goes through some general data recovery tips and hints:

[http://www.datarecoveryadvice.org/](http://www.datarecoveryadvice.org/)

---

