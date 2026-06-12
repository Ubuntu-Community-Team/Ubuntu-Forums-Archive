---
title: "No Matching Swap Device Is Available"
date: 2019-05-18
forum: New to Ubuntu
---

### Post by a7madfayed on 2019-05-18
> **Rick St. George said:**
> YES ... somehow it was not correct. So corrected it, rebooted, and have not seen the error.
Thanks!

Could you, kindly, make it more simple for me as a beginner because I'm facing the same issue.
Thanks in advance.

---

### Post by #&amp;thj^% on 2019-05-18
> **a7madfayed said:**
> Could you, kindly, make it more simple for me as a beginner because I'm facing the same issue.
Thanks in advance.

Please start your own thread as this is Solved, and may not relate to your problem.
Also in the meantime have a look here: [https://askubuntu.com/questions/1060917/swap-from-partition-to-file-now-get-no-matching-swap-device-is-available](https://askubuntu.com/questions/1060917/swap-from-partition-to-file-now-get-no-matching-swap-device-is-available)
And one other for your reading pleasure: [https://ubuntuforums.org/showthread.php?t=2401012](https://ubuntuforums.org/showthread.php?t=2401012)

---

### Post by a7madfayed on 2019-05-18
Thanks alot.
Sorry for inconvenience.

---

### Post by DuckHook on 2019-05-18
*Post moved to its own thread in **New to Ubuntu** with a new and more appropriate title.*

Please do not hijack threads. Although a problem may seem similar, it may be due to entirely different causes. The OP deserves a properly focused solution as do you. Describe your problem fully and in detail here.

---

### Post by a7madfayed on 2019-05-18
Thanks a lot & Sorry for inconvenience.

Now, It appeared that because of encrypting swap, I have 2 swap partitions, and my cryptswap partition UUID keeps changing.
and, back again to "What to do ?!" point.
> sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.130ubuntu3.7) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.130ubuntu3.7) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-50-generic
blkid: -t needs NAME=value pair
Try 'blkid --help' for more information.
W: initramfs-tools configuration sets RESUME=UUID=
W: but no matching swap device is available.

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.15.0-50-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by dino99 on 2019-05-19
Default installation nowadays is quite different of yours:
[http://linuxbsdos.com/2017/04/18/swap-partition-out-swap-file-in-on-ubuntu-17-04/](http://linuxbsdos.com/2017/04/18/swap-partition-out-swap-file-in-on-ubuntu-17-04/)

Have you set a custom install ? and how ? Is your whole device (hdd/ssd) encrypted, or simply some partitions ?

---

