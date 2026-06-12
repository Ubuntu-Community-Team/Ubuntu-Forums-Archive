---
title: "Formated USB drive is read-only"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-11-16
I had an extra 8 GB Sandisk Cruzer USB drive with ubuntu 11.04 installed and since have a 16 GB ubuntu 11.04 and 16 GB 11.10, I thought I'd use the USB drive as an NTFS data drive.

I've formated the USB drive with both gparted and "disk utility" with NTFS format and in both cases the newly formatted drive is read-only.

If I boot into Windows 7, the USB drive is writable 

Other USB drives that I've not formated with ubuntu utilities are writable in ubuntu.

I've seen information about terminal commands to make writable, but feel I must be overlooking something basic.  I've searched the internet and found many with the same issue, but no solutions other than terminal commandS.

I might try to format with windows, but seems like I should be able to format a writable USB drive with ubuntu,

Ideas?  Thanks.

---

### Post by SheaMan on 2011-11-16
I think your buntu level is higher than mine Dave, but I did a quick search.

[http://sathyasays.com/2007/06/13/formatting-usb-pen-drive-in-linux-using-terminal/](http://sathyasays.com/2007/06/13/formatting-usb-pen-drive-in-linux-using-terminal/)

Helpful? :guitar:

---

### Post by Denver Dave on 2011-11-16
Thanks SheaMan.  If my expertise is greater than yours, we both have a long way to go.

I'm wondering if because the usb drive was previously used for ubuntu, that that might have something to do with it.

I was hoping to find a GUI - gparted or disk utility solution.

OK, for fun, let's see if I can format the USB drive with windows 7 - maybe the USB stick is defective.  Also, I suppose it wouldn't hurt to reboot the laptop, just in case.

- rebooting into ubuntu - still get read-only file system error.  Frustrating that right clicking on the drive and also displaying information does not give info that is read-only - only when I try to save do I know there is an issue.

- Let's see if I can format the USB drive with Windows 7 and use with ubuntu.   

Examining the USB drive with Windows 7 - properties / security - see all permissions checked except Full control.   
- looking at another Sandisk drive not formatted with ubuntu - interesting, completely different properties popup window.

non changed smaller sandisk is Fat and my ubuntu formated disk is NTFS - wonder if that has something to do with the read-only issue?

Anyway - back to original test - wonder how format with windows 7 - OK formatted with Windows 7 and NTFS.  test can still save to disk with windows - created folder and txt file.  Same looking properties dialog for drive as before.

- reboot into ubuntu - read-only

At this point the issue may be NTFS vs FAT, not whether formatted with ubuntu or windows 7, so I'll look into how to make NTFS writable with previous link - <grumble that can't seem to do from GUI>

If others have insight - please share.

= = = = =
Just found this old thread - seems pretty involved just to be able to write to my USB drive:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

and this - maybe I'll try editing the fstab file - saw that talked about other places:
[http://opensuse.swerdna.org/susentfs.html](http://opensuse.swerdna.org/susentfs.html)
- - perhaps fortunately for me there doesn't seem to be a file fstab in the /etc folder

*** all seems very strange - according to the disk utility, the main hard drive (not my boot USB) on my laptop is NTFS and I don't have any trouble writing to it.

---

### Post by arochester on 2011-11-16
Have you got? ntfs-3g
See:[http://manpages.ubuntu.com/manpages/lucid/man8/ntfs-3g.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/ntfs-3g.8.html)

I would normally format a USB stick with Fat32.

---

### Post by Rex Bouwense on 2011-11-16
I believe that arochester is correct in that the flash drive should be formatted in FAT32 to have read and write access in Linux and Microsoft Windows.

---

### Post by Jacobonbuntu on 2011-11-16
just tried to format my usb stick, with the same result,
BUT,
if I create a new partition on it (ntfs) with disk utility after formatting, it is writable :)

still, I think it is a bug

---

### Post by coffeecat on 2011-11-16
@Denver Dave, the most likely explanation since you are using 11.10 is that the ntfs-3g read-write driver has been uninstalled somehow. Which is why arochester was asking whether it was installed. If you don't have ntfs-3g the system falls back to the read-only ntfs kernel module.

Point of information. This is not a bug. ntfs-3g comes with a default installation of 11.10 but some people are losing it, possibly because they have (unnecessarily) installed the package ntfsprogs which now conflicts with ntfs-3g. The utilities provided by ntfsprogs in earlier versions of Ubuntu are now built in to the version of the ntfs-3g package that comes with 11.10. If you try to install ntfsprogs in 11.10, the package manager  removes ntfs-3g, but not before asking you.

Long story short: make sure you have ntfs-3g installed.

---

### Post by Jacobonbuntu on 2011-11-16
> **coffeecat said:**
> @Denver Dave, the most likely explanation since you are using 11.10 is that the ntfs-3g read-write driver has been uninstalled somehow. Which is why arochester was asking whether it was installed. If you don't have ntfs-3g the system falls back to the read-only ntfs kernel module.

Point of information. This is not a bug. ntfs-3g comes with a default installation of 11.10 but some people are losing it, possibly because they have (unnecessarily) installed the package ntfsprogs which now conflicts with ntfs-3g. The utilities provided by ntfsprogs in earlier versions of Ubuntu are now built in to the version of the ntfs-3g package that comes with 11.10. If you try to install ntfsprogs in 11.10, the package manager  removes ntfs-3g, but not before asking you.

Long story short: make sure you have ntfs-3g installed.

speaking for me, I do have ntfs-3g installed, but the drive is only writable until I take the extra action to create an ntfs-partition (that should be there already of course)

---

### Post by coffeecat on 2011-11-16
> **Jacobonbuntu said:**
> speaking for me, I do have ntfs-3g installed, but the drive is only writable until I take the extra action to create an ntfs-partition (that should be there already of course)

I don't quite follow that. Creating a partition and creating a filesystem in a partition are two different things. What do you do to get a partition which is not writable?

---

### Post by Jacobonbuntu on 2011-11-16
> **coffeecat said:**
> I don't quite follow that. Creating a partition and creating a filesystem in a partition are two different things. What do you do to get a partition which is not writable?

here is what I do: I plug in the drive, open disk utility, unmount and format the drive (ntfs). when I mount it again, it is "read only". 
...I unmount it again, choose "delete partition", then "create partition" (maximum size, ntfs) and it is read/write
weird but true..

on my netbook (Xubuntu) it does work in one action.

---

### Post by coffeecat on 2011-11-16
> **Jacobonbuntu said:**
> here is what I do: I plug in the drive, open disk utility, unmount and format the drive (ntfs). when I mount it again, it is "read only". 
...I unmount it again, choose "delete partition", then "create partition" (maximum size, ntfs) and it is read/write
weird but true..

Yes, that is weird. :) I'll do some testing myself on my system and see what I get. The OP has tried both disk utility and Gparted, so I'll do the same.

**EDIT**: No, I can't reproduce this on my system. Whatever I do when formatting a USB pendrive NTFS in 11.10's Disk Utility, it is always read-write in another Ubuntu 11.10 system. I have uncovered one oddity though. Disk Utility doesn't rewrite the partition table ID when reformatting so you get 0x06 (FAT16) in the partition table (for example) with a NTFS filesystem, but that doesn't appear to affect functionality.

---

### Post by mister_playboy on 2011-11-16
Using any journaled filesystem (i.e. ext3 or NTFS) on a USB flash drive is a bad idea because the constant journal writes will greatly shorten the drive life.

I would stick with FAT32 or ext2.

---

### Post by Jacobonbuntu on 2011-11-16
> **coffeecat said:**
> 
**EDIT**: No, I can't reproduce this on my system. Whatever I do when formatting a USB pendrive NTFS in 11.10's Disk Utility, it is always read-write in another Ubuntu 11.10 system. I have uncovered one oddity though. Disk Utility doesn't rewrite the partition table ID when reformatting so you get 0x06 (FAT16) in the partition table (for example) with a NTFS filesystem, but that doesn't appear to affect functionality.
...Indeed the same happens the other way around, formatting to FAT, partition type still NTFS. Strange thing is that after formatting both directions several times, I cannot reproduce the problem anymore...
maybe OP should do the same :)

