---
title: "problems with partition"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by eaterofbrainz13 on 2008-05-09
hi yes I just have a quick question. I have been dual booting windows XP with Gutsy and I recently upgraded to Hardy. Now when I start my computer it says out of range 63.9Khz / 59 hz. I have no idea what this means, but when I try to boot windows it just gives me a blank screen. Also it shows I have four types of ubuntu partitions and a memory test. Does this just mean that my old version of Ubuntu is still on my computer with my existing one?
Confused.Please help.

---

### Post by hotchkikr on 2008-05-09
that is your monitors vertical/horizontal refresh rates
You will have to get the actual numbers for your screen and put them in your /etc/X11/xorg.conf file 

as for windows, It's prolly just playing dumb with you.

oh and go with the newer version, it just leaves the old kernel versions on there for some reason (backup?) and the memory test is for your convience.

---

