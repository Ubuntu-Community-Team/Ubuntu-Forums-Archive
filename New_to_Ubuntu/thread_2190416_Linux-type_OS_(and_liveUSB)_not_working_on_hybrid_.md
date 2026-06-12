---
title: "Linux-type OS (and liveUSB) not working on hybrid Intel/Nvidia graphics"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by kbuzar on 2013-11-27
Hello all,

After using a OSX platform for some time I decided to buy a Clevo notebook (157SM, i7-4700MQ, Geforce 770M) for the use of Ubuntu and overall more freedom of interaction with the machine.

Windows seems to be working fine in every way, but there is no known way for me to run Ubuntu (or any other linux as far as i know) on this machine.

My first failed attempt was tu use my trustworthy Slax liveUSB, that worked well for me for the past years. I was surprised that it did not boot, almost at the last possible moment, when the resolution is changing to show the login screen, everything went black.
I tried the same with Ubuntu liveUSB that seemed to work on any other platform it was inserted into, but it had the same result. It did not load more that showing start up screen, and than some unreadable green letters (sorry for not being more specific).

My next step was to insert an additional HD, and install Ubuntu from windows. The system does not start up as well. I get the message:

[I]Try (hd0,0) NTFS5: No wubildr
Try (hd0,1) NTFS5: error: "prefix" is not set.

[/I]Another thing I got was this prompt:
[IMG][[IMG]http://img845.imageshack.us/img845/508/23ja.jpg[/IMG]]("http://imageshack.us/photo/my-images/845/23ja.jpg/")  Uploaded with [ImageShack.us]("http://imageshack.us")[/IMG]

As far as my research goes, the problem is connected to the two grphics cards, Intel HD 4600, the Geforce 770M and the Nvidia Optimus Technology that switches between them. 
I did find the supposed solution, Bumblebee/bbswtich, but it seems that I need to install it on a WORKING Linux. But I cannot do that as I mentioned it.

Is there anything more I can do? Am I missing something? 
I will appreciate any help! Thanks in advance!

With regards

---

### Post by kbuzar on 2013-11-27
I also found this thread:
[http://ubuntuforums.org/showthread.php?t=2168625&highlight=haswell](http://ubuntuforums.org/showthread.php?t=2168625&highlight=haswell)

But I don't feel it entirely refers to my problem.

---

### Post by grahammechanical on 2013-11-27
What version of Windows did that machine come with? If it is Windows 8 then the Ubuntu Windows installer (wubi.exe) is not compatible with windows 8. Is the boot system BIOS or UEFI? Is fast boot enabled?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you are using Ubuntu 12.04.3 (the latest download) or 13.04 or 13.10 then secure boot will not be a problem. There are all of manner issues with installing Linux on any machine with Windows 8. But your problem may simply be the need to run the live session with the nomodeset option enabled.

1) At the first purple screen press Enter
2) at the select language screen press Enter to select English as the default language.
3) At the Try - Install screen press F6.
4) At the small menu that appears at the bottom right select nomodeset aand press Enter.
5) When abck at the Try - Install screen press Enter to run the live session.

See if that does better.

Regards.

---

### Post by kbuzar on 2013-11-27
I am afraid that I cannot perform any of this. The freeze with the live USB occurs before I can do anything, and immediately the green letters occur. And except the prompts of errors, I don't get anything from the Ubuntu installed on the HD.

I will attempt the procedure with liveUSB, but it might come to nothing.

Thanks for the help!

---

### Post by kbuzar on 2013-11-27
I have a installed Windows 7, and I am using BIOS on the matter before.

---

