---
title: "USB drive appears unformatted."
date: 2012-01-08
forum: New to Ubuntu
---

### Post by wigout on 2012-01-08
Hi-

I have got this usb drive that has exhibited the following behavior a few times:

Format drive (different fs types, sometimes 1 sometimes more partitions)
use drive 3-5 times with no issues
Drive appears unformatted and is useless. 
Can't run recovery software.

Plugging in the device results in nothing but a stub:
There's an entry in the dev folder, /dev/sdb
and lsusb shows the device.

That's it.
Gparted doesn't detect the device at all.
Disk Utility shows the device as an unformatted "memory bar"
dd, ddrescue and the like say "no medium found"

Now, I am stupid for having used the device more than twice. Twice of the same sort of error and no solution should have made me move on to a different device.

Currently there are (were) couple of large files on the drive. I'd like to be able to try and recover them.

But with no partitions showing up and only disk utility with it's basic "reformat it" tool available do I have any possibility of bringing those files back?

Thanks,
wigout

INFO:
I'm running 11.10 64bit, usb drive is 8gb vfat.

dd if=/dev/sdb of=sdb.test
dd: opening `/dev/sdb': No medium found


ddrescue /dev/sdb test
ddrescue: Can't open input file: No medium found


sudo mount /dev/sdb mountpoint
mount: no medium found on /dev/sdb


lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
[B]Bus 002 Device 010: ID 090c:1000 Feiya Technology Corp. Flash Drive
[/B]Bus 002 Device 004: ID 8086:0189 Intel Corp. 


dmesg
[80217.424224] usb 2-1.2: new high speed USB device number 11 using ehci_hcd
[80218.144915] scsi16 : usb-storage 2-1.2:1.0
[80220.035727] scsi 16:0:0:0: Direct-Access              USB MEMORY BAR   1000 PQ: 0 ANSI: 0 CCS
[80220.035976] scsi: killing requests for dead queue
[80220.036297] scsi: killing requests for dead queue
[80220.043423] scsi: killing requests for dead queue
[80220.049077] scsi: killing requests for dead queue
[80220.055408] scsi: killing requests for dead queue
[80220.055727] scsi: killing requests for dead queue
[80220.059436] scsi: killing requests for dead queue
[80220.059760] scsi: killing requests for dead queue
[80220.063759] sd 16:0:0:0: Attached scsi generic sg2 type 0
[80220.063769] sd 16:0:0:0: Embedded Enclosure Device
[80220.065382] sd 16:0:0:0: Failed to get diagnostic page 0x8000002
[80220.065395] sd 16:0:0:0: Failed to bind enclosure -19
[80220.071077] sd 16:0:0:0: [sdb] Attached SCSI removable disk

sudo gparted /dev/sdb
======================
libparted : 2.3
======================
Error opening /dev/sdb: No medium found


 hdparm /dev/sdb

/dev/sdb:
 HDIO_DRIVE_CMD(identify) failed: Bad address
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 1024/0/62, sectors = 0, start = 0

---

### Post by wigout on 2012-01-09
Does anyone have any suggestions as to what is possible for recovery?

---

### Post by Mark Phelps on 2012-01-09
Some folks have had good results using testdisk:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

If you have access to a Windows PC, you can also try using GetDataBack for FAT from Runtime Software.  Their downloadable trial version doesn't do actual recovery -- but you can see how good a job it does at detecting directories and files.

---

### Post by wigout on 2012-01-09
I have used testdisk successfully in the past- in this case though, just like ddrescue and gparted, testdisk simply doesn't "see" the drive.

---

### Post by bluexrider on 2012-01-09
I have Windows XP in a VirtualBox and recovered and reformatted a thumb drive Linux couldn't 'see'

---

### Post by wigout on 2012-01-09
I can format the drive in "Disk Utility" but I don't want to- I want to save the files that are still on there using something like testdisk or ddrescue... but for whatever reason they refuse to work on the usb device.

-wigout

---

### Post by Mark Phelps on 2012-01-09
> **wigout said:**
> I have used testdisk successfully in the past- in this case though, just like ddrescue and gparted, testdisk simply doesn't "see" the drive.

Sorry to hear that.  Then, if you still want to recover the files, read my second suggestion in my post.  It's some work, but I've had the product recover files from unmountable partitions.

---

### Post by Double.J on 2012-01-09
> **wigout said:**
> I can format the drive in "Disk Utility" but I don't want to- I want to save the files that are still on there using something like testdisk or ddrescue... but for whatever reason they refuse to work on the usb device.

-wigout

I've had luck with recovering data from failed sd cards before using photorec(not just photos) so it can't hurt to try?

[photorec live]("http://www.cgsecurity.org/wiki/PhotoRec")

---

### Post by wigout on 2012-01-11
Thanks to everyone's suggestions so far.

I guess I am puzzled as to why all recovery software fails to even detect the drive. It seems like I should be able to make a dd dump of the drive even if it had nothing on it- even if it was unformatted.

I can't figure out how to force the issue- and that seems to be a real stumbling block for possible file recovery.

This has become more academic at this point- I get that the files are effectively gone. But I remain perturbed that I can't use any rescue software on an apparently partitionless drive. It would seem that there would be a tool for this challenge in the ever functional linux arsenal. 

I won't be using this drive for anything in the future- except to try and figure out desperate recovery measures.

I am still interested in alternative rescue suggestions, so please keep them coming if you have any.

I will get around to trying windows, but I have had zero luck accomplishing any recovery in windows- I have put my faith in linux.

-wigout

PS: photorec is awesome and have used it before. Just like testdisk by the same author, however, it doesn't find the device/partition of the usb drive so no dice.

---

### Post by Mark Phelps on 2012-01-11
I join you in your disappointment ...

Maybe there's something specific about USB sticks and memory cards that makes file recovery a lot harder.  I've had ZERO successful results with any of these -- and I've used a variety of Windows and Linux tools.

I recently had an SD card go bad (Windows would no longer assign a drive letter to it), so I tried using a specific Windows-based memory card recovery tool -- and it failed to even "see" the card because, apparently, Windows wouldn't assign it a drive letter.

I also tried another recovery program, and although it "saw" the drive and files, and appeared to work, from a sampling of the files, they all appeared to be corrupted.  Filenames and sizes were correct, but the contents were useless.

I've gone through a half dozen USB sticks and cards now, and not been able to successfully recover files from any of them.

---

### Post by beefalo on 2012-08-08
> **wigout said:**
> I can format the drive in "Disk Utility" but I don't want to- I want to save the files that are still on there using something like testdisk or ddrescue... but for whatever reason they refuse to work on the usb device.

-wigout

Disk Utility does NOT work either ....

I have the exact same problem (maybe even the same stick :-)), but i my case it would suffice to have the stick usable again. Formatting with Disk Utility simply produces "Error creating partition table: helper exited with exit code 1: cannot open /dev/sdb: No medium found" 
which somehow doesn't really surprised me

greets
beef

---

### Post by lkraemer on 2012-08-09
Wigout,
I've had two similar type things happen.  I think my problem was using my USB Flash drive in an Older Compaq Laptop,
that had USB 1 and a newer Laptop that had USB 2.  I've updated my Old Laptop with a USB PCMCIA Card to prevent that
from happening again.  I'm wondering if this is your problem?


**In Linux **
A Linux command to make the USB Flash Drive Read/Write should be hdparm. To locate the device use one of the following commands
after inserting the device, to determine what the USB Flash Drive is detected as:
```

