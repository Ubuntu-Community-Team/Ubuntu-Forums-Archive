---
title: "Can't boot into 16.04 message reboot and select proper boot device"
date: 2016-08-09
forum: New to Ubuntu
---

### Post by simongatti on 2016-08-09
Last week I downloaded openGl so that I could use SketchUp on my desktop (SketchUp doesn't recognise my Haswell on board graphics chip).  /the next day I rebooted my machine and it came up with the message missing NTLDR file. Nothing I do stops the message above just "reboot and select proper boot device".
I've downloaded and used  Boot-Repair-Disk and these are the files it gave me:

Before repair: [http://paste.ubuntu.com/22800310/](http://paste.ubuntu.com/22800310/)
After repair  : [http://paste.ubuntu.com/22800605/](http://paste.ubuntu.com/22800605/)

the repair didn't work and I got ~/Boot-Info_2016-08-09_13h20.txt

it also told me to set the bios to  sda1/EFI/shimx64.efi file but that option doesn't appear in my bios or I don't know how to set it.

I desparately need to get into my computer to print off drawings for my builders and order materials etc so any help would be appreciated

Thanks

---

### Post by grahammechanical on 2016-08-09
Are you sure that the message said: "NGLDR?" I cannot find anything in Wikipedia to explain the meaning of NGLDR. On the otherhand, NTLDR = NT loader. It is a Windows boot loader. If the BIOS/UEFI is set to load a Windows boot loader then you will get that message as Windows is not installed on that machine.

I do not have a UEFI boot system motherboard so I do not speak from practical experience but I understand that the UEFI would need to be set to load from sda and that there should be a label in the UEFI that lets you load Ubuntu.

Regards

---

### Post by simongatti on 2016-08-09
you're right of course it was NTLDR - should have checked my spelling more closely. Thank you! I have edited the post accordingly. The UEFI gives me 4 options for booting and I triied all 4 in turn with no joy. Today I had to download another usb boot because it wouldn't boot from the one I used yesterday? Before trying the BootRpair Disk I tried installing 16.04 again on a new partition but it failed to reboot once the installlation was complete.

Regards

---

### Post by mook765 on 2016-08-09
I guess you need to work with windows, wich is installed on your  1TB hraddrive.
Try to boot directly this drive, you have to enter UEFI-Bios and change the boot order.
There might be a boot-override-option where you can directly choose where to boot from.
If you still get the message "Can not find NTLDR" then you have a problem in windows, to find out how to fix that wouldn't be a topic for this forum.
Something went wrong on your 500GB drive, where all this linux-distributions are installed.
You have an interesting mix off MBR and GPT and i would recommend that you wait for more replies from the gurus here.
But in the time off waiting, try to boot directly to windows, if that works, you might be out off a big headache...
good luck...

---

### Post by mook765 on 2016-08-09
My last post appeared twice in the thread and I couldn't find an option to remove it.

---

### Post by mook765 on 2016-08-10
This might be helpful:
> [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

---

### Post by simongatti on 2016-08-15
> **mook765 said:**
> This might be helpful:

Thanks for those suggestions.  Trouble is that, after successful downloads, I can't actually get BootRepairDisk to extract and run either of them.
Is there a way that I could save the contents of one partition to my portable Samsung hard drive then reformat my hard drive on my Desktop and do a fresh install of 16:04?
BootRepairDisk allows me access to some files but, strangely, not others.
I realise it would mean re-installing some programs but at least I would have a working computer......

---

### Post by mook765 on 2016-08-15
If you have still your installation media (pendrive or DVD) with Ubuntu you could boot from that media in a live session ( Try Ubuntu without installing ).
That will give you full access to your data and you should be able to copy your data to an external drive.

---

### Post by simongatti on 2016-08-16
No I didn't have the media intact - I wiped it to load BootRescueDisk!  But I've downloaded 16.04 again and with the help of a friend's laptop I've burnt it to a usb stick using Rufus. I'm just about to shut down and see if it will boot from the stick. Fingers crossed.
Many thanks for your suggestion.

---

