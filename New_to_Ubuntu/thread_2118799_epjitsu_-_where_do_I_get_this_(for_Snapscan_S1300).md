---
title: "epjitsu - where do I get this? (for Snapscan S1300)"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by noideawhatimdoingatall on 2013-02-22
*SOLVED*

Hi

I'm reading this thread: [B][http://ubuntuforums.org/showthread.php?t=1461915](http://ubuntuforums.org/showthread.php?t=1461915)

[/B]I'm still fairly new to Ubuntu, but I can follow instructions and know my mouse from my space bar.

It seems fairly straight forward, apart from the fact I don't have /usr/share/sane/epjitsu/ 

In my /sane I just have "Xsane" which I installed earlier.

I'm assuming I have to install the epjitsu backends(?) from somewhere? There is a ppa given in the thread but it doesn't seem to work.

I can/'t find anything in the Software Centre either.

Any ideas??

Thanks):P

---

### Post by schragge on 2013-02-22
You don't need the PPA. The package *libsane* is part of the main Ubuntu distribution. It includes epjitsu backend since oneiric (Ubuntu 11.10).

It's clear from the linked thread that you need to create the directory */usr/share/sane/epjitsu/* and put there the firmware for your scanner extracted from the Windows driver. Manually. If you have a Windows machine where you can install the driver for Snapscan S1300 then do it, locate the file *1300_0C26.nal*, and copy it over to */usr/share/sane/epjitsu/* on Ubuntu.

---

### Post by noideawhatimdoingatall on 2013-02-22
Thanks!

---

### Post by oldos2er on 2013-02-22
Please mark this thread as 'Solved' using the Thread Tools menu at the top of this page. Thanks.

---

