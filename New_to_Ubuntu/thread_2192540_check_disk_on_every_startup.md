---
title: "check disk on every startup"
date: 2013-12-08
forum: New to Ubuntu
---

### Post by anishtain4 on 2013-12-08
Hi,
I've this problem for a while that every time I boot the system it starts to check disk. I've tried to figure it out from previous forums but none of the approaches worked for me. It is not something scheduled. and if I skip it for a couple of times, after the startup screen I just get to the terminal without any graphic!!!
I checked my fstab and there is this error in it
UUID=a6cfa831-5938-47c8-bf94-8450eef649b1 /               ext2    errors=remount-ro 0       1
In some forum people say it is the way it meant to be, but I'm suspicous to this.

---

### Post by sandyd on 2013-12-08
> **anishtain4 said:**
> Hi,
I've this problem for a while that every time I boot the system it starts to check disk. I've tried to figure it out from previous forums but none of the approaches worked for me. It is not something scheduled. and if I skip it for a couple of times, after the startup screen I just get to the terminal without any graphic!!!
I checked my fstab and there is this error in it
UUID=a6cfa831-5938-47c8-bf94-8450eef649b1 /               ext2    errors=remount-ro 0       1
In some forum people say it is the way it meant to be, but I'm suspicous to this.

Hi, what version of Ubuntu are you using?

Is there a specific reason for using ext2 as your root filesystem?

---

### Post by ajgreeny on 2013-12-08
Can you also show us the output of the command ```
sudo tune2fs -l /dev/sda#
``` where sda# is your root partition.

---

### Post by amjjawad on 2013-12-08
> **anishtain4 said:**
> Hi,
I've this problem for a while that every time I boot the system it starts to check disk. I've tried to figure it out from previous forums but none of the approaches worked for me. It is not something scheduled. and if I skip it for a couple of times, after the startup screen I just get to the terminal without any graphic!!!
I checked my fstab and there is this error in it
UUID=a6cfa831-5938-47c8-bf94-8450eef649b1 /               ext2    errors=remount-ro 0       1
In some forum people say it is the way it meant to be, but I'm suspicous to this.

Hi,

I have never faced this issue before but I'm wondering how did you install your system? is it the only installed system? are you dual-booting? it happens everytime you turn your machine ON? what if you reboot while the machine is ON, still see this check?

---

