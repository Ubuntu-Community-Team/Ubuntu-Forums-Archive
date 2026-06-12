---
title: "Did Last Kernel Update Break Hotplug of USB Sticks?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by GregA on 2008-10-18
It's been awhile since I last posted, as Gutsy and Hardy have been running great on my PC's.   But this week, the kernel was updated once or twice.

Before that update, on this HP A250N (AsysTek A7N8X mobo), all my usbsticks could be hot-plugged - that is - they would be mountable and worked perfect if plugged in after the PC was on.   

Now, these devices are not seen at all by Ubuntu if not already plugged in at system start-up.

But if I leave the devices in the USB ports, and restart the PC, they are recognized and auto-mounted?

Has anyone else seen this behaviour, and besides a re-boot, is there a work-around or possibly a bug reported to Canonical??

Advise appreciated.

---

### Post by Pro-reason on 2008-10-18
> **GregA said:**
> 
But if I leave the devices in the USB ports, and restart the PC, they are recognized and auto-mounted?


I don't know.  You tell me.

If you're talking about an external USB hub, then it's [a known issue]("http://ubuntuforums.org/showthread.php?t=950214") with the recent kernel.

---

### Post by GregA on 2008-10-18
Greetings Pro;

My apologies in being less than clear, but USB sticks are auto-mounted if they are plugged in to my Belkin 4 port external hub prior to system startup - - that always works, as will a reboot with the device plugged in.  

If one USB stick is mounted (because of cold-plug or reboot as above), then I can successfully hot-plug a 2nd USB device.

I read the other thread you referenced, in that this is a probable bug in the newest kernel build, but I haven't tested using lsusb to have the stick mount shortly thereafter.

What I would prefer to do, while Canonical sorts this out, is to boot into the prior kernel.   But, unlike my duel boot system, Ubuntu is the only OS on this desktop, and I don't see the startup screen where you can select another kernel.   Is there a way I can access that screen, or revert to the older kernel?  Thanks for the help.

*********************

Update: . . . . . yes, just invoking the "lsusb" command (scanning for the devices) triggers the device on, registers it, and automounts.  It takes just 2 or 3 seconds to accomplish this.   That's an acceptable work-around, but I'd like to see more user testing of kernel updates - - - with Ubuntu's huge userbase, this is one way to catch these issues before a general release.

---

### Post by Pro-reason on 2008-10-18
The GRUB screen where you choose operating systems is controlled by the file /boot/grub/menu.lst.

---

