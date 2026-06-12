---
title: "Long start up"
date: 2018-03-04
forum: New to Ubuntu
---

### Post by droll80 on 2018-03-04
Hi all,
There is an Embedded System that uses Compact Flash. I use Ubuntu Server 12.04 with Real Time patch. The kernel with the patch was recompiled on the Embedded System. The system rises in about 35 seconds. The problem is the following, if I put the Compact Flash into another similar Embedded System, then the rise time increases to > 1.10 seconds. Tell me, please, why and how to fix this?
[IMG]https://itmages.ru/image/view/6516682/371e7ab9[/IMG][[img]http://storage8.static.itmages.ru/i/18/0304/s_1520162719_7290343_371e7ab980.png[/img]](https://itmages.ru/image/view/6516682/371e7ab9)

---

### Post by TheFu on 2018-03-05
Welcome to the forums.

Support for 12.04 ended a year ago, unless you have paid Canonical support. [https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)  If you have paid support, contact Canonical.

Are the systems identical?  Same CPUs, same chipsets, same network chips?

---

### Post by droll80 on 2018-03-05
> **TheFu said:**
> Welcome to the forums.

Support for 12.04 ended a year ago, unless you have paid Canonical support. [https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)  If you have paid support, contact Canonical.

Are the systems identical?  Same CPUs, same chipsets, same network chips?

Everything is the same. 
In dmesg I see that kernels starts in 13 seconds. It means that the problem is between grub and kernel. What can it be?

---

### Post by TheFu on 2018-03-05
No, everything isn't the same.  There is a difference.  
If the systems were identical, then it would work the same. So, figure out what is different and that will be the answer.
* failing hardware
* bad power
* different firmware
* bad interface to the CF

Something is different.

Assuming the CF used is identical - not just a copy.  I would check the logs for any reported issues - AFTER I moved to a supported release.  Unsupported release is the first issue.

---

