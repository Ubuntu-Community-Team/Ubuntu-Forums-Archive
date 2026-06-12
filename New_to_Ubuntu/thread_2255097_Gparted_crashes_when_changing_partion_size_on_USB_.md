---
title: "Gparted crashes when changing partion size on USB Disk-on-key"
date: 2014-12-02
forum: New to Ubuntu
---

### Post by lavikl on 2014-12-02
Hi Everyone,
I have a Disk-on-key USB flashdrive which I installed Ubuntu 14.04 on it.
I've been trying to change the persistent settings by following a post (2nd in the following link):
[http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb](http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb)

I did all the neccessary changes in Gparted but when I clicked the green "V" mark, Gparted halts and terminates itself without doing any changes to the USB drive. There's no error message when its crashing. I then tried to break the process into two pieces, first changing the size of the partion and clicking "V", and it crashes at this point.

I'm running the process from my PC using a fresh install of Ubuntu 14.04.1, after updating the system files (apt-get update and install), and after I've removed Gparted and installed it again to make sure I have the latest version.

Did anyone encouter this error ? Can anyone recommend an alternative to Gparted for this purpose (change partition size, reformart a new partition etc.) ?

Thanks !
Adi

---

### Post by sudodus on 2014-12-02
- Are you booting from another system or from the same system as the one you are trying to modify? You should boot from another system.

- Have you unmounted the partition(s) that you are trying to modify?

- Have you tried to repair the file system of the partition(s) that you are trying to modify?

---

### Post by gedakc on 2014-12-05
Ubuntu 14.04 has an older version of GParted.  You might try booting from media containing [GParted Live]("http://gparted.org/livecd.php") (current version 0.20.0-2) which includes a number of important bug fixes.

---

### Post by lavikl on 2014-12-08
Thanks sudodus and gedakc !

sudodus: I've been using a different system from the sustem I with to modify. I did unmound the partition before modifying it. I havn't tried to repair the file system yet. 
The same error occured using another USB stick and another PC.

gedakc: Thank you, I will try it now

---

### Post by lavikl on 2014-12-08
ok, so I've created a live CD of Gparted. 
At least now it doesn't crash... but I still can't create a new partition.
I've resized the existing partition but when I click on "new" on the unallocated space I get an an error that I can't create more than 1 extended partitions. 

This is getting frustrating...

---

### Post by lavikl on 2014-12-08
and another update:
I've reformatted the USB drive.
Re-installed Ubuntu using the pendrive install tool.
I've deleted the casper-re file (following a tutorial for creating a persistent ubuntu with a persistnent drive larger than 4gb).
I've loaded the gparted live CD, changed the size of the partition which holds the ubuntu files (changed it to 2.5GB).
Then I clicked on the new un-allocated space and chose "new". I chose ext4 file system and gave it the lavel "casper-rw". Now I clicked on the green V mark.

I got an error message saying that shrinking the file system failed.

what am I doing wrong ?!

Following is the error output:

