---
title: "Booting issues"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by clonezonedude on 2012-10-06
Hi,

Im coming here because as always I need your help plz :(

3 days ago I was using my machine when the usual updates window popped up. I installed the updates and shut down for the night. (side note, I dont have any third party sources on my update list, just the ones the system comes with)

I went to boot next morning, and now the computer doesn't go beyond the check for mounted disks and such.

I have tried skipping that part (press S) to no avail, and now I went to manual restore (press m) and this is the message I get. I can't post pictures because I'm on my phone which is a piece of garbage

[1017.608910] ata1.00: error: {unc}
[1020.741221] ata1.00: exception emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[1020.747068] ata1.00: irq_stat 0x40000008
[1020.752781] ata1.00: failed command: read FPDMA queued
[1020.758441] ata1.00: cmd 60/08:00:28:68:1c/00:00:04:00:00/40 tag 0 ncg 4096 in res 51/40:03:2d:68:1c/00:00:04:00:00/40 emask 0x409 media error) {F}
[1020:769847] ata1.00 status: {DRDY ERR}

I honestly dont know what blew up with the updates, but I hope I dont have to reinstall my OS bc I have some stuff I dont wanna lose 

Plz help me :(

Thanks ^_^;

---

### Post by newb85 on 2012-10-06
How is your machine partitioned?

Before doing anything active, I would pop in a Live CD (or USB) and make sure you can still mount and browse all your HD partitions.  Just to eliminate the possibility that one of your partitions is corrupted.

Boot Repair may be what you need.  [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

