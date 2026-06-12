---
title: "Hitachi 7K200 External hdd won't mount!"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by TM1990 on 2012-05-15
[U]Ubuntu beginner; 
[/U]I realize that there are about a million threads about external hdd's but I've done all I can at this stage and I'm close to admitting defeat.. 
I'm running Ubuntu 10.04 on my factory Lenovo Thinkpad T61p. I just got a new hdd & am trying to use the old 100GB Hitachi  7K200-100 as an external drive. If it matters, the enclosure I'm using is the Vantec NexStar3. 
The problem is that the Hitachi hdd doesn't mount when installed in the enclosure, but does when its installed directly in the laptop. I don't think the problem is with the enclosure because I am able to mount and boot off my other hdd when it is installed in it. 
I've tried reformatting the Hitachi drive multiple times in FAT, NTFS & Ext4 but it doesn't make a difference when I put it back in the enclosure.
I am able to install and run the Ubuntu operating system on the Hitachi hdd as long as its inside the laptop.
Is there something simple I'm overlooking like could the hdd be locked or something? or is it just time to toss it at a wall?

I've attached the results of the terminal commands I've exhausted so far.
Any help would be awesome!
Cheers in advance.

---

### Post by rai4shu2 on 2012-05-15
I'd say the problem is something to do with the kernel driver:

```
[  210.596560] sd 5:0:0:0: [sdb] Unhandled sense code
[  210.596564] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  210.596569] sd 5:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  210.596574] sd 5:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  210.596580] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  210.596591] end_request: I/O error, dev sdb, sector 0
[  210.596595] __ratelimit: 126 callbacks suppressed
[  210.596598] Buffer I/O error on device sdb, logical block 0
[  210.598181] sd 5:0:0:0: [sdb] Unhandled sense code
[  210.598185] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  210.598190] sd 5:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  210.598196] sd 5:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  210.598201] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  210.598215] end_request: I/O error, dev sdb, sector 0
```

EDIT: I don't see any similar reports, so the thing to do is go here: [https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

---

### Post by TM1990 on 2012-05-16
Ok it turns out the laptop (Lenovo Thinkpad T61p) has a TPM 1.2 security chip & the hitachi hdd came encrypted. So I've been told that the drive won't work unless its plugged into the laptop. 
I dont know the key so I'm abandoning this one... not worth the effort for 100GB.
If someone has a better explanation than the security chip/ hdd encryption I'd be happy to give it a go but for now Im happy with this explanation.

---

### Post by rai4shu2 on 2012-05-16
Okay, so you can format the drive in your computer (unencrypted) and that should solve the issue with the enclosure, right?

---

### Post by TM1990 on 2012-05-17
No because the chip automatically encrypts it during the reformat.

"A password-locked HDD can be made useful again by using a low-level  utility capable of issuing the SECURE-ERASE command to it.  You will  lose all data, but at least the HDD will be usable again, as that also  unlocks the HDD."

[http://www.thinkwiki.org/wiki/Embedded_Security_Subsystem](http://www.thinkwiki.org/wiki/Embedded_Security_Subsystem)

---

