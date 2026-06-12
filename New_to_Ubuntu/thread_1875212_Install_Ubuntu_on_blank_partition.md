---
title: "Install Ubuntu on blank partition"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by xzinkx on 2011-11-04
How do I go about installing ubuntu on sda5 without touching sda2 partiton as this has my windows installation on it? Thanks.

[IMG]http://dl.dropbox.com/u/21598368/Screenshot%20at%202011-11-04%2016%3A58%3A30.png[/IMG]

---

### Post by mike555 on 2011-11-04
when you restart your computer to the ubuntu cd ,pick "other"or what ever it says, (the bottom choice) then tell it to install to the partition you want...... it will format (erase ) everything on that partition , so backup first......

 or you can resize the SDA5 to keep an area for data and make a separate partition for Linux then resize that for a swap partition (about 4GB)

---

### Post by xzinkx on 2011-11-04
Okay thanks, Once I do that, will I be able to dual-boot into windows and ubuntu? How easy is it to remove the dual-boot menu if I choose to uninstall ubuntu and use windows only?

---

### Post by WorldOfChaos 616 on 2011-11-04
hi there, did you ever figure out how to install ubuntu side by side? if not message me and i can give some guidance. possible solve your problem

---

### Post by Paqman on 2011-11-04
> **xzinkx said:**
> Okay thanks, Once I do that, will I be able to dual-boot into windows and ubuntu?

Yep, one of the things Ubuntu does is install a bootloader called Grub that sorts this out for you.

> 
How easy is it to remove the dual-boot menu if I choose to uninstall ubuntu and use windows only?

Pretty easy. 
[LIST=1]
[*][Get rid of Grub and switch back to the Windows bootloader]("https://help.ubuntu.com/community/DualBoot/Mbr#Fix_the_Mbr_for_Windows")
[*]Delete the Ubuntu partition(s) and recover the space in Windows.
[/LIST]

---

### Post by jmajeremy on 2011-11-04
Just make sure that Grub is installed on the primary partition...

---

### Post by xzinkx on 2011-11-04
> **jmajeremy said:**
> Just make sure that Grub is installed on the primary partition...

Thanks, was about to install GRUB on the other partition.

---

### Post by coffeecat on 2011-11-04
> **jmajeremy said:**
> Just make sure that Grub is installed on the primary partition...

> **xzinkx said:**
> Thanks, was about to install GRUB on the other partition.

**Do not** install grub to one of your primary partitions! If you install grub to sda1 or sda2 you will make either your recovery partition or Windows unbootable (and Ubuntu), depending on which you install it to. Let the installer install grub to the default, which is the mbr of /dev/sda, not a partition.

---

### Post by xzinkx on 2011-11-04
Okay, luckily I didn't do that. I installed Ubuntu on sda5 and GRUB on sda5. My problem is now that I can't figure out how to boot into ubuntu. It always goes into windows.

---

### Post by coffeecat on 2011-11-04
> **coffeecat said:**
> Let the installer install grub to the default, which is the mbr of /dev/sda, not a partition.

> **xzinkx said:**
> I installed Ubuntu on sda5 and GRUB on sda5.

:!:

Now you'll have to use the live CD to install grub where it should have gone in the first place.

[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

Substitute "sda5" for "sdXY" in 4, and "sda" for "sdX" in 5.

**EDIT**: by the way, I hope your sda5 partition is now an ext4 one, and not a NTFS partition. And did you create a swap partition? You might want to post the terminal output of:

```
sudo fdisk -l
```

Which you can get from the live CD session.

---

### Post by xzinkx on 2011-11-04
Whoops, so if I follow that guide, will it work? Will I have to delete the old grub?

---

### Post by coffeecat on 2011-11-04
> **xzinkx said:**
> I have to delete the old grub?

There's an awful lot of misunderstanding about grub in posts and blogs, so a quick rundown:

When you install grub to the mbr of a drive, you install about 440 bytes of code to the first 440 physical bytes of the machine and core.img to the embedding area, which is a portion of the drive reserved for boot code that is between the partition table and the first sector of the first partition. The rest of grub, including your grub.cfg file is in /boot/grub in the Ubuntu root partition.

By installing grub to sda5, you have installed the bits that should have gone to the mbr/embedding area to the partition boot sector. This is only of use when you need to chainload, which half the time doesn't work with grub 2 anyway. Just re-install grub according to those instructions and don't worry about the bits of grub in the partition boot sector. They will remain unused and will not do any harm.

Had you installed grub to the boot sector of sda1 and sda2, it would have done harm, albeit repairable. Windows doesn't like it - hence my warning.

---

### Post by xzinkx on 2011-11-04
Okay, I understand.

For step 5, shall I do,

sudo grub-install --root-directory=/mnt /dev/sda

or

sudo grub-install --boot-directory=/mnt/boot /dev/sda ?

---

### Post by coffeecat on 2011-11-04
It doesn't really make any difference. Both work equally well. But that should be:

```
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

for the second.

---

