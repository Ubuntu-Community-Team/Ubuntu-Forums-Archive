---
title: "[SOLVED] USB Flash Drive with Ubuntu partition"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by shanep-server on 2008-11-14
I just bought a USB pyn 4gb flash drive. I used Gpartd to split the USB stick into 4 partitions. I made 1 partition FAT16, 1 partition FAT32, 1 partition FAT32, 1 partition ext2. I used system>administration>create a USB startup disk. I used my ubuntu-8.10-desktop-i386.iso for my "Source disc image(.iso)or CD: then i made the startup disk with my first partition - 1 FAT16. 

I wanted this too install ubuntu on my laptop - currently winxp is destroyed cuz I tried to resize my partition on c against partition magics suggestion i don't LOL. My DVD-Rom drive doesn't work. I have no Floppy drive. So i'm stuck with Ethernet or USB to load an OS too it. I am trying to do USB.

My laptop is a Toshiba Satellite A105-s4094 - In the bios I have an option for 1st boot from USB Memory. I try this feature with my USB plugged in. I recieve this.

Intel (R) Bootagent FE v4.1.18
Pxe-e61 media test failure, check cable
Pxe-MOF Exiting intel bootagent

Does this mean that booting from a usb flash drive isn't possible? or that I could use USB bios option for External USB hard drive?

I loaded my USB stick into another computer running WinXP and it only recognizes the 1st Partition running FAT16. Is there a reason for this. When I open My Computer in winxp It shows my USB drive with the ubuntu logo.

Any ideas ?

---

### Post by nhasian on 2008-11-14
Actually that error message is not from Ubuntu.  That is your motherboard's bios trying to boot from the network adaptor.  You can disable network boot to make your pc boot slightly faster but it wont affect your pc running.  Your pc will continue booting after this message.

> Intel (R) Bootagent FE v4.1.18
Pxe-e61 media test failure, check cable
Pxe-MOF Exiting intel bootagent

---

### Post by shanep-server on 2008-11-14
After this error message it tries to boot winxp which won't work. Why is it skipping right over the USB boot? I have it as 1st boot method USB Memory

---

### Post by nhasian on 2008-11-14
In your bios make sure the boot order is something like:

1 - USB
2 - CDRom
3 - Hard Disk
4 - Floppy

You can remove the network boot entirely from the menu.  I checked the specs for your computer.  it has a DVD-Rom drive.  how come your not installing ubuntu from the liveCD?

I've never used the Create USB Startup Disc option but i'll bet anything that all those partitions you made are screwing up the boot process of the thumbdrive :)

---

### Post by shanep-server on 2008-11-14
My DVD drive is currently not working. Its still read by both the winxp ( when it was working ) and the bios. I leave my laptop on for basically 2 years LMFAO. But i think my dvd drive got too hot. 1 day I pulled out a cd from the drive and it didn't want to come out. I forced it and there was some rubber glue adhesive ( like what holds packaging together some times ) on the cd. I pulled off what i could. Now when i put a cd in the drive it doesn't spin. Like there is more glue inside gripping the cd so it can't spin. I'm going to bring it over to someones house to have them remove the drive and open it up for me. I'm pretty sure its fixable. But for now i'm on too USB.

U might be right. I think i'm going to destroy all my partitions right now and try to create another start up disk from 1 partition. I'll try that and see what happens. I wanted to have multiple partitions on it though. 1 for ubuntu live and the rest for what ever apps i want on it. I kind of was hoping it would read USB like the grub loader for multi OS's and let me select from the list of bootable partitions on my USB stick. 

[LIST]
[*]Ubuntu
[*]Ultimate Boot Disk
[*]Possibly windows XP bootable CD for reinstall.
[/LIST]
Guess i'm should just concentraite on 1 thing at a time LOL. I will try the 1 partition approach and let u know how that turns out.

---

### Post by shanep-server on 2008-11-14
1 partition attempt still failed like previous attempts.

---

### Post by hotterpop on 2008-11-27
So:
I have the same boot failure message. I have a 4 gig usb flash drive with ubuntu intalled on it. On my Satellite A105 it worked before, booted into ubuntu and ran perfectly, multiple times (I'm using the flash so I can save my preferences and change computers with it). Unlike the previous commenter I'm not trying to install to my hard drive, but simple to run it off the flash.

Now my computer won't boot into the flash drive. The order is correct, with the usb boot set before the hard drive. I've checked to see if I'm using the latest version of bios, and I"ve ran the flash in another computer to confirm it is not causing the problem. My computer runs fine in windows--simply skips over the usb boot.

I know almost nothing about ubuntu, but I do know that it was working on my computer before, and it works on other computers, so this must be an issue with my own computer. Any suggestions?

---

### Post by C.S.Cameron on 2008-11-27
The Ubuntu partition must be at least 750 MB for a Image install and 2.5 GB for a Full install.
On some computers you need to select the flash drive as the first hard disk, not USB as first in drive order.
Windows XP can only see the first partition on a flash drive.

---

### Post by shanep-server on 2008-11-27
I figured it out. I had 2 options for USB - I was trying USB Memory instead of USB Hard Disk. I have like 6 options for boot method and 5 options for boot sequence. So the last option wasn't visible until I moved some more threw my options.

Of course I figured this out after I ripped my laptop apart. Ripped out my DVD Rom and fixed that.

---

### Post by hotterpop on 2008-11-27
My computer currently doesn't recognize my drive, though others do. If that fixed it on yours, since you have the same laptop, how did you make it recognize it?
Thanks a million!

---

### Post by shanep-server on 2008-11-28
go to the last options for boot. 1, 2, 3, 4, 5. Go too the 5th option and scroll threw the options too boot. Hard disk, network, cd, USB memory, USB hard disk. Once u see hard disk stop. Then move everything above it, below it till USB hard disk option is at top. Then reboot with USB stick in and it will load.

---

### Post by hotterpop on 2008-11-28
I tried that, it doesn't boot still. What kind of formatting did you do for the flash drive? Could you just list the details?

---

### Post by shanep-server on 2008-11-29
formatting your disk shouldn't be an issue if you said u've gotten your stick to load ubuntu from another computer. I used Gparted to format my 4gb pyn usb drive. I formatted my stick with FAT32 I believe. I might have used FAT16 but I don't think so. FAT32 is what you should use if you want both windows and Ubuntu too read the formatted drive. I run both Ubuntu and windows XP on my laptop with a seperate partition too use for both OS on it. Then I have another Server running Ubuntu Desktop (desktop computer). Then I used Make USB Startup Disk from system>administration>Make USB Startup Disk. I used the .iso for Ubuntu Desktop. Installed Ubuntu on the stick. I went too the last option for boot up in my bios. I scrolled threw my options for the last option until I saw an option I couldn't see before. USB Hard Disk. Then I moved everything down the list until USB Hard Disk was the 1st boot option. Then I saved changes and exited bios. Restarted my computer and ubuntu booted from my stick.

---

### Post by hotterpop on 2008-11-29
Thanks, I'll work on that. Happy Booting!

---

### Post by w2vy on 2009-03-18
I have a laptop that also has a CD rom that works most of the time... when I boot the Live CD at times it will attempt seeks, and then reset and try again...

So... I too am trying to install from USB Pen drive.

But my BIOS will not allow me to Boot from USB, it has an option to boot from USB FLOPPY drive... but not USB Flash

Is there something I can do from the (F6) boot options to tell it to continue to load using the USB as default drive?

(Maybe more importantly is there an easy way to verify the USB is mounted at that point!)

I am even considering putting another loader on the CD that can have me boot usb-creator created live cd from USB

ideas?

---

