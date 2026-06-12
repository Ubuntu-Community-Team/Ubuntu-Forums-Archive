---
title: "How to use nVidia Card in Ubuntu 11.10"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by rakesh.swapna on 2011-11-07
**[SIZE=1]My  Dell N5110 Laptop got both Intel (R) HD Graphics and nVidia GeForce  GT525M. I am using Ubuntu 11.10. Currently Intel card is used. In  Additional drives NVIDIA accelerated graphics driver (version  current)(recommended) is activated. Please guide me how can I use nVidia  in Ubuntu 11.10 So that I can enjoy Desktop cube using  Compiz.(Installed CompizConfig Settings Manager)[/SIZE]**

ammu@ammu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)

Thankyou

---

### Post by papibe on 2011-11-07
Hi rakesh.swapna. Welcome to the forums.

You have Nvidia [Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux. Despite that fact, there are a couple of projects in progress that have some success to support it.

I would advice you to start reading a couple of useful threads. [This]("http://ubuntuforums.org/showthread.php?t=1657660") one to understand what it is (but a pessimist). And this [other]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") one (from post #7), with a more practical approach.

There are laptops that can either disable it, or simplify things by turning off the Nvidia card. Check your BIOS if you have any of those options.

I hope that helps,
Regards.

---

### Post by rakesh.swapna on 2011-12-10
I have done it with the help of Bumblebee

Thanx

---

