---
title: "Using sfdisk to fix partition table problems"
date: 2009-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by unutbu on 2009-06-20
[SIZE="4"]Introduction:[/SIZE]

This is not a tutorial for beginners. Using sfdisk incorrectly can make a computer unbootable, or your data inaccessible. Please be careful.

Occasionally people end up with a partition table where a primary partition is located inside of an extended partition. At least from GParted's point of view, this is a heinous error which makes the entire partition table invalid. If you try to run GParted on this drive, it will simply show the entire drive as unallocated space. (See attached image, below.)

This can be quite worrisome if you know you have data on the drive, and just can't access it. It can also cause boot and installation problems. 

Often people don't realize there is a problem with their partition table because Windows may seem to deal with it just fine. (In fact, the problem is most likely caused by a maverick Windows partition editor which allowed the user to write a partition table which did not conform to specifications).

Below I describe how sfdisk can be used to fix this problem.

Although I only show how to fix this single problem, the technique is generalizable. Once you understand how sfdisk works, you can use it to do just about anything fdisk can do. (One thing sfdisk can not do is change C/H/S disk geometry.) 

The attraction of sfdisk is that you can ask someone to post their partition table as a file, you can edit and repost that file, then tell the person a single command to fix their partition table. 

Please note I am not an expert. Most of what I know comes from watching caljohnsmith and meierfra use sfdisk:

