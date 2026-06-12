---
title: "installing from .iso"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-04-14
I'm having a huge problem with something that should be dead simple, yet I cannot seem to find anything or figure out how to. 
I'm trying to install from an .iso - I have managed to mount the .iso but fail to understand what comes next... there is nothing I can click and it auto starts, typing in the terminal gives me the same "folder cannot be located" and I'm starting to get extremely frustrated. Could someone please explain to me how to install from a mounted .iso

I have ubuntu 11.10 and am using Gnome Classic shell.

Thank you ever so much.

---

### Post by lisati on 2012-04-14
I have never installed directly from ISO, and will defer to the wisdom of others who might have tried using that method.

What I usually do is [burn to disk]("https://help.ubuntu.com/community/BurningIsoHowto") or [copy to USB]("https://help.ubuntu.com/community/Installation/FromUSBStick") and install from my chosen medium.

---

### Post by sandyd on 2012-04-14
> **kabukiM0n0 said:**
> I'm having a huge problem with something that should be dead simple, yet I cannot seem to find anything or figure out how to. 
I'm trying to install from an .iso - I have managed to mount the .iso but fail to understand what comes next... there is nothing I can click and it auto starts, typing in the terminal gives me the same "folder cannot be located" and I'm starting to get extremely frustrated. Could someone please explain to me how to install from a mounted .iso

I have ubuntu 11.10 and am using Gnome Classic shell.

Thank you ever so much.

Are you trying to install programs from an mounted iso, or install Ubuntu from a mounted iso?

---

### Post by oldfred on 2012-04-14
You do not run ISO from inside system but reboot and use grub2 to loopmount it.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

I was using ISO on flash drives as flash was faster thatn CD, but running it from Hard Drive is faster still.

---

### Post by kabukiM0n0 on 2012-04-14
> **sandyd said:**
> Are you trying to install programs from an mounted iso, or install Ubuntu from a mounted iso?
I am trying to install programs. 

> **oldfred said:**
> You do not run ISO from inside system but reboot and use grub2 to loopmount it.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

I was using ISO on flash drives as flash was faster thatn CD, but running it from Hard Drive is faster still.

Thank you, I shall have to read up a little more, because I do not understand a word of what is said there. :s

---

### Post by oldfred on 2012-04-14
What I posted it to do a full install. If you just want programs ignore all of it.

Your install should have all the programs from the ISO. Do you not have Internet to update or add programs?

---

### Post by kabukiM0n0 on 2012-04-14
> **oldfred said:**
> What I posted it to do a full install. If you just want programs ignore all of it.

Your install should have all the programs from the ISO. Do you not have Internet to update or add programs?

I have the internet yes, everything is updated. I just do not know how to make them auto run and how to bring up the "installation box". The .iso has be mounted on a USB and I have also tried with gISOmount. Neither is there a file that would autorun.

Edit: Maybe I have to use a Virtual Box?

---

### Post by theknightlinux on 2012-04-14
I don't get it. Are you trying to run the Ubuntu 11.10 installation from inside a Ubuntu 11.10 system using an .iso image from a USB flash card. And if so, where are you trying to install the Ubuntu 11.10 installation?

---

### Post by d4m1r on 2012-04-14
You should be able to mount an .iso file and launch its contents from Ubuntu....that's how it works under Windows at least. What is contained in the .iso? If its linux files, then it should work. But you have 2 other options;

1) Burn the .iso to CD and it will format it for you (burning option should read something like "burn image")

2) Extract the contents of the .iso under your Ubuntu partition to your Home folder for example and launch it from there

---

### Post by kabukiM0n0 on 2012-04-15
> **theknightlinux said:**
> I don't get it. Are you trying to run the Ubuntu 11.10 installation from inside a Ubuntu 11.10 system using an .iso image from a USB flash card. And if so, where are you trying to install the Ubuntu 11.10 installation?

No, I'm trying to install programs.

> **d4m1r said:**
> You should be able to mount an .iso file and launch its contents from Ubuntu....that's how it works under Windows at least. What is contained in the .iso? If its linux files, then it should work. But you have 2 other options;

1) Burn the .iso to CD and it will format it for you (burning option should read something like "burn image")

2) Extract the contents of the .iso under your Ubuntu partition to your Home folder for example and launch it from there

I cannot burn into a CD as I am on a netbook.
So in windows, you would mount the .iso and from the double click the appropriate .exe to set up the installation. That's what I fail to understand. As I tried to do that but it just opens the file saying "This file cannot be opened" 

Maybe the right question would be. Once I have mounted the .iso image - how to I go about installing the data. And to answer you question, yes, the files are for linux.

---

### Post by SeijiSensei on 2012-04-15
If you're connected to the Internet, just run

```
sudo apt-get install name-of-package
```

and the system will download the package from the repositories and install it.

