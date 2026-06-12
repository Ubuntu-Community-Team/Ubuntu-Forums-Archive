---
title: "how do i install these wireless drivers?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by GMRghost on 2008-05-20
I'm a complete noob at ubuntu, this is my first time using it, my friend can't help because he doesn't have ubuntu installed currently. How do i install these drivers. ([http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi)) Can anyone help me?
:):):)

---

### Post by rogerdpenguin on 2008-05-20
Hey man, sorry I couldn't help you. My sister said that my ubuntu partition was slowing down the computer so she deleted it, somehow she figured out how to. Once I get around to reinstalling ubuntu I'll help you out with other stuff.

---

### Post by iaculallad on 2008-05-20
Download the compressed file driver then extract it from the directory you had it saved. (i.e: /home/Desktop)

Right click on the downloaded file and select "Extract from Here". After the extraction process, open your terminal and navigate the directory of where you extracted your driver file (i.e: ~/Desktop/iwlwifi-1.2.25), then issue the command ./install

ian@gutsy-gibbon:~/Desktop/iwlwifi-1.2.25$ ./install

you have to change iwlwifi-1.2.25 with the correct folder name.

---

### Post by GMRghost on 2008-05-20
I'm actually in Hardy Heron 8.04. Is it the same process or what?

Thanks for the response.

---

### Post by shae on 2008-05-20
Hardy should already have those drivers built in the kernel.  Are you having problems or are looking to update them?

---

### Post by iaculallad on 2008-05-20
> **GMRghost said:**
> I'm actually in Hardy Heron 8.04. Is it the same process or what?

Thanks for the response.

Same process of installing files on Hard and Gutsy.

---

### Post by GMRghost on 2008-05-20
> **shae said:**
> Hardy should already have those drivers built in the kernel.  Are you having problems or are looking to update them?

Basically, it detects the wireless signal and I try to connect. I put in the correct passcode and it loads like its connecting. After a while, it eventually just pops up with the screen prompting the password again.

---

### Post by sam_delta on 2008-05-20
which network card do you have? post the output of 
```
lspci
```

sam

---

### Post by GMRghost on 2008-05-20
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

justin@justin-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7950 GTX (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
justin@justin-laptop:~$

---

### Post by jimrz on 2008-05-20
look at [[COLOR="Sienna"]**_this_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=800357&highlight=3945") thread and give the backports fix in #2 a try, seems to have worked for several others in that thread

---

### Post by sam_delta on 2008-05-21
try the solution mentioned in the post jimrz mentioned, also

make sure you have your system up to date, plug a ethernet internet cable and do all updates, the fix to your wireless might already be released in the updates

sam

---

