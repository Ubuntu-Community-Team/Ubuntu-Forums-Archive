---
title: "Linux vs. Solaris, with Ubuntu as referee"
date: 2006-07-25
forum: Other OS Talk
---

### Post by kripkenstein on 2006-07-25
I just tried out [Nexenta]("http://www.gnusolaris.org/gswiki") (GNU/Solaris) inside VMWare. It's based on Ubuntu, and is... exactly like Ubuntu, to outside appearances. The only difference is the kernel underneath it all. This got me thinking.

Someone could install Ubuntu and Nexenta on the same hardware, and run some benchmarks - this would be a test of Linux vs. Solaris, with Ubuntu being the playing field. The results might be interesting.

I would do it, but I can't repartition my HD in the near future. So I can only run OSes other than Ubuntu inside VMWare, which obviously isn't a fair comparison. 

So, anyone interested in giving it a go? :)

---

### Post by XaeroVincent on 2006-07-29
I've been using Nexenta OS for a few weeks and it feels almost as fast as Linux. The SunOS kernel was optimized for HPC systems and multi-processor workstations and servers. It was not until Solaris 10 when non-SMP/single core chips were optimized too.

Nexenta isnt quite where Ubuntu is at yet. There are far fewer drivers for OpenSolaris, no DRI 3D acceleration, NTFS functionability, nor UDEV, FUSE, HAL ports. Its is also very buggy and Gnome dies with segmentation faults; system monitor is broken; add/remove utility links to Ubuntu repositories rather than Nexenta's; the installer doesnt setup GRUB for dual-booting systems; and APCI support is very poor.

While this might sound bad, most of these issues are to be addressed by the first official release and the rest soon after. It is important to note that Nexenta is in alpha testing stage (before betas and release canidates) and several months away any sort of stable release cycle.

I recently took the time to write a Wikipedia article about Nexenta and you can find it [here]("http://en.wikipedia.org/wiki/Nexenta_OS").


Regards,
Vincent

---

### Post by kripkenstein on 2006-07-29
Thanks for the input, Vincent. I can't see the driver issues because I'm running Nexenta under VMWare, so I'm glad you told me.

I wonder about the crashes that you mention - I didn't see any. Maybe I was just lucky, or maybe they are driver-related? I wonder.

Do you see any **advantage**, even in theory, to Nexenta over Ubuntu (say, after all the bugs etc. are worked out)?

---

### Post by XaeroVincent on 2006-07-29
I asked the same question on one of the Nexenta mailing lists and developer Erast Benson replied with this:

[B]* reliable kernel and runtime, its maturity
* better binary software compatibility
* binary drivers! (never tired to mention it!)
* faster TCP/IP stack
* much better SCSI and storage stacks
* more logical device organization
* ZFS (a bomb!)
* Zones
* upcoming BrandZ
* upcoming Xen
* better documentation[/B]

He seems somewhat subjective and biased here but some are worth noting. Some people dislike the idea behind binary drivers because it vialates open-source ideals. ZFS is a brand new 128 bit FS with many features.
BrandZ is techonology simular to FreeBSD's that will allow you to run Linux applications under Solaris and Nexenta at almost native speeds.
The OpenSolaris project has stricter quality guidelines that need to followed whenever contributing code. It helps ensure that OpenSolaris retains the reputation of enterprise quality, stability and robustness while transforming from a closed-source/proprietary OS to open-source.

However I am concerned that features might be leeched into the Linux kernel, invalidating any benefits of its own. That would effectively weaken the OpenSolaris project as a whole and eventually destroy it. Hopefully the CDDL license has measures to protect against this.

---

### Post by Lord Illidan on 2006-07-29
Yay...finals between Linux and Solaris!
*sits down, places popcorn in mouth, and looks out eagerly for a Zidane style headbutt, or a Rooney kick in the balls*

Oy Mark, give them a red card!!

Joking aside...

Personally, I think solaris is a dying breed. Linux and BSD are just too popular in the unix market.

---

### Post by kripkenstein on 2006-07-30
Looks like I should spend some time on the Nexenta boards, that's interesting.

I read on the ZFS site (I think... or some other Sun site) that since it is CDDL, they 'expect to see it on other OSes eventually'. So that might find it's way to Linux/BSD. On the other hand the faster TCP/IP stack probably wouldn't, I am guessing.

But OpenSolaris could benefit from Linux, by e.g. utilizing the code for driver compatibility.

So, this might be interesting to watch. Personally I am glad for Linux to have more open-source competition. And if OpenSolaris has stricter quality guidelines, then over time the competition could get quite heated.

---

