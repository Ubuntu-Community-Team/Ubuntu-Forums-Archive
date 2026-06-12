---
title: "Setting ext4 without journal on USB install (tune2fs)"
date: 2015-11-18
forum: New to Ubuntu
---

### Post by sonicwind on 2015-11-18
Do these tune2fs commands to reduce writes apply to a full USB **flash drive** install? Or are they only for SSD's?

Examples:

sudo tune2fs -O ^has_journal /dev/sda1
                sudo tune2fs -o discard /dev/sda1

One clears the discard mount option and the other clears the has_journal filesystem option.

Thank you so much guys. This forum is great.

---

### Post by TheFu on 2015-11-18
Welcome to the forums.

If you don't want journaling*then use ext2.
When there is data loss and you decide that journaling is good¸ ext4 will be here.
If you want a file system that is designed for flash memory, there are a few of those. I've never used them. Sorry.

For what tune2fs does, I would check the manpage.  That redirected me to the ext4 manpage:
```
                   has_journal
                          Create a journal to  ensure  filesystem  consistency
                          even across unclean shutdowns.  Setting the filesys&#8208;
                          tem feature is equivalent to using  the  -j  option.
                          This  feature  is  supported  by  ext3 and ext4, and
                          ignored by the ext2 file system driver.
```
and
```
                   discard
                          The file system will be  mounted  with  the  discard
                          mount  option.   This  will  cause  the  file system
                          driver to attempt to use the trim/discard feature of
                          some  storage devices (such as SSD's and thin-provi&#8208;
                          sioned drives available in some  enterprise  storage
                          arrays)  to  inform  the  storage device that blocks
                          belonging to deleted files can be reused  for  other
                          purposes.   (This option is currently only supported
                          by the ext4 file system driver in 2.6.35+ kernels.)
```

I thought discard was automatically set for SSDs that support it.  Don't know of any other devices commonly available that do.

---

### Post by Bucky Ball on 2015-11-19
As far as I know, if you switch off journaling in EXT4 you have ... EXT2.

---

### Post by TheFu on 2015-11-19
> **Bucky Ball said:**
> As far as I know, if you switch off journaling in EXT4 you have ... EXT2.

EXT4 is a new file system.  It was EXT3 that added journaling to EXT2. This is why the EXT2 file recovery tools worked with EXT3, but **Not** with EXT4.  Related, sure. Not directly compatible, however.

---

### Post by Bucky Ball on 2015-11-19
Got ya. Thanks for that. :)

---

### Post by oldfred on 2015-11-20
Newer SSD are not really different than HDD in life, so not much required.
My first no-name SSD from several years ago I did use ext4 with journal off. Somewhere was a comment that ext4 without journal was still better than ext2. But for small partitions ext2 is fine.

With my newer SSD, I make sure AHCI is on, added noatime to fstab, and created my own cron task for trim and turned off the Ubuntu one. Was not sure Ubuntu version ran on my model at it checks for models of SSD. 

[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-During-installation:-select-EXT4](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-During-installation:-select-EXT4)

While not a large sample, it shows they can last a long time.
 SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)
SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)
[http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb](http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb)

[URL="https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-During-installation:-select-EXT4"]
[/URL]

---

### Post by sonicwind on 2015-11-20
Thanks for the responses guys. I should have been clearer with my original question.

Do these tune2fs commands to reduce writes apply to a full USB 3.0 **flash drive** install? Or are they only for SSD's?

**oldfred**,  I'd love to hear your answer to this. I believe it was one of your posts where you appeared to indicate that this should also be done for  USB flash drives to reduce writes.

I'm considering a full installation of Ubuntu to a 16 or 32 gig USB flash drive. Your and C.S.Cameron's past posts have been most helpful but I was unsure on this one item.

---

### Post by oldfred on 2015-11-20
My old notes show those tune2fs commands for flash drives also. 
But trim will not work on flash drives. But then I believe discard also would not work as that is a trim function. Perhaps someone has newer info.

I have full installs in USB3 flash drives, but do not use them enough to create issues. They more are backup ways to boot, particularly my laptop that has only one drive.

---

### Post by sudodus on 2015-11-20
Almost all USB 2 and USB 3 pendrives lack the ability to use trim alias discard.

[This is an (expensive) exception with 'SSD technology'](http://www.kingston.com/datasheets/DTWS_us.pdf)

But you can wipe (overwrite with zeros), when a regular pendrive is getting slow, and it will be almost as fast as when it was new. See the following link about [pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by sonicwind on 2015-11-20
Thanks guys. I knew TRIM was only for SSD drives. That old post by oldfred made me question whether there might still be some value to using it on a USB flash drive. So maybe only the has_journal setting is worth changing.

That Kingston WorkSpace drive looks great! But a little bit pricey for my needs. :D

That second link has some great info. Sudodus, I've also learned so much this past week reading many of your old posts. Thank you.

---

### Post by mc4man on 2015-11-20
My experience with usb3 drives (ssd) is that although trim is supported it can't be run because it's a usb drive. (at least with fstrim, - ex.
```
$ sudo hdparm -I /dev/sdc |grep "Data Set Management TRIM supported"
	   *	Data Set Management TRIM supported (limit 1 block)
doug@doug-Lenovo-IdeaPad-Y510P:~$ sudo fstrim -v /
fstrim: /: the discard operation is not supported
```

Generally found best to leave alone & let the drive handle garbage collection in whatever manner it does, if any.

---

### Post by sudodus on 2015-11-21
> **mc4man said:**
> My experience with usb3 drives (ssd) is that although trim is supported it can't be run because it's a usb drive. (at least with fstrim, - ex.
```
$ sudo hdparm -I /dev/sdc |grep "Data Set Management TRIM supported"
	   *	Data Set Management TRIM supported (limit 1 block)
doug@doug-Lenovo-IdeaPad-Y510P:~$ sudo fstrim -v /
fstrim: /: the discard operation is not supported
```

Generally found best to leave alone & let the drive handle garbage collection in whatever manner it does, if any.

When this is problem, there is a way around it. Buy a standard sata SSD and an external USB 3 and eSATA box. Connect via eSATA (to another computer, maybe an old desktop computer with a cheap SATA to eSATA 'slot plate'). when the drive needs trimming. Then you can use it via USB for a week or two again. You can develop a routine to backup the data and trim the drive at regular intervals.

[SATA-to-ESATA-Slot-Plate](http://www.startech.com/Cables/Drive/eSATA/1-ft-eSATA-Data-Internal-to-External-Slot-Plate~ESATAPLATE1)

[2-port-SATA-to-ESATA-Slot-Plate](http://www.startech.com/Cables/Drive/eSATA/2-port-SATA-to-ESATA-Slot-Plate-MF~ESATAPLATE2)

---

