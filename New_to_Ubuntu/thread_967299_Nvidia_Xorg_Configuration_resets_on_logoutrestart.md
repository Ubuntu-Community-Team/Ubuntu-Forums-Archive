---
title: "Nvidia Xorg Configuration resets on logout/restart"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by poolmanjim on 2008-11-01
I'm pretty new to Linux and very new to Ubuntu so please go easy on me.

First, I have reviewed countless articles that have almost the same header as this one and not a one of them has been able to help me.

**To start, my setup...**
1x Acer P223w 22in Wide
1x Dell 17in Normal

AMD Athlon64 4600+
2GB RAM
Nvidia GeForce 8600GT

Ubuntu 8.10 with most current updates.
Nvidia glx-173 drivers

This is a fresh install, the only modifications have been enabling the Nvidia drivers and attempting to configure the montiors.

**What I want to do**
I would like to have the Acer monitor act as my primary monitor (the one immediately in front of me) and my Dell act as a second monitor. I would like them both to act independently almost as if they were on two separate systems, I believe enabling both to act as "Separate X Screens" would accomplish this.

**The Problem**
I first began reading on how to do this and everyone suggested I manually edit the Xorg.conf file to make the monitors function correctly. I never had any luck with this, in fact, it proved to only create more problems. I don't have the exact configuration(s) I tried as they were obtain by doing searches and when they didn't work I reverted to backups.

I then attempted to use the Nvidia-settings GUI provided by the driver install. I followed the directions and did exactly as many of the forums suggested (using sudo,gksu,my acct and my acct after being added to root). Everytime I rebooted/logged-out/Ctrl+Alt+Bksp my Xorg.conf file would reset and nothing would change.

I then tried doing TwinView and still had no success. I then decided that I had installed the drivers incorrectly so I just reinstalled the OS and started from scratch. I repeated the process almost to the letter and I still didn't have any luck.

I hope this was enough information. I tried to give as much as I could and be as detailed as I could. Let me know if there is anything else that is needed or if I misformatted this or something. 

Thanks in advance for any and all help!

Poolmanjim

P.S. My Xorg.conf file is still the default one after all these changes.

---

