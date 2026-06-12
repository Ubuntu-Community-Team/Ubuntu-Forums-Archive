---
title: "[SOLVED] No XP boot option in Grub menu"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Portugeezer on 2008-09-25
I loaded Ubuntu 8.04 via a CD and selected the guided installation which I believe allows the disk to be partitioned so I can have the option to boot to XP or Unbuntu.

When I restart the machine and hit <esc> in the grub menu I dont get XP as an option.

Did I do something wrong? Have I wiped XP?

I have looked around the forum and checked the stage.1 file and have hashed out hidemenu, but I still get the same issue.

Please help !

---

### Post by Elfy on 2008-09-25
Can you open a terminal and run this command

```
sudo fdisk -l
```

Terminal is in accessories menu and password needed is your normal one - it will be invisible, that is normal.

---

### Post by CLomax on 2008-09-25
Did you do the following?:

Change the menu.lst (gksudo gedit /boot/grub/menu.lst) adding:
> title         Windows XP
root         (hd?,?) {Where ?,? is the drive and partition XP is installed to
makeactive
chainloader +1
?

---

### Post by Portugeezer on 2008-09-26
Output here 

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19268   154770178+  83  Linux
/dev/sda2           19269       19452     1477980    5  Extended
/dev/sda5           19269       19452     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)

I also installed the start up manager but the operating systems do not show XP.

Thanks for the reply and help

---

### Post by Portugeezer on 2008-09-26
Hi

I have the following

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4c3b5c63-0624-43d5-a29e-75f3dbe509ab ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4c3b5c63-0624-43d5-a29e-75f3dbe509ab ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

How do I find out what partition XP is on?

Thanks

---

### Post by bumanie on 2008-09-26
You have wiped your xp unfortunately. You could try to retrieve it with testdisk or ntfsundelete which is part of the ntfsprogs tools.

PS: I am assuming that the FAT32 drive is a data drive. If it is in fact windows follow as noted below - it would be unusual, but not unknown for xp to be on a FAT32 filesystem.

---

### Post by Crafty Kisses on 2008-09-26
To me it looks like your Windows XP partition is gone, but in the future this is a good reference. So in order to edit and access the GRUB menu, you need to run this command in the Terminal:
```
sudo gedit /boot/grub/menu.lst
```
Then look at this output, and it should direct you where Windows is located at:```
sudo fdisk -l
```
From the information you got from fdisk, you can now edit your GRUB list by putting the following lines in:
```
title Windows XP
root (hd?,?) {Where ?,? is the drive and partition XP is installed to
makeactive
chainloader +1
```

---

### Post by Orange_and_Green on 2008-09-26
[EDIT]Guys, could it be that his windows installation is on the FAT32 partition? I think it's worth a try. I have seen certain manufacturers like acer preinstall XP on FAT32 partitions...

Dear Portugeezer,

I agree with bumanie and Codename that chances are that your winodws installation is gone. However, there still is a small chance to save it so I think you might try to do as Clomax suggested and edit the menu.lst file. 

You can find out if the contents of /dev/sdb1 are your Windows installation by doing the following:```
mkdir seconddisk
sudo mount /dev/sdb1 seconddisk
sudo ls seconddisk
```

If it contains directories called "Documents and Settings", "Windows" or "Winnt", then you're in luck, that's your windows installation.To recover it, please open up a terminal and follow these steps:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksu gedit /boot/grub/menu.lst
```

Go to the bottom of the text that shows up and add the following lines (note that the spaces are important too, so copy exactly as it's written here):
```
title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
```

Save and reboot.
I hope this fixes your problem. If it doesn't, try booting into Ubuntu again, issuing the command "gksu gedit /boot/grub/menu.lst" and removing the two lines that start with "map" from the text you added.


If, on the other hand, that _was_ a data disk, then... well, I'm sorry for you...

Good luck:KS

---

### Post by Portugeezer on 2008-09-26
Oh well - looks like I've completely wiped XP - had all my data backup up - only photos and music so ok, only problem I have is Skype doesnt work with webcams for Ubuntu and cant get my Kodak printer working.

At least I've made the complete jump from Windows now!!! I do like Ubuntu , apart from the annoying fact I cant get the webcam and printer to work.

Thanks

---

### Post by Idefix82 on 2008-09-26
Congratulations on the jump! :)
If you open separate threads about the issues you are having with your webcam and printer I am sure people will sort you out.

---

### Post by Elfy on 2008-09-26
Whats on sdb1 then - at least it's a win format drive.

---

### Post by Portugeezer on 2008-09-26
External hard drive

---

