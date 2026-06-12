---
title: "Lubuntu and Xubuntu not booting from USB"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by SpazCool on 2013-09-01
To start, this is not my first time making a bootable USB OS, I've got Ubuntu 13.4 and Android on a couple of flashdrives lying about; but I would still very much consider myself a novice at all of this. 

Anyways, I go through the steps I've gone through before to try/install both Lubuntu and Xubuntu and it all goes well until I actually try to use it. I select boot from USB in BIOS and after that, the screen goes black with the cursor blinking in the corner, on the netbook I'm doing all of this for. If I attempt to use the USB on my primary machine I get some line that reads "System" or "Syslink" along with a name and date. Either way, neither machine moves beyond their respective screens. 

Again, I've booted different OSs from USB in the past on both of these very same machines. 

So far:

I've tried using both UNetBootin and 2 different versions of PenDriveLinux to mount the .iso files. 

I've also tried different releases of both Lubuntu and Xubuntu as well as different bit versions (i.e. both the 32bit and 64bit versions).


My intention is to just "try" these OS from the USB, as I have done with the straight Ubuntu flavor both before and after my attempts with these flavors. But, at this point, if I could just get the option to install the OSs outright, I'd be happy.

So, any ideas on what I'm doing wrong here? I'm completely willing to assume it's user error here, so bring on the insults ;).

---

### Post by cipherboy_loc on 2013-09-01
Two possible workarounds come to mind: installing outright, or using Grub2 to boot the ISOs. If you install outright, make sure you move the bootloader to the flash drive, other than that, it is just a matter of space (though in theory, if you slim it down far enough you could transfer it to a smaller flash drive which it wouldn't install on by default). The second option takes a little bit more work to set up (and sadly I do not have that flashdrive with me at the moment), but the general idea is to install Grub2 to an ext(2/3/4) formatted flashdrive, put an iso in the root of it, and then load it from grub (modifying the bootloader config of course). Note: this will not work on a vfat nor ntfs filesystem type. 

If you need more clarification, feel free to ask.


Thanks, 
Cipherboy

---

### Post by Petro Dawg on 2013-09-01
> **SpazCool said:**
> I'm completely willing to assume it's user error here, so bring on the insults ;).

Sure thing :D

Just to rule out a lot of other things...  If you plug in one of the bootable USBs that you successfully made in the past (Ubuntu 13.04 for example), will they boot now?   Please check and verify that they still boot as expected.

Did you download the ISOs from torrents or from a mirror or did you let UNetbootin download it for you?  I typically use a mirror from [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

Also, did you verify the md5 hash of the ISOs to ensure your downloads were good ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM))

---

### Post by SpazCool on 2013-09-03
Petro,

Yes, my other USBs still work (both Ubuntu 13.04 and Android).

At this point I have downloaded a dozen different files from nearly as many sources, I've tried direct/mirror downloads, torrents and I have allowed UNetbootin to download a file for me. 

I have just gotten around checking md5 about 10 minutes ago, actually; and, assuming I know what I'm doing, none of the downloads for Lubuntu are matching up.

I have now downloaded the "alternate" file onto a wholely different USB drive, and it is now working. Whether it was the alternate file or the USB drive I don't know. I'm still curious, however.

Thanks for your suggestions and your time.

---

### Post by SpazCool on 2013-09-03
One possibility. The USB drives I have been using both have had some proprietary bloatware on them; San-disk's U3 system tray. Maybe that was interfering...

---

### Post by mörgæs on 2013-09-03
If you follow the link in my signature (upgrading) there's advice on removing the stuff from a Sandisk flashdrive.

---

### Post by SpazCool on 2013-09-03
Thanks, just finished reformatting the disks after deleting that blasted software. And, now I can boot from Lubuntu from the USB I wanted to use.

---

### Post by mörgæs on 2013-09-03
Good, then please mark the thread 'solved'.

---

