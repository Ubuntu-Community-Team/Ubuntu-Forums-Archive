---
title: "disk problem following reboot"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by GarethA on 2008-07-19
TI'm running 8.0.4 with latest patches
couple of weeks ago I changed my partitions to have a seprate /home ... but this has been working fine too.

Yesterday with evolution running the system froze - everything went grey - eventually an error msg came back (with the no entry sign but the text was just squares?)

I tried a shutdown but although the gui closed down I had to power off (I did leave it for an hour - but just had a black screen.)

When I booted up again it's running fsck (I assume)

The following message has been looping round for 15 hours now:

[53373.68124] ata3: irq_stat 0x00000040, connection status changed
[53375.68129] ata3: SError {DevExch}
[53375.68132] softreset failed (device not ready)
[53378.68170] softreset failed (device not ready)
[53375.68186] softreset failed (device not ready)
[53375.68190] exception Emask 0x10 Sact 0x0 SErr 0x40000000 action 0xa frozen

The numbers on the left are slowly going up.

Shuold I let this run to conclusion? Is it doing anything?

---

### Post by CRCarl on 2008-07-19
The machine lockup was probably a symptom of a failing hard drive. I would suggest you start the machine with a live CD and try and take a backup of your data, then replace the drive. 

Craig

---

### Post by GarethA on 2008-07-19
Thanks Craig 

I tried booting up with my gparted livecd (which worked last week) and it failed (twice)

used my 8.0.4 livecd and everything fine - mounted all partitions no probs and got my data

rebooted and fsck ran and fixed a few issues on dev/sda1 (the partition with the OS on)

now everything 'appears' fine

should I still look at replacing HD?   PC is less than a month old

I did have a problem with the PC initially where the HD cable was not connected properly - once I did connect it properly everything has been fine.   Could this have caused a hardware problem with the HD so that it needs replacing?

I know virtually nothing about hardware and would appreciate any advice.

Gareth

---

### Post by bumanie on 2008-07-19
I would just keep a backup of important data and see how things go. Probably a minor filesystem corruption which fsck has fixed. If it happens regularly, then a suspect drive may be the issue. If it is the drive don't be surprised to hear "we  don't support linux or linux must have wrecked it." Not true of course for the latter point.

---

### Post by hyper_ch on 2008-07-19
> **bumanie said:**
> I would just keep a backup of important data

That's an advice everybody should follow - even if there are no problems ;)

---

