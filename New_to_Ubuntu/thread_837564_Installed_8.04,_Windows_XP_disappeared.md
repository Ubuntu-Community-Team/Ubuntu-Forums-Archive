---
title: "Installed 8.04, Windows XP disappeared"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by mcalevy on 2008-06-22
I installed 8.04 on my gateway laptop, and my windows XP disappeared. Grub does not show XP as a boot option.  I reloaded XP from my gateway disk and it reloaded, so the partition is there as the C: drive. 

From other posts, I tried running the fdisk -l command and I get no listing from that command.

I need this laptop next tuesday as a windows laptop for a job.  I either have to get this running or trash the linux install.

Thanks for advance for the help

---

### Post by TeoBigusGeekus on 2008-06-22
Type in a terminal
```
sudo fdisk -l
```
(-L)
and post us its output or any error messages.

---

### Post by mcalevy on 2008-06-22
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8f6105d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             766        7671    55472445    7  HPFS/NTFS
/dev/sda2   *           1         765     6144831    b  W95 FAT32
/dev/sda3            7672        8916    10000462+  83  Linux
/dev/sda4            8917       14593    45600502+   5  Extended
/dev/sda5            8917        9165     2000061   82  Linux swap / Solaris
/dev/sda6            9166       14593    43600378+  83  Linux

Partition table entries are not in disk order

In using the xp restore tools it looks like my install changed the C: drive to D: and D: to C:

---

### Post by TeoBigusGeekus on 2008-06-23
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-20-386
root		(hd0,4)
kernel		/vmlinuz-2.6.15-20-386 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd		/initrd.img-2.6.15-20-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-20-386 (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.15-20-386 root=/dev/mapper/Ubuntu-root ro single
initrd		/initrd.img-2.6.15-20-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```


Your menu.lst will look something like that (at its end). 
Open it up for editing
```
sudo gedit /boot/grub/menu.lst
```
After the "end debian..." line add these lines
```
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
save the file and reboot.
Don't forget to post us what happened...

---

### Post by mcalevy on 2008-06-23
I inserted the code and restarted, no change.  There is still no xp option showing up in grub.

Rechecked the grub file with menu.lst, and the changes are there.

---

### Post by mcalevy on 2008-06-23
here is the fdisk listing again

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8f6105d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             766        7671    55472445    7  HPFS/NTFS
/dev/sda2   *           1         765     6144831    b  W95 FAT32
/dev/sda3            7672        8916    10000462+  83  Linux
/dev/sda4            8917       14593    45600502+   5  Extended
/dev/sda5            8917        9165     2000061   82  Linux swap / Solaris
/dev/sda6            9166       14593    43600378+  83  Linux

Partition table entries are not in disk order

---

### Post by RequinB4 on 2008-06-23
I think you need to look at the last post [here. (link)]("http://ubuntuforums.org/archive/index.php/t-120828.html")

[quote=Renton]
I have figured out the problem!

When I reinstalled Ubuntu the partition numbers got changed. I was always able to boot into Ubuntu so the grub on floppy would not have helped in this situation ( But I DO have one anyway).

Old BOOT.INI:

timeout=30
default=multi(0)disk(0)rdisk(0)partition(5)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft...

[B]New BOOT.INI:
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

Only problem was that the boot partition is NTFS and I needed windows to write to it:
/dev/hda1 * 1 19 152586 7 HPFS/NTFS

I didn't want to recompile the Kernel with NTFS write support and couldn't find a livecd with NTFS already on it. Most DOS boot disks don't have NTFS support either. Finally I found NTFS4DOS at [http://www.datapol.de/dpe/freeware/](http://www.datapol.de/dpe/freeware/)
Just installed it onto my work machine, make a bootable floppy, put the new BOOT.INI file on the floppy, rebooted with the floppy, and copied the new BOOT.INI file to the boot partition.
[/quote]

Edit:  Sef's got it right

---

### Post by Sef on 2008-06-23
The boot is in the wrong place.  It should be on sda1, which would be your XP partition.  

With the Ubuntu Live CD, do this:

Applications > Accessories > GParted

You can right click to change the boot order.  If I remember correctly, you would highlight sda1 then right click.

---

