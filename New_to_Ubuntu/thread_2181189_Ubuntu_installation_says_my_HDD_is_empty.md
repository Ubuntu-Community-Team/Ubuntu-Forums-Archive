---
title: "Ubuntu installation says my HDD is empty"
date: 2013-10-16
forum: New to Ubuntu
---

### Post by lifelikeweeds on 2013-10-16
Hi there!

Sooo, I have decided to finally install Ubuntu on my PC. I downloaded the 12.04.3 Desktop 64bit version and got it on an USB flash drive using Universal USB Installer.

While trying to boot from the stick, I encountered some Kernel Panic which caused everything to freeze, but after loading Ubuntu on the USB flash drive again and making sure that the drive stays in the exact same USB port, it booted. When I try to install Ubuntu, though I only have two options - formatting the harddrive and installing from scratch, or making the partition myself. Yeah, the latter was exactly what I was looking for, so I chose that. But behold - another problem right here: The installation only shows an empty 1TB drive. It shouldn't be empty, though. I actually have two partitions on there - Windows 7 is installed on one of them - and about 100 GB of unallocated space.

The partition style of my HDD is MBR. The laptop came installed with Windows 8, which I didn't like, so I formatted the drive and installed Windows 7. Back then, I had to switch the boot mode from UEFI to Legacy Bios in order for the PC to recognize the HDD, so I think I may have made a mistake at some point there.

Does anybody have an idea what the problem might be? Or how I could fix it? I'm pretty new to Ubuntu and I'm ashamed to admit that the whole UEFI-thing is a little bit of uncharted territory to me, as well.

Thanks in advance,
lifelikeweeds

---

### Post by oldfred on 2013-10-16
When you install Windows in BIOS/MBR over a gpt drive it converts drive from gpt to MBR(msdos). But it does not do it right. It leaves the backup gpt partition table, so you have both a MBR partition table and a backup gpt partition table. Windows seems to ignore backup but Linux tools get confused on whether you really have MBR or gpt.

If Windows is now MBR you just need to remove backup gpt partition table.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by lifelikeweeds on 2013-10-16
Thanks a lot for the answer! 

I downloaded fixparts and ran it as an Admin. It doesn't matter what I type, though, I always get the error
 
'Loading MBR data from x
Problem opening 1 for reading!'

Do you, by any chance, have an idea why I get this error? And what I could do?

Edit: By the way, gdisk gives me the same error.

---

### Post by oldfred on 2013-10-16
Are you running that from Linux? Best from the Ubuntu liveDVD or flash drive.
Did you in Windows create more than 4 partitions? It converts to dynamic which does not work with anything.

---

### Post by fantab on 2013-10-17
Boot your computer with Ubuntu DVD/USB and 'Try Ubuntu without Installing'. Open the Terminal and post the output of the following:

```
sudo fdisk -l
sudo parted -l
```

Like oldfred points out if you have created more than 4 primary partitions in Windows then Windows will convert the HDD to "Dynamic" and this is not recognized by Linux, as 'Dynamic' is a Windows proprietory. But since you say you have only two partitions this cannot be it.
If you had converted your GPT Disk to 'msdos' then there will be some backed up GPT data at the end of the HDD. You can remove this with 'Fixparts' as already suggested. You MUST run fixparts from Ubuntu DVD/USB. I suspect its most likely the issue of GPT leftover.

---

### Post by newb85 on 2013-10-17
As has been stated, trying to change a partition table for a hard drive from within an OS running from that hard drive is probably not the best approach, even if it's not the partition table in use.

Oldfred, perhaps you could give specific instructions for installing fixparts on Ubuntu.  It's not in the repos, and the downloads page at the link you gave has an .rpm (no good for Ubuntu) and a .tar.gz packages that looks like it needs to be compiled.

---

### Post by lifelikeweeds on 2013-10-17
Thank you, I'll try it again from the Ubuntu disc.

The limit of 4 partitions still exists in Ubuntu, doesn't it? 
I mean, if I wanted to create a linux partition, a /home partition and a partition for the swap file, I would not be able to, because that would total 5 partitions?

Edit: Ah, nevermind. I just remembered that I can use the 'slot' for an extended partition and install Ubuntu on logical partitions.

---

### Post by lifelikeweeds on 2013-10-17
Sooo, I've spent the past two hours trying to install/run fixparts on Ubuntu, but to no avail. Installing the .deb via Software Center does not work; it just gives me an error to the effect of "couldn't install application". I also downloaded and unpacked the .rpm, but couldn't start the application in there.

Anyway, I'm stuck. Could somebody please give me a step-by-step explanation how to install and run fixparts?

---

### Post by fantab on 2013-10-17
I still need to look at the output of those commands in from my post #5.

No, .rpm will not work with Ubuntu (Ubuntu is Debian based, so only .deb). The link which oldfred gave you for [fixparts]("http://www.rodsbooks.com/fixparts/") is definitive and quite simple.

Try installing the .deb package from the terminal [ctrl+alt+T]:
1. Put the downloaded fixparts.deb file in /home/downloads

Open Terminal and run the commands one by one:
```
cd ~/Downloads
sudo dpkg -i fixparts.deb
```

If any errors are reported post the exact output here (copy-paste).

Edit: Download the correct version of fixparts, ie, 32bit or 64bit.

@newb85: the link does have .deb packages, look again: [HERE]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.8/fixparts-binaries/").

Good Luck...

---

### Post by oldfred on 2013-10-17
I have not used fixparts. But this page shows both 32 bit & 64 bit .deb downloads. Be sure do download the same probably 64 bit version as your Ubuntu install is.

[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.8/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.8/fixparts-binaries/)

Above shows this for 64 bit version:
[fixparts_0.8.8-1_amd64.deb]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.8/fixparts-binaries/fixparts_0.8.8-1_amd64.deb/download")

---

### Post by newb85 on 2013-10-17
> **fantab said:**
> @newb85: the link does have .deb packages, look again: [HERE]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.8/fixparts-binaries/").

I must be losing it. I searched that page three times for the.deb. file without seeing it.

---

