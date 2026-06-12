---
title: "After an update of my Nvidia drivers, Ubuntu won't boot."
date: 2016-04-15
forum: New to Ubuntu
---

### Post by egg2 on 2016-04-15
Hello, I am kinda new to Ubuntu so please be patient. 

I've been having difficulties with my Nvidia drivers. I was never able to shutdown my pc without the screen freezing on my desktop, forcing me to manually force shutdown. I found on some forums that this could be because of my Nvidia drivers. So I switched from the Nouveau drivers to a proprietary one, rebooted, and Ubuntu never booted again. I can get to Ubuntu, with Linux 4.2.0-27 generic but not Linux 4.2.0-35 generic. 

Also, even on this kernel, Ubuntu will randomly freeze (often when I try to access Software and updates). 

Feel free to ask me to run certain commands for info. 

Thanks in advance.

Edit: I've been watching videos for 30mn, decided to open Software and updates, went to Additional drivers, and I didn't make 10s before Ubuntu froze. Can't do anything now. So there definitely is a correlation, that's not just a coincidence.

---

### Post by egg2 on 2016-04-16
After installing the latest Nvidia drivers, now even the previous version won't boot up, telling me "the system is running in low graphics mode" and not allowing me to proceed. Thing is, I can't even try and launch things from a live key, because Linux will try to boot first even after I've changed the boot order in the bios. So I'm completely blocked. Also grub only comes up once in a blue moon when I hold shift at start, I sometimes have to reboot 50 times before I can get to grub.

---

### Post by RobGoss on 2016-04-16
Hello and welcome, A few weeks ago after booting up one of my machines I had the same problem but could no find out what was causing this. I was in the process of upgrading anyway to 16.04 so I did not waist a lot of time trying to trouble shoot it. After the fresh install of Ubuntu 16.04 all was ok...

You might find this post helpful with your problem
[http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

---

### Post by Geoffrey_Arndt on 2016-04-16
Hard to diagnose without knowing a thing about your machine.   System specs please.    Also, what method did you try "originally" to install the proprietary drivers?    Did you install more than once?

---

