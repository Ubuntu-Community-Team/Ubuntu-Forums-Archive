---
title: "DVD drive won't detect Live CD for Ubuntu 11.10"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by ryan4 on 2013-08-03
I installed 12.04 LTS but the kernel gave my computer problems, and I couldn't get the downgrade to work either. I need to install a version with kernel 3.2 or lower, so I decided to install "[PC (Intel x86) desktop CD]("http://old-releases.ubuntu.com/releases/oneiric/ubuntu-11.10-desktop-i386.iso")" only my DVD drive doesn't detect the CD. I have no problems with the DVD drive detecting 12.04. What is going on here?

---

### Post by ryan4 on 2013-08-03
Will 11.10 CD not work because of UEFI? Is that it?

---

### Post by Vladlenin5000 on 2013-08-03
Probably not UEFI related... What's your PC/laptop?

---

### Post by ryan4 on 2013-08-03
I have an ASUS X75A.

---

### Post by Vladlenin5000 on 2013-08-03
I can't find a single reason to use an older version in such hardware. If not the latest LTS I would use the newer 13.04, never older versions. What exactly were the problems that you think had to do with the kernel?

---

### Post by Chris of Arabia on 2013-08-04
I've had similar problems with both 12.04 and 13.04 when the iso was burnt to a CD about a week back. Eventually, I burnt the iso to a USB using the LiLi USB Creator, and had no problems at all booting into those - might be worth giving that a go instead.

---

### Post by ryan4 on 2013-08-04
The drivers for my wireless, Ralink RT3290,  will not work unless I am running kernel 3.2 or earlier, according to this fix:
[http://ubuntuforums.org/showthread.php?t=2104690](http://ubuntuforums.org/showthread.php?t=2104690)

Is there a fix to get it to work with the newer kernel?

---

### Post by 5l4y3r on 2013-08-04
Check the md5 of the ISO you've downloaded. If it shows any errors you'll have to download 11.10 again and check the md5 before burning it to a CD.

---

### Post by Chris of Arabia on 2013-08-04
Would a small USB wireless adaptor get you round the issue, by requiring different drivers? It may not be the most elegant solution, but it may turn out better value than the alternative.

---

### Post by sandyd on 2013-08-04
Ive found that even the cheap ~$10 ebay adaptors work under linux - just check the chipset to make sure they are compatible

---

