---
title: "Messed up partiton table after windows install"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by editheraven on 2011-12-04
I have installed win7 on a 70gb partition outside a extended partition (container for 3 ext4 partitions)

The free space in extended partition should not exist. The last 2 partition are windows7 partitions.

[http://imageshack.us/photo/my-images/189/screenshotctx.png/](http://imageshack.us/photo/my-images/189/screenshotctx.png/)
[http://imageshack.us/photo/my-images/851/screenshot1sh.png/](http://imageshack.us/photo/my-images/851/screenshot1sh.png/)


le : it seems that my 2 ntfs partition got tagged inside the lba. Anyway, this is impossible, because they are created as primary. Anyhow, there was no space inside ext, as you can see in gui app.

This is why i hate windows.

The missing partition is the selected one in here : [http://imgur.com/eLejP](http://imgur.com/eLejP)

---

### Post by oldfred on 2011-12-04
Please just copy & paste command line output. If long use the code tags (highlight & click #) in edit panel. You can also directly post screenshots and upload those. 

If you need to reorganize partitions this program often works:

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Best to backup partition table first and copy to another device.
sudo sfdisk -d /dev/sdb > parts_sdb.txt

---

### Post by editheraven on 2011-12-04
That did it. Thanx.

---

