---
title: "Dual boot problem with windows 8 and ubuntu 14"
date: 2014-06-28
forum: New to Ubuntu
---

### Post by Mohit_Manrai on 2014-06-28
Hi,

I installed ubuntu 8 on my dell laptop(preinstalled windows 8) following the instructions on this [webpage]("http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html")
After installing ubunutu, i ran into bootup issues. Basically, on startup it goes straight into windows. I ran boot repair and it has generated following error report: [http://paste.ubuntu.com/7715364/](http://paste.ubuntu.com/7715364/)

Thanks

---

### Post by kc1di on 2014-06-28
this isn't the best solution but it worked for me on one of my machines here.
you may want to try REFind boot manager. [found here.]("http://www.rodsbooks.com/refind/index.html")

---

### Post by grahammechanical on 2014-06-28
The web page is good, I assume, for the Windows part but it is not so good for the Ubuntu part. To start with the page makes no mention of the fact that we can install Ubuntu with secure boot enabled. Nor does it mention this important information.

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

So, we need to confirm that Ubuntu was installed in the same mode as Windows 8 was installed.

Regards.

---

### Post by oldfred on 2014-06-28
Have you gone into UEFI to see if Ubuntu entry works from there. Or from one time boot key?

```
You show ubuntu entry in UEFI.
       BootOrder: 0002,0004,2001
Boot0000* UEFI Onboard LAN IPv4
Boot0001* UEFI Onboard LAN IPv6
Boot0003* EFI USB1 PATH1 (USB DISK 2.0)
Boot0004* Windows Boot Manager
Boot2001* EFI USB Device
Boot0002*[COLOR=#ff0000] ubuntu[/COLOR],BootCurrent: 0003


```    

It also looks like Boot-Repair updated kernel as -30 is now the signed version where -29 was the unsigned version.

Have you tried with both secure boot on and with secure boot off, but both in UEFI not CSM mode?

Not just Precision models but any Intel system.
       Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

---

