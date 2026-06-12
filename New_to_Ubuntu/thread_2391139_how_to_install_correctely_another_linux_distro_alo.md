---
title: "how to install correctely another linux distro alonside with ubuntu mate 18.04"
date: 2018-05-06
forum: New to Ubuntu
---

### Post by hilario_ferreira on 2018-05-06
I would like to install on my desktop alongside with ubuntu mate 18.04 another linux distro, but I woul like to keep as my primary boot option the ubuntu mate.

How to do it correctely ??

---

### Post by yancek on 2018-05-06
The first thing we would need to know would be whether you are using a Legacy/MBR system or the newer UEFI as the method varies.  With the older Legacy system, if you want to keep the Ubuntu bootloader as the primary, you would install Grub bootloader of the second system to the filesystem partition rather than the defaul, MBR.  The method with UEFI is different but can easily be set.

---

### Post by hilario_ferreira on 2018-05-06
To be honest I don't know  anything about legacy or UEFI. !!!! 

How do I find which system I am using ??

---

### Post by Dennis N on 2018-05-06
> I would like to install on my desktop alongside with ubuntu mate 18.04 another linux distro, but I woul like to keep as my primary boot option the ubuntu mate.

Consider using the installer's option to install the new OS side-by-side with the existing OS. Is your computer a BIOS or UEFI computer? What you do afterwards depends on that.

---

### Post by yancek on 2018-05-06
It would be useful if you indicated which of the 500+ linux distributions you intend to use, that is, if you've made that decision.  Boot Ubuntu, open a terminal and run the command below and post the output here.  If it shows an EFI partition, you are using UEFI, if not you are not.

```
sudo parted -l
``` Lower case Letter L in the command. 

There are many tutorials available on dual booting Ubuntu with another linux and I'm sure you can also find threads here at these forums using the Search option.

---

### Post by hilario_ferreira on 2018-05-06
Here it is:

Modelo: ATA TOSHIBA DT01ABA1 (scsi)
Disco /dev/sda: 1000GB
Tamanho de sector (lógico / físico): 512B/4096B
Tabela de Partições: msdos
Sinalizadores do Disco: 

Número  Início  Final   Tamanho  Tipo      Sistema de ficheiros  Sinalizadores
 1      1049kB  181GB   181GB    primary   ext4                  boot
 2      181GB   1000GB  819GB    extended
 5      181GB   1000GB  819GB    logical   ext4


Modelo:   (scsi)
Disco /dev/sdb: 15,9GB
Tamanho de sector (lógico / físico): 512B/512B
Tabela de Partições: msdos
Sinalizadores do Disco: 

Número  Início  Final   Tamanho  Tipo     Sistema de ficheiros  Sinalizadores
 2      2746kB  5138kB  2392kB   primary                        esp


I will probably install elementary OS

---

### Post by Dennis N on 2018-05-06
> **hilario_ferreira said:**
> Here it is:

Modelo: ATA TOSHIBA DT01ABA1 (scsi)
Disco /dev/sda: 1000GB
Tamanho de sector (lógico / físico): 512B/4096B
Tabela de Partições: msdos
Sinalizadores do Disco: 

Número  Início  Final   Tamanho  Tipo      Sistema de ficheiros  Sinalizadores
 1      1049kB  181GB   181GB    primary   ext4                  boot
 2      181GB   1000GB  819GB    extended
 5      181GB   1000GB  819GB    logical   ext4


Modelo:   (scsi)
Disco /dev/sdb: 15,9GB
Tamanho de sector (lógico / físico): 512B/512B
Tabela de Partições: msdos
Sinalizadores do Disco: 

Número  Início  Final   Tamanho  Tipo     Sistema de ficheiros  Sinalizadores
 2      2746kB  5138kB  2392kB   primary                        esp


I will probably install elementary OS

