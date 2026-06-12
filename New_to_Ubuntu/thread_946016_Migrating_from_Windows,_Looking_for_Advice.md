---
title: "Migrating from Windows, Looking for Advice"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by wausaubill on 2008-10-12
Hello all,

I know things like this have been touched on and probably written about, but I will start out asking for some direction so that I have a better idea where to look, so as to flatten my learning curve a bit.

I have been using XP for some time now and few months back  my SO and I bought a laptop with Vista on it.  The new laptop runs slower than my XP machine (it should be faster, of course) so I can see the writing on the wall and know it is time to make the switch.

In the past I have tried to switch to Linux, but have been stymied with techincal issues -- mostly the dreaded partition.  But now I think I have a way around that.

External USB drives are almost cheaper than internal ones, so I can get a USB drive and use it as my Linux drive.  I am not talking about a little thumb drive, but a full size 500GB or larger box here.  Might as well go all the way. :)

I am going to assume that my Intel box will not boot from a USB drive, so what is the best way to go about this?  A live CD?  Any tutorials on how to configure those external drives?

Any other ideas, comments or suggestions??

Thanks so much!

Bill

---

### Post by Jackelope on 2008-10-12
Just burn a live CD at about 4x and then pop it in the drive, reboot, and you should be up and running with a live desktop in 10-20 minutes. From there, you can install by clicking the desktop icon. 

Did you plan to install Ubuntu on the external drive? If so, there are a few extra considerations compared to a normal install...just check the forums for posts on external hard drive installs.

---

### Post by wausaubill on 2008-10-12
Thanks, Jack. :) Yes, I was hoping I could install on the USB drive, that way it would become portable (or perhaps somewhat portable...)  

I'll look for more advice in the forum here...

Thanks!

---

### Post by Bucky Ball on 2008-10-12
If you check the options in your BIOS you will probably find that you can boot from USB. :)

It should be right there in the options for first boot device. Partitioning is quite straightforward now with the desktop iso, so if you read up a bit, and there is plenty of info out there, that shouldn't be a problem either. Simply, you would create three (basic) partitions like these:

/
/home
/swap

/ = your root partition where Ubuntu is stored - this partition should have the boot flag on and be around 10+ Gb
/home = your personal data
/swap = the swap partition which should be about twice the size of your physical RAM.

To this partition list you could add whatever you wish:

/video
/pictures
/music

Linux needs to be on EXT3 type partition and the swap chooses the type automatically. Just leave the disk you have in the box which will show up as NTFS type if you have Windoze on it. If you have free space on the disk or an empty disk, you can choose to let Ubuntu automatically partition your drive/free space also. 

Good luck whichever way you go. \\:D/

---

### Post by SteveNorman on 2008-10-12
To start with you can just use the guided partition during install. It will give you one partition plus a swap unless they changed that from when I installed. Ubuntu is a great cross over distribution to start with. It is still a good idea to learn some command line stuff and not be entirely dependent on the gui. That was my big stumbling block when switching over. Now I prefer the command line as it seems things dont go wrong as often as with guis, command and apps run quicker, and I am more aware of what my computer is doing. It takes time and a bit of hair-pulling but the pay-off is well worth it.

I used this:
[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)
in addition to some basic linux tutorials to get me going with command line basics.

here is a link to some dedicated usb/linux boot info

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

good luck!

---

### Post by unutbu on 2008-10-12
Hello wausaubill, welcome to the forums.
Two things come to mind which I think might be useful to you:

[list]
[*]First, when you install Ubuntu on an external USB drive, in the 7th and final step entitled "Ready to install", make sure you click on the "Advanced" button. By default Ubuntu will be set to install its bootloader (GRUB) on your first (internal) drive which it refers to as (hd0). This would not be a very good thing for you, because it would mean your computer could not boot Windows without the external drive connected. To avoid this, change the "Device for boot loader installation" to (hd1). This will be your second drive, the USB external drive. 

Then proceed with the installation.

When the installation is complete, your internal drive should be untouched. You will still be able to boot Windows as usual. To boot Ubuntu, you would normally enter a BIOS menu to tell the BIOS that you wish to boot from the 2nd drive. If you have a fairly new computer, you should be able to boot from a USB drive. 

Since you say this is a new laptop, I think BuckyBall is right -- you probably do have the option to boot from a USB drive.

[*]However, if you find you do not have this option, then one very nice idea is to boot from a CD which you can create, and which has GRUB on it. The CD can be configured to give you the ability to boot the USB drive. This is very nice for portability: you just connect the drive to any computer, stick the CD in at boot, and tell the BIOS you wish to boot from the CD.

If you wish to create such a CD, check out this page: [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB).
[/list]
For general information on how to install Ubuntu: [https://help.ubuntu.com/8.04/installation-guide/i386/index.html](https://help.ubuntu.com/8.04/installation-guide/i386/index.html)

---

### Post by aysiu on 2008-10-12
Another option to avoid partitioning is Wubi, which sets up a dual boot by installing a virtual Ubuntu hard disk as a huge file inside Windows and then edits the Windows boot loader menu to include an entry for Ubuntu.

Instructions here:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by wausaubill on 2008-10-13
Thanks folks for all of the wonderful ideas.  It would seem that things have come a long way since I last tried to install Linux.

WUBI looks like a very interesting technique to be up and running very quickly for a Windows switcher such as myself.

I will make one slight correction...I am not looking to install Ubuntu on the laptop (which runs vista) but rather on my XP desktop machine.  The laptop is being used by the SO and she is not quite as adventurous as I am.  But in using Vista it is pretty obvious that Vista is "worse" than XP -- in a whole lot of ways.  So it tells me it is time to change.

Thanks again, I will be checking out all of the information given here and when I make the move, I will let you know.  I have already DLed WUBI and will probably check it out tonight.

Bill

---

### Post by wausaubill on 2008-10-14
So, I ran the Ubuntu installer and after two aborted installs (the installer would only download the needed files at about 4K, said it would take about 48 hours or so...) I downloaded the iso file and ran WUBI and rebooted.  

Unfortunately, I had not read this thread again just before doing that, so I missed doing the advanced disk drive change and when I rebooted, I got "Error 1" because my file paths for the boot loader are relative and not absolute, so it is back to the drawing board for now.  Will try again...

Bill

---

