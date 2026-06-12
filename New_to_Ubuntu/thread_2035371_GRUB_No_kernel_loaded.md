---
title: "GRUB: No kernel loaded"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by han5vk on 2012-07-30
Hello, I am new to Ubuntu, and I have wanted to install ubuntu on my USB stick with persistance (or how is it called). I followed this tutorial - [http://rudd-o.com/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive ]("http://rudd-o.com/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive")step by step, no errors, I just edited filenames "initrd.gz" to "initrd.lz". But now, when I try to boot from the USB stick, there is a black screen with something like this "**Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device/flies completions" **, and I do not know what to do now. When I type in "boot" it says, that kernel was not loaded. I have searched in google, found some threades, but I just can not make it work, I think it has something to do with the grub.conf file, which I have set as in that tutorial, but when I see the ones in the others threades they are not alike. Would someone, please, describe me, what I have to do and why? Beacause, I am a newbie and I just do not understand what I should do from the others threads. I am using ubuntu 11.10. Thank you.

---

### Post by oldfred on 2012-07-30
Grub2 now has a loopmount feature, so you do not have to extract kernel & init to boot like with grub legacy.

The grub entry is grub legacy says set root (hd0,0) which is first drive, first partition. Even though flash drive may not be first, if you select it from BIOS to boot from it will be hd0, but you installed to the second partition. then it should be (hd0,1) in grub legacy. Note that grub2 starts partition numbers at 1, where grub legacy starts at 0.

Boot multiple ISOs from one flash:
These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

Same thing as your link except using grub2.
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by barrykgerdes on 2012-07-30
I had that screen come up after an upgrade from 10.10 to 11.04 (on the way to an upgrade to 12.04). The upgrade completed satisfactoraly and asked for a reboot. I never got a solution on the forum and eventually killed it and started anew.

I was told all sorts of problems could happen with upgrades and other un related information but not an answer that would restore the program that should have booted if the upgrade had completed correctly.

Is there a simple command that can be entered at the prompt that will restore the program.

Barry

---

### Post by oldfred on 2012-07-30
No kernel loaded is usually a grub configuration issue. I get it when my manual configure of grub to boot something is not quite correct.

With grub2 this will solve many boot issues, but it does not work with grub legacy as that has not been the standard with Ubuntu since last used in 9.04.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by han5vk on 2012-07-31
Maybe I did not understand, but I have deleted all partitions on my USB, created a new, big one, on which I have installed grub by this [HowTo]("http://ubuntuforums.org/showthread.php?t=1288604"), It created the boot folder, I have created the grub.conf file, and then copied the ubuntu 11.10 LiveCD .iso file to the "isos" folder. But when I try to boot now, GRUB is all the same and says No Loaded Kernel.. What have I done wrong?

---

### Post by oldfred on 2012-07-31
Post your grub.cfg file and what path is the iso file?

This is my path from my hard drive's Ubuntu, so it has the extra media and label from the flash drive of MC4GB, note case is also important:
/media/MC4GB/boot/iso

This is my entry for 11.10. All my recent installs have used a similar ISO boot but from another hard drive.
I often have to experiment with this as with multiple drives it often changes. hd0 usually works better than the /dev/sdd.
(/dev/sdd,msdos1)


```

set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600
menuentry "Ubuntu 11.10 Oneiric 64bit" {
    set isofile="/boot/iso/oneiric-desktop-amd64.iso"
    loopback loop (/dev/sdd,msdos1)/$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by han5vk on 2012-07-31
This is my grub.conf file 
```

menuentry "Ubuntu" {
    set isofile="/boot/isos/ubuntu.iso" 
    loopback loop (hd0,1)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```
The .iso file is on the only one partition of my USB drive, labelled "HanUSB". The .iso file is in "isos" folder which is in "boot" folder, so from the root of the bootable partition /dev/sdb1 labelled "HanUSB" it is "/boot/isos/ubuntu.iso". All my files should be lowcase. I was experimenting now with multiple settings in grub.conf file, but I have always end on the same black screen saying the same creepy sentence. When I type "boot" it always says the same..

---

### Post by oldfred on 2012-07-31
Does your grub work with grub.conf? Ubuntus' grub2 is grub.cfg, but I have seen grub.conf with other distributions, I think.

You may just be missing a /

loopback loop (hd0,1)$isofile
loopback loop (hd0,1)[COLOR=Red]/[/COLOR]$isofile

---

### Post by han5vk on 2012-07-31
Well, uh, I have mistakenly created a grub.conf, not grub.cfg config file, so that was the reason for these troubles. Now, it launches the menu, with the "Ubuntu" option. But, when I click that it displays two errors, first something like "cannot read the Linux header"; and the second one something like "you need to load the kernel first". So, what is the matter here?

---

### Post by oldfred on 2012-07-31
Which Ubuntu ISO are you booting. I assume you did rename it to ubuntu.iso?

I never could get some of them to work, only desktop versions.

Grub does not loopmount alternate
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926)

I also had similar issue with server version. Kernel is not in the same place in ISO and even when corrected, it starts to load, but then gets lost.

---

### Post by han5vk on 2012-07-31
Well, I do not know what exactly u r asking, but I have downloaded ubuntu 11.10 live CD .iso from somewhere, renamed it to "ubuntu.iso" and copied to the isos folder. How did I get server version? :DD Well, I will try it with freshly downloaded Precise Pangolin in a while.. // edit: well, it is working, but showed me some internal ubuntu error after start.. Could someone tell me how to set it to use persistence with my casper-rw file? Thanks.

---

### Post by oldfred on 2012-07-31
This was for older version. Not sure if persistence works with the grub loopmount boot?

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

With grub2 persistent C.S.Cameron post#5 10.10:
[http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)
With grub2 persistent 10.04 C.S.Cameron post#15:
[http://ubuntuforums.org/showthread.php?t=1593656](http://ubuntuforums.org/showthread.php?t=1593656)

---

### Post by han5vk on 2012-07-31
So by the third link, #15 post, I just make a partition casper-rw with ext2 filesystem, and the Ubuntu will automatically store customizations in here?

---

### Post by drs305 on 2012-07-31
At the grub menu, go to the command line (press c) and see exactly where your file is located (according to grub):
Mount the ISO file and then check
```
ls (loop)/boot/isos/
ls (loop)/isos
```
See which one contains your ISO file and use that one in your $isofile name. It's possible Grub 'mounts' /boot as the root of that partition, in which case the file would be in /isos rather than /boot/isos.

Also check that the drive is (hd0) and not (hd1).

---

### Post by oldfred on 2012-07-31
ext2 is a Linux format. ext2 is an older one without any journal like FAT32 for Windows does not have a journal and NTFS does. 

Generally you want a journal, but for Flash or SSDs you may not to reduce wear. I have seen newer instructions for SSD that say to use ext4 but then turn journal off. I think that was what I did on my last install to flash.

Some posssible settings, sda1 is just the example, use your partition:
With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

