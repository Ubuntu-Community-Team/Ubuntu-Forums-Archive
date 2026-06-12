---
title: "[SOLVED] Dual boot grief"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by spoketire on 2008-08-01
I'm setting up dual boot with xubuntu and windows xp on 2 hard drives.  Xubuntu will be on a SATA and xp will be on an ATA drive.  I have gotten both systems installed, but the GRUB menu isn't working right.  The first time I installed xubuntu, I clicked "Advanced" (the last option in the installer), and the default option for the bootloader was to put it on hd0.  After that install, my Linux drive didn't do anything when booted (just a blinking cursor), and the windows drive brought up the GRUB menu when booted. All options in the GRUB menu worked at that point.  The only problem was that my BIOS always boots the SATA(linux) drive first, and there is no way to change that. So I wanted the Linux drive to boot to the grub menu. Here's what I did:

(device.map said hd0 is sda (linux), and hd1 is sdb (windows))

```
sudo grub
root (hd0,0)
setup (hd0,0)
```
To my knowledge, that was supposed to make the linux drive bring up the GRUB menu when booted.

Then I ran FIXMBR on the windows drive, from the Windows recovery disk, to restore the windows xp bootloader.

After I did those two things, the windows drive booted windows with no grub menu (like I intended), and the Linux drive started GRUB. However, in the GRUB menu, none of the boot options worked. The ubuntu options gave this error:
```
Error 17: Cannot mount selected partition
```
And the Windows XP option just went back to the GRUB menu without booting windows.

I'm pretty sure GRUB has the right partitions though, because when I press 'e' on the options, it says hd1,0 for the linux ones and hd0,0 for the windows option.

After that, I decided to reinstall Xubuntu, choosing to install the bootloader to /dev/sdb1 this time. (/dev/sdb1 is the partition to which I install xubuntu.)

Does anyone know what I should do in this situation? I would appreciate any help!

---

### Post by benfindlay on 2008-08-01
Running FIXMBR wipes your grub config away unfortunately, as it supercedes it with entries in the master boot record. You can repair this by booting the ubuntu live cd and rerunning grub to resetup your partitions, however I would recommend downloading [Super Grub Disk]("http://www.supergrubdisk.org/") and using it to repair your grub instead as I have heard nothing but good things about how easy it is to use!

Hope this helps!

---

### Post by Paqman on 2008-08-01
> **benfindlay said:**
> I would recommend downloading [Super Grub Disk]("http://www.supergrubdisk.org/") and using it to repair your grub instead as I have heard nothing but good things about how easy it is to use!

Super Grub Disk will automate installing GRUB, but I wouldn't really describe it as easy to use. The menu structure in it isn't very well designed.

---

### Post by benfindlay on 2008-08-01
> **Paqman said:**
> Super Grub Disk will automate installing GRUB, but I wouldn't really describe it as easy to use. The menu structure in it isn't very well designed.

Really? I've never had to use it my self but hear people say how good it is. I'll bear that in mind for future! So is using the ubuntu live cd easier then?

---

### Post by Paqman on 2008-08-01
> **benfindlay said:**
> Really? I've never had to use it my self but hear people say how good it is. I'll bear that in mind for future! So is using the ubuntu live cd easier then?

Depends. If you've already got a copy of SGD and know how to use it, it 's probably quicker. Booting up the LiveCD can take a while. However, if all you're doing is setting GRUB up once then it's going to be a lot quicker to just pop in your LiveCD and do 30 secs of simple CLI work than it is to d/load and burn a new disk.

---

### Post by spoketire on 2008-08-01
> **benfindlay said:**
> Running FIXMBR wipes your grub config away unfortunately, as it supercedes it with entries in the master boot record.
That's what I was trying to do. I wanted GRUB to be on the Linux drive, and not the Windows drive. I was thinking that it could just boot the Windows drive and run windows from there, since right now, if I boot the Windows drive directly in BIOS, it skips grub completely. I don't need grub to be on the windows drive, do I? I thought you were supposed to have grub on the Linux drive, and boot that one by default.

I hope that makes sense.

Why can't GRUB mount the Linux drive when I choose to boot linux? That doesn't make any sense to me, because it was doing it just fine when the GRUB menu came up from booting the Windows drive.

---

### Post by kansasnoob on 2008-08-01
> Xubuntu will be on a SATA and xp will be on an ATA drive.

Now, this was probably the beginning of your problem. Not so much the difference between SATA and ATA, but simply that the boot order of your BIOS was wrong for where GRUB was installed.

My idea, and for Pete's sake verify this, is to create a small GRUB partition (512mb is plenty) on the primary boot drive.

Herman's GRUB page is great:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

How to make a dedicated  GRUB Partition is here:

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

---

### Post by spoketire on 2008-08-01
> Now, this was probably the beginning of your problem. Not so much the difference between SATA and ATA, but simply that the boot order of your BIOS was wrong for where GRUB was installed.
Well, the SATA comes before ATA in the boot order, and I intended for GRUB to be on the SATA. Isn't that how it's supposed to be?

I think it is on the SATA, because I have the /boot/grub directory and all the usual stuff in it, but there was something to do with grub on the windows drive as well, because otherwise it wouldn't have brought up the boot menu when I booted the windows drive.  I don't really understand exactly how GRUB works though, so I'm probably wrong.

---

### Post by kansasnoob on 2008-08-01
Well, I'm curious what 

```
find /boot/grub/stage1
```

shows? That will tell us where GRUB is installed.

I'd also need a screenshot of all drives, but many folks here can do this all from cli.

---

### Post by spoketire on 2008-08-01
I think find /boot/grub/stage1 said (hd1,0), but I can't remember.

Either way, I figured it out, FINALLY.

I had to first switch Linux to be hd0,0 and Windows to hd1,0 in menu.lst.  That fixed the Linux boot option.  But Windows still didn't want to boot because it was the second hard drive.  So I found this on Herman's GRUB page:
```
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
boot
```

I was so lucky to see that on Herman's grub page and try it out. I almost gave up on that website, since I tried some stuff from it before.  Thanks everyone! By the way, if anyone has any ideas on how this could be completely avoided from the start, or exactly what was going on all along, that would be helpful.

---

### Post by spoketire on 2008-08-02
> **kansasnoob said:**
> Well, I'm curious what 

```
find /boot/grub/stage1
```

shows? That will tell us where GRUB is installed.

The reason I couldn't remember this before is because I got two answers from this command.  Inside Xubuntu from the terminal it says (hd1,0), but if I do the command in the grub CLI before I boot an OS, it says (hd0,0).  In both situations, I have tried geometry on the drive that it says for stage1, and it always tells me it's the Linux drive.  I suppose this means that grub is really on the Linux drive, but I'm not sure why I get a different answer from "find /boot/grub/stage1" once I'm in xubuntu.

---

