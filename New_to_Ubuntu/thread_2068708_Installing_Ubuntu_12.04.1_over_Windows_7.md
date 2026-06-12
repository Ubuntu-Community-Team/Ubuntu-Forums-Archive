---
title: "Installing Ubuntu 12.04.1 over Windows 7"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by Barbus2012 on 2012-10-09
Hi, guys. I got a new Sony Vaio S-series laptop with Windows 7 (64 bit) and want to completely erase Windows and install Ubuntu 12.04.1. 
 I have created the CD disk with Ubunutu iso image. But it does not want to boot from it. I checked BIOS and all the settings seem to be Ok (with the internal CD drive as the primary for booting). What can you advice, guys? I can create another CD, though the one I have was created (with InfraRecorder) without any problems.
 And I have another question (once I figure out this booting issue) - I see in BIOS that the boot is either UEFI or Legacy. Will this give me any problems when I will start installing Ubunutu over Windows 7?

 Thanks in advance.

---

### Post by NikTh on 2012-10-09
> **Barbus2012 said:**
> 
 I have created the CD disk with Ubunutu iso image. But it does not want to boot from it. I checked BIOS and all the settings seem to be Ok (with the internal CD drive as the primary for booting). What can you advice, guys? 
Hi, 
CDs/DVDs are quite sensitive , especially when data burned on. 
If you want to make another CD, be sure that you burned in the lower speed. 

I would suggest to create a bootable Usb . IMO are more accurate.
Use this program from within Windows : [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If you scroll down you will also see installation examples. It is easy.
 > **Barbus2012 said:**
> And I have another question (once I figure out this booting issue) - I see in BIOS that the boot is either UEFI or Legacy. Will this give me any problems when I will start installing Ubunutu over Windows 7?

You have done good you mentioned this.(with UEFI). Although I don't think you will have any problem (cuz you will delete completely Windows) if you have , try to use this automate tool : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) (from a Live session) to repair the Grub. 
In your position I would turn the BIOS to legacy. 

Thanks and good luck.
Welcome to the Forums

---

### Post by Barbus2012 on 2012-10-09
Wow, that was fast! NikTh, thanks for the response. Will have the tool you mention in hand just in case.

---

