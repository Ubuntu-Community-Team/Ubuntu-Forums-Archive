---
title: "Strange partition"
date: 2016-10-06
forum: New to Ubuntu
---

### Post by dave6 on 2016-10-06
I had to do a file backup of my photographs as the 2tb drive in the "win7 photograph only" computer again. So I bought a 3Tb Toshiba sata drive and used this computer which is my Ubuntu unit to format the drive (down side being I _had to_ format in useless NTFS) so I done a backup of my files which are all RAW camera files, this took 3 days 6.7MB/second ( 6 point 7 ) I am still waiting for the PCI - USB3 card to arrive.

The drive is fitted inside a new caddy and I have done a copy/paste of the caddy speck at bottom of page.

As a test I plugged the thing back into the Ubuntu computer and got screen-shot 1 appear, when I clicked the OK to get of it I went Applications/system tools/preferences/disk utility and got screen-shot 2
That is supposed to be one partition of 3TB aka 2.7 Terra Bytes, you will also note the drive is in fact a Hitachi Drive ? I supposed its just a relabelled drive.......... 

What would you recommend I do, leave well alone as it works on the other computers, or re format the drive using windows which may not work 

A wee bit worried of what to do

Dave

The Drive Caddy
[SIZE=1][FONT=Arial][FONT=Arial][FONT=Arial]**Turn A 3.5&#8221; SATA Hard Drive Into A UASP-Supported USB 3.0 External Hard Drive**
The DRX-U35DUK USB 3.0 External Hard Drive Enclosure with UASP converts a 3.5inch SATA III hard drive into a portable external hard drive. The enclosure supports hard drives up to 4TB in capacity, maximizing system storage expansion and backup capabilities. The ecnlosure features high quality brushed lightweight aluminum construction which offers excellent heat dissipation abilities. The kit includes everything you need including screw driver and screws for your new hard drive (**hard drive not included**).

The bridgeboard PCB utilises the ASMedia ASM1153E third-generation USB 3.0 to SATA controller which supports SATA III 6Gbit/s connectivity and UASP, delivering optimal performance with a USB 3.0 interface for high speed data transfer whilst at the same time remaining backward compatible with USB 2.0/1.1 host connections

Point of Note
The attached Thumbnails are back to front 
[/FONT][/FONT][/FONT][/SIZE]

---

### Post by oldrocker99 on 2016-10-06
I've personally never had a problem accessing an NTFS partition of a disk, or, for that matter, a  whole NTFS disk. You might try reformatting within Windows. It [b]should]/b\ work, and might be a lot faster.

Good luck!

---

### Post by westie457 on 2016-10-06
Is the problem with the 3TB drive that has copies of the contents from the 2TB drive? Only asking to be sure your Data is already safe.

The drive might just need Windows to fix the drive with a CHKDSK.

Boot Windows then connect the problem drive, Windows will suggest a solution.

Only reformat if Windows cannot fix the drive. If you have to reformat use Easeus Partition Wizard (free) or something similar

---

### Post by mook765 on 2016-10-06
The drive does not have a partition-table and no partitions.

---

### Post by oldfred on 2016-10-06
Disks is saying unknown scheme?
Is it some proprietary partitioning? Some larger drives used that to be compatible with XP as XP did not support gpt or then very large disks.
It should be gpt, to support over 2TiB.

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

