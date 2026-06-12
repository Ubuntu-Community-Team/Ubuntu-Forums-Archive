---
title: "Linux and Hardware....."
date: 2007-12-14
forum: Other OS Talk
---

### Post by ElEdwards on 2007-12-14
Are the Debian-based distros the only ones that truly recognize the most hardware without "fiddling"?

Basis for my question:
I have a Linksys PCMCIA Wireless Card (WPC54G)..... Ubuntu, Kubuntu, Mint and other Debian distros immediately see my card without any intervention.

Fedora doesn't...... OpenSuse doesn't..... FreeSpire doesn't...... and that's all I've really played with so far.

I'm using Mint 4.0 right now....but just thought I'd ask before I try more distros for a while.
....and I know I could use ndiswrapper one way or another... but right now, I don't have time to try that.

Thanks for your advice and patience ;)
El

---

### Post by tgalati4 on 2007-12-14
Each distro family has a different hardware detection algorithm.  SLED 10 detects my Dell 992 monitor and selects the appropriate modline 1280 by 1024 at 99 Hz, but Ubuntu defaults to 60 Hz.  Copying the modlines from the SLED 10 xorg.conf file to Ubuntu's xorg.conf worked.  So hardware detection is different.  Also SLED 10 allows power-button suspend-to-RAM in 5 seconds.  Ubuntu Gutsy borked suspend-to-RAM.

Trying different distros is really the only way to find out which works best for your system.  Sometimes you can cross-fertilize to get things to work properly.  If nothing else, it's a learning opportunity.

For your wireless, print out a copy:

$lsmod > lsmod_output.txt

and

$lspci -vv . lspci_output.txt

and compare between distros to see what modules are being loaded and how the hardware is being detected.

---

