---
title: "No network drivers (?) after problematic USB-install, now unsure how to proceed."
date: 2015-12-23
forum: New to Ubuntu
---

### Post by eric100 on 2015-12-23
Hi there,

Complete novice to ubuntu/linux, so bear with me.

I recently set up a dual-boot of Ubuntu (14.04) from Windows 10. Apparently, there is a known problem with Nvidia graphics cards/drivers, which forced me to include "nomodeset" during the ubuntu installation - I assume to remove these problematic drivers. As a result, I now have a Ubuntu partition without any network connectivity, meaning I am incapable of accessing the required drivers. 

I attempted to download "compat-wireless-2.6.tar.bz2" and transfer it by USB to my linux computer, but windows was unable to properly extract it on said windows partition.

As such, I am stuck with a installed Ubuntu partition, but with no drivers/network connectivity.

I've attempted to manually install WiFi/Ethernet connection, but it does not appear to work. "Connection information" is greyed out, and inaccessible. The partition of Windows 10 on the same computer has no problems accessing WiFi/Ethernet.

Thankful for some help.

Eric

EDIT: Potentially relevant information: I am unable to restart/turn off the computer from my Ubuntu partition - it simply ends up stuck with the ubuntu-with-the-five-dots-under-it logo, ultimately forcing me to force shutdown the computer.

---

### Post by Kris_M on 2015-12-23
noob here.  I installed a couple days ago without using that  and my Nvidia works fine
Terminal (ctrl-alt-t) command "lshw"   shows GeForce GTX 650 Ti .
Maybe difference - I installed dual boot from Win7.

Suggest re-install w/o using that and see what happens...


GA-Z87N-WIFI mobo, i5 4670K, CoolerMaster Hyper TX3 hsf, 8GB ballistix 1600(2x4), Win7 Pro x64 SP1 current, Sammy 250GB Evo SSD, BitFenix Prodigy black case.

---

### Post by eric100 on 2015-12-23
Found this thread: [http://ubuntuforums.org/showthread.php?t=2248919&page=2](http://ubuntuforums.org/showthread.php?t=2248919&page=2) which appears to describe a scenario very similar to mine; I also have the MSI GS60 series computer.

---

### Post by eric100 on 2015-12-23
I think the problem is mainly with newer Nvidia cards,

As mentioned in this link: [http://ubuntuhandbook.org/index.php/2015/01/install-nvidia-346-35-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2015/01/install-nvidia-346-35-ubuntu-1404/)

I have the GTX 970M.

---

### Post by buzzingrobot on 2015-12-23
> **eric100 said:**
> ...Apparently, there is a known problem with Nvidia graphics cards/drivers, which forced me to include "nomodeset" during the ubuntu installation - I assume to remove these problematic drivers. As a result, I now have a Ubuntu partition without any network connectivity, meaning I am incapable of accessing the required drivers. 


The video card driver is unrelated to any network drivers.

If an Nvidia card is active, it will be detected and, by default, the open source Nvidia driver, called Nouveau, will be used. However, some Nvidia cars are incompatible, to some degree or another, with Nouveau.  This, ultimately, is because only Nvidia's developers have access to full information about these cards. It's further complicated because cards bearing the same name sometimes vary from vendor to vendor.

"Nomodeset" is a temporary option that deals with this by getting you a functioning, but usually degraded, display.  Most users then install the proprietary Nvidia driver and reboot to enable it.  Canonical makes these drivers available via the "Additional Drivers" tab on the Software Update tool, which can be found in System Settings or by tapping the Windows key and entering "updates".

---

### Post by eric100 on 2015-12-23
I see my beginner assumptions were incorrect - thanks for straightening me out, buzzingrobot.

My problem is accessing these nvidia drivers, since I do not have access to the internet due to the network issues (which appears to be another issue entirely, according to the thread I mentioned earlier). I suppose this is solveable through USB memory sticks, or potentially through my windows partition if I can access the same files through Ubuntu, afterwards.

Thanks

---

### Post by buzzingrobot on 2015-12-23
If you have access to a wired ethernet connecton, I'd recommend using that until you get the Nvidia situation straightened out.  If you boot Ubuntu, either a live Ubuntu image or installed Ubuntu, on wired ethernet, the odds are tremendous it will "just work".  Everything needed is included in a standard installation; you do not need to locate or install anything else. (Ubuntu will try to negotiate a DHCP connection via that Ethernet link, just as Windows does. If there's anything like a typical internet service provider on the other end, it should work without user intervention.)

Once you have net access, you can install Nvdia's proprietary driver via Additional Drivers.  You *may* also see a wireless driver offered there.

If you don't have wired ethernet access, and the wireless connection is not detected and enabled automatically by the live image running in "Try" mode, then it is possible that you have a wifi card that also requires a driver that isn't open source. (This is the only instance in which you actually need to install a driver to get the net connection working.)  If that happens, I'd suggest starting a new thread about that specific issue, and be sure to include the identity and specs of your machine, especially the wifi card.

Finally, if your machine has onboard Intel video and the BIOS allows the Nvidia to be disabled and the Intel enabled, you may find that Intel video is sufficient.  It very often is if a user isn't a gamer or processing demanding video products. Intel works closely with the Linux community and their open source driver is part of every install by default. I.e., it's used automatically if Intel video is detected as the only active graphics chip.

---

### Post by eric100 on 2015-12-23
Thank you again for taking the time to reply, buzzingrobot. 

The Nvidia drivers are currently being installed on my computer, whereas the network problem is now my main problem. The more I read, the more I learn, but I still have not solved it. As it now stands, I believe the problem has been largely solved very recently ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184) post #324). What's left is to carry out the steps as described in that bug post.

They recommend installing "inux-image-extra-4.2.0-16-generic", which I have done, but also to install (or?) "linux-firmware 1.149.2", which is where I am confused. I have downloaded the required file in a .tar format, and am unsure how to proceed. 

If you suggest that I open another thread with this specific problem, I will do so; however, I imagine I am quite close to the solution with just a tad of guidance.

Thank you again!

EDIT: To expand on the ethernet cable part: plugging it in does nothing, and I've played around in try mode with both wifi and ethernet. Judging by the fact that this problem has resulted in a (now solved) extensive bug post, I think this is where the problem lies.

---

### Post by eric100 on 2015-12-23
I'll start a new thread - thank you for the feedback!

---

