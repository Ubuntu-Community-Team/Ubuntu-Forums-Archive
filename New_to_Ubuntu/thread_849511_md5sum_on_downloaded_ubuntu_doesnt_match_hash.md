---
title: "md5sum on downloaded ubuntu doesnt match hash"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by woodley42 on 2008-07-04
Hi
ive just downloaded ubuntu and the winMd5sum program but the mD5 sum (c69e34e92d5402d1b87e6babc739f774) that is found when i scan the file i burnt to disc does not match any hash that i could find on here: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Does anyone know why this is and what i can do about it?  Was it somehow corrupted during download?  All recommendations should be made in simpleton talk as im very new to this and am just about coping using all the read me guides.

Thanks
P (UK)

---

### Post by Elfy on 2008-07-04
If it doesn't match then simply you will need to download it again. Maybe use the torrent if you have a client - you can get the torrent from here

[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

---

### Post by drs305 on 2008-07-04
> **woodley42 said:**
> Hi
ive just downloaded ubuntu and the winMd5sum program but the mD5 sum (c69e34e92d5402d1b87e6babc739f774) that is found when i scan the file i burnt to disc does not match any hash that i could find on here: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Does anyone know why this is and what i can do about it?  Was it somehow corrupted during download?  All recommendations should be made in simpleton talk as im very new to this and am just about coping using all the read me guides.

Thanks
P (UK)

I don't think they have the hash for the latest iso posted yet. The one listed on the page you mentioned is for hardy 8.04 and the latest iso is probably for 8.04.1  Check your filename. If it contains "8.04.1" that is probably the reason the md5sum isn't working.

---

### Post by woodley42 on 2008-07-04
thanks i'll try again

---

### Post by woodley42 on 2008-07-04
HI drs
i just checked it and you're right it's 8.04.1


What should i do now? Wait for the new hash to come out?

Thanks

---

### Post by Elfy on 2008-07-04
> **drs305 said:**
> I don't think they have the hash for the latest iso posted yet. The one listed on the page you mentioned is for hardy 8.04 and the latest iso is probably for 8.04.1  Check your filename. If it contains "8.04.1" that is probably the reason the md5sum isn't working.

catch :)

---

### Post by Otto-C on 2008-07-04
I just downloaded 8.04.1 and did a md5sum and my result matches yours.

c69e34e92d5402d1b87e6babc739f774  ubuntu-8.04.1-desktop-i386.iso

I am now proceeding as valid.

otto-c

---

### Post by drs305 on 2008-07-05
> **Otto-C said:**
> I just downloaded 8.04.1 and did a md5sum and my result matches yours.

c69e34e92d5402d1b87e6babc739f774  ubuntu-8.04.1-desktop-i386.iso

I am now proceeding as valid.

otto-c

That's the same as I have.

For the 64-bit AMD LiveCD, my md5sum:
b78ef719e3361e726b89bab78c526ad0

---

### Post by hyper_ch on 2008-07-05
use torrent to download it... it will auto-check integrity.

---

### Post by plucky on 2008-07-05
From [Releases.Ubuntu.com](http://releases.ubuntu.com/8.04/MD5SUMS)

> 38e3f4d0774a143bd24f1f2e42e80d63 *ubuntu-8.04.1-alternate-amd64.iso
bbd21ded02c06b41c59485266833937a *ubuntu-8.04.1-alternate-i386.iso
b78ef719e3361e726b89bab78c526ad0 *ubuntu-8.04.1-desktop-amd64.iso
c69e34e92d5402d1b87e6babc739f774 *ubuntu-8.04.1-desktop-i386.iso
e7351d79903588699a383ae77854f734 *ubuntu-8.04.1-server-amd64.iso
7232c6004ba438890cd09aded162dc8e *ubuntu-8.04.1-server-i386.iso


Looks Good

---

