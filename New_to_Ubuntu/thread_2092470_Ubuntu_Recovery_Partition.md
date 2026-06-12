---
title: "Ubuntu Recovery Partition"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by StatusFresh on 2012-12-07
Hello, I'm new to Ubuntu, and I have several questions, and many of them might be simple. My laptop uses Windows 7, and Ubuntu 12.10

1. I read a good article listing and explaining in detail many things beginners should do once installing Ubuntu back when I first heard of it, and I've searched for some such as top 10s etc..But would you guys have any suggestions on articles or instructions for important things to do after installing Ubuntu?

2. After I installed BURG, I noticed I have a Ubuntu Recovery Partition; Is this partition needed for anything? I still use Windows as my primary OS and use it for most things and intend on doing that until I get better at Ubuntu, so how would I go about deleting it, I don't know which partition it is in the disk management screen in Windows?

3. In the BURG bootloader menu, is there a way for me to slow it down before it automatically boots selected option? I would like that, so in the future, I'd be able to press power and leave room without waiting to pause the menu myself.

4. How can I make Windows my primary boot with BURG? or at least have it be the default selected OS

5. Just in general, what does a flashing underscore before loading OS mean? is it something bad? I noticed on my old Windows computers, as they get older, they would start showing that symptom before booting.  Now when I boot Ubuntu, it appears for a time interval longer than when I used to single boot Windows.  Is this normal?

Sorry for all the questions, and I would appreciate any answers and help, thank you.

---

### Post by zombifier25 on 2012-12-08
> **StatusFresh said:**
> Hello, I'm new to Ubuntu, and I have several questions, and many of them might be simple. My laptop uses Windows 7, and Ubuntu 12.10

1. I read a good article listing and explaining in detail many things beginners should do once installing Ubuntu back when I first heard of it, and I've searched for some such as top 10s etc..But would you guys have any suggestions on articles or instructions for important things to do after installing Ubuntu?

This depends on who asked though. My recommendations are installing restricted extras and install some tools like MyUnity or Ubuntu Tweak in order to tweak the system.
> **StatusFresh said:**
> 
2. After I installed BURG, I noticed I have a Ubuntu Recovery Partition; Is this partition needed for anything? I still use Windows as my primary OS and use it for most things and intend on doing that until I get better at Ubuntu, so how would I go about deleting it, I don't know which partition it is in the disk management screen in Windows?

It's probably recovery mode, not a partition (I'm not aware of any recovery partitions stuff) It's for recovering the Ubuntu systems when things go awry. You'll log in as root directly when going into recovery mode.
> **StatusFresh said:**
> 
3. In the BURG bootloader menu, is there a way for me to slow it down before it automatically boots selected option? I would like that, so in the future, I'd be able to press power and leave room without waiting to pause the menu myself.

4. How can I make Windows my primary boot with BURG? or at least have it be the default selected OS

