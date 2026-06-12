---
title: "Force USB boot from HD or DVD"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-12-02
Somehow, recently, I've lost the ability to boot from a USB drive on my desktop.  I was running 11.04 just fine and then one day when I booted up my PC with the USB connected, the PC ran forever against the hard drive, until I eventually unplugged. it.

After that (might be unrelated), the bios option to boot from a USB drive is no longer present on my Compaq Presariou SR2030NX Windows XP computer.  For data purposes the PC can read and write to the USB, just no longer boot from it.

I've read up a little about programs that update the Master Boot Record and I'm not sure I wish to risk that, since the PC is running windows fine and some linux versions (including ubuntu 11.04) from the DVD.

So I was wondering ...   Is there someway to boot my PC from the hard drive or from the DVD drive minimally and throw the operations to run off of a USB, so that when I take the USB to my laptop which does boot from the USB that I have all my applications without modifying the Master Boot Record on my PC?

I've found boot.ini on my XP PC and it contains these commands:

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /fastdetect /NoExecute=OptIn
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

I'm not quite sure what the boot.ini does, because doesn't the bios recognize the drives earlier in the process.   Would adding something to boot.ini help?

Would adding a 2nd hard drive help ? - I'm sure I have some laying around.

This also might help others that have PCs where their bios does not allow booting from a USB and they are not ready to change their boot record on their main hard drive.

Ideas?  Suggestions?

---

### Post by lechien73 on 2011-12-02
I was asked a question similar to this a while ago, and documented the details on my blog here: [http://blog.mattrudge.net/2010/08/04/booting-ubuntu-through-ntldr/](http://blog.mattrudge.net/2010/08/04/booting-ubuntu-through-ntldr/)

If you're reasonably confident with a hex editor, then it's a (relatively) painless process :)

---

### Post by Denver Dave on 2011-12-02
Note - worked fine - with 2nd boot with no changes - thanks !!!!!

Thanks for the information.  Does feel like on a promising track, but of course it didn't work the first time.

Running XP with several usb devices attached

- I booted up with the ubuntu 11.04 DVD
- sudo dd if=/dev/sdb of=./bootsect.bin bs=512 count=1
- managed to get bootsect.bin over to the root of my hard drive
- installed XVO32
*** - did a goto 0064 and noticed that the content was 3C not FF
- Changed it anyway to 81 (after making a backup of bootsect.bin
- attrib -r -h -s \boot.ini
- added C:\bootsect.bin = "Ubuntu" after the last like boot.ini
- plugged in my ubuntu 11.04 thumb drive
- rebooted PC
- noticed that Ubuntu was at the bottom of a boot menu

Could not use my down arrows to move down and eventually Windows XP booted.

Wonder if I created the bootsect.bin - is there anyway to know by looking at it if it is reasonable?

Will reboot again and see if there is some way other than the down arrow on the keyboard to select Ubuntu.

Wonder why my 0064 was 3C not FF

First double check 0064 .... 
In the first column the row is 
0
19
32 which is the 3rd row.  81 is in the 0064 (decimal) location, if I'm doing this right.

.... rebooting ... will report back.

Things to look for?  Thanks !

= = = = = == = 
After rebooting the 2nd time - worked like a champ and I'm using my ubuntu 11.04 USB drive right now (for some reason 11.10 does not work on my desktop, but that's a different thread).   Maybe I was so excited the first time that I didn't press the down arrow key correctly.    Thanks !!!!!!!!!!!!!!!!!

Questions:

There must be quite the consistency in the MBR data to be able to do this.  Wonder what the 3C (instead of FF) was, didn't seem to hurt anything.

Does the word "Ubuntu" matter in the boot.ini file or could I have booted another unix distro, like Knoppix this way?  Guess I'll try and see when I have an additional USB boot drive.

Many thanks - I'm going to go back to my friend that had an old laptop that would not recognize his USB to boot from and see if we can get this to work for him.

Pretty neat !!!!!

= = = = 
and "icing on the cake" my desktop still boots into Windows XP when I don't pick the Ubuntu USB.  :)

---

### Post by lechien73 on 2011-12-03
Great - glad it's working for you.

In answer to a couple of your questions - you can boot any operating system this way if you export the boot sector in the same way. "Ubuntu" is just a label, so it could read anything you like: "Denver Dave's Awesome Linux USB" if you wanted :D

In answer to why 3C was at address 0064 and not FF, I'm not sure, but I'm glad it's working. If you want to PM me a copy of your bootsect.bin file, I'd be happy to take a look.

The boot sector always has to contain a small assembly language program to initiate the boot process. It needs to be in assembler, because it has to be very low level - before any portion of the operating system is loaded.

Grub creates a standard boot sector, so that's why we can change it like that. It does differ slightly between Grub versions, though, so maybe that accounts for the difference in yours.

---