```


GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize

Libparted 2.3
Shrink /dev/sdb1 from 7.47 GiB to 2.59 GiB  00:00:05    ( ERROR )
     	
calibrate /dev/sdb1  00:00:00    ( SUCCESS )
     	
path: /dev/sdb1
start: 2048
end: 15667199
size: 15665152 (7.47 GiB)
check file system on /dev/sdb1 for errors and (if possible) fix them  00:00:03    ( SUCCESS )
     	
fsck.fat -a -w -v /dev/sdb1
     	
fsck.fat 3.0.26 (2014-03-07)
fsck.fat 3.0.26 (2014-03-07)
Checking we can access the last sector of the filesystem
There are differences between boot sector and its backup.
This is mostly harmless. Differences: (offset:original/backup)
1:58/5a, 3:53/4d, 4:59/53, 5:53/57, 6:4c/49, 7:49/4e, 8:4e/34, 9:55/2e
, 10:58/31, 90:fa/00, 91:fc/00, 92:31/00, 93:c9/00, 94:8e/00, 95:d1/00
, 96:bc/00, 97:76/00, 98:7b/00, 99:52/00, 100:06/00, 101:57/00, 102:1e/00
, 103:56/00, 104:8e/00, 105:c1/00, 106:b1/00, 107:26/00, 108:bf/00
, 109:78/00, 110:7b/00, 111:f3/00, 112:a5/00, 113:8e/00, 114:d9/00
, 115:bb/00, 116:78/00, 118:0f/00, 119:b4/00, 120:37/00, 121:0f/00
, 122:a0/00, 123:56/00, 124:20/00, 125:d2/00, 126:78/00, 127:1b/00
, 128:31/00, 129:c0/00, 130:b1/00, 131:06/00, 132:89/00, 133:3f/00
, 134:89/00, 135:47/00, 136:02/00, 137:f3/00, 138:64/00, 139:a5/00
, 140:8a/00, 141:0e/00, 142:18/00, 143:7c/00, 144:88/00, 145:4d/00
, 146:f8/00, 147:50/00, 148:50/00, 149:50/00, 150:50/00, 151:cd/00
, 152:13/00, 153:eb/00, 154:62/00, 155:8b/00, 156:55/00, 157:aa/00
, 158:8b/00, 159:75/00, 160:a8/00, 161:c1/00, 162:ee/00, 163:04/00
, 164:01/00, 165:f2/00, 166:83/00, 167:fa/00, 168:4f/00, 169:76/00
, 170:31/00, 171:81/00, 172:fa/00, 173:b2/00, 174:07/00, 175:73/00
, 176:2b/00, 177:f6/00, 178:45/00, 179:b4/00, 180:7f/00, 181:75/00
, 182:25/00, 183:38/00, 184:4d/00, 185:b8/00, 186:74/00, 187:20/00
, 188:66/00, 189:3d/00, 190:21/00, 191:47/00, 192:50/00, 193:54/00
, 194:75/00, 195:10/00, 196:80/00, 197:7d/00, 198:b8/00, 199:ed/00
, 200:75/00, 201:0a/00, 202:66/00, 203:ff/00, 204:75/00, 205:ec/00
, 206:66/00, 207:ff/00, 208:75/00, 209:e8/00, 210:eb/00, 211:0f/00
, 212:51/00, 213:51/00, 214:66/00, 215:ff/00, 216:75/00, 217:bc/00
, 218:eb/00, 219:07/00, 220:51/00, 221:51/00, 222:66/00, 223:ff/00
, 224:36/00, 225:1c/00, 226:7c/00, 227:b4/00, 228:08/00, 229:e8/00
, 230:e9/00, 232:72/00, 233:13/00, 234:20/00, 235:e4/00, 236:75/00
, 237:0f/00, 238:c1/00, 239:ea/00, 240:08/00, 241:42/00, 242:89/00
, 243:16/00, 244:1a/00, 245:7c/00, 246:83/00, 247:e1/00, 248:3f/00
, 249:89/00, 250:0e/00, 251:18/00, 252:7c/00, 253:fb/00, 254:bb/00
, 255:aa/00, 256:55/00, 257:b4/00, 258:41/00, 259:e8/00, 260:cb/00
, 262:72/00, 263:10/00, 264:81/00, 265:fb/00, 266:55/00, 267:aa/00
, 268:75/00, 269:0a/00, 270:f6/00, 271:c1/00, 272:01/00, 273:74/00
, 274:05/00, 275:c6/00, 276:06/00, 277:46/00, 278:7d/00, 280:66/00
, 281:b8/00, 282:46/00, 283:ee/00, 286:66/00, 287:ba/00, 292:bb/00
, 294:80/00, 295:e8/00, 296:0e/00, 298:66/00, 299:81/00, 300:3e/00
, 301:1c/00, 302:80/00, 303:a1/00, 304:f3/00, 305:42/00, 306:6f/00
, 307:75/00, 308:74/00, 309:e9/00, 310:f8/00, 311:02/00, 312:66/00
, 313:03/00, 314:06/00, 315:60/00, 316:7b/00, 317:66/00, 318:13/00
, 319:16/00, 320:64/00, 321:7b/00, 322:b9/00, 323:10/00, 325:eb/00
, 326:2b/00, 327:66/00, 328:52/00, 329:66/00, 330:50/00, 331:06/00
, 332:53/00, 333:6a/00, 334:01/00, 335:6a/00, 336:10/00, 337:89/00
, 338:e6/00, 339:66/00, 340:60/00, 341:b4/00, 342:42/00, 343:e8/00
, 344:77/00, 346:66/00, 347:61/00, 348:8d/00, 349:64/00, 350:10/00
, 351:72/00, 352:01/00, 353:c3/00, 354:66/00, 355:60/00, 356:31/00
, 357:c0/00, 358:e8/00, 359:68/00, 361:66/00, 362:61/00, 363:e2/00
, 364:da/00, 365:c6/00, 366:06/00, 367:46/00, 368:7d/00, 369:2b/00
, 370:66/00, 371:60/00, 372:66/00, 373:0f/00, 374:b7/00, 375:36/00
, 376:18/00, 377:7c/00, 378:66/00, 379:0f/00, 380:b7/00, 381:3e/00
, 382:1a/00, 383:7c/00, 384:66/00, 385:f7/00, 386:f6/00, 387:31/00
, 388:c9/00, 389:87/00, 390:ca/00, 391:66/00, 392:f7/00, 393:f7/00
, 394:66/00, 395:3d/00, 396:ff/00, 397:03/00, 400:77/00, 401:17/00
, 402:c0/00, 403:e4/00, 404:06/00, 405:41/00, 406:08/00, 407:e1/00
, 408:88/00, 409:c5/00, 410:88/00, 411:d6/00, 412:b8/00, 413:01/00
, 414:02/00, 415:e8/00, 416:2f/00, 418:66/00, 419:61/00, 420:72/00
, 421:01/00, 422:c3/00, 423:e2/00, 424:c9/00, 425:31/00, 426:f6/00
, 427:8e/00, 428:d6/00, 429:bc/00, 430:68/00, 431:7b/00, 432:8e/00
, 433:de/00, 434:66/00, 435:8f/00, 436:06/00, 437:78/00, 439:be/00
, 440:da/00, 441:7d/00, 442:ac/00, 443:20/00, 444:c0/00, 445:74/00
, 446:09/00, 447:b4/00, 448:0e/00, 449:bb/00, 450:07/00, 452:cd/00
, 453:10/00, 454:eb/00, 455:f2/00, 456:31/00, 457:c0/00, 458:cd/00
, 459:16/00, 460:cd/00, 461:19/00, 462:f4/00, 463:eb/00, 464:fd/00
, 465:8a/00, 466:16/00, 467:74/00, 468:7b/00, 469:06/00, 470:cd/00
, 471:13/00, 472:07/00, 473:c3/00, 474:42/00, 475:6f/00, 476:6f/00
, 477:74/00, 478:20/00, 479:65/00, 480:72/00, 481:72/00, 482:6f/00
, 483:72/00, 484:0d/00, 485:0a/00, 504:fe/00, 505:02/00, 506:b2/00
, 507:3e/00, 508:18/00, 509:37/00
Not automatically fixing this.
Boot sector contents:
System ID "SYSLINUX"
Media byte 0xf8 (hard disk)
512 bytes per logical sector
2048 bytes per cluster
32 reserved sectors
First FAT starts at byte 16384 (sector 32)
2 FATs, 32 bit entries
15604224 bytes per FAT (= 30477 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 31224832 (sector 60986)
3901041 data clusters (7989331968 bytes)
63 sectors/track, 255 heads
2048 hidden sectors
15665152 sectors total
Reclaiming unconnected clusters.
Checking free cluster summary.
/dev/sdb1: 248 files, 504715/3901041 clusters
shrink file system  00:00:02    ( ERROR )
     	
using libparted
libparted messages    ( INFO )
     	
GNU Parted cannot resize this partition to this size. We're working on it!

========================================
Create Primary Partition #1 (ext4, 4.88 GiB) on /dev/sdb

========================================

```

