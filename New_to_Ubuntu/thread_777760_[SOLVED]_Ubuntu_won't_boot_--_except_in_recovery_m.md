---
title: "[SOLVED] Ubuntu won't boot -- except in recovery mode -- then stalls out"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by willz06jw on 2008-05-01
Thanks for your help,

I just installed Hardy Heron on the whole second hard drive on my computer.  When I select Ubuntu in grub, it spits out a bunch of errors before stopping completely about an hour later (without ever entering gnome).

But when I select Ubuntu recovery mode, it spits out errors, but eventually boots into Ubuntu.  After it boots and I open a web browser or two, it stalls and locks up the machine.

What could the problem be?  Which logs should I attach to this question to help you help me find the problems?

Thanks,
Will

---

### Post by cmnorton on 2008-05-01
What are your computer's specifications? 

Are you dual-booted?

Offhand, this sounds like a graphics problem, but I would use recovery mode and then go check your logs, /var/log/messages and /var/log/syslog for starters.

You could use dpkg-reconfig xserver-xorg from recovery mode, and select either vesa or vga -- forgetting for the moment that your graphics won't look good -- just to see if you could boot normally. 

This is a major step, and you would need to back up your /etc/X11/xorg.conf file before doing it. Taking the default answers, other than selecting a different display driver, usually is a safe way to run it.

---

### Post by willz06jw on 2008-09-03
The reason I was getting thousands of ATA.04 messages when I booted up (it was also causing a horribly long boot) was that my hard drive was failing.  I changed hard drives and it worked

Will

---

