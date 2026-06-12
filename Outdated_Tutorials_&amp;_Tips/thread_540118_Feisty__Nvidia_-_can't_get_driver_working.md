---
title: "Feisty / Nvidia - can't get driver working"
date: 2007-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by jonathanku on 2007-09-01
Hi - I know there are many similar threads out there, but I just can't get them to sort my problem. I'm trying to install the proprietary NVidia drivers and failing.

Current situation:

When I enabled the NVIDIA driver in "restricted drivers", GDM wouldn't start. Errors were complaining that the NVIDIA kernel-module wa v.1.0-9755 whereas my X module was v1.0-9631.

According to this page [http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)
installing nvidia-glx will use the 9631 module for NVIDIA. Should be good that the kernel versions match... yes?

Got a new error when trying to restart
**Failed to initialize the NVIDIA kernel module! Screens found but none have a usable configuration**

I made sure that the h-sync & v-sync settings were correct for my monitor.


**What should I try next!??**
[LIST]
[*]change other monitor settings in xorg.conf?
[*]update my X module kernel version (how?) to match the latest nvidia kernel version (i.e. nvidia-glx-new - driver 9755)?
[*]other?
[/LIST]

Thanks..
JK

---

