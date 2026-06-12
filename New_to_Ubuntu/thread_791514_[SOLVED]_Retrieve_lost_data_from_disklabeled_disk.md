---
title: "[SOLVED] Retrieve lost data from disklabeled disk"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Nevyn on 2008-05-12
Ok, time to walk into the pillory...*sigh*
I've been having important data on all of my different partitions on my two harddrives and wanted to switch to 32bit Hardy from my already installed 64bit Hardy. On my primary drive I had one partition for Linux, one for Windows, the swap and one big (NTFS) for important data. 

To start merging the partitions I first cleaned the Win-partition from data and then formatted it to ext3 (I don't want anything to do with Win anymore). I then looked for a way to merge it into my Linux partition to be able to move around my data and free up another partition to format to ext3. I didn't find the option in gparted but I did find the option to set at Disklabel on my now empty partition. Thinking that the disk needed a label to merge, I misread the warning that said " all data will be erased on sda!" (I misread the ! for 1, stupid I know) and set the msdos disklabel on the hard drive.

So now I have unallocated space where I used to have data that was very important to me... And the question is: does anybody have any idea if and how the data is retrieveable?

Waiting and hoping for a positive answer I'll now install Hardy 32bit on a different partition.

Cheers!

---

### Post by logos34 on 2008-05-12
Try TestDisk or PhotoRec.

---

### Post by Nevyn on 2008-05-13
Thanks, this seems to be exactly what I need. Trying it out now.

---

