---
title: "Can you check MD5 sum from extracted .iso (now a CDFS)?"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by decktrio on 2012-05-24
Is it possible to check the MD5 sum of an .iso that has already been extracted and burned onto a cd (a .cdfs)?

---

### Post by oklokl on 2012-05-24
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://ubuntuforums.org/showthread.php?t=1941596](http://ubuntuforums.org/showthread.php?t=1941596)


md5sum /dev/cdrom

cd ~/Downloads

echo "" > test.txt
md5sum *.iso >> test.txt
sha1sum *.iso >> test.txt
sha224sum *.iso >> test.txt

sha256sum *.iso >> test.txt
sha384sum *.iso >> test.txt
sha512sum *.iso >> test.txt


# view
cat test.txt

---

### Post by Paqman on 2012-05-24
> **decktrio said:**
> Is it possible to check the MD5 sum of an .iso that has already been extracted and burned onto a cd (a .cdfs)?

Not if the checksum you have is for the original ISO, no. Making any changes to a file (such as extracting it) will change the checksum value. Even changing a single bit out of megabytes of data will change the checksum, that's sort of the whole point of checksums.

---

### Post by bodhi.zazen on 2012-05-24
> **decktrio said:**
> Is it possible to check the MD5 sum of an .iso that has already been extracted and burned onto a cd (a .cdfs)?

You do not extract an iso. You burn the iso to a CD or put it onto a flash drive.

[https://help.ubuntu.com/community/CdDvd/Burning](https://help.ubuntu.com/community/CdDvd/Burning)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

---

