---
title: "downgrading to kernel 2.6.22"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by benji.ijneb on 2008-05-09
Hi,

I'm running ubuntu hardy, and have been experiencing the freezing problems shown in this thread: [http://ph.ubuntuforums.com/showthread.php?t=765510&page=7](http://ph.ubuntuforums.com/showthread.php?t=765510&page=7)

many people have said that downgrading to kernel 2.6.22 fixed it.
my question is, how do i do this and will it muck up my system?

I need step-by-step instructions as i'm a bit of a newb. Thanks for all your help

P.S. This is really annoying! It seems that 8.04 is no where near as fast/stable/easy/friendly/.... err... good as 7.10 was. hmm.

---

### Post by benji.ijneb on 2008-05-10
sorry to do this, but

b-b-b-b-bump

---

### Post by DBrocks on 2008-05-10
[FONT=Verdana]It should work.

This is a good site, but make sure, whenever he talks about "[/FONT][FONT=Verdana]Kernel [/FONT][FONT=Verdana]2.6.15.4", just substitue it out for "2.6.22".  Good luck!

[/FONT][http://www.geocities.com/amit_saha_works/linux/html/kernel_compile.html](http://www.geocities.com/amit_saha_works/linux/html/kernel_compile.html)[FONT=Verdana]
[/FONT][FONT=Palatino Linotype][FONT=Verdana]
~Dan[/FONT][/FONT]

---

### Post by nowshining on 2008-05-10
or install from the kernel.org main site and customize ur kernel while @ it. :) or even upgrade to the newest kernel ver. note if u click on the link for the kern. ver. u'll download a patch, u'll need to go into the main kernel folder @ the site to download it. Links are @ top of the kernel.org page.

---

### Post by Nepherte on 2008-05-10
A complete & detailed how to compile a kernel: [The Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158")

---

### Post by landeel on 2008-05-13
You can get it here:
[http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-14-generic]("http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-14-generic")

You can install with 'sudo dpkg -i --force-all file.deb'. It can cause broken dependencies. Do it at your own risk.

---

