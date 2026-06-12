---
title: "New Kernel Updates Backported to Ubuntu 20.04 LTS?"
date: 2020-11-06
forum: New to Ubuntu
---

### Post by cephalopoda2 on 2020-11-06
Hello,

I'm new to Linux, and I'm currently learning about kernel updates.

I've recently read that the 5.7 kernel update added native support for exFAT thanks to some work by Samsung.

My current understanding is that Ubuntu uses kernel 3.8 for stability, but will backport some new features to the older kernel from time to time.

Is it possible that native support for exFAT from 5.7 would ever find its way to the kernel in Ubuntu 20.04 LTS? If so, where would I go to read about kernel backports / releases / updates etc.? I'd be especially interested to stay updated on any news of this native exFAT support finding its way to the Ubuntu images for the Raspberry Pi 4.

Thanks!

---

### Post by mrdc76 on 2020-11-06
You probably meant 5.4, because 3.8 must be like 10 years old. Hardware enablement stack to be released early 2021 will backport kernel from 20.10 to 20.04.

---

### Post by deadflowr on 2020-11-06
Short answer, yes, as Ubuntu 20.04 will eventually get the 5.8 kernel.
You can install it now though with
```
sudo apt install linux-generic-hwe-20.04-edge
```
> My current understanding is that Ubuntu uses kernel 3.8 for stability,
No version currently uses that kernel outside of possible cloud images or some other specialized system.
> I'd be especially interested to stay updated on any news of this native exFAT support finding its way to the Ubuntu images for the Raspberry Pi 4.

The raspi kernel should get the same updated kernel as the generic kernel.
It should be the specific linux-raspi-hwe package, though I don't know whether it'll be named -20.04 or not.

To avoid confusion, Ubuntu builds a variety of kernels, generic are for most desktops and servers.
and then they build special kernels specifically for devices such as raspberry pis and other specific devices.
Most kernels are built from the same source, so if the current version of 20.04 is the 5.4 kernel it's built from the upstream 5.4 kernel series.

You can read more about Ubuntu's methodology of porting updated kernels here:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

---

### Post by Impavidus on 2020-11-06
Ubuntu 20.04 comes with kernel 5.4, Ubuntu 20.10 with kernel 5.8. That kernel from 20.10 will be made available to 20.04 via the linux-generic-hwe-20.04 package, probably somewhere in January. The kernel from the interim releases (and the next LTS release) is always made available to the previous LTS release in that way about three months after the release that comes with that new kernel by default. There are also the -edge packages, which make the new kernel available even sooner.

---