---

### Post by Jacobonbuntu on 2011-11-16
> **mister_playboy said:**
> Using any journaled filesystem (i.e. ext3 or NTFS) on a USB flash drive is a bad idea because the constant journal writes will greatly shorten the drive life.

I would stick with FAT32 or ext2.


I will stop formatting at FAT :)

---

### Post by Denver Dave on 2011-11-16
I'm not trying to be radical here - just trying to determine and follow best practices.  Seems like if running ubuntu on a USB drive, that one or more additional USB drives for the data that are readable by windows would be a good idea.

Original recommendation for NTFS drive came from this thread:
[http://ubuntuforums.org/showthread.php?p=11463666#post11463666](http://ubuntuforums.org/showthread.php?p=11463666#post11463666)

I'm just trying to figure-out what is recommended and best.

= = = = =
In the "disk utility" I don't see how to delete the partition.  I've unmounted the drive and am trying to format again (maybe 2nd times a charm?)   ..... no still read-only.

OK - this is getting ridiculous  Let's format with different format:

1st choice - Scheme
- Master Boot Record
- GUID Partition Table
- Don't partition
- Apple Partition Map

Wonder which of these I should choose for a data USB where I'm using the whole drive for data.   No idea - I'll pick Master Boot Record because maybe will help windows PCs read the drive??

Looks like I have to create at least one partition - I was looking for FAT32, but only see FAT - wonder what version?  Let's pick, other than NTFS and EXT4, don't recognize any of the others.  Result says FAT32.

I can now save files to the disk fine with ubuntu.  Rebooting into windows yep can see there and save file - rebooting into ubuntu 11.10 - yep can see windows created file and save new one with ubuntu on USB FAT32 formatted drive. 

For an 8 GB USB data drive, is FAT32 preferable to NTFS?   If so, I'm done, if NTFS is a better way to go, I'll have to figure out how to make it writable.  Very strange neither gparted or disk utility indicate how to make readable.  Also, weird, my main HD is NTFS and no problems writing to it.

Thanks !

---

### Post by rng on 2011-11-16
Will it make a difference if we try to access it as root using command 'sudo nautilus' ?  Are any permissions issues involved?

---

### Post by mister_playboy on 2011-11-16
> **Denver Dave said:**
> 

For an 8 GB USB data drive, is FAT32 preferable to NTFS?

There is the technical issue of 4GB as the max file size limit on FAT32 filesystems... do you anticipate dealing with such large files often?

When necessary, you can always get over 4GB files into FAT32 by splitting them with 7zip or RAR and reassembling them once moved from USB.

I see zero reason to use NTFS on Flash media.  Even Microsoft doesn't do this... they developed exFAT as a FAT32 replacement.  I don't think we have a exFAT driver in Linux yet, however.

---

### Post by Denver Dave on 2011-11-16
******* ubuntu 11.10 USB boot issue vs 11.04 USB boot ********

I believe that the read-only problem is new to ubuntu 11.10.  Here is why I think that:

When I boot my Acer Windows 7 laptop from my ubuntu 11.04 USB drive, I can write to my MyBook 2 TB NTFS drive and also to my laptops NTFS hard drive.

When I boot my Acer Windows 7 laptop from new ubuntu 11.10 USB drive, I can not write to my  MyBook 2 TB NTFS drive nor my laptops NTFS hard drive.

I'll run from the original ubuntu 11.10 installation DVD and report back.

Well isn't that interesting - when I boot from the 11.10 DVD, I can write to my laptop's NTFS hard drive and when I boot from the 11.10 USB boot thumb drive I can't.

Any clues where to look?  On the boot DVD there are no programs listed with the windows key, starting with nt or config.

---

### Post by Denver Dave on 2011-11-17
> Long story short: make sure you have ntfs-3g installed.

Seems like a reasonable theory and perhaps easy for me to check - how would I go about telling if I have the ntfs-3g driver?

Before I try to do all of the steps in the link below, I'd like to know if I already have it:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

or maybe this NTFS-config tool might help:
[http://mygeekopinions.blogspot.com/2011/06/how-to-install-ntfs-config-in-ubuntu.html](http://mygeekopinions.blogspot.com/2011/06/how-to-install-ntfs-config-in-ubuntu.html)

. . . looking for a folder called drivers - haven't found it yet - clues?

---

### Post by Jacobonbuntu on 2011-11-17
> **Denver Dave said:**
> Seems like a reasonable theory and perhaps easy for me to check - how would I go about telling if I have the ntfs-3g driver?

Before I try to do all of the steps in the link below, I'd like to know if I already have it:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

or maybe this NTFS-config tool might help:
[http://mygeekopinions.blogspot.com/2011/06/how-to-install-ntfs-config-in-ubuntu.html](http://mygeekopinions.blogspot.com/2011/06/how-to-install-ntfs-config-in-ubuntu.html)

. . . looking for a folder called drivers - haven't found it yet - clues?


nonono, it is easy, open a terminal, type "ntfs-3g." if it is installed, you get a list of copyright information, options etc. if so, you know it is there. If you have synaptic installed, search for ntfs-3g and install it if necessary.

---

### Post by Denver Dave on 2011-11-17
[quote]nonono, it is easy, open a terminal, type "ntfs-3g." if it is installed, you get a list of copyright information, options etc. if so, you know it is there. If you have synaptic installed, search for ntfs-3g and install it if necessary.[quote]

OK - I can do the first part at least.
....  in terminal window while running 11.04
get
ntfs-3g: No device is specified.

ntfs-3g 2010.8.8 ... copyright stuff... looks like I found it in 11.04 - always nice to have something to compare to.

.... rebooting into 11.10 USB drive ....
term - ntfs-3g
The program 'ntfs-3g' is not installed.  You can install it by typing: sudo apt-get install ntfs-3g .... giving it a go ... looks like it is doing something... boy takes a while ... ok done - wonder if have to reboot ... let's try without.  

verify file there with home icon tool .... verify running 11.10 USB ... maybe using system info - yep

THANKS !!!!!!  At least for me solved the writable NTFS drive issue for ubuntu 11.10 disk for me.

I don't believe I did anything unusual when creating USB drive except for installed 3rd party stuff option.

Thanks again. whew, check that one off.

---

### Post by Jacobonbuntu on 2011-11-17
....congratulations :)

---

### Post by Denver Dave on 2011-11-17
Thanks again!  I'm able to now write to NTFS data drives when running Ubuntu 11.10 from a USB boot drive

Opinions were expressed on this thread about FAT 32 vs NTFS that were not included in the which is better choice for data drive discussion at:
[http://ubuntuforums.org/showthread.php?t=1879124](http://ubuntuforums.org/showthread.php?t=1879124)

If you're interested, please join in.

If you have the ntfs-3g driver and still have the read-only issue, should probably mention it again here - there may be other causes that haven't been tracked down.

---

### Post by Jacobonbuntu on 2011-11-17
> **Denver Dave said:**
> Thanks again!  I'm able to now write to NTFS data drives when running Ubuntu 11.10 from a USB boot drive

Opinions were expressed on this thread about FAT 32 vs NTFS that were not included in the which is better choice for data drive discussion at:
[http://ubuntuforums.org/showthread.php?t=1879124](http://ubuntuforums.org/showthread.php?t=1879124)

If you're interested, please join in.

If you have the ntfs-3g driver and still have the read-only issue, should probably mention it again here - there may be other causes that haven't been tracked down.

thanks! I'll take a look!

---

