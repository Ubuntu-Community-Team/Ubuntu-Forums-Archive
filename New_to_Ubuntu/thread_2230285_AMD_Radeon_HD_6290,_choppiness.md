---
title: "AMD Radeon HD 6290, choppiness"
date: 2014-06-18
forum: New to Ubuntu
---

### Post by Tar_Ni on 2014-06-18
Hi,

I have a AMD Radeon HD 6290 graphic cards and I am experiencing unbearable choppiness when watching videos in Ubuntu 14.04. I have the latest pepperflash in Chromium and I have tried both the open sourcee and proprietary AMD driver in my installation to Ubuntu to no avail.

I've falled back on Windows 7, as I primairily purchased this second-hand for watching video and I dont have this problem on Windows. I can watch just about every video without issues.

So what's the matter here? I have heard that some AMD graphic cards just don't perform well on Ubuntu. Is there a solution to solve this, for a non-techy user?

---

### Post by monkeybrain20122 on 2014-06-18
For that card I would suggest using the latest open driver instead of the fglrx (unless you are a gamer)
[https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers)
I have an AMD HD6300 and it works great and it supports vdpau decoding for videos if you install "mesa-vdpau-driver" as well.

But I would suggest disabling the ppa once you get everything working, as it updates everyday and you may get hit by a bug if you do that often enough , also install ppa-purge just in case.

---

