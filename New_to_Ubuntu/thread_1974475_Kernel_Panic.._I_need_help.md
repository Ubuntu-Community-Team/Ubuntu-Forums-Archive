---
title: "Kernel Panic.. I need help"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by Loma Rozza on 2012-05-06
Since 4 days i installed lubuntu 12.04 on my pc, but it has happened already 3 times that I get a black screen that says at the top "Kernel panic - not syncing: Fatal exception in interrupt" instead of the bottom of the screen it says "Panic occurred, switching back to text console" but I can not do anything, I have to turn off your PC... Can someone help me?

---

### Post by buzzingrobot on 2012-05-06
> **Loma Rozza said:**
> Since 4 days i installed lubuntu 12.04 on my pc, but it has happened already 3 times that I get a black screen that says at the top "Kernel panic - not syncing: Fatal exception in interrupt" instead of the bottom of the screen it says "Panic occurred, switching back to text console" but I can not do anything, I have to turn off your PC... Can someone help me?

Loma, I can't help you on the specific kernel panic you are experiencing.  However, it would be rare if no one else had experienced the same thing.  Put the words the kernel displayed into a search query on Google or some place else and see what you can find.

Also, check the kernel logs the next time you restart after a panic and see if anything in it helps point to a cause.  If you don't have a log viewer, the kernel logs are in /var/log and they're called "kern.log".  The logs are voluminous and not meant for easy reading, but can often help.  The entries are time-stamped, so look for entries just before the time of the panic.

---

### Post by Loma Rozza on 2012-05-07
> **buzzingrobot said:**
> Loma, I can't help you on the specific kernel panic you are experiencing.  However, it would be rare if no one else had experienced the same thing.  Put the words the kernel displayed into a search query on Google or some place else and see what you can find.

Also, check the kernel logs the next time you restart after a panic and see if anything in it helps point to a cause.  If you don't have a log viewer, the kernel logs are in /var/log and they're called "kern.log".  The logs are voluminous and not meant for easy reading, but can often help.  The entries are time-stamped, so look for entries just before the time of the panic.

I checked the kernel log and it says 
"fbcon: radeondrmfb (fb0) is primary device" 
"Console: switching to color frame buffer device 160x64" 
"fb0: radeondrmfb frame buffer device" 
"drm: registered panic notifier" 
"[drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0" on many lines. It should be the video card? I checked the other components, but they work well. I don't know anything about the linux world, this is my first experience.

---

### Post by buzzingrobot on 2012-05-07
The "radeon" references are to your video card.  It might be worth switching to another driver for the card.

You have two drivers available to you. One is the open source driver prepared by the Linux community.  The other is the proprietary driver prepared by the AMD company that made your Radeon card.  

I don't know which driver you are using at the moment, but that's not important.  You just want to switch to the other one.

Open "Details" and then open "Additional Drivers". If you are **not** running the proprietary driver you will see something like " No Proprietary Drivers Are In Use on This Machine".  If that's what you see, select the option to install  a proprietary driver.  Two driver options will probably be offered.  Take the one that is recommended. After it is installed, reboot and the proprietary  driver should be installed. "Additional Drivers" may tell you that it failed to install the driver. That is almost certainly a mistake and the driver is actually installed correctly.

On the other hand, if you see in "Additional Drivers" that you are currently running a proprietary driver, you want to select the option to remove it, and then reboot.  The open driver will be installed.

You will find plenty of threads in these forums about video card problems.

---

### Post by Loma Rozza on 2012-05-09
> **buzzingrobot said:**
> The "radeon" references are to your video card.  It might be worth switching to another driver for the card.

You have two drivers available to you. One is the open source driver prepared by the Linux community.  The other is the proprietary driver prepared by the AMD company that made your Radeon card.  

I don't know which driver you are using at the moment, but that's not important.  You just want to switch to the other one.

Open "Details" and then open "Additional Drivers". If you are **not** running the proprietary driver you will see something like " No Proprietary Drivers Are In Use on This Machine".  If that's what you see, select the option to install  a proprietary driver.  Two driver options will probably be offered.  Take the one that is recommended. After it is installed, reboot and the proprietary  driver should be installed. "Additional Drivers" may tell you that it failed to install the driver. That is almost certainly a mistake and the driver is actually installed correctly.

On the other hand, if you see in "Additional Drivers" that you are currently running a proprietary driver, you want to select the option to remove it, and then reboot.  The open driver will be installed.

You will find plenty of threads in these forums about video card problems.

Solved, thank you:)

---