You can install from an ISO image, but you'll need to rewrite /etc/apt/sources.list to use a file:// URL that points to the mounted ISO.  That's a lot more difficult than just installing over the Internet.  Why not do that?

If you have a CD/DVD drive, burn the ISO, then run the system's Package Manager.  You'll see an option to change the "Software Sources."  There should be CD-ROM entries in the list with their check boxes empty.  Check the boxes, save and update the source, then put the CD in the drive.  The installer should then look at the CD.  Again, though, it's really not worth the effort to do this compared to installing over the Internet.

---

### Post by oldfred on 2012-04-15
Linux is not Windows. You do not normally install applications like you would with downloading .exe files. A .deb is equivalent to a .exe, but almost all the .deb you ever would want are in the software repository and easily downloaded. 

You can use command line like SeijiSensei posted if you know the name of the package which is not usually exactly the same name as the software, or you can use Software Center, or Synaptic. Synaptic may not be installed in newer versions as Ubuntu is trying to use Software Center. But not everything seems to be in Software Center.

[http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre](http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre)

---

### Post by theknightlinux on 2012-04-15
So did you download the DVD .iso image from Ubuntu, where it has all the updates?

---

### Post by theknightlinux on 2012-04-15
Well, I'm assuming you don't have an internet connection on your netbook and downloaded the DVD .iso, and placed the image on your netbook OS, and then mounted the image.
Lets see if this can work for you:
Go to the top right corner- sytem settings- software sources. In there, check the box where it says: Installable from CD/DVD ROM.

You usually need a burned CD/DVD ROM for it to work, but you can give it a try and lets see if the Software Sources can recognize the image as a Physical drive.

---

### Post by theknightlinux on 2012-04-15
You can also try on the tab where it says: Other Software, then go to: Add Volume, and see if the .iso image is recognized. Remember the .iso image should be mounted.

---

### Post by theknightlinux on 2012-04-15
Tell us if any of those worked, as there are more steps to follow, I believe.

---

### Post by WindowsToLinux on 2012-04-15
my experience was as follows...

Installed ubuntu 11.10 as a dual boot alongside windows
Opened ubuntu and discovered that it very easily burns discs very easily from within nautilus
I downloaded the .iso from ubuntu website and burned a disc
restarted laptop with disc in the drive and it booted the install process

I picked the option to install only ubuntu and DUMP WINDOWS

very simple, very easy and I think I can sleep easily tonight 

:lolflag:

---

### Post by kabukiM0n0 on 2012-04-15
> **oldfred said:**
> Linux is not Windows. You do not normally install applications like you would with downloading .exe files. A .deb is equivalent to a .exe, but almost all the .deb you ever would want are in the software repository and easily downloaded. 

You can use command line like SeijiSensei posted if you know the name of the package which is not usually exactly the same name as the software, or you can use Software Center, or Synaptic. Synaptic may not be installed in newer versions as Ubuntu is trying to use Software Center. But not everything seems to be in Software Center.

[http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre](http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre)

But the program I'm trying to install has nothing to do with linux, in the sense that I will not find it in the software center, this is why I'm having such trouble installing it - as everything else I've needed is there - that's why I wonder; maybe I need to use a virtual box to install it?

---

### Post by kabukiM0n0 on 2012-04-15
> **theknightlinux said:**
> Well, I'm assuming you don't have an internet connection on your netbook and downloaded the DVD .iso, and placed the image on your netbook OS, and then mounted the image.
Lets see if this can work for you:
Go to the top right corner- sytem settings- software sources. In there, check the box where it says: Installable from CD/DVD ROM.

You usually need a burned CD/DVD ROM for it to work, but you can give it a try and lets see if the Software Sources can recognize the image as a Physical drive.

No, as I said before I have the internet on my netbook and downloaded the .iso and then mounted the image (look at previous posts) 

Nope, tried that and still nothing. I am seriously beginning to think that it has to be run from a virtual box. For example - how would one install something that isn't listed on the software, yet you have the .iso mounted?

---

### Post by Peripheral Visionary on 2012-04-15
In order to install it, you need to **BOOT** from the iso (image, not data). That's why we burn it to a CD. Then insert the CD into your computer's drive and re-boot. During the restart, on most computers the manufacturer's screen offers a boot menu for a few seconds (on my Dell it's "F12 for Boot Options). Choose "Boot from CD-ROM drive."

---

### Post by Cheesemill on 2012-04-15
If you can tell us what software you are trying to install it would be a great help.

Also a file listing of the mounted iso would be good (a sreenshot will do).

I think people here are getting confused as to exactly what it is you are trying to install.

---

### Post by 3Miro on 2012-04-15
> **Cheesemill said:**
> If you can tell us what software you are trying to install it would be a great help.

Also a file listing of the mounted iso would be good (a sreenshot will do).

I think people here are getting confused as to exactly what it is you are trying to install.

