---
title: "Mouse pointer disappearing at the top of the screen"
date: 2015-09-11
forum: New to Ubuntu
---

### Post by ensar-kilinc123 on 2015-09-11
The mouse pointer disappears when the pointer touches the very top of the screen, the whole pointer dissapears. Mouse doesn't go up the screen it just disappears and when i slightly pull it down it comes back. It kinda bugs me when I'm trying to access the "File Edit View" kinda thing I lose track of what it is and i click the wrong thing. I've tried multiple Nvidia drivers but it has nothing to do with that.

Ubuntu 12.04.03 LTS 64-bit all updates installed and I'm using an ASUS K555LB which has 12 GB of ram, 1TB HDD, Nvidia Geforce 940M aka Geforce GT 940M, Intel Core i5-5200U and a 1366x768 display if those have anything to do with this somehow?

---

### Post by sandyd on 2015-09-11
You need a nvidia driver that is newer than 349.12, see [here]("https://devtalk.nvidia.com/default/topic/807168/linux/possible-346-35-regression-hardware-cursor-not-drawn-on-top-screen-edge/2/") for details on the issue.

And here comes the issue:
Default Ubuntu 12.04 repo only goes up to nvidia-331
Xorg-Edgers PPA's newest version for precise is nvidia-346

I can't find another PPA at this time that provides graphics drivers newer than 349.12 for precise, so you will either have to upgrade to Ubuntu 14.04, or install from nvidia's site.

---

### Post by ensar-kilinc123 on 2015-09-12
Oh I made a mistake I'm actually using ubuntu 14.04.03 LTS

---

### Post by ensar-kilinc123 on 2015-09-12
And I'm using the 346.82 updates version. Same thing happens with the tested version :(

---

