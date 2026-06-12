---
title: "I can't burn data files in DVD"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by kmisad on 2013-10-23
Since some time now, I can't succeed burning CD or DVD
Some of those times the system doesn't even rcgnise that there is a CD or DV inside...
last it happend it was this resalt below.

Can someone undertand and explaine me?





Devices
-----------------------
Optiarc DVD RW AD-7593A 1.05 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 2049302 (4196970496 bytes)

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.8.5 (4.8.5)
QT Version:  4.8.1
Kernel:      3.2.0-54-generic

Used versions
-----------------------
mkisofs: 1.1.11
cdrecord: 1.1.11

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.11
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'Optiarc '
Identification : 'DVD RW AD-7593A '
Revision       : '1.05'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) (current)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1277952 = 1248 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 11080 KB/s
Track 01: data  4002 MB        
Total size:     4596 MB (455:24.02) = 2049302 sectors
Lout start:     4597 MB (455:26/02) = 2049302 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 249194
Starting to write CD/DVD at speed   8.0 in real SAO mode for multi session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Starting new track at sector: 0
Track 01:    0 of 4002 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.017s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   26.444s
Average write speed 111.0x.
Fixating...
Fixating time:    0.004s
/usr/bin/wodim: fifo had 192 puts and 1 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=8 -sao driveropts=burnfree -multi -data -tsize=2049302s -

mkisofs
-----------------------
2049302
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using PEUGEOT_COUPE_1000.PNG;1 for  My work/My Drawings/Peugeot_Coupe_1.png (Peugeot_coupe_1.png)
Using _______________________0000.JPG;1 for  My work/Originals/&#928;&#961;&#969;&#964;&#959;&#967;&#961;&#959;&#957;&#953;&#945; 08 129.jpg (&#928;&#961;&#969;&#964;&#959;&#967;&#961;&#959;&#957;&#953;&#945; 08 119.jpg)
Using _______________________000.JPEG;1 for  My work/Photography/Black &White/&#931;&#967;&#959;&#953;&#957;&#959;&#973;&#963;&#945;_&#967;&#969;&#961;&#953;&#954;&#972;&#962;_01.jpeg (&#924;&#949;&#963;&#945; &#945;&#960;&#959; &#964;&#959; &#954;&#945;&#961;&#945;&#946;&#953;_01_noir_blanc.jpeg)
Using NAFPLION_OLD_TRAIN_STATI000.JPG;1 for  My work/Photography/Black &White/Nafplion_old_train_station_hue_sat.jpg (Nafplion_old_train_station_b&w_sep_light_&_shadows.jpg)
Using B_W_01000.JPG;1 for  My work/Photography/Black &White/b&w_01.JPG (B&W_01.JPG)
Using _______________________0000.JPG;1 for  My work/Photography/Collection_01/&#928;&#961;&#969;&#964;&#959;&#967;&#961;&#959;&#957;&#953;&#945; 08 287.jpg (&#928;&#961;&#969;&#964;&#959;&#967;&#961;&#959;&#957;&#953;&#945; 08 279.jpg)
Using _______________________0001.JPG;1 for  My work/Photography/Collection_01/&#928;&#961;&#969;&#964;&#959;&#967;&#961;&#959;&#957;&#953;&#945; 08 279.jpg (&#928;&#961;&#969;&#964;&#959;&#967;&#961;&#959;&#957;&#953;&#945; 08 274.jpg)
Using _______________________B000.JPG;1 for  My work/Photography/Collection_01/&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_05.jpg (&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_04.jpg)
Using _______________________B001.JPG;1 for  My work/Photography/Collection_01/&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_04.jpg (&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_03.jpg)
Using _______________________B002.JPG;1 for  My work/Photography/Collection_01/&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_03.jpg (&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_02.jpg)
Using _______________________B003.JPG;1 for  My work/Photography/Collection_01/&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_02.jpg (&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_01.jpg)
Using NAFPLION_OLD_TRAIN_STATI000.JPG;1 for  My work/Photography/Collection_01/Nafplion_old_train_station_hue_sat.jpg (Nafplion_old_train_station_b&w_sep_light_&_shadows.jpg)
Using _______________________B000.JPG;1 for  My work/Photography/eikonostassia/&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;&#945;_b&w/&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_05.jpg (&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_04.jpg)
Using _______________________B001.JPG;1 for  My work/Photography/eikonostassia/&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;&#945;_b&w/&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_04.jpg (&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_03.jpg)
Using _______________________B002.JPG;1 for  My work/Photography/eikonostassia/&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;&#945;_b&w/&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_03.jpg (&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_02.jpg)
Using _______________________B003.JPG;1 for  My work/Photography/eikonostassia/&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;&#945;_b&w/&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_02.jpg (&#917;&#953;&#954;&#959;&#957;&#959;&#963;&#964;&#940;&#963;&#953;_b&w_01.jpg)
Using FLYER_IN_PAGE_1_DUOTONE_000.SVG;1 for  My work/Photography/Exposition flyer/Flyer_in_page_1_duotone_sharpen_more_bloom_dark_glass.svg (Flyer_in_page_1_duotone_sharpen_more.svg)
Using FLYER_5_DUOTONE_SHARPEN_000.SVG;1 for  My work/Photography/Exposition flyer/Flyer_5_duotone_sharpen_bloom_colorise.svg (Flyer_5_duotone_sharpen_bloom.svg)
Using NOUVELLE_MAISON_02_SCENE000.SKP;1 for  My work/sketch up/Nouvelle maison_02 Scene _01_Sketchy.skp (Nouvelle maison_02 Scene _01.skp)
Using BUFFET_BOXES_01_METAL_RE000.JPG;1 for  My work/sketch up/buffet_boxes_01_metal_red_simple_jpeg.jpg (buffet_boxes_01_metal_red_simple.jpg)
  0.02% done, estimate finish Mon Oct 21 18:50:59 2013
  0.05% done, estimate finish Mon Oct 21 17:09:08 2013
  0.07% done, estimate finish Mon Oct 21 16:36:12 2013
  0.10% done, estimate finish Mon Oct 21 16:19:17 2013
  0.12% done, estimate finish Mon Oct 21 16:08:51 2013
  0.15% done, estimate finish Mon Oct 21 16:02:14 2013
  0.17% done, estimate finish Mon Oct 21 16:06:59 2013
  0.20% done, estimate finish Mon Oct 21 16:02:13 2013
  0.22% done, estimate finish Mon Oct 21 15:58:20 2013
  0.24% done, estimate finish Mon Oct 21 15:55:20 2013
  0.27% done, estimate finish Mon Oct 21 15:52:53 2013
  0.29% done, estimate finish Mon Oct 21 15:50:50 2013

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid My work -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-kmisad/k3bHZ5523.tmp -rational-rock -hide-list /tmp/kde-kmisad/k3bwD5523.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-kmisad/k3bWr5523.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-kmisad/k3bBz5523.tmp

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid My work -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-kmisad/k3bEV5523.tmp -rational-rock -hide-list /tmp/kde-kmisad/k3brc5523.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-kmisad/k3bYM5523.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-kmisad/k3bll5523.tmp

---

