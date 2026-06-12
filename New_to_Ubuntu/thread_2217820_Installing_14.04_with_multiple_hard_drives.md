---
title: "Installing 14.04 with multiple hard drives"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by patchwerkadams on 2014-04-18
Hello,

My computer has 3 storage devices, a standard HDD with Windows 8.1 on it, and two solid states that I use for games. If I were to install Ubuntu 14.04 by selecting the option to install it alongside Windows, will it just partition the main hard drive that I use? or will it attempt to split the solid states as well? I'm new to this and I don't want to screw up my partition tables by doing anything that I don't fully understand.

Any help on this would be greatly appreciated.

---

### Post by grahammechanical on 2014-04-18
We tell the installer which drive we want Ubuntu to be installed on. But to be on the safe side, disconnect those two SSDs.

My main concern would be the fact that Windows 8 is on the machine. In this and other sections of the forums there are many posts from people who have problems with dual booting Ubuntu with Windows 8 and in those threads is advice on the best way to do it. Please check those posts as part of your preparation.

Regards.

---

### Post by oldfred on 2014-04-18
Is Windows 8 UEFI or BIOS Booting? 
Either way you must have fast boot off or the always on hibernation.
And you need to use Windows partition tools to shrink Windows to make unallocated space, but do not create any partitions. Immediately reboot so it can run chkdsk and repair its size change. Double check that fast boot is still off as Windows likes to keep turning it or secure boot back on.

If UEFI see link in my signature.

---

