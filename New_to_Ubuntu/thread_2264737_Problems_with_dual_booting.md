---
title: "Problems with dual booting"
date: 2015-02-09
forum: New to Ubuntu
---

### Post by aleksandar13 on 2015-02-09
I am trying to dual boot Windows 8.1 Pro and Ubuntu (14.04),** I had Ubuntu on the same PC I'm using now** and that I wish to have dual boot, but it just won't go easy..

_Disabled Fast Boot_
_Disabled Secure Boot_
_Created bootable USB_ (used two Kingstons, it's not problem with them)
I have unallocated space for Ubuntu (32 GB)

And first problem I had today:
Restarted my PC, jumped in boot menu, I've selected the USB drive, and tried 
**Try Ubuntu without installing**, as well as **Install Ubuntu**, and in both cases Ubuntu (installation) ends up with loading,
and I get installation wizard or Ubuntu desktop (depending on those previous options), and everything seems cool for 5-10 seconds
until my PC restarts. (I tried it a couple of times, everytime was the same, sometimes I don't even get to click next on the installation wizard)

And now somehow I don't have that problem, or I'm just unable to get that problem, 
because now installation (or Try Ubuntu without installing method) won't even start, it just keeps loading 
and it never ends.

[IMG]http://linoob.com/wp-content/uploads/2011/04/Ubuntu-Bootscreen.png[/IMG]


..and when I press F2, a console opens for one millisecond[SIZE=2] before my PC restarts.

System specifications
[/SIZE][IMG]http://s1.postimg.org/j1e4p8a6n/Capture.png[/IMG][SIZE=2]
[/SIZE]

I've also tried with 12.04 version and it was same situation, although I had Ubuntu 12.04 dual booted with Windows 7 on same PC 10 months ago.

---

### Post by fantab on 2015-02-09
Is this a OEM branded PC or an assembled one?
How did you install Windows8.1? Did you use same partitioning that you used with 12.04 and Win7 or did you change things?

Have you tested the boot media on another machine to rule out 'burn' issues?
Have you done a [SHA256Sum Check]("https://help.ubuntu.com/community/HowToSHA256SUM") on the ubuntu.iso?
Have you disabled [FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html") in Win8?

---

### Post by aleksandar13 on 2015-02-10
Assembled one.
Fresh new install, deleted previous systems.

No, no, and Yes.
You wouldn't believe what happened, I tried Wubi, Windows installer for Ubuntu, although it's outdated, 
and after installation I tried to run Ubuntu but same error again, it kicked me before I could do anything with Ubuntu
installation wizard. Therefore, I've uninstalled it, and tried again with previously made bootable Ubuntu USB,
and.. well I'm writing this from fresh installed Ubuntu (not a single error).
Just one thing
when I was in installation wizard I had option to _Dual Boot Ubuntu alongside Boot Manager _(didn't have dual boot with Windows 8.1 written),
_delete previous system and start with Ubuntu_, or [U]Other.
[/U]I chose Other and created two new partitions from Unallocated space, primary and swap, and moved with installation.
*Everything is cool for now.*

---

