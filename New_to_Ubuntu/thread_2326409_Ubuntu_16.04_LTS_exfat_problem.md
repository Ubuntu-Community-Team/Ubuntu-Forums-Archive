---
title: "Ubuntu 16.04 LTS exfat problem"
date: 2016-05-31
forum: New to Ubuntu
---

### Post by ezile.nomkuca on 2016-05-31
Hi people

Ive recently installed Ubuntu and Im having a great time with this OS. I installed exfat-fuse and exfat-utils because I was reading an exfat formatted drive and it worked well. Now Ive developed a problem, The drive cant be read or mounted anymore. It gives me this error whenever I try to open the drive.

```
Error mounting /dev/sdb1 at /media/big-zee/SUSPECT: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/big-zee/SUSPECT"' exited with non-zero exit status 1:
stdout: `FUSE exfat 1.2.3
'
stderr: `ERROR: 'SHOGUS_BUZZ TRACK_S015 + 052_EXT_DAY_T001.MOV' has invalid checksum (0x7871 != 0x7579).
'
```
Any assistance is greatly appreciated.

---

### Post by X-RED_Tech on 2016-06-01
If you have some recent Windows available try using the drive with it. It should inform about (logical) errors and offer to correct them.

---

### Post by HermanAB on 2016-06-03
I can't figure why you needed special software to handle exfat in the first place.  Exfat utils should be installed by default.

---

### Post by X-RED_Tech on 2016-06-03
exFAT is proprietary. -> [https://en.wikipedia.org/wiki/ExFAT](https://en.wikipedia.org/wiki/ExFAT)
Perhaps it explains why it isn't shipped by default? Although the same could be argued for NTFS and that has native support for some time now. The fact is up to this day Ubuntu ships without OOTB support for exFAT, hence the need to install the utils.

---

### Post by izznogooood on 2016-06-04
Try removing [COLOR=#000000]exfat-fuse, exfat-utils should be all you need....[/COLOR]

---

### Post by Bucky Ball on 2016-06-04
> **izznogooood said:**
> Try removing [COLOR=#000000]exfat-fuse, exfat-utils should be all you need....[/COLOR]

Removing them? Those are the two things you need for exfat and things were working fine using them. :-k

---

### Post by izznogooood on 2016-06-04
No, just exfat-fuse! I have only ever needed exfat-utils...

---

### Post by Morbius1 on 2016-06-04
Anyone think that maybe the disk just went bad ?

Besides, exfat-fuse is a depenancy of exfat-utils:
> tester@vub1604:~$ sudo apt-get install exfat-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  exfat-fuse
The following NEW packages will be installed:
  exfat-fuse exfat-utils


---

### Post by X-RED_Tech on 2016-06-04
> **Morbius1 said:**
> Anyone think that maybe the disk just went bad ?

Yes, I do, from the start, but decided to wait until more data is provided namely how does it work in other PCs???
And, back to the post #2... To the OP: Have you done that already? Can't/won't? If so why? It should be easy to find someone with a Windows PC among family, friends, co-workers, etc. that you can borrow for 2 minutes... Yes, that's all you need to test and correct any eventual (logical) errors it may have. You can't correct those errors from a Linux system, I think, much like what happens with a NTFS drive. Also nothing can repair physical errors.

It's a waste of time installing/removing this and that if the drive is bad already.

---

### Post by Bucky Ball on 2016-06-05
> **Morbius1 said:**
> Anyone think that maybe the disk just went bad ?

Yes. It's quite possible as this was working fine then it wasn't. Can't see it would have anything to do with exfat-utils or exfat-fuse in any case.

---

