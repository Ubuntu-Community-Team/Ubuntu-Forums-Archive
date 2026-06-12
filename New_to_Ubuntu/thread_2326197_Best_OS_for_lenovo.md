---
title: "Best OS for lenovo"
date: 2016-05-29
forum: New to Ubuntu
---

### Post by cressrt2 on 2016-05-29
My wife has a Lenovo laptop currently running Lubuntu 15.04, but is quite slow, it has an AMD E1-6010 processor with a RAM 6GB, is there a better OS for this machine?

---

### Post by sudodus on 2016-05-29
Lubuntu is the lightest flavour in the Ubuntu 'family'. But there are ultra-light alternatives, for example Puppy Linux and Tiny Core.

---

### Post by arochester on 2016-05-29
With 6Gb of RAM you should not have a problem. What is the MODEL of your Lenovo laptop?

---

### Post by cressrt2 on 2016-05-29
G50-45 80e3

---

### Post by Impavidus on 2016-05-29
Surely there is a better OS for that computer. Lubuntu 15.04 is end-of-life. Installing a supported release will improve things, and not only its performance. I see that laptop has some kind of AMD graphics. Lubuntu 16.04 may provide better drivers. First test it in a live session.

6GB memory is plenty for any member of the Ubuntu family.

---

### Post by cressrt2 on 2016-05-29
OK will download and try, thanks

---

### Post by grahammechanical on 2016-05-29
That machine has plenty of memory and Lubuntu 16.04 has the lowest memory usage of all the Ubuntu flavours

[https://bryanquigley.com/memory-usage/ubuntu-16-04-livecd-memory-usage-compared](https://bryanquigley.com/memory-usage/ubuntu-16-04-livecd-memory-usage-compared)

But do not expect an AMD proprietary video driver in 16.04 because AMD are not providing one.

> The fglrx driver is now deprecated in 16.04, and we  recommend its open source alternatives (radeon and amdgpu). AMD put a  lot of work into the drivers, and we backported kernel code from Linux  4.5 to provide a better experience. 


When  upgrading to Ubuntu 16.04 from a previous release, both the fglrx  driver and the xorg.conf will be removed, so that the system is set to  use either the amdgpu driver or the radeon driver (depending on the  available hardware). 


More information is available at [https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)


[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Regards

---

### Post by MartyBuntu on 2016-05-29
> **cressrt2 said:**
> ...but is quite slow, it has an AMD E1-6010 processor...

That's a fairly anaemic processor. I wouldn't hold my breath for any desktop environment switching magic.

---

