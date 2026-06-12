---
title: "watchdog bug soft lockup cpu stuck"
date: 2020-02-18
forum: New to Ubuntu
---

### Post by andrew752 on 2020-02-18
Hello, I'm new to linux and just recently installed ubuntu.  All was going well until I installed 'wine' today.  After I installed 'wine', it asked me to reboot the laptop.  When I did this, I'm now confronted with the below message: 

watchdog: BUG: soft lockup - CPU#3 stuck for 23s! 


I then selected to boot via advanced mode and then chose recovery, then chose to exit recovery and log in via normal mode.  I managed to get back to the ubuntu GUI desktop, but the graphics have changed.  All the icons are much larger.  The display has changed.  Also, I keep getting the above watchdog message every time I try to reboot.  I have to go through that advanced mode procedure to get to the GUI.  I'd be very grateful if someone could advise me on how to fix this issue. Im running 18.04 version release. 

Thanks, 
Andrew

---

### Post by andrew752 on 2020-02-18
Update, the error has changed slightly now. Previously the error was repeating continuously.  Now it spits out a few error lines and then finishes with the below error: 

NMI watchdog: Watchdog detected hard LOCKUP on cpu 3

I tried installing a new graphics driver for the laptop video card "AMD Radeon(TM) Vega 3 Graphics".  I tried to install [Radeon&#8482; Software for Linux® version 18.20 for Ubuntu 18.04]("https://www2.ati.com/drivers/linux/amdgpu-pro-18.20-673703-ubuntu-18.04.tar.xz")

But that doesn't seem to have fixed it.

---

### Post by Impavidus on 2020-02-19
Can you find any clues in the log files? Problems like this should normally be logged. I'd expect something in syslog or kern.log. Have a look in /var/log/. I don't really expect your graphics driver or wine to have anything to do with it. Which kernel do you run? Use```
uname -r
```to see.

> **andrew752 said:**
> 
I then selected to boot via advanced mode and then chose recovery, then chose to exit recovery and log in via normal mode.  I managed to get back to the ubuntu GUI desktop, but the graphics have changed.  All the icons are much larger.  The display has changed.
That is to be expected. When booting via recovery mode, the system doesn't use proprietary graphics drivers and may end up using a different screen resolution.

AMD graphics drivers are nowadays built into the kernel, if you have the recent 5.3 kernel. Ubuntu 18.04 can come with two different kernels, 4.4 or 5.3. The graphics driver you tried to install is for a specific kernel. But you shouldn't install graphics drivers from websites. The additional drivers utility can tell you which drivers to install and install them with a few clicks.

---

### Post by andrew752 on 2020-02-19
Its gotten worse.  After trying to install some video drivers, I made it worse.  It wouldn't even go into the recovery GUI mode.  I could only get the root shell.  So I decided to just blow away the ubuntu partition and reinstall windows and re-setup the dual boot system I had before.  Now when I boot my laptop, I go to a screen that says "gnu grub version 2.02 Minimal BASH-like line editiing is supported" and presents a prompt "grub>"

So I cant even boot from the ubuntu usb now to reinstall it.  And I can't even seem to to get into bios.

---

### Post by Impavidus on 2020-02-20
Grub is the Linux boot loader that attempts to load an operating system. It fails, because it needs some files that used to be on the Ubuntu partition that you just deleted. But that shouldn't affect your ability to boot a live disk. To do that, you have to use the bios/uefi to select booting from the live disk before it transfers control to grub. And your problem doesn't affect your ability to get into the bios/uefi, but that may be difficult to access anyway.

---

### Post by andrew752 on 2020-02-20
Yeh, I have a lot to learn regarding ubuntu.  Anyway, I went into bios via my windows 10 OS (laptop is dual booted) and deleted the option to boot from ubuntu.  I just reformatted the partition and reinstalled ubuntu.

---