[http://ubuntuforums.org/showthread.php?t=1095606](http://ubuntuforums.org/showthread.php?t=1095606)
[http://ubuntuforums.org/showthread.php?t=1008458](http://ubuntuforums.org/showthread.php?t=1008458)
[http://ubuntuforums.org/showpost.php?p=6423096&postcount=22](http://ubuntuforums.org/showpost.php?p=6423096&postcount=22)
[http://ubuntuforums.org/showthread.php?t=1036239](http://ubuntuforums.org/showthread.php?t=1036239)
[http://ubuntuforums.org/showpost.php?p=6663919&postcount=716](http://ubuntuforums.org/showpost.php?p=6663919&postcount=716)
[http://art.ubuntuforums.org/showthread.php?t=224351&page=74](http://art.ubuntuforums.org/showthread.php?t=224351&page=74)
[http://ubuntuforums.org/showpost.php?p=7103244&postcount=847](http://ubuntuforums.org/showpost.php?p=7103244&postcount=847)

Many thanks to caljohnsmith and meierfra for generously sharing their knowledge. All mistakes are my own. I welcome corrections.

[SIZE="4"]Background:[/SIZE]

[list]
[*] Each drive has 1 partition table. 

[*]A partition table can have a maximum of 4 primary partitions. If the drive is called sdc, the the primary partitions are called sdc1, sdc2, sdc3, sdc4.

[*]A partition table can have at most 1 extended partition. The extended partition must also have a name whose numerical part is between 1 and 4: that is, the extended partition must be named sdc1 or sdc2 or sdc3 or sdc4.

[*]Logical partitions always have device names whose numerical part is greater than or equal to 5. (e.g. sdc5, sdc6, etc.)

[*]The partition table is located at sectors 447--512 on the drive.
[*]A sector = 512 bytes.

[*]You can save the partition table in its native binary format with the command
```

sudo dd if=/dev/sdc of=PT_sdc.img bs=1 count=66 skip=446
```

[*]and you can restore the partition table with the command
```

sudo dd of=/dev/sdc if=PT_sdc.img bs=1 count=66 skip=446
```

I mention this so you can have a picture in your mind about where the partition table is located. We won't be using dd to manipulate the partition table, however. We'll use sfdisk instead.
[/list]


[SIZE="4"]The sfdisk commands:[/SIZE]

You can save the partition table in an ascii format with the command```

sudo sfdisk -d /dev/sdc > PT.txt
```

This saves the partition table on /dev/sdc to a file called PT.txt.
What's particularly lovely is that is file is in ASCII format. 

You can edit it in a normal text editor, then tell sfdisk to write a new partition table based on our edited PT.txt:
```

sudo sfdisk --no-reread -f /dev/sdc -O PT.save < PT.txt
```

"--no-reread" means don't check if disk is unmounted
-f force
"-O PT.save" means save a backup of original partition table in PT.save. PT.save is in binary format.

To restore the partition table using PT.save:
```
sudo sfdisk --force -I PT.save /dev/sdc 
```

[SIZE="4"]An example use case:[/SIZE]
We start with a valid partition table:
```

sudo fdisk -l /dev/sdc

Disk /dev/sdc: 2004 MB, 2004877312 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006aba6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          80      642568+   b  W95 FAT32
/dev/sdc2              81         160      642600   83  Linux
/dev/sdc3             161         243      666697+   5  Extended
/dev/sdc5             161         200      321268+   7  HPFS/NTFS
/dev/sdc6             201         243      345366   82  Linux swap / Solaris

```

Here we dump the partition table to PT.txt:
```

sudo sfdisk -d /dev/sdc > PT.txt
cat PT.txt 

# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size=  1285137, Id= b
/dev/sdc2 : start=  1285200, size=  1285200, Id=83
/dev/sdc3 : start=  2570400, size=  1333395, Id= 5
/dev/sdc4 : start=        0, size=        0, Id= 0
/dev/sdc5 : start=  2570463, size=   642537, Id= 7
/dev/sdc6 : start=  3213063, size=   690732, Id=82
```

Now we do some math to find the end points:
```

        start         end    math   
sdc1       63     1285200    63+1285137=1285200
sdc2  1285200     1413722    1285200+128522=1413722
sdc3  2570400     3903795    2570400+1333395=3903795
sdc5  2570463     3213000    2570463+642537=3213000
sdc6  3213063     3903795    3213063+690732=3903795

```
If you wish to edit PT.txt, here are some things you should note:
[list]
[*] sdc3 is an extended partition. sdc5 and sdc6 are logical partitions that sit inside sdc3. You can confirm that by looking at the start and end positions of the three partitions.

[*] there is no partition called sdc4. 
Notice that sfdisk writes (in PT.txt) a blank entry in this case:
```

/dev/sdc4 : start=        0, size=        0, Id= 0
```

[*] sdc3 starts at 2570400 but sdc5 starts at 2570463. There is a 63 sector gap between the start of an extended partition and the start of a logical partition.

[*] sdc5 ends at 3213000 and sdc6 starts at 3213063. Again, there is a 63 sector gap between the end of a logical partition and the start of the next logical partition.

[*]In contrast, notice that there is no gap at all between primary partitions.
It is possible to have larger gaps between partitions, but never smaller than 63 sectors for logical partitions, (and obviously) never smaller than 0 for primary partitions. Partitions must not overlap.
[/list]

Now we create a messed up partition table:
```

cat PT_messed_up.txt

# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size=  1285137, Id= b
/dev/sdc2 : start=  1285200, size=  1285200, Id=83
/dev/sdc3 : start=  2570400, size=  1333395, Id= 5
/dev/sdc4 : start=  2570463, size=   642537, Id= 7
/dev/sdc5 : start=        0, size=        0, Id= 0
/dev/sdc6 : start=  3213063, size=   690732, Id=82
```


I edited PT_messed_up.txt by changing sdc5 to sdc4.

This makes a partition inside of an extended partition into a primary partition.
This is a no-no. 

Here we write the messed up partition table to disk:```

sudo sfdisk --no-reread -f /dev/sdc -O PT.save < PT_messed_up.txt
...
Successfully wrote the new partition table
```

Now we are in a pickle. How do we fix it?

Or, imagine you find a partition table in this invalid state. Below I show how to fix it.
```

sudo fdisk -l /dev/sdc

omitting empty partition (5)

Disk /dev/sdc: 2004 MB, 2004877312 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006aba6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          80      642568+   b  W95 FAT32
/dev/sdc2              81         160      642600   83  Linux
/dev/sdc3             161         243      666697+   5  Extended
/dev/sdc4             161         200      321268+   7  HPFS/NTFS
/dev/sdc5             201         243      345366   82  Linux swap / Solaris
```

Notice that "sudo fdisk" reports
```
omitting empty partition (5)
```

Whenever you see this, it means there is an error in the partition table.

By virtue of having a number between 1 and 4, sdc4 is a primary partition. 
It starts at cylinder 161, inside the extended partition sdc3. This is an error.

GParted refuses to operate on invalid partition tables:
```

gksu gparted /dev/sdc

======================
libparted : 1.8.9
======================
Can't have overlapping partitions.
```
See the attached image below.

GParted displays the entire drive as being unallocated.

Given PT_messed_up.txt, we need to move the primary partition sdc4 to a logical partition. Since the name sdc5 is free, we could simply change "sdc4" to "sdc5" in PT_messed_up.txt.
Indeed, this gives us back PT.txt.

So, to fix the problem, we simply run
```

sudo sfdisk --no-reread -f /dev/sdc < PT.txt
```

```
sudo fdisk -l /dev/sdc

Disk /dev/sdc: 2004 MB, 2004877312 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006aba6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          80      642568+   b  W95 FAT32
/dev/sdc2              81         160      642600   83  Linux
/dev/sdc3             161         243      666697+   5  Extended
/dev/sdc5             161         200      321268+   7  HPFS/NTFS
/dev/sdc6             201         243      345366   82  Linux swap / Solaris
```

Here we see the partition table is back in a valid state, and GParted successfully parses the partition table and once again allows us to operate on it.

If we make a mistake in PT.txt, we can revert to the previous partition table
by running
```

sudo sfdisk --force -I PT.save /dev/sdc 

```

[SIZE="4"]
Caveats:[/SIZE]
sfdisk can be finicky about the format of PT.txt. 
Spaces and end-of-line characters are important to sfdisk.
Here are some technical caveats:
[list]
[*] In PT.txt, you can't have trailing spaces at the ends of lines, after the "ID" field
[*] In PT.txt, the end of lines (EOLs) have to be unix-style line feeds (LF), and can't be Windows/DOS style carriage return + line feed (CR+LF).
[*] You can check for either problem by doing "cat -A partition_table.txt"
It puts a  $ at the end of lines that end with unix-style LF and 
it puts an M at the end of lines that end with Windows-style CR+LF and 
[/list]
[SIZE="4"]
Some further info:[/SIZE]
Example of using sfdisk to change a logical partition into a primary partition:
[http://ubuntuforums.org/showthread.php?t=1036239](http://ubuntuforums.org/showthread.php?t=1036239)

Example of using sfdisk to change a primary partition into a logical partition:
[http://ubuntuforums.org/showpost.php?p=7103244&postcount=847](http://ubuntuforums.org/showpost.php?p=7103244&postcount=847)

Here is the specification of the partition table format:
[http://www.win.tue.nl/~aeb/partitions/partition_tables.html#toc3](http://www.win.tue.nl/~aeb/partitions/partition_tables.html#toc3)

---

### Post by wieman01 on 2009-06-21
Nice, unutbu. Thank you!

---

### Post by tedrogers on 2009-12-29
```
[B]CAVEAT: Readers might want to read my initial post concerning my goals. 

It should help shed light on some of what I'm saying below.

[http://ubuntuforums.org/showthread.php?t=1366638](http://ubuntuforums.org/showthread.php?t=1366638)[/B]
```

Hi all (and hi there Wieman01...it's been a while!),

I'm trying to reorder my partitions using sfdisk, and I would welcome some assistance so I get it right.

This is the output of my PT.txt:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20964762, Id=83, bootable
/dev/sda2 : start=115105725, size=  2104515, Id=82
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start= 20964825, size= 94140900, Id=83
```

As you can see, /sda2 is at the end of the disk (this is my swap space), /sda3 has no physical size, and /sda4 (my /home space) is before /sda2 (swap) and after /sda1 (boot).

What I want to do is remove sda3 completely, physically move sda2 on the disk to just after the boot space, and move sda4 to directly after the swap space and rename it to sda3.

To do all the physical moving of partitions (i.e. move sda2 and sda4), I will use gparted, but to rename them can I use sfdisk to change the partition table like this (assuming that it would have new START and SIZE information based on the fact I had moved the partitions using gparted):

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20964762, Id=83, bootable
/dev/sda2 : start=115105725, size=  2104515, Id=82
/dev/sda3 : start= 20964825, size= 94140900, Id=83
```

Thanks for your assistance. I'm happy to answer any questions you might have.

All the best.

---

### Post by meierfra. on 2009-12-29
You can reorder the partition with fdisk:


```
sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
w  #  write the changes to disk
```

Reordering the partition table  requires reinstall grub. Asked for help if needed.

Also instead of mowing the swap partition, I would just delete it. Then create a new swap partition after you moved /dev/sda3. That's much faster.

Only drawback, the UUID of the swap partition will change. But that is easy to fix. After you repartitioned and reordered

```
sudo mkswap -U the_old_uuid /dev/sda3
```

(you can look up the old UUID  in /etc/fstab, or before repartitioning via "sudo blkid")

---

### Post by wieman01 on 2009-12-29
> **tedrogers said:**
> Hi all (and hi there Wieman01...it's been a while!)...
Hey there, Ted! Nice seeing you around!

---

### Post by tedrogers on 2009-12-29
Okay, thanks for your replies!

If I do this (I haven't written the partition table yet),  it produces this partition list:

```
Disk /dev/sda: 255 heads, 63 sectors, 7296 cylinders

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 80   1   1    0 254  63 1023         63   20964762 83
 2 00 254  63 1023 254  63 1023   20964825   94140900 83
 3 00   0   0    0   0   0    0          0          0 00
 4 00 254  63 1023 254  63 1023  115105725    2104515 82
```

So as you can see I still have a zero size partition. How would I resolve this?

Also, is there any problem with leaving my swap at the end of the disk like it would be if I reordered the partitions using fdisk as described. I might just leave it at the end if it won't do any harm or hinder the performance.

Thanks.

---

### Post by SecretCode on 2009-12-29
That "partition of zero size" isn't a problem - there are 4 slots for primary partitions and you don't have to use them all. Some tools display that empty slots as zeroes.

---

### Post by tedrogers on 2009-12-29
> **SecretCode said:**
> That "partition of zero size" isn't a problem - there are 4 slots for primary partitions and you don't have to use them all. Some tools display that empty slots as zeroes.

That partition of zero size used to be a partition of 10GB.

Are you saying that if I rename sda4 as sda3 then it will no longer display that "slot"?

---

### Post by SecretCode on 2009-12-29
I'm confused. You only have three partitions shown in any of your posts in this threads.

What I'm saying is that sfdisk will always display a row for every one of the 4 possible primary partitions. E.g. here's one of my external drives, which has only one partition:
```
$ sudo sfdisk -d /dev/sdc
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size=976768002, Id= 7
/dev/sdc2 : start=        0, size=        0, Id= 0
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0
```

I can't see any reason why you need to 'rename' sda4 to be sda3, or have the partition table entries in disk order. What are you trying to achieve?

---

### Post by tedrogers on 2009-12-30
> **SecretCode said:**
> I'm confused. You only have three partitions shown in any of your posts in this threads.

What I'm saying is that sfdisk will always display a row for every one of the 4 possible primary partitions. E.g. here's one of my external drives, which has only one partition:
```
$ sudo sfdisk -d /dev/sdc
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size=976768002, Id= 7
/dev/sdc2 : start=        0, size=        0, Id= 0
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0
```

I can't see any reason why you need to 'rename' sda4 to be sda3, or have the partition table entries in disk order. What are you trying to achieve?

Ahh, I see what you mean now.

This is what I'm aiming for...it's quite fussy really...but that's how we learn.

[http://ubuntuforums.org/showthread.php?t=1366638](http://ubuntuforums.org/showthread.php?t=1366638)

---

### Post by meierfra. on 2009-12-30
> So as you can see I still have a zero size partition. How would I resolve this?

I didn't know, that fdisk would leave an  empty partition in the third slot. 

If you want to rewrite the partition table with sfdisk, do 

```
sudo sfdisk -d /dev/sda > PT.txt
```


and then swap the last two rows in "PT.txt". (I'm pretty sure that you do need the fourth row with all values equal to 0)

PT.text now should look like
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20964762, Id=83, bootable
/dev/sda2 : start= 20964825, size= 94140900, Id=83
/dev/sda4 : start=115105725, size=  2104515, Id=82
/dev/sda3 : start=        0, size=        0, Id= 0


```
(You can also change /dev/sda4 to /dev/sda3 and vice versa, but sfdisk ignores whose labels, they are just there to make to table easier to read)

Then rewrite the partition table with
```

sudo sfdisk --no-reread -f /dev/sda -O PT.save < PT.txt
```

Make sure that you save the file PT.save some place other than on your  hard drive. (If the partition table is messed up you won't be able to access your hard drive until you fixed it).

But you should be aware that editing the partition table is risky and that moving the empty partition from the third to the fourth spot has no benefits whatsoever. **So I do not recommending doing this.**

---

### Post by tedrogers on 2009-12-31
Thanks for staying with me on this meierfra.

But if I reorder the partitions in the manner you suggest at the top of the last post, from this:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20964762, Id=83, bootable
/dev/sda2 : start=115105725, size=  2104515, Id=82
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start= 20964825, size= 94140900, Id=83
```

...to this:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20964762, Id=83, bootable
/dev/sda2 : start= 20964825, size= 94140900, Id=83
/dev/sda4 : start=115105725, size=  2104515, Id=82
/dev/sda3 : start=        0, size=        0, Id= 0
```

...wouldn't I first have to physically move the data associated to these regions on the disk using gparted's MOVE function?

Or am I just confusing myself now?

I suspect it is the latter, rather than the former. :)

And when you say I can reorder the naming of the partitions, but then **sfdisk** ignores these...does this mean that the **fdisk** would also ignore these and would not present them to me in numerical ascending order?

Sorry for all the questions, I just want to be sure I fully understand the implications of this before I attempt anything.

I'm also going to fully backup my system using partimage first! ;)

Thanks.

---

### Post by SecretCode on 2009-12-31
tedrogers, can you run GParted? And post a screenshot?

It seems to be that your disk is already full (of partitions) and the partitions are in the order you want them *on the disk*, just not in the partition table. There's no data to move!

---

### Post by meierfra. on 2009-12-31
> ...wouldn't I first have to physically move the data associated to these regions on the disk using gparted's MOVE function?

Yes. 

> but then sfdisk ignores these...does this mean that the fdisk would also ignore these and would not present them to me in numerical ascending order?
No.  

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20964762, Id=83, bootable
/dev/sda2 : start= 20964825, size= 94140900, Id=83
/dev/sda4 : start=115105725, size=  2104515, Id=82
/dev/sda3 : start=        0, size=        0, Id= 0
```


and

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20964762, Id=83, bootable
/dev/sda2 : start= 20964825, size= 94140900, Id=83
/dev/sda3 : start=115105725, size=  2104515, Id=82
/dev/sda4 : start=        0, size=        0, Id= 0 


```


and

```
# partition table of /dev/sda
unit: sectors

Just: start=       63, size= 20964762, Id=83, bootable
some: start= 20964825, size= 94140900, Id=83
comment : start=115105725, size=  2104515, Id=82
        : start=        0, size=        0, Id= 0

```
will produce the exact same partition table. sfdisk will write the partition in the exacts same order has they are physically listed in the file PT.txt.

```
tedrogers, can you run GParted? And post a screenshot?
```
Good idea.

---

### Post by tedrogers on 2010-01-01
Here we go.

[IMG]http://img231.imageshack.us/img231/4532/screenshotdevsdagpartedq.png[/IMG]

---

### Post by SecretCode on 2010-01-01
Good stuff. Now, ignoring the partition numbers, how do you want to move those partitions in the screenshot. 

Possibly not at all? :)

---

### Post by tedrogers on 2010-01-01
Thanks loads for your help!

I'd like the order to be sda1 (boot), sda2 (home) and sda3 (swap).

Right now it is sda1 (boot), sda4 (home) and sda2 (swap).

I want to keep the positions on disk, I don't see a point in changing them, so I'll leave the swap at the end of the drive.

So what do I need to do then?

---

### Post by meierfra. on 2010-01-01
> I want to keep the positions on disk, I don't see a point in changing them, so I'll leave the swap at the end of the drive.

That makes it easier (although you could move your home partition to the end, see my first post)

> So what do I need to do then? 

Download the attach file PT.txt to your desktop and rewrite the partition table with
```

cd ~/Desktop
sudo sfdisk --no-reread -f /dev/sda -O PT.save < PT.txt
```

Make sure that you save the file PT.save some place other than on your  hard drive. (If the partition table is messed up you won't be able to access your hard drive until you fixed it).

But you should be aware that editing the partition table is risky and  has no benefits whatsoever. **So I do not recommending doing this.**

---

### Post by tedrogers on 2010-01-01
Is there any benefit to moving my home partition to the end of the disk, so that the partitions go sda1 (boot), sda2 (swap), sda3 (home)?

I suppose what I'm asking is will the system run slightly better with the swap file near the boot partition?

---

### Post by meierfra. on 2010-01-01
> will the system run slightly better with the swap file near the boot partition? 

No. Theoretically,  there might be  a very small improvement. But not enough to notice. And with 1.5GB of Ram you probably aren't even using your swap. (You can check by typing "free" in  a terminal)

---

### Post by tedrogers on 2010-01-01
Great! You're right...zero usage on the swap.

Thanks for all your help...and it seems to have worked well.

[IMG]http://img707.imageshack.us/img707/4147/screenshotdevsdagparteda.png[/IMG]

I have one error though, and I hope this will be gone once I reboot.

[IMG]http://img94.imageshack.us/img94/6796/screenshotjeu.png[/IMG]

[IMG]http://img46.imageshack.us/img46/3995/screenshotinformationab.png[/IMG]

...which it was, so everything is fine!

[IMG]http://img231.imageshack.us/img231/8809/screenshotdevsdagpartedf.png[/IMG]

Now what else can I mess about with pointlessly in the hope that I don't break it?! ;)

Happy new year! :)

---

### Post by DShad on 2010-02-12
I need help please...

I managed to find the PT.txt I have. Here it is:

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start= 0, size= 0, Id= 0
/dev/sda2 : start= 63, size=1929743802, Id=83
/dev/sda3 : start=1929743865, size= 23776200, Id= f
/dev/sda4 : start= 0, size= 0, Id= 0
/dev/sda5 : start=1929743928, size= 23776137, Id=82


I want to get rid of the sda1 & sda4 so I can only have something like:
/dev/sda1 : start= 63, size=1929743802, Id=83
/dev/sda2 : start=1929743865, size= 23776200, Id= f
/dev/sda3 : start=1929743928, size= 23776137, Id=82

Can I just do that (as above) and put it back as my new PT.txt?

Thanks for your help.
DShad is online now Report Post   	Edit/Delete Message

---

### Post by tedrogers on 2010-02-13
I think that would do it yes [***[COLOR="Red"]BUT I WAS DEFINITELY WRONG ABOUT THIS - SEE BELOW[/COLOR]***]...but as I had **a lot** of help getting mine to work, and the person who helped me actually configured the file for me to use, I would not be totally confident in advising you to try this.

If you back up your entire system with partimage though, then you can mess about to your hearts content without fear of not being able to go back if you have problems.

[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)

---

### Post by meierfra. on 2010-02-13
```
Can I just do that (as above) and put it back as my new PT.txt?
```
**No, you can't. **
Details to follows.

---

### Post by meierfra. on 2010-02-13
> /dev/sda1 : start= 0, size= 0, Id= 0
/dev/sda2 : start= 63, size=1929743802, Id=83
/dev/sda3 : start=1929743865, size= 23776200, Id= f
/dev/sda4 : start= 0, size= 0, Id= 0
/dev/sda5 : start=1929743928, size= 23776137, Id=82


I want to get rid of the sda1 & sda4 so I can only have something like:
/dev/sda1 : start= 63, size=1929743802, Id=83
/dev/sda2 : start=1929743865, size= 23776200, Id= f
/dev/sda3 : start=1929743928, size= 23776137, Id=82

You cannot get rid of /dev/sda4. You partition table always has to  have four primary partition. (A primary partition is partition listed  in the MBR and has a number from 1-4)
But  a "zero" row (like /dev/sda4)  causes no harm. You will never see it anywhere, except if  you use a tool like "sfdisk" which is designed to display every little detail of the partition table.

You actually have only two real partitions, /dev/sda2 and /dev/sda5.  /dev/sda3 is an extended partition, that is a container for a logical partition (A logical partition, is a partition which is not listed in the MBR and   is  numbered 5 or higher) .
So you can either turn /dev/sda5 into a primary partition and delete the extended partition /dev/sda3 or your have  to leave /dev/sda5 as it is. 

**Option 1    Leave /dev/sda5 as a logical partition**

/dev/sda1 : start= 63, size=1929743802, Id=83
/dev/sda2 : start=1929743865, size= 23776200, Id= f
/dev/sda3 : start= 0, size= 0, Id= 0
/dev/sda4 : start= 0, size= 0, Id= 0
/dev/sda5 : start=1929743928, size= 23776137, Id=82

**Option 2  Convert /dev/sda5 into a primary partition:**

/dev/sda1 : start= 63, size=1929743802, Id=83
/dev/sda2 : start=1929743928, size= 23776137, Id=82
/dev/sda3 : start= 0, size= 0, Id= 0
/dev/sda4 : start= 0, size= 0, Id= 0


In either case, since your current /dev/sda2 is converted to /dev/sda1, you will have to reinstall Grub.

**But I recommend to leave the partition table as it is. ** There is no reason to change your current partition table and messing with a partition table is risky.

---

### Post by meierfra. on 2010-02-13
[SIZE="5"]Note for anybody considering to use sfdisk for cosmetic reason[/SIZE]

Unutbu's  HowTo is meant to fix a broken partition table, not to change the appearance of  partition table.  Using sfdisk to alter the partition table is risky and you have to know exactly what you are doing.  I will no longer give assistance in this thread, except if your partition table is broken, even if you are getting wrong  advice from other forums members.

---

### Post by tedrogers on 2010-02-15
Thanks meierfra.

I have edited my post to reflect your advice.

---

### Post by opodaniel on 2010-10-31
Normally the computer is working without any problems, but I see that I have some errors in the MBR. The Hdd is 250 Gb.
Here are the info :

~$ sudo sfdisk -l

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   3924    3925-  31527531    7  HPFS/NTFS
/dev/sda2       3925+   5428-   1504-  12078080   83  Linux
/dev/sda3       5428+  30400   24973- 200588993    5  Extended
        start: (c,h,s) expected (1023,254,63) found (1023,210,30)
/dev/sda4       5915+   8693    2779-  22322282+   7  HPFS/NTFS
/dev/sda5       5428+   5793-    365-   2928640   83  Linux
/dev/sda6       5793+   5914-    122-    974848   82  Linux swap / Solaris
/dev/sda7       8694+  27835   19142- 153758083+   7  HPFS/NTFS
/dev/sda8      27836+  30400    2565-  20599579    7  HPFS/NTFS
        start: (c,h,s) expected (1023,254,63) found (1023,120,8)

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 63055062, Id= 7, bootable
/dev/sda2 : start= 63055872, size= 24156160, Id=83
/dev/sda3 : start= 87214079, size=401177986, Id= 5
/dev/sda4 : start= 95024545, size= 44644565, Id= 7
/dev/sda5 : start= 87214080, size=  5857280, Id=83
/dev/sda6 : start= 93073408, size=  1949696, Id=82
/dev/sda7 : start=139669173, size=307516167, Id= 7
/dev/sda8 : start=447192907, size= 41199158, Id= 7

GParted see all Hdd as Unallocated while spiting this on terminal : Can't have overlapping partitions.

---

### Post by driven1 on 2011-05-05
Hello,
I also have the problem that gparted cannot read the partition tables. I want to use some free space to install Natty, but the installer only sees the entire hard disk. I would also like to eliminate one of the two swap disks. I would appreciate some advice before I start making modifications. I have an XP primary partition. In the extended partition I have a 2.1gb XP backup file, then 76 gb that I use for shared storage between Linux Mint and XP, I have 40 gb allocated for Mint, 8gb unallocated, and two swap disks 1.1gb and 1.8gb. I need to fix this so I can use gparted. Thanks.

```
 sudo fdisk -l /dev/sda
omitting empty partition (10)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9358c633

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19458   125573737+   f  W95 Ext'd (LBA)
/dev/sda5            3825        4085     2096451    7  HPFS/NTFS
/dev/sda6            4086       13287    73907476    7  HPFS/NTFS
/dev/sda7           19327       19458     1049600   82  Linux swap / Solaris
/dev/sda8           14262       19113    38964224   83  Linux
/dev/sda9           19113       19327     1714176   82  Linux swap / Solaris

Partition table entries are not in disk order

```

here are the contents of the current PT.txt
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 61432497, Id= 7, bootable
/dev/sda2 : start= 61432621, size=251147475, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 61432623, size=  4192902, Id= 7
/dev/sda6 : start= 65625588, size=147814952, Id= 7
/dev/sda7 : start=310480896, size=  2099200, Id=82
/dev/sda8 : start=229113856, size= 77928448, Id=83
/dev/sda9 : start=307044352, size=  3428352, Id=82
```

---

