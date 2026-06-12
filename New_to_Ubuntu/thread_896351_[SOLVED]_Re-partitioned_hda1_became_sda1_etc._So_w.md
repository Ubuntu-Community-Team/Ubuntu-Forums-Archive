---
title: "[SOLVED] Re-partitioned: hda1 became sda1 etc. So what..?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by 2CV67 on 2008-08-21
Hi community!

I just did a clean install of Hardy to replace my earlier Gutsy.

Figuring this would be a good opportunity, I re-did my partitioning, using Gparted, to add a /home partition.

As far as I can tell, all this went OK & Hardy is running OK, but I am surprised to find all my partitions have changed name.

Previously I had 4 primaries: hda1, hda2, hda3 & hda4.
Now I have 3 primaries, plus an extended with 2 logicals: sda1, sda2, sda3, sda5 & sda6.

I did not deliberately ask for the sda names, nor did I notice where/when they appeared.

My Hard Drive is a WDC WD1200BB-22FTA0  IDE type, which I thought should use hda names.

Does this matter?
How could it have happened?
Do I need to do anything about it?
How?

Thanks for any advice!

---

### Post by fiddledd on 2008-08-21
[Here](http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce) is some info about it. It looks like you don't need to do anything.

---

### Post by mcduck on 2008-08-21
That's normal. Linux developers found out that the SATA/SCSI driver handles PATA drives better than the old PATA driver did, so they use now same driver for all hard disks. This caused the device naming to change.

You don't need to do anything about it. Everything works just like before.

---

### Post by 2CV67 on 2008-08-21
Thanks for those quick replies!

Can't say I understood much in the linked article (from 2006...) except:> Really. There is a risk that the new drivers won't work for you, or may harm your data (unlikely, but not impossible). If you want to be safe, use the old drivers. 

Hopefully you are both right about not needing to do anything, so I won't...

Thanks again!

---

### Post by mcduck on 2008-08-21
> **2CV67 said:**
> Thanks for those quick replies!

Can't say I understood much in the linked article (from 2006...) except: 

Hopefully you are both right about not needing to do anything, so I won't...

Thanks again!

THat was 2 years ago. If there was any problems, the change wouldn't be in normal use yet.

---

### Post by 2CV67 on 2008-08-21
> **mcduck said:**
> If there was any problems, the change wouldn't be in normal use yet.

Ho! Ho! Ho! :-P

Ok, I will believe you this time!

Seriously, thanks for the replies!

---

