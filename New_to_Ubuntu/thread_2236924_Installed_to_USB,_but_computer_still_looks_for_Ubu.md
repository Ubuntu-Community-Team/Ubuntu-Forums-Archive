---
title: "Installed to USB, but computer still looks for Ubuntu instead of Windows"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by bphillips79 on 2014-07-29
Hi Folks - 

Super newbie here!  Needs help to save the day!  Er.  Anyway, I put the Ubuntu iso on a jump drive, booted into "Try Ubuntu w/o install", then installed Ubuntu to a second jump drive.  I wanted to keep Windows 7 and Ubuntu separate, hence doing a full install to the jump drive.  My goal was that if the jump drive wasn't present, Windows 7 should load like it always does.  However, unless the jump drive with the Ubuntu install is present, the computer just boots to a grub prompt.  Any help would be appreciated!

Ben

---

### Post by Bashing-om on 2014-07-29
bphillips79; Hi Welcome to the forum....

What you are saying in effect, is that even though, in bios you have the drive that Window 7 is installed to selected to boot, you can not boot Windows ?
And as well, when selecting the jump drive to boot in bios, even ubuntu -install- will not boot ?

Then we are looking at the situation as grub was installed to the hard drive containing Windows 7. ( not at all what you intended !)

Required in this case is to (RE-)install Window's boot code to the effected hard drive,
And from that liveUSB install grub to that other jump drive.

I can not advise on the use of Window's 'fixmbr' utility, but once Window's boot code is restored:
Boot the liveUSB to terminal, run terminal command
```

sudo fdisk -lu

```
to identify the live(USB) designation ( say 'sdc' (??)).
Once identified, now plug in the ubuntu install jump disk, rerun 'fdisk' and get that identifier ( say it is seen as 'sdd'); and as well identify the partition that the operating system is installed to ( usually the 1st partition -> in this case becomes sdd1)

OK, you KNOW what device is which and what, now install grub properly to that installed ubuntu operating system;
```

sudo mount /dev/sdd1 /mnt ## where the device is identified as 'sdd' AND the operating system (/) is installed to the 1st partition##
sudo grub-install --boot-directory=/mnt /dev/sdd ## install to the device NOT to the partition##
sudo umount /mnt

```
All done here, restart, pull the liveUSB, reboot and set in bios to boot up the ubuntu install jump drive.
Boot into ubuntu install and in this install run the commands:
```

sudo fdisk -lu ## to once more identify what the system sees the device as##
sudo grub-install --recheck /dev/sdb ##let's say that the device is now seen as 'sdb' rather than 'sdd'##
sudo update-grub ##to pick up and chainload Windows to grub's boot menu.##

```

Reboot once more, all should be finer than a frog's hair !


[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

