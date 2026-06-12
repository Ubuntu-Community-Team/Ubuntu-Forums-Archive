---
title: "Radeon 3000hd  help please"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by mikee55 on 2013-07-13
Hi all, I've been using Xubuntu on this machine for a while, but it is capable of running Unity, I believe and now have 13.04 R.Ringtail installed. 
So, I have an issue with my graphics, Xubuntu gave me full resolution of my monitor 1600 x 1200. Right now I'm getting 1024 x 768 or 800 x 600.
Apparently I have no additional drivers to install. I tried to Google and came up with this 
[http://manpages.ubuntu.com/manpages/raring/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/raring/man4/radeon.4.html)
but, I've drawn a blank.
Where do I start, please?

Mike

---

### Post by mikee55 on 2013-07-13
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780L [Radeon 3000] (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 8388
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at c000 [size=256]
	Memory at fe9f0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fe800000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: radeon

---

### Post by mastablasta on 2013-07-13
radeon 3000 uses opensource drivers only in 13.04. if you want adidtional drivers you need to use 12.04.1 (the .2 will also have new kernel that doens't support the legacy drivers

---

### Post by mikee55 on 2013-07-13
Okay Thanks

---

