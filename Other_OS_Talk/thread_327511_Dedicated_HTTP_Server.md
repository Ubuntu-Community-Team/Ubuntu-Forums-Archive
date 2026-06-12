---
title: "Dedicated HTTP Server"
date: 2006-12-29
forum: Other OS Talk
---

### Post by PacShady on 2006-12-29
Hey all

I have an old dual-CPU Pentium Pro 180MHz system that I'm looking to turn into a small web server on my home network. But I'm having a little trouble going about it.

What's the best starting distro to use on such an old crappy system? I don't need X, but I do need Apache, MySQL, PHP, SSH and SFTP (so I don't need to physically do stuff on it), and it needs to be SMALL (the hard drive ain't too big). I can install it using a CD (preferably using SYSLINUX as opposed to ISOLINUX, so may need a boot floppy), but it can't be CD-based (like Devil-Linux for instance), because I don't think the power supply on this box is strong enough to easily run both a hard drive and a CD-ROM effectively at the same time for general use (the box was originally designed for a much smaller system using one CPU instead of two).

Any ideas on the best way to go about this?

'Shady

---

### Post by jdhore on 2006-12-29
if i was you, i'd try a HD install of Damn Small Linux and then install the packages you need via MyDSL or apt-get/Synaptic...it'll run pretty decently on those specs and you get a GUI...if it happens to NOT, run well, then i'd suggest maybe trying Smoothwall and adding the other stuff onto it...i've run Smoothwall on a P1 100MhZ box with 8MB RAM before...

---

### Post by PacShady on 2006-12-30
I'm actually playing around with DSL now, and it does seem like it might do the job, after I install XAMPP or something on it. But I have noticed a problem, that haunted me when previously trying to install SmoothWall on it for the purpose of a firewall, fast returning to irritate me.

It would seem that the combination between Linux, my dual-CPU PPro motherboard, and the network card doesn't like to work nicely for me. System installs fine (except for the fact that, following the HDD install instructions for DSL [here]("http://www.damnsmalllinux.org/dsl-hd-install.html") appears to do a Frugal install instead of a proper hard drive install, which means my already limited RAM is being consumed by what I assume is a RAM disk), it detects my network card and my firewall assigns an IP address to it. However, that's as far as communication goes. I can't ping. I can't access sites or other computers on the network. The funny thing is though, if I pass the 'nosmp' option at boot, everything works fine.

Anyone know what might be causing this?

'Shady

---

