---
title: "HOW-TO: ATI fglrx driver latest version"
date: 2005-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by mlomker on 2005-10-18
To discuss this thread **[click here.]("http://ubuntuforums.org/showthread.php?t=76116")**  

I am not actively supporting this how-to anymore.  Most of the problems are related to the newest cards (the drivers always seem to be 6 months behind) and I don't want to keep upgrading in order to figure out the latest problems.  This how-to has been posted as a wiki so that the community can keep it up-to-date.   

[The How-to at the unofficial ATI Wiki.]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide").

**Supported Cards**
The fglrx driver supports ATI cards from 8500 and up, with the exception of the 9100 IGP, the Mobility 9000 (IBM/Lenovo), and possibly a few others (read the release notes on the download page on ATI's website).  As of this writing the x800 cards are difficult to get working and the x1600+ cards are not supported, but check the support forum (below) for the latest information.  

**Troubleshooting**  
Review the /var/log/kern.log and Xorg.0.log files if you experience problems.  Those two files contain all of the useful error messages for troubleshooting.

**Support Forum**
My recommendation is to search Google for your error message (will often refer you to threads on the Ubuntuforums) and then search ATI's [unofficial support forum]("http://www.rage3d.com/board/forumdisplay.php?f=88").

---

### Post by mlomker on 2005-10-18
**This is the second method, using alien to convert ATI's RPM into a .deb file.**

This method is obseleted by using the first method.

---

