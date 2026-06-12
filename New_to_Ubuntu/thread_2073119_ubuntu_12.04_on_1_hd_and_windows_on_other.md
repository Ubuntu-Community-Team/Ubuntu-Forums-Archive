---
title: "ubuntu 12.04 on 1 hd and windows on other?"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by mikesuperrc on 2012-10-19
Hi.
 I'm very new to Linux in general and multi/dual booting(still learning correct terminology for things).

 I have just built a computer mainly for my wife to run Photoshop cs5 and viewnx 2 on.

Computer specs:
 CPU: amd Fx-6100 6core 3.3gz 
Gpu: nivida geforce 8500gt 
Mobo: Asus m5a97 r2.0 Ram: 
Corsair xms3 1600Mhz 4g x2
Psu: 400w (not sure what brand)
hard drives: 160g seagate barracuda
                                500g seagate barracuda

I would like to run xp (soon to be win7 64 bit) on the 500g drive and Ubuntu 12.04 on the other. 
Only have it so windows can ONLY use and/or see the 500 drive and Ubuntu can ONLY use and/or see the 160. 

Is this possible and what is the best way to install them this way with out either of them messing with the other.

Also if possible can i get it to boot win automaticly and either boot from uefi or press a certain key (like booting from a CD) to boot Ubuntu.

thanks in advance for any help

Mike

---

### Post by 2F4U on 2012-10-19
> Only have it so windows can ONLY use and/or see the 500 drive and Ubuntu can ONLY use and/or see the 160.

This part will most likely be a problem. If both drives are connected, both operating systems will see them. To prevent this, you would have to physically disconnect one of the drives.

> Also if possible can i get it to boot win automaticly and either boot  from uefi or press a certain key (like booting from a CD) to boot  Ubuntu.

If you plan to use Ubuntu's boot loader Grub, you will be able to tell it the order in which the operating system appear and which OS to boot by default.

---

### Post by NikTh on 2012-10-19
Hi , 
and Welcome to the Forums and to the Ubuntu(Linux) World.


> **mikesuperrc said:**
> 
Only have it so windows can ONLY use and/or see the 500 drive and Ubuntu can ONLY use and/or see the 160.  
Windows naturally can see but cannot use the Ubuntu partition - Filesystem. But Ubuntu can see everything. It is not dangerous cuz the partitions not mounted automatically , so You have to mount the partition to interfere with. 

> **mikesuperrc said:**
> Is this possible and what is the best way to install them this way with out either of them messing with the other. 
I will tell you now a way (probably you already think it)....unplug the drive. If you want to have an Ubuntu install and nothing to be wrong or messed up , unplug the 500GB drive with Windows and make the installation.

> **mikesuperrc said:**
> Also if possible can i get it to boot win automaticly and either boot from uefi or press a certain key (like booting from a CD) to boot Ubuntu.

I don't have a UEFI , but even you cannot boot from UEFI options , the grub-bootloader will be installed in the 160GB HDD. Linux(Ubuntu) grub-bootloader has the ability to see all the Operating Systems (including Windows). So if you change the boot order from within BIOS , to boot first from the 160GB HDD and then in Ubuntu open a terminal and give this command ```
sudo update-grub
``` I think you will have no problem. 

You can open a terminal with Ctrl+Alt+T keys. 

Thanks and Good Luck.

---

### Post by mikesuperrc on 2012-10-19
Ok so i just unplug the sata and power to the 500g. 
Power up and install Ubuntu, should i create any partitions or any thing or just a normal install.

Do i need to install grub or is it with Ubuntu

Thanks again
Mike

---

### Post by 2F4U on 2012-10-19
You would install Grub on the 500g drive - the other is disconnected - and you can either create your own partition layout or go with what Ubuntu suggests, which is usually fine. Everything you need to install the system is included.

---

### Post by mikesuperrc on 2012-10-19
sorry but im a little confused now. :confused:
just to confirm
1. Ubuntu installer will take care of installing grub for me?
2. if not do i put it on the 500g windows drive as 2F4U says 
or do i put it on the 160g Ubuntu drive as NikTh says.

I just don't want to get this wrong:)

Thanks again, Really appreciated:P

---

### Post by jaycee23 on 2012-10-19
> **mikesuperrc said:**
> sorry but im a little confused now. :confused:
just to confirm
1. Ubuntu installer will take care of installing grub for me?
2. if not do i put it on the 500g windows drive as 2F4U says 
or do i put it on the 160g Ubuntu drive as NikTh says.

I just don't want to get this wrong:)

Thanks again, Really appreciated:P

Go with what NikTH says.

Unplug 500Gb Windows drive.
Install Ubuntu on other drive. It will install Grub automatically.

Reconnect Windows drive.
As has been said Windows will not see Ubuntu but Ubuntu will see the Windows driver via Grub and will give you the option to boot into either OS. 

You will have to pick which drive the computer boots to via your BIOS options.

Honestly it's not very complicated.

---

### Post by stinkeye on 2012-10-19
> **jaycee23 said:**
> Go with what NikTH says.

Unplug 500Gb Windows drive.
Install Ubuntu on other drive. It will install Grub automatically.

Reconnect Windows drive.
As has been said Windows will not see Ubuntu but Ubuntu will see the Windows driver via Grub and will give you the option to boot into either OS. 

You will have to pick which drive the computer boots to via your BIOS options.

Honestly it's not very complicated.
Also once you have reconnected your windows drive and selected the Ubuntu drive as the boot device and logged into Ubuntu run....
```
sudo update-grub
``` 
so your windows install can be added to the boot menu.

---

### Post by mikesuperrc on 2012-10-19
Thanks heaps guys:P

I'm pretty sure i got it all good now. I'll let you now how i go, may not be for another week or so yet, got to clean up n grab some stuff off of the 160g first.

I'm really keen to start using Ubuntu, I've played with it for a little bit any really enjoyed the experience.

Thanks again, 

                    mike

---

### Post by StinkySQL on 2012-10-19
I have a laptop with three physical drives. I just plug in the one I want (Vista, Win7, Ubuntu) when I need it. 

Downside is that I have to completely shut down to do so. 

Upside is that I rarely take the Ubuntu out. LOL

---

