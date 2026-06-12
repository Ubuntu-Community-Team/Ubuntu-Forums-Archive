---
title: "Problems installing into blank drive"
date: 2013-12-16
forum: New to Ubuntu
---

### Post by svsaunders on 2013-12-16
Hi,

I have a hard drive with did have windows 8 on it until I deleted along with the partition tables.

The problem now is if I boot from the cd running either 12.04 or 13.10 I cannot get anything to work, constant syncing errors when trying to install to the PC and the same when trying to boot without installing. 

Can anyone give me some tips pls ? Is there a command prompt screen I can access to create a partition before installing or is this not what's causing the problem ?

Thanks

---

### Post by MartyBuntu on 2013-12-16
If this is the only drive in the computer, you'll have better luck switching Secure Boot / UEFI off in the BIOS settings.

---

### Post by amjjawad on 2013-12-16
> **svsaunders said:**
> Hi,


Hello and welcome :)

>  I have a hard drive with did have windows 8 on it until I deleted along with the partition tables.
Have you done that using GParted?

> The problem now is if I boot from the cd running either 12.04 or 13.10 I cannot get anything to work, constant syncing errors when trying to install to the PC and the same when trying to boot without installing. 
 
Can you post the output of: ```
sudo lshw
```

Or just tell us in summary what are the hardware details of your machine?

> Can anyone give me some tips pls ? Is there a command prompt screen I can access to create a partition before installing or is this not what's causing the problem ?

Thanks

Yes :)

1- Have you checked MD5SUM for the ISO you have downloaded it?[ See this]("https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME#Downloading_Ubuntu_GNOME_13.10") - despite it is for Ubuntu GNOME, this check-list applies to all Ubuntu Flavours!

2- Please, make sure to check your media (LiveCD/LiveUSB) for error 

[IMG]https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME?action=AttachFile&do=get&target=2.png[/IMG]

Check Disc for Defects - this will save your time

3- Does your machine support booting from USB? have you tried to use a LiveUSB?

---

### Post by amjjawad on 2013-12-16
> **MartyBuntu said:**
> If this is the only drive in the computer, you'll have better luck switching Secure Boot / UEFI off in the BIOS settings.

@OP

If your machine is new and it has UEFI, please have a read at: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You may want to try amd64 of 13.10 (I think 12.04 amd64 will work too) because if your machine has UEFI, i386 ISOs will not work!

---

### Post by phoyce2 on 2013-12-17
> **amjjawad said:**
> @OP

If your machine is new and it has UEFI, please have a read at: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You may want to try amd64 of 13.10 (I think 12.04 amd64 will work too) because if your machine has UEFI, i386 ISOs will not work!

Good advice here.  I'd try this before anything else.

---

### Post by fantab on 2013-12-17
> **svsaunders said:**
> ... if I boot from the cd running either 12.04 or 13.10 I cannot get anything to work, constant syncing errors when trying to install to the PC and the same when trying to boot without installing. 


Sounds to me like a bad burn.
How did you 'burn' the ubuntu .iso to the DVD? Try again.

If UEFI is enabled, then you have make a 300-500Mb EFI partition, formatted with FAT32 and with a 'boot' flag.

---

### Post by jimmyh1972 on 2013-12-17
Since you had Windows 8 installed the problem is not Ubuntu the problem is in the BIOS
Microsoft implemented 2 (fu@#$%^) features in Win8 - UEFI & secure boot
those features must be enabled in the BIOS otherwise Windows8 won't boot
You must enter to Boot_Options and disable UEFI & secure boot
After doing that you will be able to boot your Ubuntu & install it
to read more about UEFI [http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
and secure boot [http://technet.microsoft.com/en-us/library/hh824987.aspx](http://technet.microsoft.com/en-us/library/hh824987.aspx)

---

### Post by fantab on 2013-12-17
> **jimmyh1972 said:**
> 
Microsoft implemented 2 (fu@#$%^) features in Win8 - UEFI & secure boot


UEFI is not really a MS's implementation. Its developed by a consortium Hardware manufacturers, like Intel, AMD, MS etc, as a long overdue repalacement for a thirty years old BIOS. BIOS has limitations when communicating with newer hardware, for one.
[http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement](http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement)

You are right, however, about 'Secure Boot', which is more of a Marketting gimmick than a real 'security' feature, IMO.

---

### Post by oldfred on 2013-12-18
Are you booting installer in BIOS mode or UEFI mode? Purple screen is BIOS, grub menu is UEFI.

What video card/chip do you have?
Have you partitioned in advance or using auto install. Did you use gparted? or Windows tools?

---

