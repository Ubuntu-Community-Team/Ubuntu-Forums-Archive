---
title: "I can install Ubuntu but it does not boot"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by alex335 on 2015-02-18
Hi,
im trying to install Ubuntu on my new PC and the Installation works good but when i restart after the Setup it somehow does not recognize it as a OS and it just says "Please select proper boot device..." .My new mainboard has this UEFI thing and i have no idea what it is and how it affects the boot process i dont want it so can i just turn it off maybe?At the moment i am running the "I want to test Ubuntu" option on my USB Stick and it works perfect.The Mainboard is an MSI 970A-G46.

---

### Post by oldfred on 2015-02-18
You are able to install in either UEFI or the 35 year old BIOS mode. But UEFI for new systems does have advantages. But it also is relatively new. Apple converted to UEFI when it changed to Intel chips several years ago and all new Windows 8 systems use UEFI.
       
Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Some systems require UEFI/BIOS settings. Many laptops only boot Windows by using the description which is not per UEFI standard. But if a motherboard, it should not have that issue.

Are you booting in same mode UEFI or BIOS as you installed?
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

 
Some MSI issues, not sure if same with your model.
 MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[http://forum-en.msi.com/](http://forum-en.msi.com/)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524)

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by alex335 on 2015-02-18
I reinstalled the OS but it still doesn't work it says "Read error" when i try to boot or just "Insert proper boot device".
That's what the boot-repair hast to say: [http://paste.ubuntu.com/10293435](http://paste.ubuntu.com/10293435)

---

### Post by oldfred on 2015-02-18
You have installed in UEFI mode with LVM. 
I do not know LVM type installs.

But you may need a /EFI/Boot/bootx64.efi for an external drive to boot.
I just might create that folder in the efi partition and copy grub or shim into it.

Standard example, your efi is sdf1, so change drive in example below.
 From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
sudo mount /dev/sda1 /mnt
#only if not already existing, 
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

---

### Post by alex335 on 2015-02-19
Ok so the problem was not the software but a broken SATA cable.I was able to install the OS on the harddrive but i could not boot from it untill i changed the cable.Took me a whole day to figure that out.It is now running in UEFI mode without any issues.Thanks for your help!

---

