---
title: "Should I Dual Boot Ubuntu and Windows 7"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by ads2996 on 2012-06-05
Hi

I have a Ubuntu 10.04 Server running at home. I was considering dual booting my laptop with Windows 7 (currently Installed) and Ubuntu 12.04 LTS. The probelm I have is that my 320gb hdd has 3 partations. Windows 7 80gb, window system 200mb and a data partition of 219gb. I had previously tried installing a release of Ubuntu along side windows. Though it just crashed and failed. The next problem is that my laptop is touchscreen and i also need windows 7 so i can run visual studio and i need it for school work. Also for looking after my backup server of VHS V1.

I would also like an alternative boot loader to windows

My laptop is the HP touch smart Tm2 1010ea

Thanks in advance.

---

### Post by Mark Phelps on 2012-06-05
IF your laptop came preinstalled with Win7, there is most likely ANOTHER partition you missed -- a Recovery partition containing a compressed OEM image of Win7 that can be used to restore your PC to factory condition.

If that is the case, then you already have the 4 partition limit -- and while you CAN force the Win7 Disk Management tool to create a fifth partition, doing so will then convert all your partitions to Dynamic Disks -- something that Linux OSs can not handle.

You would have to verify that you do NOT already have 4 partitions before any more work can be done regarding dual-boot.

And, do NOT be tempted to boot from the Ubuntu CD/USB and use the option to install side-by-side using a Slider.  Doing that risks corrupting your Win7 and rendering it unbootable.

---

### Post by ads2996 on 2012-06-05
My laptop did come shipped with a recovery partation. But after my first failed attempt to install ubuntu the recovery disks didin't work so i completely reinstalled windows removing the recovery partation and splitting it into sysyem and data and the forced system partation.

---

### Post by Paqman on 2012-06-05
OK, if you've definitely only got 3 partitions then you can put Ubuntu inside an extended partition. You can then put both of Ubuntu's partitions (root and swap) inside that.

---

### Post by ads2996 on 2012-06-05
do you have any suggestions on how to go about this. Would G parted be a good tool to manage the partations

---

### Post by zombifier25 on 2012-06-05
GParted is definitely good. It's included in Ubuntu's LiveCD (if my memory is correct) Create an extended partition, then you can have Ubuntu's installer create partitions and swap inside it.

---

### Post by ads2996 on 2012-06-05
Thank you very much for your help in this matter. I'll let you know how it get on

---

### Post by ads2996 on 2012-06-05
Got windows and Ubuntu to dual boot with the swap and root partitions in an extended partitions. Is 8gb swap enough or too much

---

### Post by zombifier25 on 2012-06-06
I don't know about your RAM, but 8 GB may be a little too much. Generally, swap should be half the size of your RAM, or the size of your RAM if you can spare a few gigabytes.

---

### Post by Paqman on 2012-06-06
> **ads2996 said:**
> Is 8gb swap enough or too much

Almost certainly too much. Your swap needs to be at least the same size as your RAM if you intend to use hibernation. Otherwise 1GB is fine on any machine with 1GB or more of RAM.

---

### Post by ads2996 on 2012-06-09
Thank you for all your help

---

