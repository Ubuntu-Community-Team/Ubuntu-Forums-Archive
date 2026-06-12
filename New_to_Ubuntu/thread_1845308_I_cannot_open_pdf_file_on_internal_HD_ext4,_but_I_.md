---
title: "I cannot open pdf file on internal HD ext4, but I can open same file on external ntfs"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by vincegata on 2011-09-16
Hello,

I am running Ubuntu 11.04.

I cannot open some larger pdf files. I can open some smaller pdf files but I am not sure if this problem is related to size of the files.

I can open all pdf files from the external (backup) HD formatted as ntfs.

I tried both Evince and Acrobat, the result is the same.

Please help.

TIA!

---

### Post by Lisiano on 2011-09-16
Could you tell us the size of the files and how much RAM your PC has left (System -> Administer -> System Monitor -> Resources)? Is there any error while/after/before opening?

---

### Post by vincegata on 2011-09-16
This is not size related. I can open pdf file (a book) which is 16GB, but I cannot open the class notes that are 100 KB.

Memory: 2.1 GiB out of 7.7 GiB.

There are no errors, Acrobat just silent, Evince is trying to open with "wait" icon spinning and it stops in 10 sec.

---

### Post by Lisiano on 2011-09-16
Odd. Maybe something is wrong with your EXT4 partition. First run mount and find where your / or /home or /wherever.
```
lisiano@Lisiano-Ubuntu:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
/dev/sda1 on /home type ext4 (rw,commit=0)
lisiano@Lisiano-Ubuntu:~$ 
```
So say It's in your Documents (~/Documents) then you need /home (sda1)
now run the following command and post it's output
```
sudo fsck.ext4 -f -n -v /dev/sdXX
```
Replace XX with the needed partition you got from mount.
-f means Force fsck to run even if it's clean.
-n do a read-only pass (Nothing will be changed AKA Everything is Safe)
-v Verbose

---

### Post by vincegata on 2011-09-16
e2fsck 1.41.14 (22-Dec-2010)
Warning!  /dev/sda2 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 661725 was part of the orphaned inode list.  IGNORED.
...........................................
Inode 21762324 was part of the orphaned inode list.  IGNORED.
Deleted inode 21763446 has zero dtime.  Fix? no

Inode 21763809 was part of the orphaned inode list.  IGNORED.
..........................................
Inode 22423018 was part of the orphaned inode list.  IGNORED.

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(2655674--2655675) -(38240459--38240860) -(51262464--51264361) -(53037861--53037868) -(53062486--53062493) -(53067084--53067097) -
.........................................................................
90290362) -(90304816--90304835) -(90305509--90305511) -(90307388--90307389) -(90307392--90307399)
Fix? no

Free blocks count wrong (62696568, counted=62575178).
Fix? no

Inode bitmap differences:  -661725 -2228266 -13238656 -13239302 -13239311 -13239398 -13239635 -13239753 -13239780 -13239789 -13239945 -13239964 -13240206 -13240256 -
.........................................................................
22153282 -22153305 -22423018
Fix? no

Free inodes count wrong (29514300, counted=29512230).
Fix? no


/dev/sda2: ********** WARNING: Filesystem still has errors **********


  402884 inodes used (1.35%)
     846 non-contiguous files (0.2%)
     426 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 369503/176/1
56958088 blocks used (47.60%)
       0 bad blocks
      21 large files

  322860 regular files
   35739 directories
      59 character device files
      26 block device files
       0 fifos
     396 links
   46134 symbolic links (35052 fast symbolic links)
      58 sockets
--------
  405272 files

---

### Post by vincegata on 2011-09-16
If I copy a pdf file from external to internal drive I cannot open it ( I can open it on external).

I use rsync to backup my files from internal (ext4) to external (ntfs). However I can open other pdf files that went through rsync. 

I also checked permissions and everything is in order.

---

### Post by Lisiano on 2011-09-16
Odd #2. Looks more or less normal. Those errors are from the partition being in use. So no need to worry.
Correct me if I'm wrong but I understand your problem this way, you try to open a file on your internal HDD and it fails, moving the file to a external HDD and it works? Does the reverse apply (Moving back to internal and overwriting)?

---

### Post by Lisiano on 2011-09-16
I'm just going to throw stuff I can think up. I'm seriously dumbstruck as to why exactly it might be doing this.
Did you recently update evince or adobe reader?
Did you do any major updates?
If you have a older kernel, does opening the PDF under a older kernel work?
Since when are you experiencing this behavior and did this happen before?
If you have another Ubuntu PC that you can use, does opening the files from their internal drives work?
(If you have a VM) Can you open the same files inside a VM via shared-folders?
Can you see any pattern at all between which files open and which don't? For example mostly don't open small files or large files, or even mostly books open while notes don't.
If you can. Give us as much information that you can think of. Vague is better than nothing. Although solid info is better than vague.

---

### Post by vincegata on 2011-09-16
Ah, sorry, my bad :((

I was running Nautilus under gksu, and I forgot about it.

Thank you for your time, at least I know my HD is alright.

---