---

### Post by sudodus on 2014-12-08
> **lavikl said:**
> ok, so I've created a live CD of Gparted. 
At least now it doesn't crash... but I still can't create a new partition.
I've resized the existing partition but when I click on "new" on the  unallocated space I get an an error that I can't create more than 1  extended partitions. 

This is getting frustrating...

In an MSDOS partition table it is possible to have maximum 4 primary  partitions. Only one of these can be an extended partition. But the  extended partition can contain a large number of logical partitions, and  linux has no problems with logical partitions. So instead of trying to  make another extended partition, you should make the current extended  partition fill all unallocated space, and after that create one or more  logical partitions inside the extended partiiton.

-0-

But there are things we don't know, so it is not possible to give detailed and relevant information.

Please post information about the current partitions of the drive you want to modify!

Either post the output of

```
sudo parted -l
```

('space minus ell' at the end)

and the output of

```
df
```

Click on **Go Advanced**, and then copy & paste the output of the two commands. Mark it in the editing window and click on the **#** icon above the window to put the output text within code tags.

-o-

or a screenshot of gparted (displaying the drive you want to modify)

Click on **Go Advanced**, and then **Manage Attachments**, and attach the screenshot image (png or jpg file) if this is your way to show the content of the drive.

---

### Post by sudodus on 2014-12-08
> **lavikl said:**
> and another update:
I've reformatted the USB drive.
Re-installed Ubuntu using the pendrive install tool.
I've deleted the casper-re file (following a tutorial for creating a persistent ubuntu with a persistnent drive larger than 4gb).
I've loaded the gparted live CD, changed the size of the partition which holds the ubuntu files (changed it to 2.5GB).
Then I clicked on the new un-allocated space and chose "new". I chose ext4 file system and gave it the lavel "casper-rw". Now I clicked on the green V mark.

