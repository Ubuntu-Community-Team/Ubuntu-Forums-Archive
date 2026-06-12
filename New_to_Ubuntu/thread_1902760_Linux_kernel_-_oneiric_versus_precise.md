---
title: "Linux kernel - oneiric versus precise"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by PeterTaps on 2011-12-31
Folks,

At [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/), there are two versions of 3.1.6 kernel - oneiric and precise. What is the difference between the two?

I am currently running Ubuntu 11.04 and need to upgrade the kernel to 3.x to get the new drivers for my A75-based motherboard.

Regards,
Peter

---

### Post by uRock on 2011-12-31
Oneiric and Precise are the code names for ubuntu releases. Precise(ubuntu 12.04) is in development and will not be released until April. [Oneiric(ubuntu 11.10)]("http://www.ubuntu.com/download/ubuntu/download") is the most recent version of ubuntu.

---

### Post by gandaran on 2011-12-31
[http://www.upubuntu.com/2011/11/how-to-install-kernel-31-on-ubuntu.html](http://www.upubuntu.com/2011/11/how-to-install-kernel-31-on-ubuntu.html)

---

### Post by grahammechanical on 2011-12-31
This is the way that I understand things: The next Ubuntu is developed on top of the previous Ubuntu. So, we start with 11.10 and slowly things are changed until 11.10 becomes 12:04 and Oneiric turns into Precise in the process.

This is why there is a section on this forum called Ubuntu+1. The next day after the latest Ubuntu distribtion is released work begins on the next.

So, for a while both Oneiric and Precise will get the same kernel updates but at some point support for Oneiric will stop as it did for Natty but Precise will continue to get kernel updates until its support ends.

Regards.

---

### Post by PeterTaps on 2011-12-31
Thank you all for your help.

Regards,
Peter

---

### Post by Bucky Ball on 2011-12-31
> **grahammechanical said:**
> ... at some point support for Oneiric will stop ...

Eighteen months after release for everything but the LTS releases which are supported for three years (server for five). 12.04 LTS is the next LTS release (10.04 LTS is current and is supported until April 2013). 11.10 has eighteen months from October 2011.

This says it all:

[http://www.ubuntugeek.com/the-ubuntu-release-cycle.html](http://www.ubuntugeek.com/the-ubuntu-release-cycle.html)

It is not random and support time is easy to work out from the name (read number) of the release. LTS (long-term support) releases are out every two years ... ;)

---

### Post by shuttleworthwannabe on 2012-01-01
@OP: do i understand correctly--you wish to upgrade to the latest kernel? but not upgrade the Ubuntu release/version? gandaran's link should help; not sure if this will break your nvidia/ATI propreitary drivers if already installed on older kernel; I had that experience when I did kernel upgrade in 11.10 to v3.1.x.

---

