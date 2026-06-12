---
title: "Where to install bootloader?"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by altirisx on 2013-06-20
Quick question, where would you guys find the IDEAL place to install the bootloader? I have an SSD and HDD, SSD has Windows with the Win7 bootloader on it and then I will be installed ubuntu linux on the HDD. Should I put the boot loader on the SSD or HDD?

---

### Post by altirisx on 2013-06-20
I got it already. For everyone, you need to install the GRUB bootloader over the Windows 7 one otherwise you will have two boot loaders conflicting with each other.

---

### Post by fantab on 2013-06-20
> **altirisx said:**
> Quick question, where would you guys find the IDEAL place to install the bootloader? I have an SSD and HDD, SSD has Windows with the Win7 bootloader on it and then I will be installed ubuntu linux on the HDD. Should I put the boot loader on the SSD or HDD?

> **altirisx said:**
> I got it already. For everyone, you need to install the GRUB bootloader over the Windows 7 one otherwise you will have two boot loaders conflicting with each other.

If you have installed Ubuntu on HDD then ideally, your Boot-loader must go on HDD. The two bootloaders will NOT conflict.
If you have windows on SSD and Ubuntu on HDD then just change the HDD boot order priority to make HDD your first boot disk.
This also ensures that your Windows Boot loader files are not overwritten in the MBR by GRUB on SSD. Which means if you remove Ubuntu and change the boot order in BIOS back to boot SSD first then your Windows will load. 
By installing GRUB on SSD you have damaged your Windows Boot Loader. In case you remove Ubuntu then Windows will NOT boot until you fix your MBR.

But if you have installed Ubuntu too on SSD then what you have done is correct.

---

### Post by oldfred on 2013-06-20
+1 on fantab's comments.

My goal always is reliability first, so I have a system installed on every drive and that system's boot loader in the MBR of that drive. Then each drive can boot without the other drive.

You can easily install your grub2 boot loader to your hard drive from inside your Ubuntu install.
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions or sda if not sdb):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

### Post by Odin Overland on 2013-06-20
The only thing I could add in is that if GRUB is installed after Windows 7 is installed, installing Windows Service Packs can become an issue.  There are work-arounds to this, but I really don't remember what they are off the top of my head.

---

### Post by Mark Phelps on 2013-06-20
> **altirisx said:**
> I got it already. For everyone, you need to install the GRUB bootloader over the Windows 7 one otherwise you will have two boot loaders conflicting with each other.

If you force the installation of Grub to an existing Win7 partition, not only will that NOT work, more importantly, it will create a folder in the Windows system partition with a name that is nearly identical to the folder containing the Win7 boot loader.  

As a result, Win7 will then get confused and try to load its boot loader from the wrong folder -- and fail to boot.

Not only will you have to remove the Grub stuff you forced onto Win7, you'll also have to reinstall GRUB -- properly this time.

---

