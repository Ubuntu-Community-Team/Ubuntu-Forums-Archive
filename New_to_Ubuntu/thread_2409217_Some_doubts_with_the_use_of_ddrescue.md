---
title: "Some doubts with the use of ddrescue"
date: 2018-12-29
forum: New to Ubuntu
---

### Post by dimmetrix on 2018-12-29
Hi,

I would like to ask you some doubts I have regarding ddrescue.

First of all, I want to clarify that I have chosen to make an image of the disk with this utility because I can easily mount the created disk image. Using the image directly and without having to copy, unzip, or anything like that.

I need to clone disks and pendrives to IMG files on a backup disk. This is the line that I intend to use:

```
ddrescue -d -v /dev/sdX /dev/sdX/img/image1.img /dev/sdX/img/ddrescue.log
```

As the discs I have so far have not had any errors, I'm not sure to use **option d** to enable direct access to the disk for reading. According to the manual, I understand that it disables the cache, but I ask, what would be the benefit of disabling the cache? In what situations is it advisable to use this option?

On the other hand, because I need to analyze the information of the sectors that are not assigned later, I need to copy sector by sector and I am not sure if this utility does this. Is it used to copy sector by sector, including those that are not in use and contain information that has been marked as deleted?

If I wanted to backup only the assigned sectors, which command should I execute?

Thank you.

---

### Post by dimmetrix on 2018-12-29
Hi again,

I was doing a ddrescue test and I have obtained the following:

```
About to copy 138412 kBytes from /dev/sda4 to image-132M.img.
Starting positions: infile = 0 B,  outfile = 0 B
Copy block size: 128 sectors       Initial skip size: 128 sectors
Sector size: 512 Bytes

Press Ctrl-C to interrupt
rescued:   138412 kB,  errsize:       0 B,  current rate:    2162 kB/s
    ipos:    138346 kB,   errors:       0,    average rate:    9886 kB/s
   opos:    138346 kB, run time:      14 s,  successful read:       0 s ago
Finished 
```


My Doubt is:

1 - Do ipos and opos indicate the MB that is transferred between the origin (in) and the output (out)?

2 - Why is there a difference of 128 sectors among ipos, opos with respect to rescued? 

 3 - If I'm understanding, the part where rescued appears must have the same size as About to copy. If so, it means that all sectors have been able to be read/recovered. Am I in the running?

---

### Post by jeremy31 on 2018-12-29
Threads merged, please do not post duplicate threads about the same issue

---

### Post by TheFu on 2018-12-29
using this
```
$ sudo ddrescue -d -v /dev/sdX /dev/sdX/img/image1.img /dev/sdX/img/ddrescue.log
```
is a really bad idea.

Can't just access disks directly with subdirectories off the device file. The are block devices, not directories. That means don't use /dev/sdX/img/image1.img.  It won't do anything good, if it does anything at all.

 /dev/sdX  - is the entire HDD, including the partition table and all partitions.  This can be handy, but only if that is really your intent.  Usually, it is best to create images at the partition level.

Never read and write to the same disk with image tools.  'X' needs to be 'X', 'Y' and "Z" if you are trying to spell out the different block devices.

```
sudo ddrescue /dev/sda /dev/sdg /mounted/area/not/sda/or/sdg/imaging.log
```
or
```
sudo ddrescue /dev/sda /mnt/path/to/other/disk/image.img  /mounted/area/not/sda/or/sdg/imaging.log
```
is probably what you want.
Or
```
sudo ddrescue /dev/sda1 /dev/sdg1 /mounted/area/not/sda/or/sdg/imaging_partition1.log
```

---

### Post by dimmetrix on 2019-01-02
> **TheFu said:**
> 
Can't just access disks directly with subdirectories off the device file. The are block devices, not directories. That means don't use /dev/sdX/img/image1.img.  It won't do anything good, if it does anything at all.

Very true, you are absolutely right. I did not realize that this was an unmounted route. I just typed it wrong because I know that before I mount it and the mounted route is /mnt or /media.

Thank you so much for everything. Now I understand better how I should use it. I only see that you have not specifically used the -d (direct) option. Is it necessary to use it to create an image of a disk that has no errors? In which scenarios is it recommended to use it?

Finally, could you answer the questions in the second thread?

[https://ubuntuforums.org/showthread.php?t=2409217&p=13826812#post13826812](https://ubuntuforums.org/showthread.php?t=2409217&p=13826812#post13826812)

---

