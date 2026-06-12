---
title: "rtkit bug back in the kernel again"
date: 2013-02-11
forum: Programming Talk
---

### Post by yyyc186 on 2013-02-11
Hello,

This bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/690010](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/690010)

is back in the kernel again.  If kernel is compiled with autogroup turned on rtkit does not work at all.  Turning it off via sysctl isn't a work around either.

I tried filing a bug but it was autorejected since the kernel isn't identified as a ubuntu package.

12.04 LTS  32-bit.

Really need work around.  More importantly need to know why/how this bug keeps injecting itself into the code base.

---

