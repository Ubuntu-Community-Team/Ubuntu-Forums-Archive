---
title: "Move grub to different HD"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by csc2ya on 2008-08-18
I'm running Ubuntu Ultimate Edition on my laptop in a dual boot configuration with Vista Ultimate.

I've got Vista installed on the internal drive, and Ubuntu plus grub on an external USB drive. The way it is set up at the moment, I cannot boot at all unless my external drive is connected and switched on.

However the last few days, the external drive has been having trouble spinning up when booting into Ubuntu. I can usually get it working by turning the drive on and off a few times, but i'm starting to think the drive might be on it's way out.

In case it does go, I want to move grub onto my laptop's internal drive, but i'm unsure how to do this.

The current partition scheme on both of the drives is as follows:

```
administrator@WinServ-Laptop:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x53afd72e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        6383    49732422    7  HPFS/NTFS
/dev/sda3            6384       12161    46411785    5  Extended
/dev/sda5           11920       12161     1943833+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000271e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29648   238147528+  83  Linux
/dev/sdb2           29649       30401     6048472+   5  Extended
/dev/sdb5           29649       30401     6048441   82  Linux swap / Solaris

```

The current grub configuration for both operating systems is:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f3018b0e-e23d-4258-9193-19806d2398fc ro splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f3018b0e-e23d-4258-9193-19806d2398fc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f3018b0e-e23d-4258-9193-19806d2398fc ro splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f3018b0e-e23d-4258-9193-19806d2398fc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Is it possible someone could point me to the commands I would need to enter to move grub, and still have everything bootable.

Thanks in advance.

---

### Post by markbuntu on 2008-08-18
You can change the boot parameters in your bios to boot the internal drive first and put grub on that drive with the live cd. It will overwrite the vista boot and vista may complain about that and try to fix it. There are some other threads around here about dual booting with vista that cover that issue, You shoud do a search for them.

---

### Post by unutbu on 2008-08-18
csc2ya, making your boot process independent of the external drive requires that you make a /boot (or /boot/grub) partition on your internal drive. 
As you can see below, the procedure is long and complicated.
After writing this up, I have reservations about recommending it.

If you follow the instructions below and your external drive were to fail, 
you would be able to boot Windows, but you would obviously lose Ubuntu anyway.

If you instead followed a regular routine of backing up, and do NOT use the instructions below, and your external drive fails, then all you would have to do is pop a Windows recovery CD into the machine, and reinstall the Vista bootloader to the MBR. (See "How to restore Vista MBR": [http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)). This is better because it is less complicated, achieves the same result, and you don't have to waste space on a /grub partition on your internal drive.

Anyway, to give you an idea of how complicated the procedure is, here is what I originally wrote up:

