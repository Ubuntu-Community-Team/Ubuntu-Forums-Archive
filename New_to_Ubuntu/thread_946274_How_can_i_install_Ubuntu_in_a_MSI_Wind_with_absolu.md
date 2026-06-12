---
title: "How can i install Ubuntu in a MSI Wind with absolutely NO OPERATING SYSTEM?"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Fabolous_Boy on 2008-10-13
ok guys, this is my first and probably the last post so please help a technologically crippled kid out.

ok, i just got an MSI Wind for my birthday and it doesnt have any OS preloaded into it. I know Ubuntu will be the best for me so i downloaded into a Desktop thats XP. I have tried to install it 3 times with a FlashDrive but it didnt work (PLEASE NOTE THAT THE WIND HAS NO CD-ROM DRIVE) so probably im doing it wrong.

Heres what i did:

1.I Got a FlashDrive and i used UNETBOOTIN make it bootable in the WIND (i forgot the purpose for it so...)
2.I plugged it in the USB Port on the Wind and i selected INSTALL in the menu.
3.I did the normal process...FOR LIKE 3 HOURS (but i know it was going to be WORTH THE TIME [cuz its Ubuntu])
4.I rebooted it (as the installation says so)
5.While reeboting, i expected that Ubuntu will load normally (Like with the desktop and all that) but it did like it booted before (with like the black screen and the white text ONLY [i dont know what thats called so im very sorry]).

I think i accidentaly downloaded the Server version 

(So please) people who know how to install Ubuntu in a computer with no OS and CD-ROM drive, HELP ME OUT SO I CAN USE MY LAPTOP ALREADY...thank you

---

### Post by Berean on 2008-10-13
Forgive me if I've not got this completely clear - if anything sounds dodgy please re-post - but you want to install/boot Ubuntu onto something without an OS?  Essentially, you'll need to boot from a USB device as you've stated.  I found that a 4GB drive is best, as anything smaller doesn't have the room to update, and can also fail quickly due to increased boot cycles.  You'll need to toggle your bios (F2 on a desktop/laptop, but will probably be something else on the Wind) to set it to boot from USB.  This thread should help you: [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

Either use someone elses desktop to download it to the USB following the above thread, or buy a USB with Ubuntu preinstalled.  Alternatively, as I'm doing now, boot from an external hard drive (120GB) partitioned to 40GB ext3 with Ubuntu installed on it, and 80GB NTFS/FAT32 to save files to and to read in Windows.  You'll need to install this IN ubuntu, or from Windows.

Good luck and God speed!

---

### Post by Elfy on 2008-10-13
If you downloaded and installed the server version then let it boot and when you get to the prompt - use this command to install the ubuntu desktop.

```
sudo aptitude install ubuntu-desktop
```

The password it needs is your normal password, when you type it it will not show.

---

### Post by Fabolous_Boy on 2008-10-13
> **Berean said:**
> Forgive me if I've not got this completely clear - if anything sounds dodgy please re-post - but you want to install/boot Ubuntu onto something without an OS?  Essentially, you'll need to boot from a USB device as you've stated.  I found that a 4GB drive is best, as anything smaller doesn't have the room to update, and can also fail quickly due to increased boot cycles.  You'll need to toggle your bios (F2 on a desktop/laptop, but will probably be something else on the Wind) to set it to boot from USB.  This thread should help you: [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

Either use someone elses desktop to download it to the USB following the above thread, or buy a USB with Ubuntu preinstalled.  Alternatively, as I'm doing now, boot from an external hard drive (120GB) partitioned to 40GB ext3 with Ubuntu installed on it, and 80GB NTFS/FAT32 to save files to and to read in Windows.  You'll need to install this IN ubuntu, or from Windows.

Good luck and God speed!

Is it the same with INSTALLING IT AS THE OS? i mean without having to need the Flash Drive to boot?

---

### Post by bumanie on 2008-10-13
If you have installed the 'headless' server version successfully, do as forestpixie says and that should give you the ubuntu desktop environment (GUI).

---

### Post by t0p on 2008-10-13
+1 for [www.pendrivelinux.com]("http://www.pendrivelinux.com").  There are detailed instructions for loading ubuntu via usb drive, in combination with a pc loaded with windows, with ubuntu, or with nothing except a live cd.  If you do a google search with the following search terms:

> ubuntu 8.04 site:[www.pendrivelinux.com](www.pendrivelinux.com)

you'll find links to the lot.  I used these instructions, plus tweaks from [wiki.eeeuser.com]("http://wiki.eeeuser.com") to get hardy working wonderfully on my eeepc 4G - I know the wind is a different beastie, but it is at least the same *kind* of beastie...

---

### Post by hyper_ch on 2008-10-13
here are a lot of ways on how to isntall it: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by prshah on 2008-10-13
> **Fabolous_Boy said:**
> 
it did like it booted before (with like the black screen and the white text ONLY [i dont know what thats called so im very sorry]).

I think i accidentaly downloaded the Server version 


Does the "black screen" say something like "(initramfs)" or "BusyBox"? In which case, it's not a server version install, it seems to be a faulty install.

You can follow the (detailed) directions at [www.pendrivelinux.com](www.pendrivelinux.com) to transfer an install / live image to a pendrive, and then use that to boot / live-test / install Ubuntu. Even a 1Gb flash drive / usb pendrive will suffice. (EDIT: Heh; t0p types faster than I do!)

Post back if you run into difficulties.

---

### Post by Fabolous_Boy on 2008-10-13
In [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/), it says > Important: Physically disconnect ALL internal hard drives before booting from the CD and performing the install. this will eliminate the possibility of installing to the wrong device and overwriting your MBR. Reattach the drives after completing this tutorial.

i dont get it...can someone elaborate? (sorry if im quite stupid sometimes :confused:) what does "internal hard drives" mean there?

---

### Post by Orange_and_Green on 2008-10-13
> **Fabolous_Boy said:**
> In [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/), it says 

i dont get it...can someone elaborate? (sorry if im quite stupid sometimes :confused:) what does "internal hard drives" mean there?

As this is a small laptop and opening it up might be a little challenging, the easiest way to do this is to enter BIOS setup (it will tell you what key you need to press on the very first screen that it displays after you switch it on) and disable the disk drives from there.

Internal hard drives are magnetic disks that are inside a computer and can permanently store data, even when unplugged from electric power.
See also
[http://en.wikipedia.org/wiki/Hard_drive](http://en.wikipedia.org/wiki/Hard_drive)

---

### Post by tarps87 on 2008-10-13
The guide is talking about the hard drives inside the pc you are trying to make the live cd on. It wants you to disconnect them to reduce the risk of installing over the hard drive instead of the USB stick. I would suggest using the live-cd on your other pc and using the live USB creator. There is a tutorial: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by MinstrelBoy on 2008-10-13
Is this link any use ?

[http://www.liliputing.com/2008/07/how-to-install-ubuntu-on-msi-wind.html](http://www.liliputing.com/2008/07/how-to-install-ubuntu-on-msi-wind.html)

How to install Ubuntu on an MSI Wind laptop

Cheers
MinstrelBoy

---

