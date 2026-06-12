---
title: "Boot problem"
date: 2018-01-30
forum: New to Ubuntu
---

### Post by MrGrummpy on 2018-01-30
The laptop I am working on is a Dell Inspiron 14 with 32GB eMMC and 2GB ram.  It has no spinning hard drive. 

I attempted to use Boot-Repair after a failed conversion of Windows 10 to Ubuntu Mate. 
At the end of Boot-Repair the screen said something like 
"[B]You can now reboot your computer.
Please [COLOR=#AA22FF]**do **[/COLOR]not forget to make your BIOS boot on mmcblk0 [COLOR=#666666]([/COLOR]MMC HBG4e[COLOR=#666666])[/COLOR] disk![/B]"

When I entered the BIOS to set the boot order the device that acts like a 'hard drive' (mmcblk0) was NOT listed as an option.

The options offered are

[B]Hard Drive
Diskette Drive
USB Storage Device
CD/DVD/CD-RW Drive
Network 
[/B]
I have tried all of those options. 
This results in a black screen with the message

"[B]No bootable devices  --
strike F1 to retry boot, F2 for setup utility. Press F5 to run onboard diagnostics[/B]. "

The generated paste from boot-repair is 

[https://paste.ubuntu.com/26486550/](https://paste.ubuntu.com/26486550/)

I am stumped.  Any assistance would be greatly appreciated.

---

### Post by oldfred on 2018-01-30
Do you have latest UEFI from Dell for your model system?

That error is often from booting in UEFI mode with BIOS install or vice-versa.
Or having UEFI secure boot on, but install is BIOS or UEFI without Secure boot.

Somehow system is not seeing the MBR to boot from.

---

### Post by MrGrummpy on 2018-01-31
> **oldfred said:**
> Do you have latest UEFI from Dell for your model system?


That error is often from booting in UEFI mode with BIOS install or vice-versa.
Or having UEFI secure boot on, but install is BIOS or UEFI without Secure boot.

Somehow system is not seeing the MBR to boot from.

Thank you for your reply. 

Just before attempting to replace the Windows 10 OS with Ubuntu Mate I checked the Dell update messages.  The messages claimed that the system was up to date ( at least from the manufacturer's point of view.)

I now can boot the laptop as long as the pen drive I used to install the OS is plugged into the laptop.  However, that is not how I want to operate going forward.  The system will allow me to do most of what I want, but on re-boot, all my changes are lost.  It is like the first time I logged on.  

I have found a utility called Disks ( didn't even know it was there until I looked) and I am posting a link to a screen shot of its opening screen.  I note that there are more 'partitions' than I expected.  

[https://drive.google.com/file/d/1wTrGbmSxLAInlNjbE2dKHSwG4d-7sHoy/view?usp=sharing](https://drive.google.com/file/d/1wTrGbmSxLAInlNjbE2dKHSwG4d-7sHoy/view?usp=sharing)

Perhaps this can shed some light on my difficulty.

---

### Post by oldfred on 2018-01-31
That post of partitions on mmc device is totally different than Boot-Repair summary report.
Your partitions now show a BIOS boot install using LVM or advanced volume management.
LVM is not recommended for newer users, but is required if using full drive encryption. 

Is this one of the small or lightweight type systems?
Since install is BIOS, you have to turn off UEFI Secure boot and make sure BIOS/Legacy/CSM boot is on in UEFI settings.
And since you do not have a hard drive, the MMC device may be considered as a hard drive.
[https://en.wikipedia.org/wiki/MultiMediaCard](https://en.wikipedia.org/wiki/MultiMediaCard)

---

### Post by MrGrummpy on 2018-01-31
Thank you again for your help.  
The laptop is indeed a 'small, lightweight' system. ( Budget priced and not enough resources.  It could not update Windows 10, hence the conversion to Ubuntu).  
Do you suggest I again format and attempt to install Ubuntu Mate?  If so, what format and procedure would be safest?
Or is there another alternative?
I will be out of town for about a week, so if I don't reply quickly, that is why.

---

### Post by oldfred on 2018-01-31
Any of the lightweight flavors should be ok. How much RAM?
 Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors) 

You can use UEFI or BIOS with new systems.
How you boot install media UEFI or BIOS is then how it installs.
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

### Post by MrGrummpy on 2018-03-12
I want to thank oldfred for his help.  I tried a number of times to get the Ubuntu Mate installed the way I wanted it to work.  I never got it work. It seems like everything I tried led to another problem.  I finally decided to try to reinstall Windows 10.  That worked.  I had to do a clean install using media I downloaded from Microsoft.  I admit I was surprised.  As a side note, the 'product ID' was not a problem.  It seems that for a few years most manufactures encode the Windows product ID in the 'BIOS'.  Who knew?  
A further note:  when I tried to do the clean install the installer balked when I used 'Legacy' BIOS.  When I took a chance on UEFI, things progressed well.  
So while I would have loved to convert that laptop to Ubuntu,  I have returned it to 'the dark side.'  
And one more note:  this all started when I tried to update the original Windows 10 on that machine.  It kept telling me that it needed more drive space.  Curiously,  I did a clean install and now it tells me that the operating system is the latest version.  Wow, tough way to update the system !
Again,  thank you for your help.

---

