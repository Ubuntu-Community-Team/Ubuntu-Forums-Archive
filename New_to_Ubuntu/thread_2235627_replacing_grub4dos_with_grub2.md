---
title: "replacing grub4dos with grub2"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by wimpy2 on 2014-07-22
This PC has a dual-booting system with Win XP Pro SP3 and Lubuntu 14.04, which is controlled by grub4dos. The system has no IDE drives just a SATA HDD and a SATA DVD-ROM. The motherboard has 2xSATA outlets which are dedicated to RAID. The HDD and the DVD-ROM are connected to the RAID outlets. The RAID controller allows JBOD and the BIOS will boot from that HDD. 
However, although it registers the DVD-ROM it will not offer it as a boot option. For normal working this is OK - both Windows and Lubuntu "see" the DVD-ROM and can read and write to it. I've tried to find a way of booting from the DVD through grub4dos, without success. 
Recently, I came across a statement that booting the DVD-ROM could be done from grub2. The statement contained some code which could be added to the grub2 configuration. At present grub4dos's menu.lst and other files are on the first partition's root directory, which is an NTFS one containing the Windows installation. Is it possible to replace grub4dos with grub2 so I can check out the possibility of booting the DVD-ROM?
Any help or suggestions would be greatly appreciated.

---

### Post by yancek on 2014-07-22
Are you referring to somethig like what is described in the link below, in the 8 year old tutorial?  This link is talking about Grub Legacy but it could be modified to be used with Grub2.

[http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/](http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/)

Or are you referring to booting an iso directly from a Linux partition as described below.  You can do something similar with Grub Legacy but need to etract the files and copy them to your partition first.

[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

It seems pretty strange that you can use the DVD player from your systems but no boot from it!!

---

### Post by wimpy2 on 2014-07-22
Thanks for the reply. The first link is in fact the one I found. The BIOS identifies the DVDROM as "ATAPI iHas124 E" during Boot up, but the Raid setup only sees the SATA HDD. The only boot options are FDD, USB-FDD, and the SATA HDD. There is a separate option  in the BIOS to enable booting from SATA RAID and this is set to "Enable". I had hoped to get grub4dos to boot the CD but I haven't found out how to designate it in menu.lst. (hd1,0) doesn't work. It would be nice if one could put grub4dos to the command line and ask it what drives it "sees". :)
For me, the main advantage of a bootable CD is the possibility of doing a Disk Rescue. At present, this would mean installing an IDE DVD-ROM. I have not yet found a plausible use of the USB-FDD boot option.

---

### Post by oldfred on 2014-07-22
I do not understand two SATA ports as RAID, but one is a DVD. RAID needs multiple drives, it seems you are not really using RAID??

Can you turn RAID off and use AHCI or even IDE in BIOS?

I have just installed grub2 to FAT32, NTFS, and Linux formatted partitions. On the install to NTFS it was a Windows repair flash drive and I had to make sure grub did not create a second /boot. Windows 7 has a /Boot and in NTFS case does not matter, but duplicates are not allowed. With Linux case does matter so /boot is not /Boot. 
I have not tried with my old XP install, but would expect it to work. But do not modify the NTFS partition boot sector(PBR). You can from inside the NTFS partition use grub to chain to the NTFS PBR and then Windows boots.

---

### Post by wimpy2 on 2014-07-22
The motherboard only has 2x SATA outlets. I have connected one to a SATA HDD and the other to a SATA DVD. The VIA8237 RAID controller will accept HDDs as JBOD (Just a Bunch Of Disks), without needing to set up a RAID. It's useful for installing any OS to a PC with a single SATA HDD. In this case I've used the second outlet by connecting it to a SATA DVD-ROM. Since the only HDD is a SATA drive, there is nothing connected to the 2xIDE outlets. The Windows is XP Pro SP3. As far as I know XP does not have a /boot directory. In the C:\ directory, there are some files which I presume grub4dos has placed - menu.lst, grldr and memdisk.bin. From my reading, I understand that grub4dos also alters the mbr.
There are other partitions, which I didn't think would be relevant. One contains a frugal installation of puppy Linux Lucid 5.2.8, which supplied the grub4dos. When I installed Lubuntu, I chose to have its bootloader put on an USB stick, so that it would not interfere with the grub4dos bootloader. Grub4Dos was run again and found Lubuntu and that is the current position.
As I said, apart from being unable to boot from this DVD-ROM, all the other systems acknowledge its presence and can use it. Windows just calls it a SCSI DVD ROM, Lubuntu has it as /dev/cdrom, and identifies it via lshw just as recorded in the BIOS - ATAPI iHas.... It would be useful to know how grub4dos refers to it.
If there is any more information required I'll do my best to supply it.

