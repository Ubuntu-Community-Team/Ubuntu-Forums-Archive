---
title: "Boot lag or impatient user?"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by MyTinFoilHat on 2012-11-26
I've been checking out posts about various boot issues others are having. I'm uncertain (still new enough to GNU/Linux to not know what I don't know - ha!), but I'm wondering if it might be possible that what I might perceive as a 'lag' in my laptop's boot sequence may be due to the fact that I opted for the encrypted drive.


In light of that, I believe I *may* have some minor boot issues. In total, booting takes anywhere from 2-3 minutes. I'm on a slightly older MBPro w/ Quantal/ 
  More often than not, this is how the boot appears to me:
 
[LIST]
[*]- screen goes completely white (cold boot)
[*]- screen goes black with cursor in upper left
[*]- screen flashes color (purple for Unity; blue for Gnome)
[*]- screen goes back to black with cursor
[*]- screen goes color (purple for Unity; blue for Gnome)
[*]- greeter/login
[*]- screen goes black (thinking - heavily)
[*]- desktop wallpaper appears
[*]- laptop thinks some more
[*]- remainder of desktop renders/open for business
[/LIST]
 

In all, the unity is useable. Just a little sluggish. 

Any thoughts, ideas, or advice welcome. 
  Thank you in advance!

---

### Post by DuckHook on 2012-11-26
Hard to say as these things are awfully subjective. My newer laptop with faster HD, dual CPU, faster Mem boots in half the time of my old Dell D600 with slow HD, ancient single CPU, 1/8 the Mem. More system HW info would be interesting. Not sure what it would tell us though, without stopwatching the boot process.

---

### Post by MyTinFoilHat on 2012-11-27
> **DuckHook said:**
> Hard to say as these things are awfully subjective. My newer laptop with faster HD, dual CPU, faster Mem boots in half the time of my old Dell D600 with slow HD, ancient single CPU, 1/8 the Mem. More system HW info would be interesting. Not sure what it would tell us though, without stopwatching the boot process.

 Late night. Long day. Wish I could have gotten back sooner. I completely understand what you mean about boot timing being subjective. I readily admit, I'm not running the latest and greatest in the way of hardware (I'm really holding out for an HD laptop or tablet - especially if Ubuntu for Android starts taking off like a rocket... 

It was completely abscent-minded of me not to provide viewers/responders with some HW stats. That said, here we go: 

[LIST]
[*]MacBook Pro 17&quot; (OSX was completely exorcised)
[*]Ubuntu 12.10 (quantal)
[*]Mem: 3.8 GiB
[*]Proc: Intel Core 2 Duo CPU T9300 @ 2.50GHz x 2
[*]Freq: 800MHz
[*]L2 cache: 6144kb
[*]Graphics: GeForce 8600M GT/PCIe/SSE2
[*]OS Type: 64-bit
[*]Disk: 241.9 GB
[*]GNOME 3.6.0
[*]GCC v: 4.7 (x86_64-linux-gnu)
[*]Xorg v: 1.13.0 (08 October 2012)
[*]NVIDIA: VRAM 512MB / GPU Freq 169MHz
[/LIST]
 
Thank you.

---

### Post by DuckHook on 2012-11-27
[LEFT]That is more than sufficient horsepower. Certainly better than any laptop I boot from, and my boot times vary from about 30 seconds to 1 minute. The fast machine has very little loaded whereas slowest has tons of fonts, modules and autostart apps. So, one factor could be the amount of cruft that you accumulate. Can't tell where you are in the cruft department.
[/LEFT]

Could you actually time it with a stopwatch?

If you are still convinced that boot times are unacceptably low, then the next step would be to go through the logs. I would probably start with syslog and boot.log. You may also want to look at your authority logs. I've also run into a slow bootup situation that was caused by unavailable network shares. My boot process was waiting for an NFS share that was refusing my connection request. It has to try a number of times before it gives up. You could also switch your boot process into verbose and display mode rather than the neat and tidy but completely uninformative overlay that now hides all of nitty gritty at bootup. Sorry, don't have access to my notes right now so can't remember how it's done (responding from tablet at the moment). You could probably get easy instructions by googling it.

---

