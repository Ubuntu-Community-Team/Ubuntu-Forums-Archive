---
title: "Brand New to Ubuntu, how to find memory test?"
date: 2017-01-07
forum: New to Ubuntu
---

### Post by chris.2 on 2017-01-07
I've been trying to find out if my RAM is working properly mainly because I'm using old parts and it kept showing up as only 4gb (trying 2x4gb sticks. One is original to this laptop, one is from a laptop where the HDD died) I saw online that you can do a memtest or memory test 86 or something but I can't seem to figure out how to get there. I saw others saying that on the first purple screen you should hit a keyboard etc. but I don't see a keyboard.

I'm using Ubuntu 16.04

Thanks

---

### Post by yancek on 2017-01-07
You should see the option for 'memtest' on the Grub boot menu.  If you don't see the boot menu for Grub, take a look at the link below which explains how to access it.

[http://askubuntu.com/questions/591488/how-do-i-run-memtest86/591502](http://askubuntu.com/questions/591488/how-do-i-run-memtest86/591502)

---

### Post by ajgreeny on 2017-01-07
Memtest is not available by default in grub on any UEFI booting machines which may explain your difficulty in finding it in the grub menu.

You may need to download and run the version from [http://www.memtest86.com/](http://www.memtest86.com/) which I understand works on UEFI systems, though I have never used it.

---

### Post by chris.2 on 2017-01-08
> **yancek said:**
> You should see the option for 'memtest' on the  Grub boot menu.  If you don't see the boot menu for Grub, take a look at  the link below which explains how to access it.

[http://askubuntu.com/questions/591488/how-do-i-run-memtest86/591502](http://askubuntu.com/questions/591488/how-do-i-run-memtest86/591502)

That's what I had tried and the shift key didn't seem to bring me to any boot menu (assuming that's what the grub menu is). When I did eventually get to a boot menu I didn't have the memtest option, when I tried an Ubunut Live USB it wouldn't let me boot it (I've only ever used Ubuntu Live USBs with a Windows system when I needed to create some secure bitcoin addresses haha. So I don't know how to use the live USB when I have an already Linux running machine).



> **ajgreeny said:**
> Memtest is not available by default in grub on any UEFI booting machines which may explain your difficulty in finding it in the grub menu.

You may need to download and run the version from [http://www.memtest86.com/](http://www.memtest86.com/) which I understand works on UEFI systems, though I have never used it.

Thanks I'll try and figure that out. What's a UEFI system? Google gave me "Unified Extensible Firmware Interface" which might as well be in Chinese hahaha.

Do I have to create a USB for this software? That seems to be the option I have to go with, either a CD or USB.

Edit: The USB doesn't seem to do anything for me but I'm 99% sure I'm doing something wrong. How would I access memtest now? I tried restarting and holding shift before and after I enter my password for the encryption I set up but all that holding shift does is make my mouse never show up. Is that a known glitch? It's happened to me 3x now so I know it's when I hold shift that it happens. I just have to do a forced restart again if I hold shift.

Edit2: Ughhh I'm so lost. I can't put anything on my USB because it wants to override and needs a password??? It's a brand new flash drive that I've never even used let alone needed a password for it. 

Does anyone know of a tutorial that shows step by step how to download, create the USB and run the test? I'm searching youtube but there are lots of running memtest86 and that kind of thing but nothing showing the whole process (that I've found yet).

---

### Post by chris.2 on 2017-01-08
Update: to make things simpler for me: How can I launch the Ubuntu Live USB that I have when I already have Ubuntu installed? Is that possible? I just need the memtest but it seems I'm just so stuck at this point this is my only other option.

Ok, I made a USB. Is there any special program I need to turn this into a bootable drive? All that was extracted when I unzipped was memtest86-usb.img



I just read the README. which says this:

> Booting the MemTest86 USB drive
========================================
This USB drive supports dual booting on UEFI and BIOS platforms. 
Most newer systems are able to run the UEFI version of MemTest86.
On machines that don't support UEFI, the older V4 BIOS release of MemTest86 
will be automatically booted.

To boot from the drive you may need to go into your BIOS settings and
alter your boot order. Or launch the boot menu at system startup.
The methods for doing this will vary depending on your motherboard.

To start MemTest86 insert the USB flash drive into the appropriate drive and 
restart your computer. If running on a UEFI system, the UEFI BIOS must be configured 
to boot from the device that MemTest86 is installed on. Most systems have an optional 
boot menu that is enabled by pressing a key at startup (often ESC, F9, F11 or F12).

If available use the boot menu to select the correct drive. 
You may see both the UEFI and BIOS as separate options. 
Please consult your motherboard documentation for details.

On a Mac, you need to hold down the 'c' key while the computer is booting to boot from CD. 
To boot from USB, you need to hold down the ALT / Option key on the Mac keyboard 
while powering on the machine.


Reclaiming disk space from the USB drive
========================================
You may have noticed that the MemTest86 USB drive you have created may have lost some 
disk space and normal formatting will not recover the lost space. 
For example, this can happen when a UFD contains multiple partitions, such as the
MemTest86 image. Formatting will not span across multiple partitions/volume. 
To erase the partition records and reclaim the whole disk, you will need to 
zero the MBR.

WARNING: THIS PROCESS WILL COMPLETELY DELETE THE DATA ON THE DRIVE

So I figured out I need to press Esc to get to the boot menu. Great! *phew* Finally figured that out but it's asking for commands now. I have no idea what I should be inputting. I've tried a few commands but I don't know any of that kind of thing (I'm way to young to have ever used DOS or anything similar). All youtube shows is how to do it on Windows. I can't seem to find any tutorials for linux. Huh.

On my boot menu I still have no option for memtest86. I don't know why it can't find my USBs. I tried to put my Live USB back in to see if it could boot from there and it didn't show up either. I'm at a loss.

---

### Post by ajgreeny on 2017-01-09
> **chris.2 said:**
> Update: to make things simpler for me: How can I launch the Ubuntu Live USB that I have when I already have Ubuntu installed? Is that possible? I just need the memtest but it seems I'm just so stuck at this point this is my only other option.

On my boot menu I still have no option for memtest86. I don't know why it can't find my USBs. I tried to put my Live USB back in to see if it could boot from there and it didn't show up either. I'm at a loss.
Which boot menu are you talking about above, is it the grub menu or some other menu that you see?
If you look at the info at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) you may find some more details of how to discern if you are using UEFI or BIOS.

You can also use terminal command ```
[ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode"
``` and you will be able to see; legacy mode is the old BIOS way.

---

### Post by Bucky Ball on 2017-01-09
In your case it might be fairly straightforward without the use of memtest. It only shows 4Gb but you have 8Gb installed? One of the cards is probably dead. Shut down and take one of the cards out. Boot up. Is it showing 4Gb? If so, that would be the good card. Take it out and put the other card in. Boot. Still showing 4Gb? If not, there's your answer.

As for booting the live media, just go ahead and boot it as you normally would. Nothing to do with what you have installed on the hard drive. Not related. The live boot runs from the install media, not the hard drive.

---

### Post by chris.2 on 2017-01-09
> **ajgreeny said:**
> Which boot menu are you talking about above, is it the grub menu or some other menu that you see?
If you look at the info at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) you may find some more details of how to discern if you are using UEFI or BIOS.

You can also use terminal command ```
[ -d /sys/firmware/efi ]  && echo "Installed in EFI mode" || echo "Installed in Legacy  mode"
``` and you will be able to see; legacy mode is the old BIOS  way.

I'll just go ahead and say that's way over my head. I  don't know if I'll even be able to find the right place to type that to  be honest. I think what you're saying is to type this when I press "Esc" and get a menu that says <grub> or something similar.


> **Bucky Ball said:**
> In your case it might be fairly straightforward without the use of memtest. It only shows 4Gb but you have 8Gb installed? One of the cards is probably dead. Shut down and take one of the cards out. Boot up. Is it showing 4Gb? If so, that would be the good card. Take it out and put the other card in. Boot. Still showing 4Gb? If not, there's your answer.

As for booting the live media, just go ahead and boot it as you normally would. Nothing to do with what you have installed on the hard drive. Not related. The live boot runs from the install media, not the hard drive.

It's odd because I never can get to the "Try Ubuntu, Install Ubuntu" screen anymore. I used to just hit F12 but that doesn't work anymore. I wonder if I just pop out the hard drive it'll work for me. I just ran a memtest on a machine with no hard drive in it at all and it worked (well, the computer didn't hahaha. It overheated at 70% or so.) so I know how to easily run it from a Live USB. Maybe that's what I'll just try right now.

