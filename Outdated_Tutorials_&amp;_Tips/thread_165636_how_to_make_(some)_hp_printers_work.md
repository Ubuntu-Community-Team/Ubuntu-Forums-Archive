---
title: "how to make (some) hp printers work"
date: 2006-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by spartan777 on 2006-04-24
this worked for my 712c hewlett-packard, parallel printer. I was elated to find this fix, having searched the ubuntu forums extensively for this. nothing worked until this did. 

here's the important bit:
--------------------------------------------------------
I had the same problem with my HP Deskjet 710c. Ubuntu/Kubuntu Linux identifies
the printer properly, and everything looks fine, but the printer didn't print
anything, and there were no error messages.

The problem was solved after I edited /etc/pnm2ppa.conf as suggested.

Original lines:

version
#version  720   # 710, 712, 722 also acceptable
#version  820
#version 1000


The new edited lines:
version 710c
#version  720   # 710, 712, 722 also acceptable
#version  820
#version 1000

--------------------------------------------------------

and the site to give full credit: [http://www.linuxprinting.org/forums.cgi?group=linuxprinting.hp.general;article=8162](http://www.linuxprinting.org/forums.cgi?group=linuxprinting.hp.general;article=8162)

i'm sure this will work for many printers, like the 712c, 710c for sure, and others like the 722, 720, et cetera.

---

### Post by Nais on 2006-05-15
Wanted to give you a congrats for posting this solution.
I've been having problems with my HP710c for a while now and was becoming very frustrated. 

Such a simple solution too, sheesh. Thanks so much.

---

### Post by spartan777 on 2006-05-26
yeah, i was using a livecd with the same printer, and everything worked fine. i was astonished, so i looked at the /etc/pnm2ppa.conf, and sure enough everything was as it was supposed to be, so apparently some update or fix along the lines introduced this problem. it *is[I]* such a small problem. probably the easiest bug anyone could ever fix.

you're welcome, took me too long to find this fix, so i thought i'd make it more accessible. happy ubuntu-ing (?)

---

### Post by BatteryCell on 2006-09-11
Yea I think the newer driver listing has 710 in there by default.  Oh and just wanted to say that for me the only thing that got my 712 working was manually starting hplip (/etc/init.d/hplip), unpluging/repluging, and then starting the add printer wizard again. Just in case anyone else has this...

---