I got an error message saying that shrinking the file system failed.

what am I doing wrong ?!

Which pendrive install tool did you use? From which operating system?

Did you check if the system worked (before you tried to make the persistence larger than 4 GB)?

Is it an installed system or a persistent live system?

Did you boot from the same or another drive when you tried to shrink the file system?

---

### Post by lavikl on 2014-12-08
I've used a universal-usb-installer from this web site: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
with an Ubuntu 14.04 (32 bit) iso file, installing it as a persistent live system.
I used it from Win7

I then followed this tutorial: 
[http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb](http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb)

I've tried to boot from my PC HD which runs ubuntu by itself and run gparted from there, but gparted crashed all the time so I've booted from a live cd of gparted.

I did not check that the persistent live system work before I tried to make changes to it.

---

### Post by lavikl on 2014-12-08
And here is the output you asked for:

The parted output:

```
Model: ATA WDC WD10EARS-00M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   115GB   115GB   primary   ntfs
 4      115GB   151GB   35.6GB  extended
 5      115GB   142GB   27.1GB  logical   ext4
 6      142GB   151GB   8502MB  logical   linux-swap(v1)
 3      151GB   1000GB  849GB   primary   ntfs


Model: General USB Flash Disk (scsi)
Disk /dev/sdb: 8023MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8022MB  8021MB  primary  fat32        boot, lba


```

and df output:

```
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda5       25913644 5030792  19543460  21% /
none                   4       0         4   0% /sys/fs/cgroup
udev             4034892      12   4034880   1% /dev
tmpfs             809136    1052    808084   1% /run
none                5120       0      5120   0% /run/lock
none             4045672      80   4045592   1% /run/shm
none              102400      40    102360   1% /run/user
/dev/sdb1        7802082 1009430   6792652  13% /media/lavik/UUI
```

---

### Post by sudodus on 2014-12-08
> **lavikl said:**
> I've used a universal-usb-installer from this web site: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
with an Ubuntu 14.04 (32 bit) iso file, installing it as a persistent live system.
I used it from Win7

I have better experience of Unetbootin (instead of universal-usb-installer). There is a version of Unetbootin also for Windows.
> 
I then followed this tutorial: 
[http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb](http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb)

I've tried to boot from my PC HD which runs ubuntu by itself and run gparted from there, but gparted crashed all the time so I've booted from a live cd of gparted.

I did not check that the persistent live system work before I tried to make changes to it.

The tips at Askubuntu should be reliable.

Maybe you can make a new attempt and check that the persistent live system works.

When you have a working system, you can start the process to make it persistent with a partition labeled casper-rw and and ext file system (ext2, ext3 or ext4). Check that there is a boot option **persistent**, and it should work.

