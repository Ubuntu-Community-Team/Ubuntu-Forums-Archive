---
title: "Help with net flix please"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by sean neilan on 2012-04-11
I just joined net flix and I can not get it work through my pc. I have a acer aspire 5742z and i have ubuntu10.04. Now net flix says that my fire fox is not the right version so I need to know what version I am running and how do I find that out? they also said that I may not be operating at a fast enough ghz and I do not know how to find that out? my system monitor say that I have a Pentium 6100 @2.0ghz and if anyone out there has had this problem can you please HELP me to get my net flix working I would forever be in your debt, and I am a complete newbie at this computer stuff so all the HELP I can get would be greatly appreciated THANK YOU EVER SO MUCH!

---

### Post by GWBouge on 2012-04-11
Unless something's changed very recently (as in, within the past month or so), Netflix just doesn't work on Ubuntu (or, desktop Linux at all).  Your options are pretty much:  Dual-boot and use Windows when you want to stream Netflix;  Install Windows into a Virtual Machine and use that as sort of a really bloated media player for Netflix (although, I'm not sure if your Acer can handle a VM or not);  get a Netflix app for your gaming console;  or, find an alternative.

There were rumors of a Netflix app for Chrome (through demand to get things working in ChromeOS I believe), but I think that fell through.  There was hope of running the Windows versions of Firefox and Silverlight through wine, but I'm not sure that anyone's actually ever gotten it to work yet.

---

### Post by jerome1232 on 2012-04-11
TL;DR; Use a virtual machine with XP on it, or an embedded device like a blu-ray player, Wii, PS3, Xbox, roku, etc... to view netflix. ironically a few of those embedded devices, run a Linux kernel, :sad, ironic laugh:

So netflix uses silverlight, a Microsoft technology, for running silverlight things we have moonlight. Unfortunately for us Microsoft doesn't want to port the DRM code [They say they fear hackers are going to break it if they port it to linux] for use with moonlight atm. Therefore we can't use moonlight to view Netflix's DRM protected videos.

---

### Post by lovinglinux on 2012-04-11
> **GWBouge said:**
> There were rumors of a Netflix app for Chrome (through demand to get things working in ChromeOS I believe), but I think that fell through.

Is not a rumor:

[IMG]http://i.imgur.com/2v8sh.png[/IMG]

I tried to run Netflix on Chrome OS on a VM and it doesn't work. It seems there are dependencies or DRM that only come with Chrome OS machines.

---

### Post by jerome1232 on 2012-04-11
> **lovinglinux said:**
> Is not a rumor:

[IMG]http://i.imgur.com/2v8sh.png[/IMG]

I tried to run Netflix on Chrome OS on a VM and it doesn't work. It seems there are dependencies or DRM that only come with Chrome OS machines.

It's probably similar to embedded devices, they use a chip with the drm code programmed into it.

---

