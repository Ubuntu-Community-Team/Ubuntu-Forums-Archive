---
title: "FYI ONLY Kernel Panic Has Resolved Itself"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-04-09
The Upgrade Manager came on-screen only moments after powering up the 'puter this morning. I shut down all the open programs (Chrome browser, Thunderbird, and Thunar). Ran the upgrade of about 90 meg. Went for coffee and came back to see the upgrade was jammed. I waited a while and then closed the manager. My next thought was a re-boot and that also jammed the OS and I saw (in text mode) something about a kernel panic. The OS would not shutdown and re-boot automatically. ALT-SysRq REISUBK would not re-boot, so I used the re-boot button on the box.

On rebooting I tried to load the new OS (kernel). That locked the screen, mouse and keyboard and again I had to use the button on the computer.

On next reboot, I selected a Previous Kernel. That worked fine and after logging in, I selected Update Manager to see if I could learn what had happened. It wanted to install 49 programs and remove 8 and as several of the 49 were the kernel I OK'd, entered my password and watched Linux work it's magic.

The UManager asked for a re-boot. I did that normally and the OS got back to near normal. My mistake was selecting recovery mode before finishing the updated kernel parts d/l'd by the manually selected Update Manager. From Recovery Mode, neither dpkg nor fsck would complete. /sda3 ( / ) was reported as faultless but the OS hung over /sda5 (home).

This time Alt-SysRQ REISUBK worked and I booted into the 3.2.0-40-generic-pae kernel. All seems OK.

Thank you Mr. Torvalds and the Linux Community.

---

