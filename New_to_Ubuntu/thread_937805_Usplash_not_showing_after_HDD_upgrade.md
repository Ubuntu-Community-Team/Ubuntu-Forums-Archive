---
title: "Usplash not showing after HDD upgrade"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by shafin on 2008-10-04
Hi,
I migrated my ubuntu partition to a new HDD and everything works fine. But there is one minor nuance. The Usplash is not showing. It shows for a second or so and then I get the blinking cursor until the login screen arrives. It doesn't harm anyone, but it certainly makes ubuntu look dull. How can I get it working again?
Thanks for helping

---

### Post by houbysoft.xf.cz on 2008-10-04
Hi, do you have Ubuntu Hardy Heron? Because this occured to me too, but when I updated to Heron, it worked just fine.

---

### Post by kansasnoob on 2008-10-04
I'll bet it's a uuid thing. Also check and see if swap is staying "swapon" after a restart (you can install gparted from synaptic and then just look at the gparted gui to see - or to change from "swapon" to "swapoff" or vice versa).

Read **all** of Coffeecat's posts here:

[http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

(That should be condensed into a "sticky" tutorial)

---

### Post by shafin on 2008-10-04
> **kansasnoob said:**
> I'll bet it's a uuid thing. Also check and see if swap is staying "swapon" after a restart (you can install gparted from synaptic and then just look at the gparted gui to see - or to change from "swapon" to "swapoff" or vice versa).

Read **all** of Coffeecat's posts here:

[http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

(That should be condensed into a "sticky" tutorial)
Thanks a lot for the link. My problem is,SWAP is not turned ON by default. The two uuids at **/etc/initramfs-tools/conf.d/resume** and **/etc/fstab** match, but running **sudo blkid -c /dev/null**
 gives no uuid for my swap partition, it says plain** /dev/sda7: TYPE="swap" **and nothing else

---

### Post by shafin on 2008-10-04
I took some help from [this]("http://ubuntuforums.org/showthread.php?t=880108") thread, and it gave me a new swap uuid. Entered in in fstab and resume, I'm rebooting to see if it works, will report if it does.:)

**Update**: Part of it worked, now my swap partition is working, but the usplash problem is still there.

Please help.

---

