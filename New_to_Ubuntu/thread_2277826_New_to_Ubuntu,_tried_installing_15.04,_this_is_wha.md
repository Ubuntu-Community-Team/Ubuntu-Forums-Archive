---
title: "New to Ubuntu, tried installing 15.04, this is what shows up"
date: 2015-05-11
forum: New to Ubuntu
---

### Post by nicomigs on 2015-05-11
I don't have much experience in linux distros and I tried installing ubuntu 15.04 through virtualbox and this is what shows up after installing and restarting the machine[ATTACH=CONFIG]261948[/ATTACH]

---

### Post by ian-weisser on 2015-05-11
Looks like it's trying to read a corrupt install media.
Does not look like a successful install. A successful install should not be trying to read the install media at all (the install media should be ejected anyway).
Verify the integrity of the install media, then try installing again.

---

### Post by mastablasta on 2015-05-12
re-download the ISO image. make sure md5 sums match.

how to do a md5sum check : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
note if you use torrent download the check is done during download.

Install procedure in v box (a bit old but still valid) : [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by newb85 on 2015-05-12
If you're re-downloading, you might consider going with 14.04 instead of 15.04 for its Long Term Support.  I don't know how you plan to use it, but if you use 15.04, you'll need to upgrade to 15.10 between October '15 and January '16.  Non-LTS releases are only supported for 9 months.  LTS releases like 14.04 are supported for 5 years, which means you wouldn't have to upgrade until April '19.  (Unless you're on Lubuntu, where LTS is 3 years.)

---

### Post by buzzingrobot on 2015-05-12
"dev/sr0" is the CD/DVD drive. "Squash_fs" is the compact file system used in install images. The errors were generated when problems occurred trying to read the drive.  But, after an install is completed, the install image (the DVD in this case) should be removed and the BIOS adjusted, if necessary, to boot from the actual install target drive.

If those message were produce trying to boot the install image, then, as mentioned, it's a bad image, a bad DVD, a bad drive, or all three.

If produced booting the VM, I'd guess the VM is broken.

---

### Post by suung-jo on 2015-05-13
How about trying to use the ubuntu under the "Try UBUNTU" menu before installing.

---

