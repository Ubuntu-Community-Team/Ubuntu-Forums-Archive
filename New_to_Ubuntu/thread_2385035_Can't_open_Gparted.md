---
title: "Can't open Gparted"
date: 2018-02-15
forum: New to Ubuntu
---

### Post by neovich on 2018-02-15
I shrinked windows disk and want put it to ubuntu partition, and can't open Gparter
I've got this error:
[COLOR=#ff0000]Assertion (metadata_length > 0) at ../../../libparted/labels/dos.c:2313 in function add_logical_part_metadata() failed.[/COLOR]

[ATTACH=CONFIG]278532[/ATTACH]

I want add unallocated partition to my current ubuntu partition, How to do it?

---

### Post by cruzer001 on 2018-02-15
I would first try a windows partition manager.  Are you running EFI?

---

### Post by oldfred on 2018-02-15
Post this:
sudo parted -l

Is Windows fast start up still on?
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by Impavidus on 2018-02-15
> **cruzer001 said:**
> I would first try a windows partition manager.  Are you running EFI?

I wouldn't expect Windows partition managers to handle Linux partitions correctly.

The error message calls it a libparted bug. Are you running gparted (or at least, attempting so) from a live disk? From you installed system it's not going to work anyway. What version of the live disk?

---

### Post by neovich on 2018-02-17
> [COLOR=#000000]Are you running gparted (or at least, attempting so) from a live disk? From you installed system it's not going to work anyway. What version of the live disk?[/COLOR]
From installed system and tried form liveCD, there ubuntu 16.04. In liveCD the same error [COLOR=#FF0000]Assertion (metadata_length > 0)... 


[/COLOR]> [COLOR=#000000]Post this:[/COLOR]
[COLOR=#000000]sudo parted -l[/COLOR]
```
neo@neo3:~$ sudo parted -lBacktrace has 14 calls on stack:
  14: /lib/x86_64-linux-gnu/libparted.so.2(ped_assert+0x44) [0x7f2723fc4e94]
  13: /lib/x86_64-linux-gnu/libparted.so.2(+0x1e4bf) [0x7f2723fd84bf]
  12: /lib/x86_64-linux-gnu/libparted.so.2(+0xf8ba) [0x7f2723fc98ba]
  11: /lib/x86_64-linux-gnu/libparted.so.2(ped_disk_add_partition+0x25f) [0x7f2723fca1af]
  10: /lib/x86_64-linux-gnu/libparted.so.2(+0x1ddaf) [0x7f2723fd7daf]
  9: /lib/x86_64-linux-gnu/libparted.so.2(+0x1de40) [0x7f2723fd7e40]
  8: /lib/x86_64-linux-gnu/libparted.so.2(+0x1dde9) [0x7f2723fd7de9]
  7: /lib/x86_64-linux-gnu/libparted.so.2(+0x1edd5) [0x7f2723fd8dd5]
  6: /lib/x86_64-linux-gnu/libparted.so.2(ped_disk_new+0x48) [0x7f2723fc9dd8]
  5: parted(+0x7353) [0x565381a28353]
  4: parted(+0x6c4b) [0x565381a27c4b]
  3: parted(main+0x13a4) [0x565381a271a4]
  2: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0) [0x7f27237a1830]
  1: parted(_start+0x29) [0x565381a271e9]




You found a bug in GNU Parted! Here's what you have to do:


Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:


Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:


    http://ftp.gnu.org/gnu/parted/


Please check this version prior to bug reporting.


If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:


    http://www.gnu.org/software/parted


for further information.


Your report should contain the version of this release (3.2)
along with the error message below, the output of


    parted DEVICE unit co print unit s print


and the following history of commands you entered.
Also include any additional information about your setup you
consider important.


Assertion (metadata_length > 0) at ../../../libparted/labels/dos.c:2313 in
function add_logical_part_metadata() failed.


Aborted (core dumped)                                                     
neo@neo3:~$ 



```

---

### Post by neovich on 2018-02-17
off hibernate and fast start in windows the same can't run gparted

---

### Post by Yellow Pasque on 2018-02-17
[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/1543704](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/1543704)

---

### Post by neovich on 2018-02-18
I used this theme [link]("https://ubuntuforums.org/showthread.php?t=2344157&page=3")

I did this command sudo gdisk -l /dev/sda

```
neo@neo3:~$ sudo gdisk -l /dev/sda[sudo] password for neo: 
GPT fdisk (gdisk) version 1.0.1


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************


Disk /dev/sda: 234441648 sectors, 111.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): C0273B92-27CE-4728-AB34-66F01A38CCF3
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 2048-sector boundaries
Total free space is 10642 sectors (5.2 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1026047   500.0 MiB   0700  Microsoft basic data
   2         1026048       113531354   53.6 GiB    0700  Microsoft basic data
   5       113534976       218720255   50.2 GiB    8300  Linux filesystem
   6       218722304       234438655   7.5 GiB     8200  Linux swap
neo@neo3:~$ 
```

Then use this: sudo fixparts /dev/sda 
```
neo@neo3:~$ sudo fixparts /dev/sdaFixParts 1.0.1


Loading MBR data from /dev/sda


MBR command (? for help): p


** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!


** Extended partitions are not displayed, but will be generated as required.


Disk size is 234441648 sectors (111.8 GiB)
MBR disk identifier: 0x4383B2B0
MBR partitions:


                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048      1026047   primary              Y      0x07
   2               1026048    113531354   primary              Y      0x07
   5             113534976    218720255   logical     Y        Y      0x83
   6             218722304    234438655   logical     Y        Y      0x82


MBR command (? for help): w


Final checks complete. About to write MBR data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!


Do you want to proceed? (Y/N): y
Done writing data!
Warning: The kernel is still using the old partition table.
The new table will be used at the next reboot or after you
run partprobe(8) or kpartx(8)
neo@neo3:~$ 
```

Afterwards I was able to run gparted and then extend partition to left site (at first you need move and then extend)
It was load long time without swap... 
When I resized partition swap disappeared somewhere, without swap ubuntu desktop load approximately 1 minute, again go to gparter using livecd (usb and button try ubuntu), there allocate space for swap, tag it like swap, then in ubuntu in file /etc/fstab we need add new UUID for swap, because there written old ID
To know what ID is we use command: sudo blkid -o list
and copy UUID to /etc/fstab. reboot and it will load very fast with swap

This is what I have sudo fdisk -l
```
neo@neo3:~$ sudo fdisk -lDisk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4383b2b0


Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048   1026047   1024000  500M  7 HPFS/NTFS/exFAT
/dev/sda2         1026048 113531354 112505307 53.7G  7 HPFS/NTFS/exFAT
/dev/sda3       113534975 234438655 120903681 57.7G  f W95 Ext'd (LBA)
/dev/sda5       113534976 218720255 105185280 50.2G 83 Linux
/dev/sda6       218722304 234438655  15716352  7.5G 82 Linux swap / Solaris




Disk /dev/sdb: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x8ec8b176


Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1        2048 625139711 625137664 298.1G  7 HPFS/NTFS/exFAT
neo@neo3:~$ 



```

sudo blkid -o list
```
neo@neo3:~$ sudo blkid -o listdevice                     fs_type     label        mount point                    UUID
-----------------------------------------------------------------------------------------------------------------------
/dev/sda1                  ntfs        &#1047;&#1072;&#1088;&#1077;&#1079;&#1077;&#1088;&#1074;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1086; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1086;&#1081; (not mounted) 140AB0D80AB0B856
/dev/sda2                  ntfs                     /mnt/CC3AB34C3AB33276          CC3AB34C3AB33276
/dev/sda5                  ext4                     /                              22395fce-78f2-4e01-b12b-279a220406b8
/dev/sda6                  swap                     [SWAP]                         a6fd5e27-b2ae-42e9-bd36-b63f379e7490
/dev/sdb1                  ntfs        New Volume   /mnt/706A77F76A77B884          706A77F76A77B884
neo@neo3:~$ 



```

file /etc/fstab
```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=22395fce-78f2-4e01-b12b-279a220406b8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a6fd5e27-b2ae-42e9-bd36-b63f379e7490 none            swap    sw              0       0
/dev/disk/by-uuid/706A77F76A77B884 /mnt/706A77F76A77B884 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=D 0 0
/dev/disk/by-uuid/CC3AB34C3AB33276 /mnt/CC3AB34C3AB33276 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=C 0 0



```

free
```
neo@neo3:~$ free              total        used        free      shared  buff/cache   available
Mem:        8074716     2072492     4272620      308132     1729604     5576604
Swap:       7858172           0     7858172
neo@neo3:~$ 
```

gparted
[ATTACH=CONFIG]278575[/ATTACH]
sudo gdisk -l /dev/sda
```
neo@neo3:~$ sudo gdisk -l /dev/sdaGPT fdisk (gdisk) version 1.0.1


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************


Disk /dev/sda: 234441648 sectors, 111.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 3D9E6A1B-93EA-4EC8-A5CE-BAF43BEF4F99
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 2048-sector boundaries
Total free space is 10642 sectors (5.2 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1026047   500.0 MiB   0700  Microsoft basic data
   2         1026048       113531354   53.6 GiB    0700  Microsoft basic data
   5       113534976       218720255   50.2 GiB    8300  Linux filesystem
   6       218722304       234438655   7.5 GiB     8200  Linux swap
neo@neo3:~$ 



```


as you see sudo gdisk -l /dev/sda show the same but now after resave data in fixparts it works well, I think there was something broken with partitions and fixparts corrected it.

---

### Post by oldfred on 2018-02-18
Do you have a newer UEFI/gpt system but installed Windows in the 35 year old BIOS/MBR configuration?
Windows 7 DVD only installs in BIOS mode with MBR and requires copy to flash drive and some file renaming to work as an UEFI installer. 

Windows has a bug, where when it converts gpt to MBR, it leaves the backup gpt partition table. Then Linux tools see both MBR and gpt and assume you must total erase drive. 
Fixparts or gdisk are the tools that correct see the error and fix it.

---

### Post by neovich on 2018-02-18
> [COLOR=#000000]Do you have a newer UEFI/gpt system but installed Windows in the 35 year old BIOS/MBR configuration?[/COLOR]
No have old BIOS and installed as always, I even don't know what is UEFI, UEFI replaces BIOS...  In my laptop installed BIOS. it's old laptop. Doesn't matter works as should be and well.

yes, fixparts helped, I changed nothing there, only run fixparts input p, save MBR w and afterwards gparted became works. Might have been some unknown errors inside.

---

### Post by bcschmerker on 2018-02-19
**Thanks for the heads up on a to-watch-out-for.**  The Hot Rod gPC™ packs three Toshiba® MQ1ABD050's and I've plans for a fourth; I've preplanned GPT on all four as part of the major dist-upgrade to 18.04-LTS.  Can GDisk make an entire disc into an extended physical partition for Universal Extensible Firmware Interface and Intel® Advanced Host Controller Interface?  I'm refining logical partition sizes for the dist-upgrade based on how the 16.04.4-LTS installation has performed, with two physical partitions per drive.

---

### Post by oldfred on 2018-02-19
@bcschmerker
If you have a specific question best to start your own thread. Since this thread is solved only those looking for answers may review it. 

With gpt you do not have MBR's primary, extended & logical partitions, they are all the same, in effect all primary.
If your drives are over 2TiB then you have to use gpt, but if BIOS boot must have bios_grub or if UEFI must have ESP - efi system partition. I always make those the first two partitions of every new drive, no matter which way I boot or if drive may only now be planned as a data drive.

---

