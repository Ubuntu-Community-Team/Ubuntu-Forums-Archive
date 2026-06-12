---
title: "ubuntu 20.04 lts - drive issue with external usb enclosure"
date: 2020-04-30
forum: New to Ubuntu
---

### Post by jwhiz56 on 2020-04-30
the blkid results:
/dev/sdc1: LABEL="DATA" UUID="585CEDA25CED7B60" TYPE="ntfs" PTTYPE="atari" PARTUUID="140b91dd-01"
/dev/sdh1: LABEL="2tb sata" UUID="16884D7E884D5D7D" TYPE="ntfs" PARTUUID="7034c302-01"
/dev/sdf1: LABEL="500GB spare" UUID="406668E36668DB64" TYPE="ntfs" PARTUUID="307ece58-01"
/dev/sde1: LABEL="500GB spare" UUID="E46AA01E6A9FEB94" TYPE="ntfs" PARTUUID="b91a0656-01"
/dev/sda1: LABEL="960gb spare ssd" UUID="3AF05EA8F05E6A61" TYPE="ntfs" PARTUUID="19a298c7-01"
/dev/sdd1: LABEL="1TB spare" UUID="F4D2F307D2F2CD3C" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="066813da-6360-40a6-a908-b74013eeb77d"
/dev/sdi2: UUID="4251d985-c5b7-497a-b7e2-0989c6936040" TYPE="ext4" PARTUUID="9f410f66-4354-4609-9823-a8647ef4842b"
/dev/sdg1: LABEL="2tb sata" UUID="0C925C7D925C6CE8" TYPE="ntfs" PARTUUID="481c4239-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/sdb1: PARTUUID="ed9daf22-0db9-4bbc-89e0-b4ffc45fbc75"
/dev/sdi1: PARTUUID="a7b6ad08-5b0f-473f-9f66-4efe96b9a8fb"

the /dev/sdi2: drive is drive #2 in my enclosure.  it's a windows boot drive.  under 18.04 lts, it has a UUID and i can mount it.  under 20.04 it doesn't have a UUID and my mount command times out using the old UUID from 1804.  

here is my fstab contents:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/4251d985-c5b7-497a-b7e2-0989c6936040 / ext4 defaults 0 0
/swap.img	none	swap	sw	0	0
# 960GB SSD
UUID=3AF05EA8F05E6A61 /storage/disk1 ntfs defaults 0 0
# 500GB HD
UUID=2A7045C07045938B /storage/disk2 ntfs defaults 0 0
# 1TB HD
UUID=585CEDA25CED7B60 /storage/disk3 ntfs defaults 0 0
# 500GB HD
UUID=E46AA01E6A9FEB94 /storage/disk4 ntfs defaults 0 0
# 1TB HD
UUID=F4D2F307D2F2CD3C /storage/disk5 ntfs defaults 0 0
# 500GB HD
UUID=406668E36668DB64 /storage/disk6 ntfs defaults 0 0
# 2TB HD
UUID=0C925C7D925C6CE8 /storage/disk7 ntfs defaults 0 0
# 2TB HD
UUID=16884D7E884D5D7D /storage/disk8 ntfs defaults 0 0



can anyone tell me why this is happening, what i'm doing wrong and how to fix it?

thanks in advance
john

---

### Post by dino99 on 2020-05-01
Do you get warning/error logged into 'journalctl -b' output against that usb chip ? (maybe not well identified)

---

### Post by jwhiz56 on 2020-05-01
there are 8 drives in the external usb enclosure.  it doesn't make any sense that drive 2 of 8 would have an issue and the other 7 are just fine.  there doesn't appear to be any USB errors in the log.  just the timeout on that device.

john

---

### Post by jwhiz56 on 2020-05-01
also, i have removed the drive from the enclosure and connected it to my windows computer and it's fully accessible.

john

---

