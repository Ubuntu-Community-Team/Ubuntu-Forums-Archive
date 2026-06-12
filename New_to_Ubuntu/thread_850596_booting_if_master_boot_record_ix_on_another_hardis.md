---
title: "booting if master boot record ix on another hardisk"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by amit.padhy on 2008-07-05
Hello everyone!!!

I had two hard disks-40GB and 160GB but lately the 40GB hard disk got damaged(i dont know how!!) which had the Master Boot Record and had the windows OS.But my Linux filesystem is on the 160Gb hard drive.but i am not sure about the swap partition. The other partitions on my 160GB hard drive are ntfs.

now that i am accesing internet from the live CD inserted in my CD-drive,
is it possible to say restore the normal boot procees without re-installing ubuntu again???I mean say by making some changes in the MBR ???

---

### Post by logos34 on 2008-07-05
install grub to the 160gb:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

mount your root partition and navigate to /boot/grub/menu.lst

gksudo gedit /media/disk/boot/grub/menu.lst 
(or whatever the exact path is)

change 'groot' and 'root' lines from (hd1,?) to (hd**0**,?)

tben reboot, go into the bios and change the 160 gb to first in the hard disk boot order

---

### Post by amit.padhy on 2008-07-05
there is already grub on my 160 Gb hard disk in the location /media/disk/boot.
do i need to install it again?

---

### Post by kansasnoob on 2008-07-05
> **amit.padhy said:**
> there is already grub on my 160 Gb hard disk in the location /media/disk/boot.
do i need to install it again?

Well what happens when you try to boot with the damaged drive removed?

---

### Post by logos34 on 2008-07-05
grub is installed, but there's a small file you need on the mbr of the boot disk.  The line

grub> setup (hd1)

writes it to the mbr of the 160 gb disk (only the other disk's mbr has grub on it now).  Then you'll change the boot order in the bios and boot from the 160 gb.

---

### Post by kansasnoob on 2008-07-05
> **logos34 said:**
> grub is installed, but there's a small file you need on the mbr of the boot disk.  The line

grub> setup (hd1)

writes it to the mbr of the 160 gb disk (only the other disk's mbr has grub on it now).  Then you'll change the boot order in the bios and boot from the 160 gb.

I'm not disagreeing but just curious how you know that it's HD1? I think it depends on which OS was installed last?????

---

### Post by bodhi.zazen on 2008-07-05
> **kansasnoob said:**
> I'm not disagreeing but just curious how you know that it's HD1? I think it depends on which OS was installed last?????

no, it depends on your hardware configuration ...

master = hd0
slave = hd1

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

Now the designation may change when you change your hardware (by pulling the defective drive).

---

### Post by kansasnoob on 2008-07-05
> **bodhi.zazen said:**
> no, it depends on your hardware configuration ...

master = hd0
slave = hd1

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

Now the designation may change when you change your hardware (by pulling the defective drive).

I always like creating a "map" (in black and white) of my drives and partitions before I start by booting either the Ubuntu Live Cd or a GParted live cd just so I have all the numbers written down.

Like imagine for a minute that you have a very basic, simple dual boot with no shared partitions. Could numbers be skipped?

Like this:

[ATTACH]76570[/ATTACH]

Why no SDA 3 or 4?

And, while it's odd, I've run into instances where separate drives are not recognized simply as drive #1 being hd or sd (0), or second hard drives being recognized as either hd or sd (1).

I probably did a butt poor job of explaining myself, but I have run into trouble with typical GRUB numbering if things have been removed and/or replaced.

My advice is to "map" everything and then deal with GRUB.

---

### Post by logos34 on 2008-07-05
> **bodhi.zazen said:**
> no, it depends on your hardware configuration ...

master = hd0
slave = hd1



Almost...You're confusing that with how fdisk sees IDE drives:

/dev/hda - Primary Master
/dev/hdb - Primary Slave
/dev/hdc - Secondary Master
/dev/hdd - Secondary Slave

(SATA's are all 'master' on their own channel, and are recognized differently)

But grub sees drives as 'hd_', according to their Bios boot order (unless it's a mixed IDE and SATA setup, in which case grub usually numbers the IDE drive(s) ahead of the sata regardless of the actual Bios order).  'hd0' is the boot drive, 'hd1', second in order, 'hd2' the third, etc.  The /boot/grub/device.map lists the order the hard drives are recognized in at installation.    

So in this case, since the windows disk is the boot drive (where grub stage1 is--mbr), then it's hd0, and the ubuntu disk hd1.  Unless he's already changed the bios boot order

---

### Post by logos34 on 2008-07-05
> **kansasnoob said:**
> Why no SDA 3 or 4?

Because logical partitions start numbering at '5'.  This is to avoid confusion since there is a limit of 4 primary partitions allowed on a disk, and #'s 1-4 are reserved for those, or 3 primaries + 1 extended).  See the partitions howto over at [www.tldp.org]("http://www.tldp.org")

>  And, while it's odd, I've run into instances where separate drives are not recognized simply as drive #1 being hd or sd (0), or second hard drives being recognized as either hd or sd (1).You're mixing apples and oranges.  Grub sees ALL drives as 'hd_' (again, according to bios boot order), but the linux OS sees IDE as 'hdx' and everything else (scsi, sata, USB, etc.) as 'sdx', where x=drive letter.  However this also depends on the storage driver used: Ubuntu has switched to the libata scsi driver (since Feisty), so it sees even IDE drives as 'sdx'.


ADD: But frankly it is confusing to have to deal with two different drive nomenclatures, and I wish they had tweaked GNU grub 0.97 to avoid this problem, as well as not always default to the IDE drive during installation.  Maybe Grub2 (still under development) will offer improvements in this area. And the change to the libata driver in ubuntu caused more confusion: suddenly people whose drives had previously been showing up as 'hda' or whatever switched to 'sda'...Add to this the fact that the change did not necessarily occur in a consistent manner: whether or not your drive designation switched to 'sda' depends apparently also depends on the order the storage modules are loaded at boot.  I can attest to this: I was expecting it to change back in Feisty, but had to wait to the Hardy release before my IDE drive was recognized as 'sda', all because of the order the modules loaded on my setup.

---