+1.

I have installed both Linux and Windows apps from .iso files, you mount the file (with -o loop) and then you need to find either setup.exe (run it under wine) or some Linux install script. This is all I can say without more information.

---

### Post by Cheesemill on 2012-04-15
> **3Miro said:**
> +1.

I have installed both Linux and Windows from .iso files, you mount the file (with -o loop) and then you need to find either setup.exe (run it under wine) or some Linux install script. This is all I can say without more information.

I think thats where we are getting confused. i don't think the OP is trying to install Windows or Linux. I think they are trying to install a Linux application from an iso file.

---

### Post by kabukiM0n0 on 2012-04-15
> **Cheesemill said:**
> I think thats where we are getting confused. i don't think the OP is trying to install Windows or Linux. I think they are trying to install a Linux application from an iso file.

Exactly, I've mentioned this various times. So how do I go about this?

---

### Post by Cheesemill on 2012-04-15
OK then.

Wifislax isn't an application. It's a different Linux OS (or distribution).

The easiest way to do this would be to use the startup disk creater  application that comes with Ubuntu to write the ISO to a USB stick.

Then just reboot but boot from the USB, not from your hard drive.
This shoud give you the option to either overwrite your current Ubuntu installation or set up a dual-boot system.

---

### Post by kabukiM0n0 on 2012-04-15
There's two files in the .iso - Boot and Wifislax 

How do I get it rolling?

---

### Post by critin on 2012-04-15
> I am trying to install programs. 

And to answer you question, yes, the files are for linux.

But the program I'm trying to install has nothing to do with linux, in the sense that I will not find it in the software center,

and downloaded the .iso and then mounted the image (look at previous posts) 
 
Using ISO term makes me think operating system, but you don't mean that do you?  You said the files are for linux, than said they have nothing to do with linux---?

If you would say what program/files you are trying to install it would help a lot.

I did find this reference, it may help.

[http://linux.about.com/od/kubuntu_doc/a/kubudg28t07.htm](http://linux.about.com/od/kubuntu_doc/a/kubudg28t07.htm)

Mount/unmount Image (ISO) files without burning to CD

    To mount Image (ISO) file

        sudo mkdir /media/iso sudo modprobe loop sudo mount file.iso /media/iso/ -t iso9660 -o loop

    To unmount Image (ISO) file

        sudo umount /media/iso/

---

### Post by kabukiM0n0 on 2012-04-15
> **Cheesemill said:**
> OK then.

Wifislax isn't an application. It's a different Linux OS (or distribution) which has to be installed like Windows or Ubuntu.

The easiest way to do this would be to use the startup disk creater application that comes with Ubuntu to write the ISO to a USB stick.

Then just reboot but boot from the USB, not from your hard drive.
This shoud give you the option to either overwrite your current Ubuntu installation or set up a dual-boot system.

Okay, so just make my netbook startup from usb? thank you ever so much.

---

### Post by Cheesemill on 2012-04-15
Wifislax isn't an application. It's a Live CD (just like the Ubuntu installer).

Use one of the following methods to create a bootable USB from your ISO file:

[https://help.ubuntu.com/community/Installation/FromUSBStick#From_Ubuntu_Linux](https://help.ubuntu.com/community/Installation/FromUSBStick#From_Ubuntu_Linux)
[http://www.pendrivelinux.com/liveusb-install-live-usb-creator/](http://www.pendrivelinux.com/liveusb-install-live-usb-creator/)

---

### Post by kabukiM0n0 on 2012-04-15
> **Cheesemill said:**
> Wifislax isn't an application. It's a Live CD (just like the Ubuntu installer).

Use one of the following methods to create a bootable USB from your ISO file:

[https://help.ubuntu.com/community/Installation/FromUSBStick#From_Ubuntu_Linux](https://help.ubuntu.com/community/Installation/FromUSBStick#From_Ubuntu_Linux)
[http://www.pendrivelinux.com/liveusb-install-live-usb-creator/](http://www.pendrivelinux.com/liveusb-install-live-usb-creator/)

I've already done this, I just thought that it ran inside Linux and the installation would be as if for example you're installing a game in windows. Not that it contained it's own OS.

---

### Post by theknightlinux on 2012-04-15
So yes, it'll be better to use Virtual Box to install it and try it. Or install it along your current distro.

---

### Post by 3Miro on 2012-04-15
> **Cheesemill said:**
> I think thats where we are getting confused. i don't think the OP is trying to install Windows or Linux. I think they are trying to install a Linux application from an iso file.

I meant to say Linux or Windows apps, but I make a mistake. Then it turns out OP is installing an operating system ... this is confusing.

To the OP, if you want to play around with another OS, VirtualBox is a good way with no risk to your current system. If you feel adventurous, then you can install it on a separate partition, but read about boot-loaders so you don't mess up your current installation.

---

