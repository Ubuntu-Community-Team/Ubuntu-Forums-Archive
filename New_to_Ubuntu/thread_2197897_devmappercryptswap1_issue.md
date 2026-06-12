---
title: "/dev/mapper/cryptswap1 issue"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by nothankyou273 on 2014-01-05
I just installed Ubuntu 12.04 via USB and it works fine booting my computer up, until it gives me the "The disk drive for /dev/mapper/cryptswap1 is not ready or not present." message. I have never gotten passed this loading screen. I press S or M and nothing happens, I've waited and nothing seems to happen. I can't proceed to the login screen so I can't do anything from there? Any ideas?

---

### Post by Dave_L on 2014-01-05
Instead of pressing S or M, you've tried doing nothing and waiting?

---

### Post by nothankyou273 on 2014-01-05
Last time I waited for about 30 minutes. Give or take.

---

### Post by nothankyou273 on 2014-01-06
I've looked around and here [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/874774](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/874774) it seems to be the exact same problem. But I don't know how to fix it.

---

### Post by Dave_L on 2014-01-06
Here's a longer list of bug reports. Some of them suggest workarounds, but they're not that easy to understand.

---
could not mount /dev/mapper/cryptswap1
[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/874774](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/874774)

could not mount /dev/mapper/cryptswap1 M for manual S for skip
[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1061190](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1061190)

The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present
[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1153661](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1153661)

The Ubuntu installation does not create swap partition.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1186811](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1186811)
---

I often get that message, but if I ignore it and do nothing, after a few seconds the boot process continues and completes successfully.  I'm using Ubuntu 12.04.3, but I had the same issue with 10.04.

I'm not sure what to suggest. Hopefully someone else will be able to help you.

---

### Post by nothankyou273 on 2014-01-06
> **Dave_L said:**
> Here's a longer list of bug reports. Some of them suggest workarounds, but they're not that easy to understand.

---
could not mount /dev/mapper/cryptswap1
[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/874774](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/874774)

could not mount /dev/mapper/cryptswap1 M for manual S for skip
[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1061190](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1061190)

The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present
[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1153661](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1153661)

The Ubuntu installation does not create swap partition.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1186811](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1186811)
---

I often get that message, but if I ignore it and do nothing, after a few seconds the boot process continues and completes successfully.  I'm using Ubuntu 12.04.3, but I had the same issue with 10.04.

I'm not sure what to suggest. Hopefully someone else will be able to help you.

Thanks, I'll look into it.

---