Oh and about the ram, it's from the laptop that over heated (and the hard drive died) so I just wanted to see if it worked at all. It didn't show up but after a few restarts and cleaning/tinkering it now shows up. I just don't know how well it runs, that's what I wanted to test.

---

### Post by oldos2er on 2017-01-09
Don't type it; copy and paste it into a terminal (Ctrl-Alt-t) when you're booted into Ubuntu. Then you can copy and paste the output into a post here if you wish.

---

### Post by chris.2 on 2017-01-09
> **oldos2er said:**
> Don't type it; copy and paste it into a terminal (Ctrl-Alt-t) when you're booted into Ubuntu. Then you can copy and paste the output into a post here if you wish.

What I got was:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

chris@chris-laptop:~$ [ -d /sys/firmware/efi ]  && echo "Installed in EFI mode" || echo "Installed in Legacy  mode"
Installed in EFI mode


```

---

### Post by ajgreeny on 2017-01-10
OK, so you're using a UEFI machine which will not have memtest in the grub menu, so don't keep looking for it; it will not show.

You will certainly need to download the MemTest86 V7.2 Free Edition I linked in my post #3 which appears to be as an iso file at [http://www.memtest86.com/downloads/memtest86-iso.tar.gz](http://www.memtest86.com/downloads/memtest86-iso.tar.gz) ,extract the iso file from that and either burn it to a CD or USB (as an image, not as a data file) and boot to the CD/USB.

---

### Post by chris.2 on 2017-01-10
> **ajgreeny said:**
> OK, so you're using a UEFI machine which will not have memtest in the grub menu, so don't keep looking for it; it will not show.

You will certainly need to download the MemTest86 V7.2 Free Edition I linked in my post #3 which appears to be as an iso file at [http://www.memtest86.com/downloads/memtest86-iso.tar.gz](http://www.memtest86.com/downloads/memtest86-iso.tar.gz) ,extract the iso file from that and either burn it to a CD or USB (as an image, not as a data file) and boot to the CD/USB.

I have the USB ready but I don't know how to boot it at this point. When I tried to hit F12 or Esc it didn't have the memtest86 option for me. I read the README and I've done everything properly it's just literally the last step I'm struggling with.

I have 2 Files extracted onto the USB: memtest86-usb.img and README.

Just tried again, I only have 1 option to boot into and that'd my harddrive. Any idea why the USB wouldn't be working?

---

### Post by ajgreeny on 2017-01-11
How did you copy the iso image you downloaded to the USB?
You can not simply copy it to the USB but have to create a bootable image on the USB with an appropriate application.  All the info needed to do that is on the site I linked.
You can also use a CD burner to burn the image to a CD-RW and boot to that if you prefer.

---

### Post by chris.2 on 2017-01-11
> **ajgreeny said:**
> How did you copy the iso image you downloaded to the USB?
You can not simply copy it to the USB but have to create a bootable image on the USB with an appropriate application.  All the info needed to do that is on the site I linked.
You can also use a CD burner to burn the image to a CD-RW and boot to that if you prefer.

I downloaded it then extracted it to the USB. it shows up as a .img file so wouldn't that be right?

Ahhhhhh I see what I did wrong. Ok let me do a quick reboot. I think this should work now.



GOT IT TO WORK! THANKS!

---

