---
title: "change the file system of my external hdd"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by jdrodrig on 2008-06-27
Hi,

A simple question. I got a 500gb external hdd and before I could think straight I did Acronics backups of my Windows and Ubuntu partitions on this FAT32 disk. 

Now that I want to also use it to experiment with some simple basic virtual machines (vbox), I got into the 4gb barrier. What is the easiest way to make half of this HDD (without deleting my existing backups already in there) NTFS or ext3 or something that allows > 4gb single files?

---

### Post by defrex on 2008-06-27
sudo apt-get install gparted

It's a non-destructive partition editor that'll let you turn the free space into a new partition.

---

### Post by flytripper on 2008-06-27
dunno but if you dont mind, i'm gonna watch this post cos i have an ntfs from my xp days and i am sick of clicking permanent delete all the time... so i am also looking to adjust the partition file structure with out destroying the files .....

---

### Post by flytripper on 2008-06-27
cheers, beat me to it :)

---

### Post by defrex on 2008-06-27
flytripper: you can't reformat without destroying the files. You could use gparted to make a new partition on the drive, copy all the files to it, then use gparted to delete the NTFS part and add the space to the new partition. 

Of course, if more then half the drive is full, you'll need some more storage.

---

### Post by jdrodrig on 2008-06-27
Thanks a lot to all of you...

Final question, is there a windows-based or equivalent g-parted?

---

### Post by defrex on 2008-06-27
uh... the [gparted live cd]("http://gparted.sourceforge.net/livecd.php")?

lol

---

### Post by ettercap on 2008-06-27
yeah there are...
1.acronis disk director suite
2.partition magic

but they are not free.......

that is why LINUX rocks !!!!!!!!!!!

---

### Post by mcduck on 2008-06-28
Windows has a tool that allows you to convert a partition from FAT to NTFS without destroying it's contents. Apart from that all file system changes will erase all the contetnt from that partition. (ok, ext2 can be converted to ext3 and back again but that's a bit diferent as they are versions of the same filesystem).

I'd recommend either resizing the existing partition on that disk and then making a new one (this can be done noon-destructively if there's enough free space on that drive) or copying your stuff somewhere lese and then converting the drive. Personally, I'd go for Ext3, but you said that you have Windows backup on the disk and recovering it from Ext3 might be a bit of a problem as Windows doesn't natively handle anything else than it's own file systems..

---

### Post by flytripper on 2008-06-29
hmm yeah, no thanks to defrex.. I dived in on that one before the post under mine said otherwise!
now my files are gone!! lol.. First peice of bad advice I've had on here so far tbh.
I tried to recover files in ubuntu but no joy.. am using my virtualbox xp installation to use a windows gui program to restore them. lucky it has found the files......

Does anyone know any good recovery programs for ubuntu? I just want it to scan the disk , find the files, and provide an interface to copy them to another disk.

---

