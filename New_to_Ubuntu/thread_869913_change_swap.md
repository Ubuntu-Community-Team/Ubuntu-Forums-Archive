---
title: "change swap"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by heiowge on 2008-07-25
I have an eeepc and I've got hardy installed to the SD card.  Can I remove the swap partition that's already on there and give myself more space to install to?

I use the ssd for XP (needed for work) and an external USB flash drive for storage.

---

### Post by markjensen on 2008-07-25
A **swapoff** command will turn off swap.  You can remove any existing swap partition or file at that point.   Then create your new swap partition or file.  (yes, you can have a _file_ as swap in Linux).   Edit your /etc/fstab to have the new updated swap info, then a quick **swapon -a** will turn on any swap space you have declared.

If you want to just remove all swap, it should be pretty easy.   If you want help in adding a swap file, just post again, and I (or someone else) will help with that.

---

### Post by heiowge on 2008-07-25
I want to completely remove the swap partition (eeePC doesn't need them aparently), and reuse the space freed up by adding it to the root (if I can).  I just don't know exactly how...:(

---

### Post by heiowge on 2008-07-25
Why does your "A Carafe of Ubuntu" have a different placement of the beans than my carafe?:confused:

---

### Post by markjensen on 2008-07-25
Well, let's confirm what the current partitioning is.

Can you open up a terminal and post the output of an **fdisk -l** (as root, or using sudo.  not sure how the EeePC is set up)

This will list the partitions.

Then also post the contents of your /etc/fstab file.   We can tell you the exact line to remove, though it should be obvious, as it is the only one referencing swap.   You also need to turn swap off like indicated above.

Then remove the partition.   Not sure about resizing, as I have never resized an ext3 (I assume EeePC uses ext3, but I might be wrong).   You can just create that space as FAT or ext3, if you just need extra storage space.

---

### Post by markjensen on 2008-07-25
> **heiowge said:**
> Why does your "A Carafe of Ubuntu" have a different placement of the beans than my carafe?:confused:
Different posting levels, I assume?  I never paid attention to it.

---

### Post by heiowge on 2008-07-25
Will post them but have to do it later as I'm not on the eeePC atm and about to go out.  I'll try and post tonight (within 7 hrs.)

Ta.

---

### Post by heiowge on 2008-07-25
Disk /dev/sda: 2000 MB, 2000388096 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25f025ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         242     1943833+   7  HPFS/NTFS

Disk /dev/sdb: 4024 MB, 4024958976 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b51b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         461     3702951   83  Linux
/dev/sdb2             462         489      224910    5  Extended
/dev/sdb5             462         489      224878+  82  Linux swap / Solaris

---

### Post by heiowge on 2008-07-25
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=d8091790-4172-4c82-bc5c-899c971d963a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=53650b30-9072-4daf-98ee-35d76afc5b75 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Does that help?

---

### Post by markjensen on 2008-07-25
Your swap is on sdb5 (which really is consuming the whole extended partition sdb2, so they are kind of the same thing).   It is only 1bout 220MB in size, you aren't going to be gaining a heck of a lot here.

If you want to proceed, you can turn **swapoff**, then do the following:
uncomment the UUID line that specifies your swap space by placing a # in front.

Try it like that for a while, that way you can re-add your swap, if you find oddities in performance, or problems if you call up multiple apps or such.   I would hate to direct you on a full removal if you are going to run into problems and want the swap back.

If, after satisfactory testing, you still want to reclaim that 200MB of space, you can run either fdisk or gparted to remove both the sdb5 and sdb2 (you will have to remove them in that order, due to how they were created).

Not sure if parted can 'grow' an ext3 partition.  If not, you may have to settle for creating a new separate partition (or totally re-create your partitions, which will be a lot more involved).

---

### Post by Eredeath on 2008-07-27
I could use some help in creating a swap partition. I have 4gb of memory so i thought i didn't need it, but now that i want to hibernate the computer i can't.

---

### Post by markjensen on 2008-07-28
> **Eredeath said:**
> I could use some help in creating a swap partition. I have 4gb of memory so i thought i didn't need it, but now that i want to hibernate the computer i can't.

That sounds like a good new question probably best noticed if it was its own thread.   In your case, I might suggest not mucking with your partitions, unless you are really itching to do so.   This can be accomplished by using a swap **file**.   Create it at the size you want with the following (and you can safely try different sizes without fear, and without constantly changing partitions):
**sudo dd if=/dev/zero/ of=dev/sd*x1*/swapfile bs=1M count=4096**
You will need to change sdx1 to accurately point to whichever partition you choose to put your swap (make sure you have enough room there!).  In the example above, I choose to use 1MB blocks, and told it to create 4096 of them, which would be 4GB.  I think that is the size you will need, not sure if less would work.

Now, that creates a large file, called "swapfile", but it isn't going to be **used** as a swap until you let Linux know it is swap.   Use **mkswap** on it, and add an entry to your fstab, as you can see in [this Ubuntu FAQ page](https://help.ubuntu.com/community/SwapFaq).

Hope this helps!

---

### Post by Eredeath on 2008-07-28
awsome, thx i'll try that out when i get on my own computer... untill then can you explain the code to me to make the swap file? I never seen the commands dd if= or of= before
are these to create a "blank" space on the partition?

---

### Post by markjensen on 2008-07-28
**dd** is a basic "data dump" app.  It is designed to take data from a source to a destination.

**if** is the "input file".  Remember in unix and derivatives, pretty much everything is a file.  In this case, the input file is a source that supplies zeros.

**of** is the "output file".  Here we specify a new filename, path fully qualified, so it knows what device (hard drive), partition, and file location and name.

**bs** is the block size.   You can leave it in default bytes, or specify a value in K or M type kilo- or mega- units.  Megabytes seemed to be a good value to play with, but feel free to change this if you please.

**count** is the number of iterations, or blocks of the specified size to copy/dump.   Since I specified a size of 1MB, this is the number of Megabytes to create with a zero-fill.  1024MB = 1GB, so 4096MB = 4GB.

And, yes, the result is a zero-filled file that is exactly 4GB in size.   The additional steps will allow the system to recognize it as a "swap".

---

### Post by Eredeath on 2008-07-28
excellent, thank you for the explanation!

---

