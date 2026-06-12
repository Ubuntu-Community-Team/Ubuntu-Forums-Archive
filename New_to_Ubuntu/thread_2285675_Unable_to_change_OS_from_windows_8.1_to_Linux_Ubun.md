---
title: "Unable to change OS from windows 8.1 to Linux Ubuntu"
date: 2015-07-07
forum: New to Ubuntu
---

### Post by Elliston_James on 2015-07-07
(To start I'm pretty new to Linux) I have a computer that seems to require a .efi file to boot an OS from a Live USB, I have the Bootable USB completely setup, and i have tried setting up a .efi file myself, with no luck. Any suggestions on how to get Ubuntu onto my current computer?

---

### Post by Mike_Walsh on 2015-07-07
> **Elliston_James said:**
> (To start I'm pretty new to Linux) I have a computer that seems to require a .efi file to boot an OS from a Live USB, I have the Bootable USB completely setup, and i have tried setting up a .efi file myself, with no luck. Any suggestions on how to get Ubuntu onto my current computer?

Hallo.....and welcome to the forums.

Have a look here:-

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

.....and let us know if that helps. Try also:-

[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
[http://linux.about.com/od/howtos/ss/How-To-Create-A-UEFI-Bootable-Ubuntu-USB-Drive-Using-Windows.htm](http://linux.about.com/od/howtos/ss/How-To-Create-A-UEFI-Bootable-Ubuntu-USB-Drive-Using-Windows.htm)


Regards,

Mike. ;)

---

### Post by oldfred on 2015-07-07
If you do not have the efi file, then did you by mistake download a 32 bit version. It does not have UEFI capability.
       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it 
[http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Dennis N on 2015-07-07
> **Elliston_James said:**
> (To start I'm pretty new to Linux) I have a computer that seems to require a .efi file to boot an OS from a Live USB, I have the Bootable USB completely setup, and i have tried setting up a .efi file myself, with no luck. Any suggestions on how to get Ubuntu onto my current computer?

Look at the filesystem on the USB flash drive. There should be a top level EFI folder in there, which contains .efi files in a BOOT subfolder.  A 32 bit OS installer does not have an EFI folder, or those files. Get the 64 bit installer instead.

---

### Post by Elliston_James on 2015-07-07
I tried the first 2 options, i had no luck with them, and the third option, i dont have anyway to mount the ISO fie, is there a software i might be able to use to mount the ISO image (My computer dosent have A cd drive, or the driver for one)

---

### Post by Elliston_James on 2015-07-07
> **Dennis N said:**
> Look at the filesystem on the USB flash drive. There should be a top level EFI folder in there, which contains .efi files in a BOOT subfolder.  A 32 bit OS installer does not have an EFI folder, or those files. Get the 64 bit installer instead.

I'll  try downloading the 64 bit version, I'm not too sure if i downloaded the 32 or 64

---

### Post by Geoffrey_Arndt on 2015-07-07
And no need for CD/DVD drive, just use Unetbootin to create a bootable USB Flash-Stick.   Much faster anyway than optical media (dvd/cd).   You may need to tweak your BIOS/UEFI boot device preference to enable boot from USB.   [https://launchpad.net/unetbootin](https://launchpad.net/unetbootin)

Also, read from Community WIki at Ubuntu site re install on UEFI hardware . . . and how to adjust Windows settings first (turn off fast boot, hibernation, etc.) before commencing install.

---

### Post by Elliston_James on 2015-07-08
I had gotten the thing to boot, and went to install it, we'll,  halfway through the install, it said there was an error, and the computer instantly shut down, now I try and boot it with Ubuntu, and it loads normally,  the  the screen goes black, this is a much larger problem,it wiped my drive,  and I had no fallback because I expected it to work,  what do I do now.

---

### Post by sotiris2 on 2015-07-08
Can you boot from the CD/usb again? And choose 'Try Ubuntu' ? If so open up Gparted and take a screenshot (press PrintScrn in keyboard) and post it here. 

Do you remember the error message? Do you need to recover files from the disk? In that case do NOT try reinstalling yet.

---

### Post by RobGoss on 2015-07-08
Hello and welcome. What are the specs for your machine it will help others figure out what the problem might be.

---

### Post by Elliston_James on 2015-07-08
My computer has 2 gb of ram, and 32 gb of storage, it's a pretty lightweight laptop,  and no,  I am unable to even use try Ubuntu, because my graphics driver was formatted with it,  when I try to boot it W/O installing it gives me the options to run in low graphics, set it myself,  or continue to login, it then freezes and won't let me pick any of the options I do not need to recover any of the files, they had no significance

---

### Post by Vladlenin5000 on 2015-07-08
The most important spec - graphics card/chip - is missing. That's where the problem stems from and the troubleshooting or workaround depends on knowing exactly what graphics hardware you have.

---

### Post by Elliston_James on 2015-07-08
(Intel Celeron N2840 processor
2.16GHz (with a Max Turbo Boost Speed of 2.58GHz)
2GB DDR3L SDRAM system memory
The Windows 8.1 laptop gives you options for surfing, video conferencing, documents, basic photo editing and simple computer tasks
32GB eMMC Flash hard drive
Save to flash storage for quick and easy recall. Store 21,000 photos, 9,000 songs or 16 hours of HD video and more.
802.11b/g/n Wireless LAN
Wirelessly connect to a WiFi signal or hotspot with the 802.11b/g/n connection built into your 11.6" laptop
11.6" HD AntiGlare WLED-backlit display
Intel HD Graphics
(DVD/CD DRIVE NOT INCLUDED with the Windows 8.1 laptop)
Making the laptop thin and lightweight for portability)  I pulled this off of the Walmart website,  hope it helps

---

### Post by Geoffrey_Arndt on 2015-07-08
At this point, *one option* (of several) worth trying is creating a bootable usb-flash-stick using Ubuntu with the "Mate" desktop.   That will get around the low graphics mode situation.   You can get the iso image from here:  [https://ubuntu-mate.org/](https://ubuntu-mate.org/) 

Use a tool like "unetbootin" or "pendrive Linux" to create the bootable flash-stick from the downloaded iso.   Try running the "Live" version of Ubuntu Mate (don't try installing right away).   See if your system can handle the live Mate desktop with decent performance.   If it works well,  consider installing it when you're ready.

---

### Post by oldfred on 2015-07-08
I think this is one of those 32 bit UEFI with 64 bit processor that they wanted to sell as Windows only machines since Linux did not have 32 bit UEFI support.


The *Celeron N2840* is a *Intel* Bay Trail.

 Sound issues on Bay Trail
[http://ubuntuforums.org/showthread.php?t=2255425](http://ubuntuforums.org/showthread.php?t=2255425)

 Bay Trail -The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)
But someone has it partially working:
[http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html](http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html)
Asus T100 Compile own grub 32 bit
[http://ubuntuforums.org/showthread.php?t=2191557](http://ubuntuforums.org/showthread.php?t=2191557)
 ASUS Transformer Book T100TA that was one of the early Intel Bay Trail convertible laptops/tablets. 
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)

 Some new 64 bit low cost systems with 32 bit UEFI
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

---

### Post by Geoffrey_Arndt on 2015-07-09
Yikes Old Fred,  you're probably right-on.   I wonder if it's possible to convert a UEFI machine to standard BIOS (flashing the firmware??).   Or perhaps, just setting UEFI to legacy BIOS emulation . . would that work for the OP?

---

### Post by oldfred on 2015-07-09
Some of these systems are UEFI Class 3 devices.
UEFI class 3 means it does not have the CSM chip.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

I expect in a year or two, that all UEFI will be class 3 as vendors will want to eliminate the chip and all the now very old BIOS support. New hardware needs new drivers and writing both UEFI & BIOS versions just adds costs. As long as supporting only old hardware the CSM has worked for now.

---

### Post by Elliston_James on 2015-07-09
> **oldfred said:**
> I think this is one of those 32 bit UEFI with 64 bit processor that they wanted to sell as Windows only machines since Linux did not have 32 bit UEFI support.


The *Celeron N2840* is a *Intel* Bay Trail.

 Sound issues on Bay Trail
[http://ubuntuforums.org/showthread.php?t=2255425](http://ubuntuforums.org/showthread.php?t=2255425)

 Bay Trail -The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)
But someone has it partially working:
[http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html](http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html)
Asus T100 Compile own grub 32 bit
[http://ubuntuforums.org/showthread.php?t=2191557](http://ubuntuforums.org/showthread.php?t=2191557)
 ASUS Transformer Book T100TA that was one of the early Intel Bay Trail convertible laptops/tablets. 
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)

 Some new 64 bit low cost systems with 32 bit UEFI
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)
I was able to run the OS fine, with no errors, though when i was installing it there had been a error halfway through the download 
P.S. I still haven't been able to fix it, but i am trying to download the Ubuntu mate, which i hope will work

---

### Post by Elliston_James on 2015-07-10
I was unable to get Linux mate to install either

---

