---
title: "HD video not playing on dell inspiron 3558"
date: 2016-10-08
forum: New to Ubuntu
---

### Post by vishalpatel6602 on 2016-10-08
i am new to ubuntu,
Facing problem while playing HD video file,
iam using dell inspiron 3558 and ubuntu 14.04 LTS,
is there any harware problem or i need to install driver,
kindly help.

vishal

---

### Post by TheFu on 2016-10-08
Welcome to the forums.

If it has the Intel Core i3-5015U, then I can say that it shouldn't have any issue with any video under 1080p.  I have a chromebook with that same CPU and it handles all videos. However, I'm running 16.04 on it and it uses the current i915 video driver. I didn't have to do anything special, but that i3 CPU didn't exist when 14.04 was released.  Can you upgrade to 16.04? That might be the best long-term answer. If you do, be certain to make a full, complete, backups so you can go back if something bad happens.

Also, I'm not running the stock ubuntu with unity. Running without any DE, but at the GPU driver level, that shouldn't matter.

```
$ lsmod |grep i915
i915                 1208320  3
video                  40960  1 i915
i2c_algo_bit           16384  1 i915
drm_kms_helper        147456  1 i915
drm                   364544  4 i915,drm_kms_helper

and
$ uname -a
Linux cc3550 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:42:33 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```
What does your's look like when you run those commands?

And which video player are you trying to use?  VLC can play almost anything.  Some other players are picky about video codec support.

---

