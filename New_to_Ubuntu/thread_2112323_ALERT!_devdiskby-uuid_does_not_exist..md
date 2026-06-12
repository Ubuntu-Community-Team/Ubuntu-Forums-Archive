---
title: "ALERT! /dev/disk/by-uuid/ does not exist."
date: 2013-02-04
forum: New to Ubuntu
---

### Post by l1ghtwe1ght on 2013-02-04
Hi,

Total linux noob, hope you can help!
Background: booted a laptop from a liveUSB, and installed Ubuntu 12.04 to another USB drive using [this tutorial (link).]("http://fernhilllinuxproject.com/guidesandhowtos/installubuntutousbdrive.html")

I created a 2Gb swap partition, and installed to the remaining 14Gb ext4 partition.
When I try to boot from the usb drive (the non-liveUSB one), I get the error above.

I tried booting it on another machine; a desktop with 2x HDDs, and got the same error.

I tried the boot repair thingy (results are [here (link)]("http://paste.ubuntu.com/1609285/")), but no dice.

I tried hitting 'e' at the grub prompt, taking out the floppy line and replacing the root=<uuid> with /dev/sdc1 (and sdd1), still the same.

I've done a chroot remove and reinstall grub, no luck there either!

There's quite a few references to this issue out there, but most are solved by one of the above methods, not mine though!

Help please?

---

### Post by oldfred on 2013-02-04
Welcome to the forums.

You need to change fstab back to UUIDs. With multiple removeable drives, the device order will keep changing. That is where UUID works but a /dev/sdb1 will not. Grub is also using UUIDs, so that should be ok.

When I installed from one flash to another ages ago, I did have to manually edit grub as it seems to stop searching by UUID when I had a gap in device order. I edited search out and set drive to hd0 in grub as when you boot directly from BIOS grub will see boot drive as hd0. But Ubuntu will still have drive order.

---

### Post by l1ghtwe1ght on 2013-02-04
Ah, yes, forgot I'd tried that too!
Tried switching it back, but got the same error.

I will try editing out search and setting it to hd0, and see if that helps.

Thanks for the fast response!

---

### Post by l1ghtwe1ght on 2013-02-04
Having set fstab back to how it was originally, tried editing the grub command line:
- deleted the whole line starting 'search...'
- changed 'hd3' to 'hd0'

Still the same... :(

Any other ideas? :confused:

---

### Post by Bashing-om on 2013-02-04
l1ghtwe1ght; Hi !

Your posts read to me like you do not have grub installed in the usb drive.
Howtos:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)
[INDENT][INDENT]hth

[/INDENT][/INDENT]

---

### Post by oldfred on 2013-02-04
@Bashing-om
If you look at link to BootInfo in first post, grub was in sdd and install was in sdd, but drive order seems to change.
But sometimes a reinstall of grub does fix something even though it looks correct.

---

### Post by l1ghtwe1ght on 2013-02-04
The boot fixer reinstalled grub for me, and I did it manually, using chroot - both times I used disk utility to ensure it was being installed to the right device (and not to the partition). 

The boot order does change, because the live usb sometimes ends up as sdb, sometimes sdc, sometimes sdd, as does the usb which contains the actual installation I'm trying to fix. 
Once it's working, I can lose the live usb, which will make things better!

---

