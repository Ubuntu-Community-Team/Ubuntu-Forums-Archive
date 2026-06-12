---
title: "Installed Ubuntu 14.04 on my computer, won't boot, says no OS on hard disk"
date: 2014-11-13
forum: New to Ubuntu
---

### Post by vanceternowski on 2014-11-13
Hello,

Computer specs: AMD E1-2500 APU, 4gig memory. It's HP, which I know has EFI problems.

I installed Ubuntu, replacing Windows. When I reboot the computer, I am told that no operating system is on the hard disk. However, when I hit F9 to see the boot menu, Ubuntu shows up as an option. Selecting it tells me again that there's no OS. I tried running boot repair, and selecting backup and rename, and a few other tricks that I've found on the forum so far, but no dice. 

When I restart the computer with the LiveDVD in the machine, it brings up the initial option of Try Ubuntu, Install without Trying, etc. Everything otherwise seems to say that Ubuntu is on the hard drive.

Here's my URL: [http://paste.ubuntu.com/8996436/](http://paste.ubuntu.com/8996436/)

I can't really afford to go out and buy Windows to reinstall it, and I can't imagine that there is not some kind of solution to my problem. Any help would be appreciated.

Thanks.

---

### Post by JeQhdMD on 2014-11-13
It may be worthwhile to do a re-install with "_secure boot on" versus disabled . . ._ and if that doesn't work out, you can also try a re-install in legacy mode (secure boot off) but I'm not sure if that will work as your hdd is gpt.   The only version of Ubuntu that works on EFI systems is the 64 bit version so be certain that's what you have.

IF, repeat, IF, you live in a larger metro area, there may be a Linux Local Users group in the area.  Those folks could figure it out (might have to bring in the unit to the club meeting).

---

