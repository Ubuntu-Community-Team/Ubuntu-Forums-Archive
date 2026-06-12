---
title: "Server edition cannot see other hard drive can anyone help?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by mark.tj on 2008-08-11
Just installed Ubuntu Server 8.04 to my IBM X-Series 206 server. It had a much older version of Ubuntu on it before and was running 2 300gb disks in RAID. I did all this ages ago so cannot remember how I managed to set it all up before so please treat me as a complete newbie

I backed everything up and decided to remove the RAID to double the capacity. I have disabled RAID in the bios and installed Ubuntu again but my other windows computers only seem to be able to see the one disk or total size 275 gb so something is wrong.

If I type lshw -C Disk I get the following information on the disks;

Disk:0
description: ATA Disk
product: Maxtor 6v300f0
verdor: Maxtor
physical id: 1
bus info: scsi@1:0.0.0
logical name: /dev/sda
version: VA11
serial: V60HLTYG
size: 279GiB (300gb)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=00099a9a

Disk:1
description: ATA Disk
product: Maxtor 6v300f0
verdor: Maxtor
physical id: 0.1.0
bus info: scsi@1:0.1.0
logical name: /dev/sda
version: VA11
serial: V60HLV2G
size: 279GiB (300gb)
configuration: ansiversion=5 

Can anyone tell me is this working or do I need to re-install and do something differently? (Above is not cut and paste I hand keyed so any spelling mistakes are mine).

---

