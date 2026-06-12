---
title: "installed gcc version 4.2.4 does not match kernel gcc version 4.2.3"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by janraem2008 on 2008-11-22
Hi,

As a beginner in Ubuntu I have been trying to install my modem over the last week. I found out that is a PCtel micromodem, found the correct (?)driver and tried to install/compile.

My version of Ubuntu is 8.04 freeware and gnome 2.22.3. After scanmodem I reset the EXTRAVERSION parameter within Makefile from '= 0.3' to "=  " 
On trying to run./setup from the command get the respons that my gcc version does notmatch the kernel gcc version:
" [I]checking for running kernel version...2.6.24
checking for ptserial...ptserial-2.6.c
checking for gcc...4.2.4
checking for kernel gcc version...4.2.3
** error
installed gcc version 4.2.4 does not match kernel gcc version 4.2.3
installing the kernel driver module is not possible
installing a different version of gcc, or your kernel, is necessary
** compilation error
please read the FAQ about reporting compilation problems
and report this problem.  A transcript of the build process
has been saved in src/make.log.  When reporting problems to
the development team, please send us this file.[/I]

What to do next? can I check these versions and reinstall? According to Synaptic, I have the following versions installed gcc : 4:4.2.3-1ubuntu6, gcc-4.2: 4.2.4-1ubuntu3, gcc-4.2-base: 4.2.4-1ubuntu3. My Kernel version is 2.6.24-21-generic.

Ideas?

Thanks

Jan

---

### Post by Zill on 2008-11-22
It sounds like your PCtel modem is a winmodem - i.e. designed for use with MS Windows.  These are notoriously difficult to use with other operating systems, such as Linux, as the drivers require Windows to work.

Although you *may* be able to get this modem working, you are quite likely to end up in "dependency hell" if you have to change gcc versions etc.

Unless you are very experienced with Linux I suggest the best solution is to buy an ethernet modem or, preferably, broadband router, which should work with Linux "out of the box".

---

### Post by janraem2008 on 2008-11-23
Thanks

I got a driver and actually only use the modem to send faxes. Just can't see the problem. newbie hé

Jan

---

