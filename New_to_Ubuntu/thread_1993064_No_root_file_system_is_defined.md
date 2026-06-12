---
title: "No root file system is defined"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by franksenemy on 2012-06-01
I'm trying to install Ubuntu 12.04 on an older laptop.  Everything has gone fine until a box appeared and said "No root file system is defined.  Please correct this from the partitioning menu."  

When I click the "ok" button I get the same box.

I've checked the settings but couldn't find anything that would point me to the partitioning menu.

How can I correct this?

Thanks!

---

### Post by critin on 2012-06-01
You need to [COLOR=Red]choose / [/COLOR]for the partition.  

When I see this: >  "No root file system is defined.  Please correct this from the partitioning menu."  I'm on the page that shows which partition I want to install to.  Click 'BACK' and highlight the partition and click 'CHANGE' .  On the right list, choose[COLOR=Red] / [/COLOR] and it should prepare the partition.

[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/)

The pic you want for this issue is about the middle of the page.

If this is the only OS on the laptop, just choose install on entire disk and it will (should) format and make changes itself.

---

