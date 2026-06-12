---
title: "Hard Drive mounted, but no size."
date: 2008-10-12
forum: New to Ubuntu
---

### Post by i_have_a_sempron on 2008-10-12
The only OS I have been able to use is Slax from the liveCD. I activated the Krusader module from Slax's website ad through Krusader I was able to mount my hard drive. My filesystem that was on the drive is ext3. Through Krusader when I mount my hard drive it says that there "Total Size 0." I have a Gparted Livecd but it wont but because "there is no live filesystem." Is there anyway I can fully erase the drive even though I can't find content, or amount of mem on the drive?

---

### Post by jemate18 on 2008-10-12
Please post the output of
```

df -h
```

or ```
sudo fdisk -l
```

---

### Post by i_have_a_sempron on 2008-10-12
```
root@slax:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  127M   14M  114M  11% /
httpfs                127M   14M  114M  11% /mnt/live/memory/httpfs/krusader-1.90.0.lzm
httpfs                127M   14M  114M  11% /mnt/live/memory/httpfs/pixfrogger.lzm
root@slax:~# sudo fdisk -l
bash: sudo: command not found
root@slax:~# fdisk -l

Unable to read /dev/hda
root@slax:~#        
```

Forgot I didnt need sudo.

---

### Post by jemate18 on 2008-10-12
ok here is mounting.....

if you have SATA

mount /dev/sda[1-5] /mnt      -> where 1 to 5 is your partition


if you have ATA

mount /dev/hda[1-5] /mnt         



assuming you have one hardisk and it is in the first IDE and master


if it is in the first IDE and slave, it would be sdb or hdb plus the number partition.

---

### Post by i_have_a_sempron on 2008-10-12
```
root@slax:~# mount /dev/hda1 /mnt
mount: special device /dev/hda1 does not exist
root@slax:~# mount /dev/hdb1 /mnt
mount: special device /dev/hdb1 does not exist
root@slax:~#
                     
```

---

### Post by jemate18 on 2008-10-12
> **i_have_a_sempron said:**
> ```
root@slax:~# mount /dev/hda1 /mnt
mount: special device /dev/hda1 does not exist
root@slax:~# mount /dev/hdb1 /mnt
mount: special device /dev/hdb1 does not exist
root@slax:~#
                     
```

can you post the output of
```
dmesg | grep [hs]d[a-d]

```

---