dmesg | tail
sudo blkid
mount
fdisk -l

```

To turn off disk device`s write protect, use the low level system utility hdparm like this: (where x is the letter of your device [a..z])
```

man hdparm
sudo hdparm -r0 /dev/sdx

```
where I assume that /dev/sdx is the Physical disk device you are working on.

Once the device is Read/Write see if you can use Testdisk/Photorec to recover the files you need to save.
If those packages fail, you may want to run fsck on the USB Flash Drive to see if it can be repaired.
```
fsck /dev/sdx1
```


**In Windows:**
To test this I used Windows XP "Diskpart" as follows:

1. Start Menu - Run Program - CMD
2. When the command console opens, type DISKPART
3. List the drives by typing LIS DIS
4. Select the USB drive by typing SEL DIS 1 (if disk 1 is your USB drive)
5. Inspect the details for that disk by typing DET DIS
Check if the disk is marked as Read-only
6. Type ATT DIS CLEAR READONLY to clear the ReadOnly attribute and then type DET DIS again to check it has been cleared.

(optional - if the drive still is Readonly try this) Type CLEAN to erase all contents from the drive
(make sure you have selected the correct drive!!!!!)

7. Finally type EXIT to quit Diskpart

If this process works it might be the easiest fix. I executed DISKPART on XP, and looked at the commands via HELP. But, I don't
have a USB Flash Drive that is READ-ONLY right now.

If that doesn't work, I've got one more suggestion.  But, I'll wait until you have exhausted your ideas for that test.

Larry

---

### Post by chimarrao on 2012-10-17
Okay, I had this problem and just as I was about to give up I tried flipping the locking switch to "lock" and then trying to read it - it worked! Why? I have no idea. I was able to remove the SD card, flip the switch back to "unlocked" and reformat it as well. I was not trying to get any files off it but simply trying to be able to use it again. Extreme weirdness for me, but maybe the locking switch has something to do with the SD card-computer interface (gee, didn't expect that) that may have gotten around the problem, which then made the card accessible? dunno, but just thought I'd share.

---

### Post by Bashing-om on 2012-10-17
I'll pop another thought out for nothing... do usb thumb drives also have a backup super block ? As the drive is formated in vfat, can windows re-write the super block from the maybe back up ?

[INDENT]not much, but it is a thought <==BDQ

[/INDENT]

---