---

### Post by yancek on 2014-07-22
What are you trying to boot from the DVD?  If it's an iso of a bootable system, you can boot it with Grub, either Grub Legacy or Grub2.  With Grub Legacy, you need to extract it.  Also, Grub2 won't boot just any iso directly.

---

### Post by wimpy2 on 2014-07-22
Ignore this.  It was a duplicate of another post.  I must have clicked "submit" when I meant "preview".

---

### Post by wimpy2 on 2014-07-22
I suppose the only iso I would like to be able to boot would be a rescue CD. I would be prepared to construct it any way which would be acceptable to the bootloader. It is not that important. These systems are old and the hardware should not last very much longer. If it can't be done, I would accept it and move on.

---

### Post by oldfred on 2014-07-22
In my list of entries I have this, but never have used it. You can add it to 40_custom in grub2.

```
 # Boot whatever is in the CD drive
menuentry "CD on (sr0)" {

 insmod udf
set root= (sr0)
chainloader +1

 }
```

If you have Lubuntu you should just be able to install grub2.
Boot-Repair may do it automatically if desired.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You may not even have to do purge.

 # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

      
 gksudo gedit /etc/grub.d/40_custom

 #update grub menu after any change
sudo update-grub

---

### Post by wimpy2 on 2014-07-22
Thanks. I'll have a go at that. This is being written on an all linux machine because the previous PC's PS2 keyboard socket has stopped working. I'll get hold pf a USB keyboard and report back, later. Hopefully, I'll  be able to mark this thread as "solved"
My thanks to everyone who replied.

---

### Post by wimpy2 on 2014-07-25
@oldfred I've installed grub2 on the Linux only machine (previously used grub4dos). All the OSes, like lubuntu and the various frugal installed puppies, load fine, though a bit slower than under grub4dos. Grub did warn about a possible failure because of the distance along the disk to the grub files, and even hinted at the possibility that it wouldn't work at all. It suggested making a small partition at the start of the disk for the grub boot loader. I'll have a think about that. However, using your code, it will not boot what's in the DVDROM - says it cannot find sr0. How can I find out what grub2 calls the DVDROM?

UPDATE: There is another method referenced in a few websites, which involves memdisk.bin and sbootmgr.dsk.
I added the following code to /boot/grub/custom.cfg (lubuntu is on sda2):
> menuentry "CDROM" {
insmod ext4
set root='(hd0,1)'
linux /boot/grub/memdisk.bin
initrd /boot/grub/sbootmgr.dsk
}


It fiddled around and then re-booted :(

---

### Post by oldfred on 2014-07-25
Perhaps it also needs:
insmod iso9660

Grub has many insmod files, but I cannot find much documentation on what each does other and looking at the name.

Why boot from grub to CD/DVD? You should be able to use one time boot key or BIOS.

I now find I only use DVD to make image backups of my most important files. I use flash drive for lots of data now and directly boot my install ISO with grub from hard drive.

 Sometimes plop will work to boot other things:
[URL="http://www.plop.at/en/bootmanagers.html"]http://www.plop.at/en/bootmanagers.html

[/URL] menuentry "Plop Boot Manager"{
set root ='(hd0,1)'
linux16 /boot/plpbt.bin
}

[URL="http://www.plop.at/en/bootmanagers.html"]
[/URL]

---

### Post by wimpy2 on 2014-07-25
I think I'll just pass on this, and accept that it can't be done. The only reason for perservering with grub2 was to be able to boot a CD from it. If it can't do it, I'll just revert back to grub4dos, which seems to be a lot quicker, on this system. 
Thanks again for all your help and suggestions.  I'll just keep reading and learning.

---