Later on you should use the mount option **noatime** to reduce writing to the drive, and you might skip journaling if you wish (in ext3 and ext4, ext2 lacks journaling).

---

### Post by lavikl on 2014-12-08
Thanks for all the info!
I've gone through the whole process again using Unetbootin.
I'm now checking to see the system works without modifying the persistent settings.

A few days ago I did the whole thing with another USB drive and with a 64bit version of Ubuntu 14.04 and after some struggling (mainly due to crashes of gparted) I finally got it to work. Could it be an issue with the USB drive or a 64/32 bit installation ?

---

### Post by sudodus on 2014-12-08
If you have problems also with Unetbootin, I suggest that you check the iso file with md5sum (that the download was good). It will be be interesting to see if it runs before you start tweaking the system to get a partition for persistence. If it works now, it should work also after the final steps.

It is possible that you pendrive does not cooperate well with your computer (and its UEFI/BIOS system and motherboard hardware). What pendrive is it? "General USB Flash Disk", does not tell much about the brand name and model.

---

### Post by lavikl on 2014-12-08
so... the Live USB works when I do not tweak it. I've created a persistent Ubuntu live with Unetbootin with a 4000MB persistent file within it. So the iso file should be ok.
But, when I try to change the partitions I get the error saying that gparted cannot resize the partition to the requested size. The partition holds ~1Gb of data, and I've tried to resize it to 2Gb, 2.5Gb and 3Gb each time, without success.
I can't give any more info about the pen drive. My best guess it is somthing very cheap, as I got it as a gift at a conference a year ago.
I will buy another one tommorrow and give it a try.

Thanks for help !
I'll squeez another question while at it: I wish to clone this drive (after I'll get the partition thing solved) to several other pendrives. I need to clone the whole thing, including partition structure. Is that possible or would I have to clone it, and then change the partitions manually for each pendrive copy ?

---

### Post by sudodus on 2014-12-08
When this works, I would ***not*** blame the USB pendrive. I think something else is wrong, some software problem. You have to remove the casper-rw file before trying to shrink the FAT32 partition. And you have to unmount the FAT32 partition.

Another alternative is to make the FAT32 partition small (slightly bigger than the iso file) at the very beginning (using gparted), and to create the casper-rw partition behind it. Then use Unetbootin and install the system into the FAT32 partition. The following old link might help you, use a casper-rw *partition* instead of a casper-rw *file*, but the boot option **persistent** will be the same.

[http://ubuntuforums.org/showthread.php?t=1885392&p=11546560#post11546560](http://ubuntuforums.org/showthread.php?t=1885392&p=11546560#post11546560)

---

### Post by lavikl on 2014-12-09
I did remove casper-rw file before shrinking the FAT32 partition, and the partition was unmounted.
I will attempt another go at it, hopefully tomorrow.

In order to maximize the space available for storing data and manipulating it, should I shrink the fat32 to a size ~500mb bigger than what is occupied by the Ubuntu files and use the rest (~6Gb) for the casper-rw partition ?

I'll post my findings as soon as I get it done

---

### Post by sudodus on 2014-12-09
The most straight-forward way would be to remove the partitions and ***create*** a new partition with FAT32 of suitable size (use ***gparted*** to do it). I'd say you need no more than 100 MB extra (500 MB extra space in the FAT32 partition is a waste of space unless you want the space to store files, that should be readable from Windows (transfer between Windows and linux).

Then create the ext partition and give it the ***label*** **casper-rw**

After that install the system using ***Unetbootin***. Finally add the boot option **persistent** according to the link in my previous post.

-o-

Resizing a partition is more difficult and more likely to fail (than to give it the correct size in the beginning).

There might also be problems with bad sectors on the drive. Such problems can be fixed with work-arounds:

The ***FAT32*** partition should be checked and fixed with ```
chkdsk /r X:
``` in Windows, where X is the 'Windows drive letter'.

The ***ext*** partition should be checked and fixed with ```
sudo e2fsck -fc /dev/sdxy
``` in linux, where x is the drive letter and y is the partition number. The partition must *not* be mounted.

---

### Post by lavikl on 2014-12-15
Thanks Sudodus ! 
Got it !

---

