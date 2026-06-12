---
title: "HowToMD5SUM"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by paulmagarey on 2011-12-26
Recently in checking if my downloaded version of 10.04 was OK, I conducted a MD5Sum check on the iso file in my Downloads folder according to guidelines found at [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM). The MD5Sum for my iso file happily matched the one found at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes).

The guideline page ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)) also that the command:

md5sum /dev/cdrom

"will almost NEVER" produce the "same hash as the iso image that was  burned to the disk, because this command includes the empty space at the  end of the disk, which changes the hash. So you must check 
*only* the part of the disk that was on the iso."

However, twice recently, once with my the Ubuntu 10.04 CD that I burnt and also with a Linux Mint 12 disk that I burnt (the installation of which didn't seem to work), I've found that md5sum /dev/cdrom did produce exactly the same MD5Sum as both the ISO file and the Ubuntu Hashes page. 

I'm wondering if I've done something wrong or if the advice at [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) needs to be updated.

Any advice would be appreciated.

Paul

---

### Post by wolfen69 on 2011-12-26
I just do
```
md5sum ubuntu.iso
```
and have the original md5 opened on the web page or whatever. In a quick glance, you can just compare the first few numbers. If those are correct, you can be assured it is OK. Then just verify (in the burning app) after burning. Never had a problem this way.

---

### Post by lolpenguin on 2011-12-26
Or boot into the Live image if you've already burned it, and in the boot menu (of the CD/DVD/USB) and select "Check installation medium" or something similar.

---

### Post by bodhi.zazen on 2011-12-27
> **paulmagarey said:**
> I'm wondering if I've done something wrong or if the advice at [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) needs to be updated.

Any advice would be appreciated.

Paul

The advice on [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) is wrong, md5sum /dev/cdrom should give you the same result as the md5sum ubuntu-desktop.iso

---

### Post by paulmagarey on 2011-12-27
> **bodhi.zazen said:**
> The advice on [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) is wrong, md5sum /dev/cdrom should give you the same result as the md5sum ubuntu-desktop.iso

Thanks.

---