For these, you can edit the /BURG config files manually. But since you're new, you should use a graphical tool instead. (still, if you're not careful you can mess it up)
[Super Boot Manager](http://www.omgubuntu.co.uk/2011/05/super-boot-manager-eases-burg-grub-plymouth-tweaking-pains)
(note: at the final command for installation, remove the question mark. It's probably an error)
> **StatusFresh said:**
> 
5. Just in general, what does a flashing underscore before loading OS mean? is it something bad? I noticed on my old Windows computers, as they get older, they would start showing that symptom before booting.  Now when I boot Ubuntu, it appears for a time interval longer than when I used to single boot Windows.  Is this normal?

Sorry for all the questions, and I would appreciate any answers and help, thank you.

Beats me. My guess is that it means the graphical desktop is loading up. Does not seems to represent anything at all.

I hope I have answered all your questions fully.

---

### Post by Wim Sturkenboom on 2012-12-08
> **StatusFresh said:**
> 5. Just in general, what does a flashing underscore before loading OS mean? is it something bad? I noticed on my old Windows computers, as they get older, they would start showing that symptom before booting.  Now when I boot Ubuntu, it appears for a time interval longer than when I used to single boot Windows.  Is this normal?

That's just a text cursor while the system is still in (some kind of) text mode; nothing to worry about.

---

### Post by mcduck on 2012-12-08
> **StatusFresh said:**
> 
2. After I installed BURG, I noticed I have a Ubuntu Recovery Partition; Is this partition needed for anything? I still use Windows as my primary OS and use it for most things and intend on doing that until I get better at Ubuntu, so how would I go about deleting it, I don't know which partition it is in the disk management screen in Windows?

Like somebody already mentioned, it's not a recovery parittion, it's te option to start Ubuntu in recovery *mode*. So it's not usign any additional disc space or partitions. There's no reason to, or benefit from, removing it. And I'd indeed recommend strongly against doing such thing. The recovery mode is valuable tool fro solving certain types of problems if things go wrong...
> **StatusFresh said:**
> 
3. In the BURG bootloader menu, is there a way for me to slow it down before it automatically boots selected option? I would like that, so in the future, I'd be able to press power and leave room without waiting to pause the menu myself.

Sure, just edit /etc/default/burg file and there's an option to change the timeout. You'll need to run "sudo update-burg" afterwards to update burg's settings. Or, alternatively, try using some of the graphical tools like the Burg Manager.

> **StatusFresh said:**
> 
4. How can I make Windows my primary boot with BURG? or at least have it be the default selected OS

Same as above, the setting is in /etc/default/burg. Just change the "default" number to point to correct entry.

..or, set the "default" to "saved" and enable the "savedefault" option. This will make Burh to boot the *previously used* option by default.

> **StatusFresh said:**
> 
5. Just in general, what does a flashing underscore before loading OS mean? is it something bad? I noticed on my old Windows computers, as they get older, they would start showing that symptom before booting.  Now when I boot Ubuntu, it appears for a time interval longer than when I used to single boot Windows.  Is this normal?
Doesn't really mean anyhting, the computer is simply doing some work in the background and isn't drawing anything on the screen yet.

You didn't say anything about *how long* that takes on your computer, so it could simply be the second or two it takes to load the Linux kernel from the hard drive into memory before it can be started. Or it could be that Ubuntu is actually already laoding, but your graphics card (or it's driver) wasn't ready quickly enough and the kernel simply decided to continue with the boot and try enabling the graphics at a later stage instead. (in the later case there is an option tat allows forcing the kernel to wait for the graphics card to wake up, which results in seeing the laoding screen quicker but at the same time slows down the boot a bit)

---

### Post by grahammechanical on 2012-12-08
If we stay with 12.10 and its default Grub 2.0 menu then the recovery mode option and the options to select previously installed kernels are put into a sub-menu called Advanced Options.

It makes for a neater menu system. I do not know how Burg handles this. The operating system is Linux and it can be run with or without a Graphical User Interface. What we see briefly when we see that black screen with the flashing cursor is the basic Linux kernel doing its stuff before for it loads a splash screen (purple) and a log in manager and then the desktop environment with its User Interface.

If we select Recovery Mode then we get these options:

> resume         - resume normal boot
clean          - try to make free space
dpkg           - repair broken packages
failsafe       - run in failsafe graphic mode
grub           - update Grub boot loader
network        - enable networking
root           - drop to a root shell prompt
system-summary - system summary

Regards.

---

### Post by StatusFresh on 2012-12-08
[IMG]http://imageshack.us/photo/my-images/707/partitions.png/[/IMG][[IMG]http://img820.imageshack.us/img820/5491/partitionsj.png[/IMG]]("http://imageshack.us/photo/my-images/820/partitionsj.png/")





It is using disk space though, about 6 GB, does everyone else have this partition? Some of the pics of Burg I've seen have only one ubuntu icon shown on the boot screen.  Also thank you for all the help and replies.

---

### Post by oldos2er on 2012-12-08
I'm not familiar with whatever app is pictured (is it Windows software?), but that could be a Linux swap partition. ```
sudo fdisk -l
``` run from within Ubuntu would tell you.

---

### Post by lisati on 2012-12-08
> **oldos2er said:**
> I'm not familiar with whatever app is pictured (is it Windows software?), but that could be a Linux swap partition. ```
sudo fdisk -l
``` run from within Ubuntu would tell you.

The image looks a bit like a Vista/Win7 disk management screen to me.

+1 to the "fdisk" suggestion; it uses a lowercase "ell", not a number one.

---

### Post by mcduck on 2012-12-09
> **StatusFresh said:**
> 
It is using disk space though, about 6 GB, does everyone else have this partition? Some of the pics of Burg I've seen have only one ubuntu icon shown on the boot screen.  Also thank you for all the help and replies.

That would be your *swap* partition. Ubuntu doesn't create any kind of recovery partition, but it does by default set you up with two parttiions, one for / and one for swap.

You can simply hide the different boot option in Burg, I don't have it installed myself any more but if I remember right, the "f" key folds the options leaving you with only one icon per OS. (Press F1 in Burg menu to see all the keyboard commands).

---

### Post by Bartender on 2012-12-09
What the heck is Burg??

We're talking about GRUB, right?  GRUB as in Grand Unified Boot Loader?   

mcduck, since Windows *sees* that 6GB partition, and it's a primary partition, I'm about 99% sure it's not swap.

I'm not up-to-speed on UEFI, but since his partition map shows 4 primaries and an OEM partition (whatever that is) AND a logical drive, does that mean this has to be UEFI?  It can't be a BIOS-booting PC, right?

---

### Post by mcduck on 2012-12-09
> **Bartender said:**
> What the heck is Burg??

We're talking about GRUB, right?  GRUB as in Grand Unified Boot Loader?   

mcduck, since Windows *sees* that 6GB partition, and it's a primary partition, I'm about 99% sure it's not swap.

I'm not up-to-speed on UEFI, but since his partition map shows 4 primaries and an OEM partition (whatever that is) AND a logical drive, does that mean this has to be UEFI?  It can't be a BIOS-booting PC, right?

BURG as in "Brand-new Universal loadeR from Grub". It's a bootloader based on Grub, but with some pretty graphical themes.

[https://launchpad.net/burg]("https://launchpad.net/burg")

And since there is no other partition that could be the swap, and there is no reason why a swap partiton couldn't be a primary one or why Windows wouldn't see it (of course it *sees* all partitions, it simply doesn't recognize all partition types or filesystems), I'm still 99% sure it's the swap. ;)

---

### Post by StatusFresh on 2012-12-09
using the sudo fdisk -l brings up:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    7  HPFS/NTFS/exFAT
/dev/sda2          411648   689554655   344571504    7  HPFS/NTFS/exFAT
/dev/sda3       689555454   945829887   128137217    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda4       945829888   976773167     15471640   12  Compaq diagnostics
/dev/sda5       885022720   945829887    30403584    7  HPFS/NTFS/exFAT
/dev/sda6       689555456   872615935    91530240   83  Linux
/dev/sda7       872617984   885020671     6201344   82  Linux swap / Solaris

---

### Post by Wim Sturkenboom on 2012-12-10
```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    7  HPFS/NTFS/exFAT
/dev/sda2          411648   689554655   344571504    7  HPFS/NTFS/exFAT
/dev/sda3       689555454   945829887   128137217    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda4       945829888   976773167     15471640   12  Compaq diagnostics
/dev/sda5       885022720   945829887    30403584    7  HPFS/NTFS/exFAT
/dev/sda6       689555456   872615935    91530240   83  Linux
/dev/sda7       872617984   885020671     6201344   82  Linux swap / Solaris
```
The only 6GB in there is the swap (on sda7).

PS please use code tags when posting command output; you can 'quote' my post to see how it's done. It preserves formatting which makes it easier to read.

---

### Post by Graymayre on 2013-01-23
This is your swap space partition.  Leave it alone.
To answer the other question, this is the disk management tool in Windows.  It is used to manage disks and their partitions and can be used to configure RAID.

> **StatusFresh said:**
> [IMG]http://imageshack.us/photo/my-images/707/partitions.png/[/IMG][[IMG]http://img820.imageshack.us/img820/5491/partitionsj.png[/IMG]]("http://imageshack.us/photo/my-images/820/partitionsj.png/")





It is using disk space though, about 6 GB, does everyone else have this partition? Some of the pics of Burg I've seen have only one ubuntu icon shown on the boot screen.  Also thank you for all the help and replies.

---

