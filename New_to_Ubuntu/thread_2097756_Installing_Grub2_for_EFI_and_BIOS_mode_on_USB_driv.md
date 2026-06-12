---
title: "Installing Grub2 for EFI and BIOS mode on USB drive"
date: 2012-12-24
forum: New to Ubuntu
---

### Post by rpowell on 2012-12-24
All,
I am trying to install Grub2 on a thumb drive for booting in either EFI or BIOS mode. 

My platform is a MacbookPro 5,5 running only Ubuntu 12.04 LTS x86-64 in EFI boot mode. The disk has 3 partitions sda1 for /boot/efi (gfdisk -l reports this as id 83 (linux) but gparted claims it is FAT32), sda2 for /, and sda3 as swap. My Grub2 version info is: (GRUB) 1.99-21ubuntu3.4. 

My USB stick is a Crucial Sandisk 8GB. It is typically recognized as sdc though I have seen it show as sdd once.

Using gparted I wiped everything on the disk and created a primary partition for EFI as FAT32 with the boot flag set and off set from the beginning by 4MiB (I did this because evidently core.img needs "space" (32kB) I believe for core.img, and a primary partition as ext4 filesystem.

I then did the following:
$ sudo mount /dev/sdc2 /mnt
$ sudo mkdir /mnt/boot
$ sudo mkdir /mnt/boot/efi
$ sudo mount /dev/sdc1 /mnt/boot/efi
$ sudo grub-install --root-directory=/mnt /dev/sdc

I rebooted and after a very long time at the macbook grey screen I was eventually presented with what looked like an EFI grub2 cli. I say it looked like EFI because while it was command line it was high resolution. If there's a way to tell at the grub cli please pass it on.

I thought it was a success and so rebooted to boot my macbook and ... I got a garbled boot screen where the Grub2 menu typically comes up and nothing more. By garbled I mean two somewhat disjoint lines of extended ascii characters.

At this point I needed to boot my LiveCD in EFI mode (on the macbook you need to hold down 'option' and wait for the BootROM to recognize the EFI partition on the CD ROM and then select that to boot from, otherwise it boots in BIOS compatibility). Then following the instructions on: [http://superuser.com/questions/376470/how-to-reinstall-grub2-efi](http://superuser.com/questions/376470/how-to-reinstall-grub2-efi) I almost got it working. After fiddling the right way for me to repair my Grub2 on sda was:

$ sudo mount /dev/sda2 /mnt
$ sudo mount /dev/sda1 /mnt/boot/efi
$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
$ modprobe efivars
$ sudo chroot /mnt
# grub-install /dev/sda
# grub-update
# exit
$ for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
$ sudo umount /mnt/boot/efi
$ sudo umount /mnt
$ reboot

and I was back to normal... this is repeatable. (oh and if someone could please tell me why mounting /dev /dev/pts /proc and /sys is required I would love to know because it is for grub-install to work correctly. As before I found that line I was doing the same thing but it was saying /dev not mounted or something similar).

So I thought maybe I need to chroot into my USB device before i run grub-install...but that I can't do because it's not a proper environment (no bash...in fact it's just an empty drive I'm trying to get to come up with grub cli...and then hopefully add kernels and filesystems etc).

So what I'm having a problem with is that everytime I run grub-install from my actual OS to make a bootable USB drive, it corrupts my original Grub2 install which I want to leave be. I think this is due to grub-probe being run as there was a warning of possible bad behavior on the ubuntu grub2 website I believe...I just don't know how to avoid corrupting my grub2 on sda when I want to install grub2 on sdc. It seems like people have had success with it however, but maybe that's because they using grub-pc and not grub-efi. 

That brings up another question which is how does grub-install know which version of grub I want to install ... grub-efi or grub-pc... Does it do grub-pc by default and if it finds an efi partition it does grub-efi as well? The ubuntu ISO is a good example of what seems to be a successfully formatted hybrid boot scheme as it can boot into either BIOS compatibility or EFI mode. I am trying to get the same boot scheme on a usb stick by hand  (no rEFIt/rEFInd or any of the other all encompassing utilities). 

This is coming from the core goal of getting Thinstation on a usb stick, however thinstation recommends SYSLINUX. I'm using GRUB2 for my bootloader so I wanted to keep things consistent.

Any help is well appreciated and I will post any snippets if it helps.

Rob

---

### Post by oldfred on 2012-12-24
I do not have a Mac, but started trying to do what you are doing. But my system is BIOS and it is difficult to get it to install to efi.

I think you will want flash drive as gpt partitioned.

Grub/Ubuntu installs grub-pc if booted in BIOS mode and grub-efi if booted in UEFI mode. With your Mac I am not sure how you are booted as Macs have a UEFI version between 1 and 2 and both Windows and Ubuntu need UEFI version 2 to boot with UEFI. Most that install Windows end up with the first 4 partitions as MBR and the rest as gpt in something called a hybrid which you have to keep in sync or else.
       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
    
But Ubuntu will boot BIOS mode with gpt partitions. I have my flash drive configured with gpt partitions and have both a efi partition and a bios_grub partition. Then grub installs its core.img to the bios_grub partition for BIOS boot and can install grub-efi to the efi partition. But since I only boot with BIOS I cannot get it to install the efi mode. But someone recently posted that there is a force command which I plan to research to see if that will work for me to force efi install even when booted in BIOS mode.

Your mounting of the other system partitions is a full chroot so you are only using the kernel to boot, but then are inside your install to update it from inside using everything but the kernel.  Required when major issues with grub2.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by rpowell on 2012-12-24
> **oldfred said:**
> I do not have a Mac, but started trying to do what you are doing. But my system is BIOS and it is difficult to get it to install to efi.

I think you will want flash drive as gpt partitioned.


RP: It was indeed originally "msdos" according to gparted and so changed it to "gpt".
> **oldfred said:**
> 
Grub/Ubuntu installs grub-pc if booted in BIOS mode and grub-efi if booted in UEFI mode. With your Mac I am not sure how you are booted as Macs have a UEFI version between 1 and 2 and both Windows and Ubuntu need UEFI version 2 to boot with UEFI. 

RP: I tried to find what version of EFI my macbook has, but it is some adulterated version of the standard as you say. However my mac is indeed booting in EFI according to the following line from:  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
It indicates I am booting in EFI mode.
> **oldfred said:**
> 
Most that install Windows end up with the first 4 partitions as MBR and the rest as gpt in something called a hybrid which you have to keep in sync or else.
       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
    
RP: I saw this site for some other things, good information regarding hybrids. Thanks. Note he does mention on his page "Apple's older EFI 1.*x* implementation" implying perhaps they have since changed which is why I can get Grub2 to work in EFI Mode?
> **oldfred said:**
> 
But Ubuntu will boot BIOS mode with gpt partitions. I have my flash drive configured with gpt partitions and have both a efi partition and a bios_grub partition. Then grub installs its core.img to the bios_grub partition for BIOS boot and can install grub-efi to the efi partition. But since I only boot with BIOS I cannot get it to install the efi mode. But someone recently posted that there is a force command which I plan to research to see if that will work for me to force efi install even when booted in BIOS mode.

RP: Does this mean you run grub-install pointing it to your /dev/usbdevice and it doesn't corrupt your /dev/harddrive grub2 installation? If so maybe then it's because when I was doing it, my harddrive was booted in EFI and my USB drive was not gpt and so it installed as grub-pc and somehow /that/ fact corrupted my harddrive Grub2? I'd like to know that when I run grub-install directing it to some device other than my internal harddrive it doesn't affect my harddrives grub installation...right now it seems like it does affect it but I don't know why or how to prevent it.
> **oldfred said:**
> 
Your mounting of the other system partitions is a full chroot so you are only using the kernel to boot, but then are inside your install to update it from inside using everything but the kernel.  Required when major issues with grub2.

RP: You're referring to how I fixed the corrupt grub2 on my harddrive? Yes I can chroot into that because there is a full system there and yes the kernel loaded is from the liveCD. I can't however, chroot into my usb drive because it has no system on it, just a blank flash device partitioned (now) as gpt with sdc1 being fat32 for efi and sdc2 partioned as ext4 for a linux build.

Will try again with the new gpt. So the goal is two fold, a bootable USB disk in either EFI or BIOS compatibility, and the ability to do it from my macbook using grub commands and not corrupt or change my internal harddrives grub2 installation.

---

### Post by rpowell on 2012-12-27
A quick update. While I did reformat the USB Stick to gpt. I did not attempt to rerun grub-install /dev/sdc as it should not matter what my usb-stick is formatted as with regards to grub-install corrupting my harddrives bootloader. So for now, I consider using grub-install as dangerous until I can figure out, or someone can tell me what it is doing that affects my harddrive and how to stop it.

To the end of still creating a bootable usb stick, i've gone the way of syslinux for now as that is the OS i'm booting. This will boot in BIOS compatibilty so the EFI side of things is still not figured out. 

That said, creating a bootable usb drive using SYSLINUX on an EFI booted system (at least for my macbook EFI booted system, PC's may be different), the ./syslinux /dev/sdc1 command did not work (I did reformat the usb stick to an MBR style drive with a FAT32 filesystem single partition: be sure to flag it as bootable). I believe this is because of the lack of the BIOS (I don't know what syslinux requires from the BIOS code but there must be something). On a PC syslinux works as would be expected (at least on Win 7, running commandline as administrator and typing 'syslinux.exe -m -a F:' where F is my usb stick). To get my macbook to be able to create it I had to follow the advice here: [http://thinstation.sourceforge.net/CF-HOWTO-2.html](http://thinstation.sourceforge.net/CF-HOWTO-2.html) in particular the EDIT in step 3. I actually had to sudo -i for it to work, probably because of the piping? however, after cat mbr.bin > /dev/sdc and then doing the usual syslinux stuff it worked (mbr.bin was in my syslinux install /usr/lib/syslinux directory).

So in general, getting a usb stick to be bootable on an EFI system isn't particularly straight forward yet. If anyone can shed any more light on the grub-install or how to get syslinux to work without the hack on an EFI system I'd be interested to hear.

Thanks.

---

### Post by ipatch on 2013-02-24
did you ever get a dual EFI / BIOS usb flash drive setup?

---

### Post by oldfred on 2013-02-24
I have no way to test.

This was for Tinycore which may give some clues on how to do it.

[http://forum.tinycorelinux.net/index.php?topic=13445.15](http://forum.tinycorelinux.net/index.php?topic=13445.15)

---

### Post by andreas-bartels on 2013-12-01
Hi Rob, you've to mount this mount points to simulate the invironment of your system. I might be not very good in english to explain, but it is a bit like that, you mount first your main partition to mnt and than you add under mnt the other parts like boot boot/efi and of course you do need in this subenvironment all your processdata and devicedata because the grub-install is doing an automated check of your equipment and installs than all what is needed to start this equipment. by changing root you will make this subenvironment for your grub-install to the environment and if there are no devices - there will be no boot possible. I hope you do understand what I am telling, because this writing in foreign languages could drive me crasy.

---

