---
title: "Problems Installing LabVIEW Run-Time Engine for Ubuntu 11.04"
date: 2011-05-25
forum: Programming Talk
---

### Post by SaveZeeDay91 on 2011-05-25
I'm relatively new to Ubuntu and its community, but have been pleasantly surprised with how easy troubleshooting has been.  Unfortunately, I've spent the last two days trying to install the LabVIEW Run-Time Engine, but keep coming up short.

I've tried a number methods from the following threads to no avail:

[http://ubuntuforums.org/showthread.php?t=1110905](http://ubuntuforums.org/showthread.php?t=1110905)

[http://ubuntuforums.org/showthread.php?t=726092](http://ubuntuforums.org/showthread.php?t=726092)

The problem I'm having now is that despite having the ia32-libs, here is what comes up:

Input:  "sudo alien - k --scripts labview-2009-rte-9.0.1-1.i386.rpm"
Response:  "labview-2009-rte-9.0.1-1.i386.rpm is for architecture i386; the package cannot be built on this system".

Alien is required because Ubuntu isn't compatible with the .rpm format.

Your help would be immensely appreciated since we use LabVIEW programs to display, manipulate and simulate our spectra.

SZD91

---

### Post by Zugzwang on 2011-05-25
Look here: [http://ubuntuforums.org/showthread.php?t=483757](http://ubuntuforums.org/showthread.php?t=483757)

You might want to boot a 32-bit version of Ubuntu from CD and run "alien" from there. The package you then obtain should be installable by "dpkg --force-architecture" (or so) on your actual 64-bit installation of Ubuntu.

---

### Post by tommpogg on 2011-07-07
Take a look [here]("http://ubuntuforums.org/showthread.php?t=1048722").
I hope it can be of some use

---

