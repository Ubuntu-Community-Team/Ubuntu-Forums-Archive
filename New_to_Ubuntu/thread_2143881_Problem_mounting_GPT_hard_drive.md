---
title: "Problem mounting GPT hard drive"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by bridgie on 2013-05-10
Hello all,

First of all excuse me if I'm not clear in my post. I'm a complete novice when it comes to Linux so bear with me. Also mods, if this is in the wrong place please could you move it?

A few days ago, I installed Bitdefender Total Security on my Windows 8 PC. It comes with an anti-theft feature, which I decided to try out. You enter a code on their website, which then locks the laptop, rendering it unusable without said code. The problem is that, when trying to enter the code, the keyboard doesn't work (tech support's suggestion of using a USB keyboard didn't work either).

Tech support then sent me a workaround - creating a Bitdefender Rescue USB, booting from that, then deleting a file from my hard drive which then removes the lock from my computer.

The reason I am posting in this forum is that Bitdefender Rescue Mode is based on XUbuntu.

I had no problem in creating the Rescue USB, or booting into Rescue Mode. My problem is that my hard drive does not show up when I am in Rescue Mode, so I cannot delete the file I need. I have tried using terminal to mount the hard drive, but keep coming up against errors. The hard drives show up both when I use the fdisk command and in GParted.

From what I have gathered, it appears to be because the file system of my hard drive (which is solid state, if that helps) is GPT. It seems that Ubuntu has problems mounting it, if I understand correctly.

So, is there any way I can access my hard drive? Any help would be hugely appreciated, as I've been locked out of my laptop for five days now, and it's becoming more than just an inconvenience.

Many thanks in advance,
Bridgie

---

### Post by bridgie on 2013-05-10
Can anyone help me? Bitdefender tech support are being no help whatsoever.

---

### Post by oldfred on 2013-05-10
Please do not bump more than once per 24 hours. We all are volunteers and respond when we can.

gpt is not the issue. It just works.

Is this an UltraBook with the small SSD that uses RAID? That often causes mounting issues.

Post this from your Linux live system terminal, you can just copy & paste here:

sudo fdisk -lu
sudo parted -l

---

### Post by arpanaut on 2013-05-10
It could also be the hibernation feature in win8 and quick boot that is preventing Linux OS from mounting the file system as it sees it as "unclean" Once you get back into the system you may want to look into disabling this feature in Win 8.

---

### Post by bridgie on 2013-05-10
Thanks very much for your replies, and apologies for bumping so quickly.

My machine is a Sony Vaio S Series laptop with a 500GB solid state drive.

I'm unable to access the internet in Rescue Mode, so cannot copy and paste. Here are the results of the commands, typed out:

bitdefender@bitdefender:[COLOR=#444444][FONT=arial]˜$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda' ! The util fdisk doesn
't support GPT. Use GNU Parted.

Disk /dev/sda: 256.1 GB, 256060514304 bytes
256 heads, 63 sectors/track, 31009 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb033c277

    Device Boot         Start               End           Blocks    Id   System
/dev/sda1                      1   4294967295  2147483647+   ee   GPT

Disk /dev/sdb: 256.1GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 8005 MB, 8005787648 bytes
32 heads, 63 sectors/track, 7756 cylinders, total 15636304 sectors
[/FONT][/COLOR][COLOR=#444444][FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=arial]Disk identifier: 0x26564f45

[/FONT][/COLOR][COLOR=#444444][FONT=arial]    Device Boot         Start               End           Blocks    Id   System
/dev/sdc1    *               63       15636095       7818016+    b    W95 FAT32




[/FONT][/COLOR]bitdefender@bitdefender:[COLOR=#444444][FONT=arial]˜$ sudo parted -l

Error: /dev/sdb: unrecognised disk label

Model: Kingston DataTraveler 102 (scsi)
Disk /dev/sdc: 8006MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number   Start      End         Size        Type       File system   Flags
  1           32.3kB  8006MB   8006MB   primary   fat32             boot


Thanks again for your help![/FONT][/COLOR]

---

### Post by oldfred on 2013-05-10
Does bitdefender do something to partition tables?
> [COLOR=#444444][FONT=arial]Disk /dev/sdb doesn't contain a valid partition table
[/FONT][/COLOR]

Otherwise you can try testdisk on sdb, not sure if MBR(msdos) or UEFI/gpt. You may have to try both from testdisk to see what it says.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Are drives in some sort of RAID?

---

### Post by bridgie on 2013-05-10
Thanks again for replying!

As far as I'm aware Bitdefender does nothing to partition tables.

I tried installing testdisk through terminal, but as I can't get on the internet in rescue mode it didn't work.

There shouldn't be a problem with my hard drive as the laptop's only a month old.

Not entirely sure what RAID is, but I've never heard it in conjunction with my laptop.

Unless anyone has any other suggestions, I guess I'll just have to wait for a reply from Bitdefender, although I don't hold out much hope for them.

---

### Post by oldfred on 2013-05-10
It may be how your SSD are configured as you have two 256GB drives not one 500GB.

---

### Post by bridgie on 2013-05-11
Any ideas what I could do if that were the problem?

---

### Post by oldfred on 2013-05-11
If you do not have a partition table and testdisk cannot recover one, it is something with Windows or a Intel SRT which is RAID and just caching Windows to make it faster. But with SSD as main drive that should not be required.
Not sure what else you can do?

Your Windows install should be in sda anyway. So can you access that with testdisk or by force mounting the NTFS partition?

 sudo mkdir /media/windows
sudo mount ntfs-3g -o rw /dev/<device-name> /media/windows
if you get a message regarding Windows not being shutdown properly, then run the following command to force the mount
But better to run chkdsk from a Windows repair CD first, only use this if you have to copy data.
sudo mount ntfs-3g -o force,rw /dev/<device-name> /media/windows

---

