---
title: "Ubuntu 8.04 installation.."
date: 2008-07-21
forum: New to Ubuntu
---

### Post by Techpenguin on 2008-07-21
Every time I attempt to boot from the live cd, (I click try without installing) I end up at the debian BusyBox.
if this is a feature, how do I get around it so ubuntu actually boots?

---

### Post by Xerp on 2008-07-21
First, I'd verify the CD checksum:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by kk0sse54 on 2008-07-21
When the boot menu comes up you can also choose to check it's integrity there too and if it has been corrupted try burning the livecd at a lower speed.

---

### Post by Techpenguin on 2008-07-21
Thanks, xerp i'll try that and c!oud I have already checked, it's fine.

---

### Post by Techpenguin on 2008-07-21
xerp is what I am supposed to check right at the beginning of the md5sum file?
because in that case it is very wrong

---

### Post by Xerp on 2008-07-21
The hashes are here:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

You probably need to get:

c69e34e92d5402d1b87e6babc739f774
	
(ubuntu-8.04.1-desktop-i386.iso)

---

### Post by Techpenguin on 2008-07-21
yeah I saw that and thats not what I have. do I replace it?

---

### Post by Xerp on 2008-07-21
If when you MD5SUM your CD it doesn't match up, then you have a bad burn. You may even need to redownload the ISO.

---

### Post by Techpenguin on 2008-07-21
k thanx

---

