---
title: "Messed Up Install, White Blinking Cursor After BIOS"
date: 2014-09-16
forum: New to Ubuntu
---

### Post by Henry_Flower on 2014-09-16
I was preparing to install ubuntu over a previous Windows 7 installation via bootable usb, when having gotten as far as the region selection screen, I decided I wanted to go back and look at the advanced partition options. Back was greyed out and closing the installer was taking a long time so stupidly, out of impatience, I reset my computer. I didn't think it would affect anything because nothing had begun installing yet but now post-bios all I get is a blinking white cursor. I've tried every possible boot order, resetting the bios to default settings, and I currently have no usb device plugged in except for the thumb drive with the installer (and of course, I tried starting with that unplugged too).

I've also tried tapping f8 and booting from the thumb drive like that. When I do, I get the message: "remove disks or other media, press any key to restart." No disks or other media are plugged in and pressing a key does nothing but advance the cursor by one line. 

Thanks in advance for the help!

Hitachi 1TB HDD
Asus p5g41-m le
Nvidia card (can't remember which)

---

### Post by Bashing-om on 2014-09-16
Henry_Flower; Hi ! My Welcome to the forum.

Panic not. Just proceed in a calm and orderly fashion. 
We will get over this little hump.
The quicker way is to once more reinstall ubuntu, paying close attention to where grub is installing the boot code;
As this indicates to me that grub did not install to the hard drive, and has in fact messed up the boot code on the USB thumb drive.
 I do suggest we start all over and burn a new image, so we know the boot code is valid on the USB thumb drive.

OK, once we have the new image verify it from the boot menu ( booting, soon as the bios screen clears, depress and hold the right -shift- key ) -> "check disk for defects " .
Now we want to know what the system sees for the disk's nomenclature:
from the liveUSB -> terminal; What returns from terminal command:
```

sudo fdisk -lu
sudo parted -l 

``` so we KNOW the location, as the system sees it, to make sure the boot code installs properly.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We do this slowly, one step at a time and get you running ubuntu !

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-09-16
What Bashing-om said. One thing, if you were setting the region I don't think you would have been at the partitioning section yet. When you do get there, the 'advanced partitioning' options are available if you choose 'something else' at the partitioning section of the install (when you are asked if you want to install alongside Windows, if Windows 7 is still there). You can then create/delete partitions as you wish.

If, after following B-om's instruction to burn a new install USB, you manage to boot into a live desktop from it, might be an idea to launch Gparted and wipe Win7 so you are starting from a clean slate as it sounds like you are installing a Ubuntu only system. One less point of confusion. 

Good luck and welcome. ;)

---

### Post by grahammechanical on 2014-09-16
According to this wiki page the region selection screen or where are you? comes after the Installation type screen. At the installation type screen there are five choices

Install Ubuntu alongside
Erase disk and install Ubuntu
Encrypt the new Ubuntu installation for security
Use LVM with the new Ubuntu installation
Some thing else

Once we have moved on from either of those selections there is no turning back as the installation has already begun. The installer does not wait until we say where we are and who we are and what password we want. It carries on installing in order to reduce the installation time.

You have an incomplete installation. There is no point trying to fix it. Install again.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

If we look at the images in that link we see that by the time we reach the Who are you? page the installer is copying files. 

Regards.

---

### Post by Henry_Flower on 2014-09-16
Thanks for the responses! I tried to load the boot menu as instructed but couldn't seem to open it. However, I did reformat and reburn the installer on the usb, tested it on two different PCs and I've concluded that the image file is corrupted so I'm redownloading it and creating the bootable disk using the instructions found [here]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") instead of the command prompt. I'm also downloading GParted as Bucky suggested and will clear the hard drive with that first. Unfortunately, I don't have internet access at home right now: I need to go to a nearby coffee shop to download anything so this might take a bit longer than it would otherwise but I think I'm on the right track now so thanks again! I'm really looking forward to never using Windows ever again.

**EDIT: **re: grammechanical: I was installing from a live demo - it had probably already begun but as far as I know I hadn't even started so I certainly don't mind starting over. Either way I think it's just a matter of getting an uncorrupted .iso and installing again.

---

### Post by Bashing-om on 2014-09-16
Henry_Flower; Great !

Safety is no accident:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

making sure what there is is
[INDENT][INDENT]good from the git-go
[/INDENT][/INDENT]

---

### Post by Henry_Flower on 2014-09-16
All right! Everything is up and running. After a little research, I decided to go with Linux mint with xfce rather than vanilla ubuntu. Thanks for your help. Any good guides on how to do basic things like change the screen resolution? I'm using 4g with poor reception right now so it's difficult to search.

---

### Post by Bashing-om on 2014-09-16
Henry_Flower; Nope,

I do not do Mint, so can not advise on that .
As this original situation is now concluded, please mark this thread solved ( top of post -> thread tools).
Open a new thread on this new issue to gain a wider audience.


[INDENT][INDENT]and just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by nerdtron on 2014-09-16
> **Henry_Flower said:**
> All right! Everything is up and running. After a little research, I decided to go with Linux mint with xfce rather than vanilla ubuntu. Thanks for your help. Any good guides on how to do basic things like change the screen resolution? I'm using 4g with poor reception right now so it's difficult to search.

Changing the screen resolution? Are you using proprietary drivers (nvidia/ati) or you haven't installed anything yet?

You should be able to change resolution on the display settings. Anyway you can try installing arandr using the software center. It's a little GUI utility for changing the resolution.

---

### Post by Bucky Ball on 2014-09-17
> **Henry_Flower said:**
> All right! Everything is up and running. After a little research, I decided to go with Linux mint with xfce rather than vanilla ubuntu. Thanks for your help. Any good guides on how to do basic things like change the screen resolution? I'm using 4g with poor reception right now so it's difficult to search.

Take note: We do not support Linux Mint on the forums here. They have an active community and forum, though. Please mark this thread as solved and post any further support requests [HERE]("http://ubuntuforums.org/forumdisplay.php?f=401") as your questions are now off-topic to the original title and topic. You would probably have more luck on the Mint forums, though. 

Thanks and good luck.

---