### Post by i_have_a_sempron on 2008-10-12
```
root@slax:~# dmesg | grep [hs]d[a-d]
    ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
hda: FUJITSU MHV2060AT PL, ATA DISK drive
hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
hda: UDMA/100 mode selected
hdc: TSSTcorpCDW/DVD TS-L462C, ATAPI CD/DVD-ROM drive
hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
hdc: MWDMA2 mode selected
hda: max request size: 128KiB
hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=65535/16/63
hda: cache flushes supported
 hda: hda1 hda2 <<4>hda: dma_timer_expiry: dma status == 0x21
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x01 { AddrMarkNotFound }, LBAsect=114382800, sector=114382800
hda: dma_timer_expiry: dma status == 0x21
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x01 { AddrMarkNotFound }, LBAsect=114382800, sector=114382800
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x01 { AddrMarkNotFound }, LBAsect=114382800, sector=114382800
hda: dma_timer_expiry: dma status == 0x21
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x01 { AddrMarkNotFound }, LBAsect=114382800, sector=114382800
hda: DMA disabled
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382800
Buffer I/O error on device hda, logical block 14297850
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382800
Buffer I/O error on device hda, logical block 14297850
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 1536kB Cache
hda: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: status error: error=0x01 { AddrMarkNotFound }, LBAsect=114382800, sector=117210112
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382800
Buffer I/O error on device hda2, logical block 0
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382800
Buffer I/O error on device hda2, logical block 0
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: status error: error=0x01 { AddrMarkNotFound }, LBAsect=114382800, sector=0
hda: drive not ready for command
hda: wcache flush failed!
hda: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: status error: error=0x01 { AddrMarkNotFound }, LBAsect=13719504, sector=117210112
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382800
Buffer I/O error on device hda2, logical block 0
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382800
Buffer I/O error on device hda2, logical block 0
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382799
Buffer I/O error on device hda1, logical block 114382736
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382800
Buffer I/O error on device hda2, logical block 0
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382800
Buffer I/O error on device hda2, logical block 0
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382799
Buffer I/O error on device hda1, logical block 114382736
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=114382796, sector=114382796
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382796
Buffer I/O error on device hda1, logical block 114382733
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382797
Buffer I/O error on device hda1, logical block 114382734
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382798
Buffer I/O error on device hda1, logical block 114382735
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382796
Buffer I/O error on device hda1, logical block 114382733
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382797
Buffer I/O error on device hda1, logical block 114382734
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382798
Buffer I/O error on device hda1, logical block 114382735
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382799
Buffer I/O error on device hda1, logical block 114382736
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382799
Buffer I/O error on device hda1, logical block 114382736
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382799
Buffer I/O error on device hda1, logical block 114382736
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382799
Buffer I/O error on device hda1, logical block 114382736
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=114382796, sector=114382796
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382796
Buffer I/O error on device hda1, logical block 114382733
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382797
Buffer I/O error on device hda1, logical block 114382734
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382798
Buffer I/O error on device hda1, logical block 114382735
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382799
Buffer I/O error on device hda1, logical block 114382736
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382799
Buffer I/O error on device hda1, logical block 114382736
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382800
Buffer I/O error on device hda, logical block 14297850
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
hda: irq timeout: status=0xd0 { Busy }
hda: irq timeout: status=0xd0 { Busy }
end_request: I/O error, dev hda, sector 114382800
Buffer I/O error on device hda, logical block 14297850
hda: status timeout: status=0xd0 { Busy }
hda: drive not ready for command
GFS2: path_lookup on /dev/hda1 returned error
GFS2: path_lookup on /dev/hdb1 returned error
root@slax:~#       
```

---

### Post by jemate18 on 2008-10-12
seems like you have a hard drive problem..
 In some point, at boot, Linux wasn't able to make your disk usable

---

### Post by jemate18 on 2008-10-12
Based on your output of the dmesg,

irq, ioports, and or dma are not assigned correctly to your HD......Leaving it unusable for the moment..... 

Have you tried other live CD?

---

### Post by i_have_a_sempron on 2008-10-12
When I try to boot I get Grub error 16 if that means much to you. Also, is there any way I can fix these problems without replacing my drive? It is an older IDE and I dont think I could find a rreplacement.

---

### Post by i_have_a_sempron on 2008-10-12
> **jemate18 said:**
> Based on your output of the dmesg,

irq, ioports, and or dma are not assigned correctly to your HD......Leaving it unusable for the moment..... 

Have you tried other live CD?

I've tried a couple Ubuntu disks and a gparted live disk and slax is the only one with any results other than Busybox. My knoppix disks freeze up when they try to enable dma accelration on boot up.

---

### Post by jemate18 on 2008-10-12
> **i_have_a_sempron said:**
> When I try to boot I get Grub error 16 if that means much to you. Also, is there any way I can fix these problems without replacing my drive? It is an older IDE and I dont think I could find a rreplacement.

Maybe this will help....
> [http://ubuntuforums.org/showthread.php?t=10030](http://ubuntuforums.org/showthread.php?t=10030)

running fsck might just work..

---

### Post by i_have_a_sempron on 2008-10-12
```
root@slax:~# fsck /dev/hda
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/sbin/e2fsck: Superblock invalid, trying backup blocks...
/sbin/e2fsck: Bad magic number in super-block while trying to open /dev/hda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@slax:~#        
```

---

### Post by i_have_a_sempron on 2008-10-12
```
root@slax:~# e2fsck -b 8193 /dev/hda
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/hda
Filesystem mounted or opened exclusively by another program?
root@slax:~# umount /dev/hda
umount: /dev/hda: not mounted
root@slax:~#             
```

---

### Post by i_have_a_sempron on 2008-10-12
bump

---

