---
title: "Grub2 &amp; iso boot"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by DJ 1 on 2014-02-25
OK... So I've looked a few posts online about. Iso booting with grub2. 

Do I have to have basic Ubuntu install to store the  iso(from what I've seen it's usually kept in the home folder)? 

I didn't know if it were possible to boot an iso on a clean partition (with no OS install on it) &  then have grub installed from that iso store all the grub config file/etc in the same area as the iso? 

Cheers.

---

### Post by ajgreeny on 2014-02-25
You may have already seen this thread [http://ubuntuforums.org/showthread.php?t=1838959](http://ubuntuforums.org/showthread.php?t=1838959) which has some more links to information about how to do what you want, but if not it's a good start.

There is also this info [Boot ISOs on USB with Grub2]("http://ubuntuforums.org/showthread.php?t=1288604") which I use a lot to boot various versions of the*ubuntu family from a USB with at the moment about 9 different iso files on it, all of which boot quickly and painlessly.

---

### Post by oldfred on 2014-02-25
Unless a separate bootable device you cannot install grub to a partition. I do install grub to every drive, flash drive or just about anything. 

But if changing ISO you normally would have to edit your grub.cfg and run sudo update-grub. And I always forget the update and have to reboot to run it.
So I now use a configure file entry in grub that calls a file that I keep in the partition with my ISO. Then if I add or change an ISO I just edit config file.

This is drive 2 and partition 4 where my ISO are. Note that boot drive is always 0, and drive order may change if you have multiple drives and boot from different drives.

```
menuentry 'Live ISOs' {
configfile (hd2,4)/iso/livecdimage.cfg
} 

```

Then I create this file in the same partition as ISOs, I also use gpt partitioning so have to add that insmod.

```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;

menuentry "Ubuntu 14.04 Trusty ISO 64bit" {
    set isofile="/iso/trusty-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd0,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}


menuentry "Ubuntu 13.10 Saucy ISO 64bit" {
    set isofile="/iso/saucy-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}


menuentry "" {
set root= 
}

menuentry "Boot-Repair Disk ISO 64bit" {
    set isofile="/iso/boot-repair-disk-64bit.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 12.04 Secure Remix ISO 64bit" {
    set isofile="/iso/ubuntu-secure-remix-12.04-64bits.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by sudodus on 2014-02-25
> **DJ 1 said:**
> Do I have to have basic Ubuntu install to store the  iso(from what I've seen it's usually kept in the home folder)? 


You need grub, but no Ubuntu (not even a linux kernel). You can start from the compressed image 'grub-n-iso' (grow the partition and add bells and whistles if you like, or simply replace the current iso file with the file you want).

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_USB_drives_with_grub2_and_iso_files_.27grub-n-iso.27](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_USB_drives_with_grub2_and_iso_files_.27grub-n-iso.27)

[https://help.ubuntu.com/community/grub-n-iso](https://help.ubuntu.com/community/grub-n-iso)

---

### Post by DJ 1 on 2014-02-25
Yeah I'll have another look... 
I know grub is installed basically on the root of the hdd etc, but the config files that update &  talks to grub are contained within a linux/Ubuntu system. 
I don't have a spare primary left on the hdd, so I was hoping to to be able to boot iso from a partition that not got Ubuntu installed (just the iso, but be able to house the config files that grub talks to...?


What I hoped to do was have for example was a gparted lives iso stored on an empty partition & and let that partition be where grub2 is controlled from(changed updated etc) Inc. It's config files... 

Cheers.

---

### Post by oldfred on 2014-02-25
Unless you have another boot loader that chains to the partition, you cannot install grub to a partition. And it is not recommended to have grub installed to a partition as it does not really fit, so it converts to blocklists which are hard coded addresses. And change in grubs files on drive from an update then requires a reinstall.

Another option is to install grub to a flash drive and use the grub in that flash drive to boot the ISO on the hard drive. I normally install grub to every flash drive. I manually add my own grub.cfg and sometimes have added boot stanzas to boot my installs on my hard drives. But I normally have my ISO on flash drive then or actually also.

       Install grub2 to USB -general info, note that path for 12.10 and later to flash drive includes your $USER name
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

            Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

    
 Multiple-Boot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
Examples:
Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
Only if Linux formatted, easier with wide open permissions. 777 otherwise not normally suggested.
sudo chmod 777 -R /media/fred/PreciseInstaller/boot

---