----------------------------------------------------------------------
There is a guide on the web to do this [http://tekguru.wordpress.com/2007/09/04/howto-moving-boot-to-its-own-partition/](http://tekguru.wordpress.com/2007/09/04/howto-moving-boot-to-its-own-partition/).
Look through the web guide. Maybe that is all you need. 

Below is essentially the same thing, perhaps a bit more tailored to your situation. (Note, the following instructions carve out some space from /dev/sda5 to make a /boot partition on your internal hard drive.)

[list=1]
[*]Read through all of these instructions before beginning. If you have any questions, post before you begin.
[*]Note that if your external drive fails, the following instructions will allow you to continue booting Windows, but you won't be able to boot Ubuntu.
[*]Boot from the Live CD
[*]Run GParted (System>Administration>Partition Editor)
[*]Resize the /dev/sda5 linux swap partition.
[*]Create a 20MB ext3 partition. Make sure you format it to be an ext3 filesystem.
[*]Note the device name of this new ext3 partition. If it is not /dev/sda6, stop here, and post the name of the partition. I'll then modify these instructions as needed.
[*]Click Apply, then exit GParted
[*]Open a terminal and type
```

sudo mount /dev/sda6 /mnt
sudo mkdir -p /mnt/boot/grub
sudo grub-install --root-directory=/mnt /dev/sda

sudo mkdir /Ubuntu
sudo mount /dev/sdb1 /Ubuntu
sudo mkdir /Ubuntu/sda6
sudo cp /Ubuntu/boot/grub/menu.lst /mnt/boot/grub/
blkid

```
The output will contain something like this:
```
/dev/sda6: UUID="33b7e11e-5bdb-4e98-b626-671b1c4d18eb" TYPE="ext3" 
```
Note the UUID.
[*]```
gksu gedit /etc/fstab
```
Add this line to the end: (change the UUID to the UUID (for /dev/sda6) that you found in the output of blkid)
```
UUID=33b7e11e-5bdb-4e98-b626-671b1c4d18eb /sda6 ext3 ro 0 2
```
Save.
[*]Now (still in gedit) open /mnt/boot/grub/menu.lst
Change (hd1,0) to (hd0,5)
Change /boot to (hd1,0)/boot

```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		(hd1,0)/boot/vmlinuz-2.6.24-19-generic root=UUID=f3018b0e-e23d-4258-9193-19806d2398fc ro splash
initrd		(hd1,0)/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		(hd1,0)/boot/vmlinuz-2.6.24-19-generic root=UUID=f3018b0e-e23d-4258-9193-19806d2398fc ro single
initrd		(hd1,0)/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		(hd1,0)/boot/vmlinuz-2.6.24-16-generic root=UUID=f3018b0e-e23d-4258-9193-19806d2398fc ro splash
initrd		(hd1,0)/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		(hd1,0)/boot/vmlinuz-2.6.24-16-generic root=UUID=f3018b0e-e23d-4258-9193-19806d2398fc ro single
initrd		(hd1,0)/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		(hd1,0)/boot/memtest86+.bin
quiet
```
[*]Also change ```

# groot=(hd1,0)     # Or whatever you have here

```
to```

# groot=(hd0,5)
```

[*]Save and quit gedit.
[*]If necessary, change your BIOS boot order so the internal drive gets booted before the external drive.
[*]Reboot to Ubuntu now using the GRUB partition installed at /dev/sda6.
[*]Type```

mv /boot/grub /boot/grub-old
ln -sf /sda6/boot/grub /boot/grub

```[/list]

---

### Post by caljohnsmith on 2008-08-19
I think its great you took the time to write up such a complete guide, unutbu, :) but just for my own understanding, I have few questions that I hope you have time to clarify for me:
> **unutbu said:**
> 
[list]
[*]Boot from the Live CD
...
[*]Open a terminal and type:
```
sudo mkdir /newboot
sudo mount /dev/sda6 /newboot    
sudo cp -a /boot/* /newboot
sudo mv /boot /oldboot
sudo umount /newboot
sudo mount /dev/sda6 /boot
blkid
```[/list]
If I understand correctly, the above would recursively copy all the folders/files *in the Live CD's /boot directory* over to the new sda6 partition. After that, the /boot folder on the Live CD is moved over to a new location "oldboot", and the sda6 partition is mounted back with /boot as its mount point. I guess I'm missing something, because can you explain what the purpose of that is? If this is all done from a Live CD, he will lose that mount point as soon as he does a shutdown/restart. Also, on my Ubuntu Live CD, the /boot folder looks like:
total 10075
```
-rw-r--r-- 1 root root  424317 2007-10-15 01:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root   75311 2007-10-15 01:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root 7124250 2007-10-15 23:26 initrd.img-2.6.22-14-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root  823535 2007-10-15 01:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root 1764280 2007-10-15 01:39 vmlinuz-2.6.22-14-generic
```
So the Live CD's /boot folder doesn't have the grub folder with all its configuration files in it. So please clarify, but how will copying that /boot folder over to sda6 enable him to use Grub from sda6? 
> **unutbu said:**
> Create a 200MB ext3 partition. Make sure you format it to be an ext3 filesystem.
Just thought I would mention that in my experience, you can make the dedicated Grub partition just 20 MB and you'll still have plenty of room, so long as you don't decide to put alot of Grub splash images on that partition, or maybe use gfxboot or something. :) Also, it seems like ext2 would be a better choice of file system in this case since it uses less overhead than ext3, and I wouldn't think that you would need the advanced journaling features of ext3 for a dinky 20 MB grub partition with just a few files.

To install Grub to its own dedicated partition, I think the safest way is to use "grub-install" with the "--root-directory" option, because grub-install will not only create all the necessary config files, but it will also generate a device.map that is relevant to the person's particular HDD setup; at least that is how I created my own dedicated grub partition. In other words, once the dedicated Grub partition is created (say sda6), to install Grub to it is as simple as:
```
sudo mount /dev/sda6 /mnt
sudo mkdir -p /mnt/boot/grub
sudo grub-install --root-directory=/mnt /dev/sdX
```
Where sdX would be sda if you want Grub installed to the MBR of the same HDD that sda6 is on, or you can specify a different HDD. The only thing grub-install doesn't do is create a menu.lst. As I'm sure you all ready know, that can be done with update-grub, or by just copying over a working one.

---

### Post by unutbu on 2008-08-19
caljohnsmith, thank you very much for reading over my post and catching some errors! I'm going to edit my previous post; please post if you see any more problems.

[list=1]
[*]> 
the above would recursively copy all the folders/files in the Live CD's /boot directory over to the new sda6 partition

You are right -- my commands for copying /boot copy from the LiveCD when I meant to copy from the Ubuntu /boot on /dev/sdb1.
[*]
> 
you can make the dedicated Grub partition