### Post by jwhiz56 on 2020-05-01
[COLOR=#000000]the 20.04 blkid results, sorted by device :[/COLOR][COLOR=#000000]

[SIZE=1]/dev/sda1: LABEL="960gb spare ssd" UUID="3AF05EA8F05E6A61" TYPE="ntfs" PARTUUID="19a298c7-01"[/SIZE][/COLOR][SIZE=1]
[COLOR=#000000]/dev/sdb1: PARTUUID="ed9daf22-0db9-4bbc-89e0-b4ffc45fbc75"[/COLOR]
[COLOR=#000000]/dev/sdc1: LABEL="DATA" UUID="585CEDA25CED7B60" TYPE="ntfs" PTTYPE="atari" PARTUUID="140b91dd-01"[/COLOR]
[COLOR=#000000]/dev/sdd1: LABEL="1TB spare" UUID="F4D2F307D2F2CD3C" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="066813da-6360-40a6-a908-b74013eeb77d"[/COLOR]
[COLOR=#000000]/dev/sde1: LABEL="500GB spare" UUID="E46AA01E6A9FEB94" TYPE="ntfs" PARTUUID="b91a0656-01"[/COLOR]
[COLOR=#000000]/dev/sdf1: LABEL="500GB spare" UUID="406668E36668DB64" TYPE="ntfs" PARTUUID="307ece58-01"[/COLOR]
[COLOR=#000000]/dev/sdg1: LABEL="2tb sata" UUID="0C925C7D925C6CE8" TYPE="ntfs" PARTUUID="481c4239-01"[/COLOR]
[COLOR=#000000]/dev/sdh1: LABEL="2tb sata" UUID="16884D7E884D5D7D" TYPE="ntfs" PARTUUID="7034c302-01"[/COLOR]
[COLOR=#000000]/dev/sdi1: PARTUUID="a7b6ad08-5b0f-473f-9f66-4efe96b9a8fb"
[/COLOR][COLOR=#000000]/dev/sdi2: UUID="4251d985-c5b7-497a-b7e2-0989c6936040" TYPE="ext4" PARTUUID="9f410f66-4354-4609-9823-a8647ef4842b"[/COLOR]
[COLOR=#000000]/dev/loop0: TYPE="squashfs"[/COLOR]
[COLOR=#000000]/dev/loop1: TYPE="squashfs"[/COLOR]
[COLOR=#000000]/dev/loop2: TYPE="squashfs"[/COLOR]
[COLOR=#000000]/dev/loop3: TYPE="squashfs"[/COLOR]
[COLOR=#000000]/dev/loop4: TYPE="squashfs"[/COLOR]
[COLOR=#000000]/dev/loop5: TYPE="squashfs"[/COLOR]
[COLOR=#000000]/dev/loop6: TYPE="squashfs"[/COLOR]

[/SIZE]my previous posts in this thread were incorrectly stated.  

/dev/sdb1: is the issue.  it doesn't have a UUID under 20.04 where it did under 18.04 (see below, /dev/sdg1).

the 18.04 blkid results:

[COLOR=#000000][INDENT][SIZE=1]/dev/sda2: UUID="53f4c033-fca8-4887-a544-a9e84b224e84" TYPE="ext4" PARTUUID="6840b843-bc52-45cf-8333-fb4a2885c922"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/sda1: PARTUUID="377eca71-e5b2-4e9d-9e28-ad8f928c4165"
/dev/sdf1: LABEL="960gb spare ssd" UUID="3AF05EA8F05E6A61" TYPE="ntfs" PARTUUID="19a298c7-01"
/dev/sdg1: LABEL="Windows" UUID="2A7045C07045938B" TYPE="ntfs" PARTUUID="881c2b75-1369-412c-905a-b9df10269d6c"
/dev/sdh1: LABEL="DATA" UUID="585CEDA25CED7B60" TYPE="ntfs" PARTUUID="140b91dd-01"
/dev/sdj1: LABEL="500GB spare" UUID="E46AA01E6A9FEB94" TYPE="ntfs" PARTUUID="b91a0656-01"
/dev/sdi1: LABEL="1TB spare" UUID="F4D2F307D2F2CD3C" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="066813da-6360-40a6-a908-b74013eeb77d"
/dev/sdk1: LABEL="500GB spare" UUID="406668E36668DB64" TYPE="ntfs" PARTUUID="307ece58-01"
/dev/sdl1: LABEL="2tb sata" UUID="0C925C7D925C6CE8" TYPE="ntfs" PARTUUID="481c4239-01"
/dev/sdm1: LABEL="2tb sata" UUID="16884D7E884D5D7D" TYPE="ntfs" PARTUUID="7034c302-01"

[SIZE=2]
assumptions:

18.04  vs  20.04
sda1   ==  sdi1 (linix partition)
sda2   ==  sdi2 (linix partition)
sdf1    ==  sda1
sdg1   ==  sdb1
sdh1   ==  sdc1
sdi1    ==  sdd1
sdj1    ==  sde1
sdk1   ==  sdf1
sdl1    ==  sdg1
sdm1  ==  sdh1
[/SIZE]
[/SIZE][/INDENT][/COLOR]
[COLOR=#000000][/COLOR]

---

### Post by Holger_Gehrke on 2020-05-01
From 'man fstab':
> 
It's also possible to use PARTUUID= and PARTLABEL=. These partitions identifiers are supported for example for GUID Partition Table (GPT).

Since the partition still has a PARTUUID you can at least try whether you can mount it that way. I don't have any idea how the normal UUID got lost ...

Holger

---

### Post by jwhiz56 on 2020-05-01
using the PARTUUID didn't work.  

messages in the journal file are:

storage-disk2.mount: Mount process exited, code=exited, status=12/n/a
storage-disk2.mount: Failed with result 'exit-code'.
failed to mount /storage/disk2.
dependency failed for Local File Systems.
local-fs.target: Job local-fs.target/start failed with result 'dependency'.


john

---