Good. You need to install in BIOS - no UEFI. Should be easy. Start installer. Select side-by-side option in Installation type. Follow the directions. After install, system will reboot to grub of Elementary. Select Ubuntu instead from grub menu. Then run these commands in Ubuntu's terminal one after the other to get Ubuntu as default:

```
sudo grub-install /dev/sda
sudo update grub

```
Reboot
Good Luck.

---

### Post by yancek on 2018-05-06
I would suggest you use the manual install method which is probably referred to as Something Else in Elementary.  When you boot, select the option to Try it and use gparted from a terminal to unmount the logical and extended partition and then shrink the logical to make room for the new OS.  At present, you have 2 partitions taking up the entire drive so you would need somewhere to install your new system.  Using the Something Else option will allow you to select the Device for bootloader installation and you would then select the partition on which you install Elementary which should be sda6. When you reboot, you should see the Ubuntu Grub menu and you can just boot it and run:  sudo update-grub.  The method suggested above should also work but I've never used these auto-install options.

---

### Post by hilario_ferreira on 2018-05-06
Ok I understood yr instructions but before doing that way I would like to tell what I am trying to do:

I have 2 partitions on my HD :

SDA1 = 168 GB  - formatted as ext4
SDA5 = 763 GB with ubuntu mate installed.

What I wanted to do is install new OS on SDA1 ,The steps I've tried are : something else ( instead of side by side) but when I select the sda1 partition I get the following message :
"no root file system is defined.Please correct this from the partioning menu" and I'm stuck here as I don't know what to do next.
Can it be done this way or not ??

Another question if I choose side by side as you sugested where is going to be installed the new system SDA1 or SDA5 ??

---

### Post by oldfred on 2018-05-06
How are you selecting sda1?
You have to press the change button, and then choose use as / and format as ext4.

I normally install to 25 or 30GB including /home. And have multiple installs.
But then save most data in /mnt/data another ext4 partition just for most of the data normally in /home. Then I can use that data in all installs without sharing /home and user settings which may conflict between installs.

---

### Post by Dennis N on 2018-05-06
> What I wanted to do is install new OS on SDA1... Good. That is the goal. Given this goal, an easy way would be to delete sda1 with gparted (using the live media) before starting the installer. If you then select side-by-side during installation, it would automatically make a new partition where sda1 was, automatically format it correctly, and install the new OS there. Reboot, choose Ubuntu, and run the commands in post #7 in the ubuntu terminal.  

The something-else method suggested by yancek and oldfred is good too. If you choose this (maybe you already have?), you would not delete sda1, and have to give some information how sda1 is going to be used and formatted (see yancek's and oldfred's posts).

---

### Post by hilario_ferreira on 2018-05-07
Something went wrong:

I diid exactelly as described by DENNIS N :

Good. You need to install in BIOS - no UEFI. Should be easy. Start  installer. Select side-by-side option in Installation type. Follow the  directions. After install, system will reboot to grub of Elementary.  Select Ubuntu instead from grub menu. Then run these commands in  Ubuntu's terminal one after the other to get Ubuntu as default:

 	Code:
 	sudo grub-install /dev/sda
sudo update grub

The reboot was correct the first time I selected ubuntu and entered the above commands on terminal.
Firs command runned ok second gave me "unknown command " !!!

Now it's only possible to boot my main os ubuntu mate.

There's another option but refers to ubuntu 17.10 that once was installed but it won't boot either.

Now if I try to reinstall elementary I have no more the option to do it side by side !!!

---

### Post by Dennis N on 2018-05-07
```
Code:
sudo grub-install /dev/sda
sudo update grub

```
There should be a "-" in the second command. Sorry about that. It should be:

```
sudo update-grub
```

No harm done. Easy to fix:

Boot into ubuntu-mate and run that command again. Then reboot and the other os should appear in grub menu.

---

### Post by hilario_ferreira on 2018-05-07
You are right.
It worked. 
Tks for your kind support.

---