Yes, my original instructions moves /boot, when really it is only /boot/grub that needs to be moved. I'm editing my instructions to make a /grub partition now. Please tell me if you find a mistake here.

[*]
> 
make the dedicated Grub partition just 20 MB and you'll still have plenty of room

Good point. I recently tried to help a guy who had a +150MB /boot because of all the kernel upgrades, so I was trying to be generous with my allocation. However, if we make a /grub partition, I agree it could be much smaller.
[*]
> 
ext2 would be a better choice

I think I read somewhere that when an ext3 partition is sync'ed or cleanly unmounted, all transactions recorded in the journal are written to disk and the journal is shrunk to 0 size. So during normal operation the ext3 journaling costs you almost nothing. I could be wrong about this though...
[*]
> 
I think the safest way is to use "grub-install" with the "--root-directory" option

I have been reluctant to suggest grub-install except when all else fails because of this

[http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall)
> 
Caution: This procedure is definitely less safe, because there are several ways in which your computer can become unbootable. For example, most operating systems don't tell GRUB how to map BIOS drives to OS devices correctly&#8212;GRUB merely guesses the mapping. This will succeed in most cases, but not always.

I really don't understand this warning however. Here are some reasons which I think you are right to suggest grub-install:
[list]
[*]Doesn't "setup (hd0)" shoulder the same risk? 
[*]I've noticed "grub-install (hd0)" is the command Hardy's LiveCD uses to install GRUB on the MBR
[*]The guide [http://tekguru.wordpress.com/2007/09/04/howto-moving-boot-to-its-own-partition/](http://tekguru.wordpress.com/2007/09/04/howto-moving-boot-to-its-own-partition/) also uses grub-install.
[*]As long as you can boot from a LiveCD, you should be able to fix GRUB, right?
[/list]
Ok, you've convinced me. I'll change my instructions to use grub-install.
[/list]
Thanks again for sharing your thoughts and catching my errors. I really appreciate it.

---

### Post by Rumel on 2008-08-19
You need to reinstall grub to the MBR of your internal hard drive. I've done something like this recently with a flash drive.

---

### Post by caljohnsmith on 2008-08-19
> **unutbu said:**
> 
I think I read somewhere that when an ext3 partition is sync'ed or cleanly unmounted, all transactions recorded in the journal are written to disk and the journal is shrunk to 0 size. So during normal operation the ext3 journaling costs you almost nothing. I could be wrong about this though...

I'm glad you mentioned that, because I've never delved into the technicalities of ext3's journaling, so I didn't realize that ext3 probably wouldn't cost any extra space in this case. Might as well use ext3 then. :)
> **unutbu said:**
> 
I have been reluctant to suggest grub-install except when all else fails because of this

[http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall)
> Caution: This procedure is definitely less safe, because there are several ways in which your computer can become unbootable. [COLOR="Blue"]For example, most operating systems don't tell GRUB how to map BIOS drives to OS devices correctly&#8212;GRUB merely guesses the mapping. This will succeed in most cases, but not always.[/COLOR]
I really don't understand this warning however.

I have never understood that either when I read it, because saying "Grub merely guesses the mapping" is what Grub *always* has to do at some point when Grub is installed.
> **unutbu said:**
> 
Here are some reasons which I think you are right to suggest grub-install:
[list]
[*]Doesn't "setup (hd0)" shoulder the same risk? 
[/list]
Actually it doesn't in the sense that "setup (hd0)" merely installs Grub's stage1 file to the MBR, and also installs Grub's stage1.5 file to the sectors immediately after the MBR, if I remember correctly. So it does not modify the /boot/grub/device.map, nor will it create one. "setup (hd0)" assumes that all of Grub's config files in /boot/grub all ready exist.

One thing I am certain of is that setup (hd0) *does not* create any of Grub's config files in /boot/grub if they don't exist, such as the stage2 file it needs nor the device.map file. That is the difference between using the Grub CLI "setup (hdX)" method vs. grub-install: grub-install does exactly what "setup (hdX)" does, but *in addition* it will create the necessary configuration files /boot/grub if they don't all ready exist (everything except menu.lst as I noted before). 

Also, I have found from experience that if "grub-install" ever returns a BIOS error complaining about HDD order or similar, then 90% of the time you can get it to work by adding the "recheck" option to grub-install:
```
sudo grub-install --root-directory=/mnt /dev/sdX [COLOR="Blue"]--recheck[/COLOR]

```
That option forces grub-install to probe for drives and create a new device.map even if it all ready exists.
> **unutbu said:**
> 
As long as you can boot from a LiveCD, you should be able to fix GRUB, right?

Yes, that has always been my experience; you never have to download and use something like Super Grub Disk unless you want to--all Grub problems I've come across can be resolved from a Live CD. But of course the Super Grub Disk is easier for beginners to use. :)

---

