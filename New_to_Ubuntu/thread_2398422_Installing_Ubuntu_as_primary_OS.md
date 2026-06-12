---
title: "Installing Ubuntu as primary OS"
date: 2018-08-11
forum: New to Ubuntu
---

### Post by nkmol on 2018-08-11
Hello community of Ubuntu,

[SIZE=4]Setup[/SIZE]
I have been looking for an alternative OS for my devices and wanted to try out Ubuntu. I came across the Ubuntu Budgie and wanted to replace it with my Windows 10 installation. To have a fresh start, I wanted to clear all my partitions and data. This I did through the Ubunutu installation wizard.

Ater this I created my partition containing of: swap, / (root), /var, /tmp, /boot and /home

[https://snag.gy/B7Gg9S.jpg](https://snag.gy/B7Gg9S.jpg)

[SIZE=4]Problem[/SIZE]
After setting up the partition through the wizard (above picture is taking aftward in GParted) I continued the installation. When the setup was installing the files, it failed on installing grub: "grub-efi-amd64-signed failed installation".

[SIZE=4]What I have tried
[/SIZE][SIZE=2]Bios: Disabling Safe Boot, switching between CMS-mode on and off
[/SIZE]Running "grub-update" and "grub-install" giving the error of "error: failed to get canonical path of `/cow'"
Installing with EFI partition (/boot/efi) with "boot,esp" flags
Running boot-repair resulting in a error: [http://paste.ubuntu.com/p/ThsKyshhhs/](http://paste.ubuntu.com/p/ThsKyshhhs/)

---------------------------------------------------

I have no clue what the problem is. Might it be because Windows used to be installed on this system and the BIOS is still correlating to that? Again, I want to note, I have **removed all partitions **before installation.

Any help in the right direction is appreciated.

With kind regards,
Nkmol

---

### Post by wildmanne39 on 2018-08-11
Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by oldfred on 2018-08-11
You must have a newer system that is UEFI hardware.
You then can install in the newer UEFI boot mode, or the now 35 year old BIOS boot mode.

But if using UEFI, you must have an ESP - efi system partition which is FAT32 with boot flag and/or esp flag. It is anywhere from 100 to 500MB. Larger if multiple booting or what to experiment. Windows typically uses the 100MB size but assumes you only have Windows.
UEFI also strongly suggest using gpt, not the old MBR partitioning.

The default install of Ubuntu will install with just / (root). It now uses a swap file instead of a swap partition. And you do not really need any additional partitions, but many like to separate data from system so use /home or /mnt/data as another partition. Having additional partition complicates thing for typical desktop unnecessarily. If running  a server and managing it, you may want additional partitions.

I like to install Ubuntu and keep old installs and test install the next version. So I have multiple root partitions, but one data partition which I mount in each & separately backup.

```
fred@bionic-z97:~$ lsblk -o NAME,size,FSTYPE,LABEL,MOUNTPOINT,MODEL
NAME      SIZE FSTYPE LABEL       MOUNTPOINT              MODEL
sda     119.2G                                            Samsung SSD 840 
&#9500;&#9472;sda1  499.7M vfat   EFI         /boot/efi               
&#9500;&#9472;sda2      2M                                            
&#9500;&#9472;sda3   24.4G ext4   trusty                              
&#9500;&#9472;sda4    1.9G swap                                       
&#9500;&#9472;sda5   10.7G ext4   iso_ssd                             
&#9500;&#9472;sda6   24.4G ext4   xenial                              
&#9492;&#9472;sda7   28.7G ext4   bionic      /                       
sdb     931.5G                                            WDC WD10EZEX-00B
&#9500;&#9472;sdb1  499.7M vfat   ESP_B                               
&#9500;&#9472;sdb2      2M                                            
&#9500;&#9472;sdb3   24.4G ext4                                       
&#9500;&#9472;sdb4  390.6G ext4   data        /mnt/data               
&#9500;&#9472;sdb5   27.9G ext4   backup                              
&#9500;&#9472;sdb6   12.6G ext4   iso_hdd                             
&#9500;&#9472;sdb7    2.1G swap               [SWAP]                  
&#9500;&#9472;sdb8   25.4G ext4   debian                              
&#9500;&#9472;sdb9   23.3G ext4   artful                              
&#9500;&#9472;sdb10  24.4G ext4   bionicb                             
&#9500;&#9472;sdb11   9.8G ntfs                                       
&#9492;&#9472;sdb12  25.4G ext4   cosmic_b   
```

---

### Post by nkmol on 2018-08-12
Thank you for the fast response Oldfred. 
As suggested, to keep it simple, I have only used the / (root) and the suggested EFI-partition. Thanks to your link I could identify my setup, seems to be the only complete tutorial on the internet ^^ I have successfully install Ubuntu on my new system, so I will mark this as answered.

Thanks once again for the fast complete answer.

[Solved]

---

