---
title: "Can't boot from USB"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by new123 on 2011-10-26
I have same problem tryng to install Ubuntu, Fedora and now Lubuntu.
For making Ubuntu LiveUSB, I used Ubuntu liveUSB creator. For Fedora I used Fedora LiveUSB creator.
for Lubuntu (now) I used UNetbootin - [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and always the same, when boot I get this message:
```
SYSLINUX 4.03 2010-10-22 CNS Copyright (C) 1991-2010 N.Peter Anvin et al
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot:
```Booting from CD/DVD is alright, I never get any error.. :confused:

---

### Post by cavh on 2011-10-26
Can you save (and then view) any file at all on the USB stick? You may have a defective unit.

---

### Post by new123 on 2011-10-26
> **cavh said:**
> Can you save (and then view) any file at all on the USB stick? You may have a defective unit.
Do you mean Edit-Save and then view? I dont know what u mean..

---

### Post by amjjawad on 2011-10-26
Hello,

Few notes and hopefully will help you to fix your problem.

1- Have you checked MD5SUM for the file that you downloaded?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Please do that and compare the result with: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2- Have you formatted your USB Dirve?
If you are using Linux, run GParted and choose from Device Menu (Create New Partition Table) then format as FAT32. Make sure to choose the correct drive. Usually it's /dev/sdb or /dev/sdc

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8073[/IMG]

If you are using Windows, try to format it and use FAT32 filing system.

3- Check your BIOS and make sure it does detect your USB.

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]

Some USB Drives are being detected as HDD0. Some other might be detected as something else.

---

### Post by sneham429 on 2011-10-26
How old is the computer you're trying to use? I have one that's so old, not only will it not boot from a USB, it can't read DVD's either, you can only boot with a CD.

---

### Post by bob-linux-user on 2011-10-26
Is this thread any use?