### Post by kbuzar on 2013-12-04
[[IMG]http://img822.imageshack.us/img822/9590/s96c.jpg[/IMG]](http://imageshack.us/photo/my-images/822/s96c.jpg/)


Uploaded with [ImageShack.us](http://imageshack.us)

I got this result in nomodset.

Are there any other possible solutions? :<

---

### Post by slooksterpsv on 2013-12-04
How are you making the live USB drive? What program? It could be an issue with that or the flash drive you're using.

---

### Post by oldfred on 2013-12-04
Do not know about your specific system but the new Haswell systems need the very newest 13.10 to boot in UEFI mode. 

       Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)


 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

      
 Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

---

### Post by kbuzar on 2013-12-05
Ok.

I did put a 13.10 on a USB with Universal USB Installer. I enabled the UEFI boot. I got the prompt menu, and i picked "Try Ubuntu".
I loaded perfectly. I saw the desctop. Than it froze. I waited for over 10min. Than the hard reset. It did not star again. I am stuck at the loading screen. No other options seem to work. The "check the disc for corruption" option gave nothing.

I will try to set the USB again, but nothing seemed to work on the UEFI mode enabled. I also do not see any other hard drives. As well as the one that has installed Ubuntu 13.10 on it. I can only boot from USB devices.

Thanks for any help!

---

### Post by oldfred on 2013-12-05
Not sure where you are at.

Best not to use hard reset unless Alt+SysRq R-E-I-S-U-B does not work. And then you may need to also remove batter, hold power switch on for a bit to drain capacitors, and then do a cold reboot.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by kbuzar on 2013-12-05
I attempted to Try Ubuntu from Live USB I made with Universal USB Installer.

I enabled UEFI boot as suggested, and booted from the prepared USB. Only USB devices (Pendrive and mass sotrage) appeared in the UEFI mode at this point.

Proper menu appeared (for the first time there was no error message of some sort). I choosed "Try Ubuntu" to check the OS.

Everything seemed fine, but the loaded system froze after few seconds, as I was attempting to move the mouse.

I waited about 10 minutes, just to be sure. Than decided to hard reset.

After this, any attempt to boot or install Ubuntu from the USB stopped at the loading screen.


I am making a new USB right now, to check again.
I will attempt the cold reboot as well.

My question is:

Why I do not see any hard Drives in UEFI mode? I have a HD with Ubuntu installed from windows desktop, but it does not seem to work with as well BIOS (I have the option to choose between Win7 and Ubuntu, but Linux does not work at all), and there is no way that I know to access it when UEFI is enabled.

I hope this clears the matter a bit.

---

### Post by oldfred on 2013-12-05
There are 3 boot modes with systems that have Windows 8 pre-installed. UEFI with secure boot, UEFI and BIOS/CSM/Legacy.
Some UEFI are clear on which mode you have set. Others seem to just have a secure boot on/off and the it auto boots to UEFI if an efi partition found or BIOS if MBR found.
If secure boot is on, then only secure boot systems will be shown as boot options.
If CSM only is a UEFI setting then only BIOS systems will boot.

The Ubuntu installer is both UEFI & CSM/BIOS bootable. And how you boot it, UEFI secure boot, UEFI without secure boot or BIOS mode is how it installs.

---

### Post by kbuzar on 2013-12-05
I have Win7 installed, but I got my notebook without any OS preinstalled.

Only options I see are to enable UEFI in "UEFI Settings" section of Boot tab of the BIOS. There is "UEFI Boot" enabled/disabled, and whet it is changed to enabled 3 options appear:

Network Stack
Ipv4 PXE SUpport
Ipv6 PXE SUpport

All with the option enabled/disabled to choose. And that is all of what I see.

The lack of options is connected to having win7 installed?

---

### Post by oldfred on 2013-12-05
If you installed Windows 7 from DVD, it auto converted to BIOS/CSM boot not UEFI. You have to take Windows 7 DVD  and copy to flash drive and make a few minor changes to make it UEFI bootable.

         Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

If you installed Windows 7 in BIOS mode it converted hard drive from gpt partitioning to MBR (msdos) partitioning as Windows only boots from gpt with UEFI.
But Windows does not correctly convert to MBR, it leaves the backup gpt partition table. Then Linux sees MBR but a backup gpt table and gets confused on which you really have.
      
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by efflandt on 2013-12-05
When I recently got a gaming laptop I specifically got it with Win7 instead of Win8, and according to BIOS it uses Legacy mode, not UEFI. It is a MSI laptop with i7-4700MQ and Intel HD 4600/Nvidia GTX 765M graphics. I put 64-bit Ubuntu 13.10 on USB stick using **Startup Disk Creator** from my 12.04 desktop, and used **nomodeset** boot parameter when booting the USB to install. My hard drive already had a D: partition, but I set Win7 to not use a drive letter for that partition and installed Ubuntu to it (/dev/sda4). After install I also added **nomodeset** to the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub figuring that was probably needed to use different modules for the dual graphics, instead of kernel mode setting.

So there is no inherent problem with that cpu or graphics (at least for 64-bit Ubuntu 13.10) during installation. It may be a problem with your USB memory stick or the way the live/install iso was written to it, with that last error showing that it cannot read /casper/initrd.lz.

My only initial issue is that I put grub2 on primary (Linux) partition /dev/sda4 because I wanted to leave the MBR on my drive untouched. But every time I set the boot flag on sda4, removed boot flag from sda2, and reboot, something keeps resetting the boot flag on sda2 and it boots into Windows. So I put grub2 on an old 256 MB USB stick and need to have that inserted to boot Ubuntu.

I did have to do some other things so 32-bit steam could find 32-bit libs, and parameters to run steam games with optirun (to use nvidia graphics), but that is another story.

---

### Post by codenine75a on 2013-12-06
Boot up to memset and check for faulty RAM chips.

---

### Post by kbuzar on 2013-12-26
Finally.

I got my hands on a Windows 8.1 copy. I cleared everything. Installed the win8.1 with UEFI enabled. Seemed to work fine except for some drivers not compatible since I got win 8 versions on the DVD.

I created UEFI enabled Ubuntu 13.10 copy with Rufus, a great USB utility I must say. Installation process was swift, and clean.

In the end there are some driver issues, but IT IS working. And I will make it work perfectly :p

Thank you all a lot. It took too much time all together, but I learned great deal of stuff along the way.
Cheers!

---

