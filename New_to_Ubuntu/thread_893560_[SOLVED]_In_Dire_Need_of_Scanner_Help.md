---
title: "[SOLVED] In Dire Need of Scanner Help"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by lenny15 on 2008-08-18
Hi, I have my ubuntu 7.1 Linux system up and running. My printer works fine. I have a new USB Scanner, a HP scanjet 3970. XSANE doesn't see it. I have searched and searched and cannot find any info on how to fix this. I am not a programmer. Can anyone tell me what to do?
Thanks in advance

---

### Post by kansasnoob on 2008-08-18
Well first go to Synaptic and type sane into the search window. Now make sure you have hplip installed. (I'd also tick hplip-gui for installation, but I'm a gui guy) If it's not then tick it for installation. Then also tick libsane and libsane-extras.

In the description for libsane-extras it says:

> This package includes some backends that are not yet included into the
official SANE distribution. Currently, they are :
  * epkowa (some EPSON scanners)
  * geniusvp2 (Genius ColorPage-Vivid Pro II)
  * hp_rts88xx (HP ScanJet 4400C, HP ScanJet 4470C)
  * hp3900 (HP ScanJet 3970C, HP ScanJet 4070, HP ScanJet 4370)
  * ls5000 (Nikon LS-5000 ED, Coolscan 5000 ED)

Cool huh?

---

### Post by kansasnoob on 2008-08-18
I may be out for a while, so just in case that doesn't work (it should) the sane driver is here:

[http://sourceforge.net/projects/hp3900-series/](http://sourceforge.net/projects/hp3900-series/)

Instructions to build here:

[http://ubuntuforums.org/showthread.php?t=288751](http://ubuntuforums.org/showthread.php?t=288751)

Hopefully that won't be necessary. I suck at building from .deb and such!

---

### Post by lenny15 on 2008-08-18
YEOW !!!!!!!!! PROBLEM SOLVED!!  Thanks! Finally a solution!  The scanner works great. The previous advice I was getting was to type in lines of code in some window I didn't know how to find. You have saved me. It doesn't get any better than this!!!!!!!!  Thanks a ZILLION!! 
It would seem you are the only person that knows about this!!
John

---

### Post by alienexplorers on 2008-08-18
Please mark this thread as solved.  Go to your first post and select thread tools.  Open the menu and select thread solved.

Thanks.....

---

### Post by timcredible on 2008-08-18
also, install and try kooka, it's another scanning program that is better imo than xsane.

---