[http://ubuntuforums.org/showthread.php?t=1663483](http://ubuntuforums.org/showthread.php?t=1663483)

However as others have said already you must have a computer that can boot from an external usb drive.

---

### Post by wgn on 2011-10-26
If you can read the files on the USB, paste the contents of syslinux.cfg

---

### Post by amjjawad on 2011-10-26
If the machine doesn't support booting from USB, that option won't be available on BIOS to begin with.

Anyway, for everyone's information, if the machine doesn't really boot from USB, there is: [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

---

### Post by new123 on 2011-10-27
> **amjjawad said:**
> Hello,

Few notes and hopefully will help you to fix your problem.

1- Have you checked MD5SUM for the file that you downloaded?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Please do that and compare the result with: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2- Have you formatted your USB Dirve?
If you are using Linux, run GParted and choose from Device Menu (Create New Partition Table) then format as FAT32. Make sure to choose the correct drive. Usually it's /dev/sdb or /dev/sdc

If you are using Windows, try to format it and use FAT32 filing system.



MD5SUM:
```
a0307761af5a0e3374f65959366d1dcb  lubuntu-11.10-desktop-i386.iso

```which is different then on [UbuntuHashes Page.]("https://help.ubuntu.com/community/UbuntuHashes") ( 76e5865ce8d0d08fa9f833d781016fe3 
    lubuntu-_11.04_.iso)
(I mentoin that in UbuntuHashes page is newest version 11.04 while my version of Lubuntu is 11.10)

Yes, I formatted (FAT32) my USB using Windows.

---

### Post by amjjawad on 2011-10-27
> **new123 said:**
> MD5SUM:
```
a0307761af5a0e3374f65959366d1dcb  lubuntu-11.10-desktop-i386.iso

```which is different then on [UbuntuHashes Page.]("https://help.ubuntu.com/community/UbuntuHashes") ( 76e5865ce8d0d08fa9f833d781016fe3 
    lubuntu-_11.04_.iso)
(I mentoin that in UbuntuHashes page is newest version 11.04 while my version of Lubuntu is 11.10)

Yes, I formatted (FAT32) my USB using Windows.

[http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/)

[http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/MD5SUMS](http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/MD5SUMS)

```

a3d9689f0f63827d8f72a38b5a80767e *lubuntu-11.10-alternate-amd64.iso 

6b2ef531916da95982eb9b9de9dcb19e *lubuntu-11.10-alternate-i386.iso 

34adee80fd0e0f37a5b898706988fe49 *lubuntu-11.10-desktop-amd64.iso 

a0307761af5a0e3374f65959366d1dcb *lubuntu-11.10-desktop-i386.iso 

```

---

### Post by new123 on 2011-10-27
> **amjjawad said:**
> Hello,
3- Check your BIOS and make sure it does detect your USB.
Some USB Drives are being detected as HDD0. Some other might be detected as something else.

Err whether the USB is plugged or not, I always have same list of boot devices, like:
FLOPPY
...
CDROM
USB-FDD
USB-ZIP
USB-CDROM
USB-HDD
...
DISABLED

And I selected USB-HDD, (there is nothing like HDD0.. :S)

---

### Post by new123 on 2011-10-27
> **wgn said:**
> If you can read the files on the USB, paste the contents of syslinux.cfg
```
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
ui gfxboot bootlogo
```

---

### Post by new123 on 2011-10-27
> **sneham429 said:**
> How old is the computer you're trying to use? I have one that's so old, not only will it not boot from a USB, it can't read DVD's either, you can only boot with a CD.
About 5-6 years....

---

### Post by wgn on 2011-10-27
Your syslinux.cfg file looks strange.  I haven't used unetbootin for Lubuntu, but here's the syslinux.cfg file I have for using it to load LPS

```
default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit loadramdisk=1 ramdisk_blocksize=4096 root=/dev/ram0 ramdisk_size=524288 splash=silent vga=791 console=ttyS3

label ubnentry0
menu label LPS 1.2.5
kernel /ubnkern
append initrd=/initrd loadramdisk=1  ramdisk_blocksize=4096 root=/dev/ram0 ramdisk_size=524288 splash=silent vga=791 console=ttyS3

```

Your file doesn't ID a kernel to load or any of the append's I would expect.  Reasonably good man page for syslinux at [http://linux.die.net/man/1/syslinux]("http://linux.die.net/man/1/syslinux")

I'm downloading Lubuntu right now.  I'll try installing it and see if I can duplicate what you got.  Let you know.

---

### Post by wgn on 2011-10-27
OK, there's something wrong with your syslinux.cfg.  Here's what I get when I install lubuntu (same version you noted in #9) with UNetbootin

```
default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Lubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Lubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label ^Back..
kernel /ubnkern
append initrd=/ubninit 

label ubnentry7
menu label menu
kernel /isolinux/vesamenu.c32
append initrd=/ubninit 

label ubnentry8
menu label oem=OEM install (for manufacturers)
kernel /ubnkern
append initrd=/ubninit oem=oem-config/enable=true

```

Boots with no problems.
Try reinstalling.  See if your problem repeats itself.

---

### Post by varunendra on 2011-10-28
*new123,*
You are booting the correct device (it doesn't matter what kind of device it is detected as by BIOS). Choosing a wrong device, you won't get this message in the first place:
> **new123 said:**
> when boot I get this message:
```
SYSLINUX 4.03 2010-10-22 CNS Copyright (C) 1991-2010 N.Peter Anvin et al
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot:
```
The above message simply means your USB drive is bootable and the OS boot process has been successfully initialized with it. However, the problem occurs at the stage of 'reading' boot and/or configuration files. Now that you have tried both live usb creator (means - the inbuilt 'Startup Disk Creator??) and unetbootin getting the same results everytime, it seems to me that the problem might be with the device itself, not with the computer or the method to make it live. Accordingly-

[LIST]
[*]Have you tried formatting it as *amjjawad *suggested?
[*]Have you tried another USB flash drive? Brand/model does matter in this particular case.
[*]Have you tried the same flash drive to boot another computer, if available?
[/LIST]
As another approach with the same drive, try formatting it as fat16 (as opposed to fat32). It has been found to work sometimes.

---

### Post by rng on 2011-10-28
> Err whether the USB is plugged or not, I always have same list of boot devices, like:
FLOPPY
...
CDROM
USB-FDD
USB-ZIP
USB-CDROM
USB-HDD
...
DISABLED

And I selected USB-HDD, (there is nothing like HDD0.. :S) 	

There must be a HARD-DISK option. Choose that (by pressing ENTER) and you may find your USB-drive listed there, along with main hard disk (as amjjawad suggested). It works like that on some computers.

---

### Post by roopeshmicasa on 2012-07-07
The root cause to this system error is FAT32. 
I think your Bios cannot understand FAT32 file system. May be your  system is old one. Format the USB with FAT16, or simply FAT file system  and then create the usb bootable stick that will definitely work....

---

