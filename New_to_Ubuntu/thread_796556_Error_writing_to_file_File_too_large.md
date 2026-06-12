---
title: "Error writing to file: File too large"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Etheredge on 2008-05-16
I cant seem to copy more then 4 gigs at a time?

Any idea on how to fix this?

---

### Post by Etheredge on 2008-05-16
up

---

### Post by prshah on 2008-05-16
> **Etheredge said:**
> I cant seem to copy more then 4 gigs at a time?
Any idea on how to fix this?

If you're copying to a FAT32 partition, then the file size limit is 4Gb (3.8GiB for hair-splitters).

Otherwise maybe a bit more information?

---

### Post by Etheredge on 2008-05-16
that would be the issue is there a way that i can format it to NTFS?

---

### Post by herbster on 2008-05-16
Unmount the drive and run Gparted.

---

### Post by PinkFloyd102489 on 2008-05-16
I posted this in another thread as well, but it applies here too.

[I]Connect the drive then open GNOME Partition Editor under System > Administration > GNOME Partition Editor.


Oh and if you dont have the option to format to NTFS, open Synaptic and install ntfs-3g, ntfsprogs, ntfs-config and libntfs-3g23.[/I]

---

### Post by Hmarroqu on 2008-11-25
is this STUPID rule only in ubuntu? how convinient that my file is 4.1 and i need to transfer it to back up but i can because ubuntu wont let me. and i dont have the luxury of formanting my drive to ntfs...what is up with that sigh....end vent/ going back to windows hopefully it will let me copy more than 4.1 gbs at a time.

ubuntu fails me yet again

---

### Post by herbster on 2008-11-25
I wonder if you could overreact a bit more and read even less.

---

### Post by prshah on 2008-11-26
> **Hmarroqu said:**
> going back to windows hopefully it will let me copy more than 4.1 gbs at a time.


This is a limitation of the FAT32 file system. It applies to any and all operating systems, devices, partitions, computers, mp3 players, phones, flash drives, etc that use the FAT32 file system. And by the way, that's 3.8GiB.

Here's another interesting tip; Do you want to create a FAT32 partition bigger than 32Gb in size during XP setup? Nope, XP won't let you. But Ubuntu, OpenSUSE, Puppy (or really any Linux), as well as 3rd party utilities and _even_ Windows 98 / ME will allow you to create a bigger-than-32gb-FAT32 partition; now _that's_ a forced limitation. Think about it.

---

### Post by neiljmac on 2010-05-13
I had the same problem and hen realised that the drive I am copying to is FAT32.  It is from an old laptop.

I am now busy reformatting it to NTFS as I am using for my Mac as well.

@prshah.  Interesting point you mentioned about the XP limitation.  Any idea why that might be, as it doesn't seem to make sense why such a limitation would be imposed?

Best regards,

Neil.

---

### Post by 3rdalbum on 2010-05-13
> **Hmarroqu said:**
> is this STUPID rule only in ubuntu? how convinient that my file is 4.1 and i need to transfer it to back up but i can because ubuntu wont let me. and i dont have the luxury of formanting my drive to ntfs...what is up with that sigh....end vent/ going back to windows hopefully it will let me copy more than 4.1 gbs at a time.

ubuntu fails me yet again

Ever wondered what the "32" part of the name "Fat32" means?

It means that file lengths in Fat32 can only be represented by 32 bits, which as we know from the current RAM situation, gives the limitation of 4 GiB.

The limitation definitely occurs in Windows, the Fat32 filesystem cannot store any more data in the file. I think Windows handles it less gracefully than Ubuntu; I've downloaded torrents that appear to have been truncated at the 4 GiB mark, which suggests that Windows will copy and truncate the file without even warning you that the file isn't complete.

---

### Post by 3rdalbum on 2010-05-13
> **neiljmac said:**
> 
@prshah.  Interesting point you mentioned about the XP limitation.  Any idea why that might be, as it doesn't seem to make sense why such a limitation would be imposed?

Bill Gates supposedly thought that nobody would need more than 600 kibibytes of RAM, maybe he thought that nobody would need more than 32 gibibytes of disk space ;-)

It was probably done to force adoption of NTFS on bigger disks, so users were less likely to come across the filesize limitation of Fat32. If your hard disk is 32 gibibytes you're quite unlikely to be working with any 4 gibibyte files.

---

### Post by japzone on 2010-06-10
I ran into this problem myself. To get around it I zipped the File to my Fat32 drive instead of copying it. My 5.1gb ubuntu drive image became a 2.1gb Zip file.
 I can't format my drive to NTFS because I: 
1)have to many files stored on it.
2)use it with devices that either don't support or aren't reliable with NTFS

---

