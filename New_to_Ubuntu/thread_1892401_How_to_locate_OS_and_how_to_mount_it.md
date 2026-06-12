---
title: "How to locate OS and how to mount it"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by JustMyAlias on 2011-12-07
I need some really basic step-by-step help please... :confused:
 
I am running Ubuntu 11.10 from a flash drive.
 
I could see my Windows drive previously, but have 'lost' it. I don't know how to find an 'Explorer' type equivalent, where I can see everthing (files, folders, etc) on my harddrive.
 
Also, I need to be able to mount it, so that I can see what is on it. (When I double clicked on it - I got the "Unable to mount OS" error.) I have tried and tried to install the pysdm program to no avail, so am wondering if there is a manual method for mounting it.
Help and thanks!!

---

### Post by josephmills on 2011-12-07
open terminal (ctrl+alt+t)
then
```
sudo fdisk -l 
```

idenity the the partition then 

```
mount /dev/<partiotion> /mnt/
```
```
cd /mnt/ && ls 
``` 
```
sudo chroot /mnt/
```
```
ls
```
when done doing what ever 
```

sudo umount /nmt/ 

```
hope that this helps ! :popcorn:

---

### Post by JustMyAlias on 2011-12-07
ok - I may have done something stupid...
before your response, I tried
sudo + the 'forced' mount option shown in the error - it did not work but I have since closed that window (so no specific details) and hope it didn't change anything with the actual windows partition ???
 
I tried what you have written...
after the: sudo fdisk -l
I entered: mount /dev/sda2 /mnt/
and I got this error:
mount: only root can do that
 
do I precede this with 'sudo' and try again?

---

### Post by josephmills on 2011-12-07
> **JustMyAlias said:**
> 
 
do I precede this with 'sudo' and try again?


Yes you are right! :D sorry about the sudo command

---

### Post by JustMyAlias on 2011-12-07
oh........
so close, yet...
 
I got this error...
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or anoher software may use it which could be identified for exampe by the help of the 'fuser' command.
 
So in my Home window (I found it...) - I right clicked on OS and unmounted it (still nothing if I double-clicked on it...), then tried again.
 
Now...
I got a whole list of 'details' that includes 3 invalid argument statements that all say
actual VCN (0x20) of index buffer is different from expected VCN (0x0).
 
:(

---

### Post by josephmills on 2011-12-07
> **JustMyAlias said:**
> oh........
so close, yet...
 
I got this error...
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or anoher software may use it which could be identified for exampe by the help of the 'fuser' command.
 
So in my Home window (I found it...) - I right clicked on OS and unmounted it (still nothing if I double-clicked on it...), then tried again.
 
Now...
I got a whole list of 'details' that includes 3 invalid argument statements that all say
actual VCN (0x20) of index buffer is different from expected VCN (0x0).
 
:(

Boot a live cd and select "try" and do again sorry :D

---

### Post by JustMyAlias on 2011-12-07
also - the OS has disappeared from my listing now.
 
I am not sure I understand what you mean...
I tried running an older version of Ubuntu from a disk, and it didn't work.  That is why I created the flashdrive.  Will a disk work differently than the flashdrive?

---

### Post by josephmills on 2011-12-07
> **JustMyAlias said:**
> also - the OS has disappeared from my listing now.
 
I am not sure I understand what you mean...
I tried running an older version of Ubuntu from a disk, and it didn't work.  That is why I created the flashdrive.  Will a disk work differently than the flashdrive?

Yes it will as there is a folder under / (root) 
called dev (or device) 
sudo fdisk -l 
means list all hardrives connected to the machine(dev)

so fdisk looks thought /dev/ (kinda)
and lists it out to you 

so if you boot a live cd then you are running from that not the usb or the harddrive so you can mount the right harddrive to /mnt/

---

### Post by illgetit on 2011-12-08
Just curious about the message indicating the filesystem is already mounted.
I'd be curious to see the output of the command 
```
mount
```
if Joseph's live cd plan falls thru

---

### Post by mastablasta on 2011-12-08
> **JustMyAlias said:**
> I could see my Windows drive previously, but have 'lost' it. I don't know how to find an 'Explorer' type equivalent, where I can see everthing (files, folders, etc) on my harddrive.

 
Explorer type equivalent is called Nautilus. i don't know where it is in new ubuntu but you can always launch it form terminal by typing nautilus in it.
 
 
windows drive is shown as "file system" often only with size or sometimes with it's volume label. if disk is corrupted or partition table is corrupted you mightnot see it propperly

---

### Post by JustMyAlias on 2011-12-08
this is what I got when I used a live cd: (I believe it is identical to the error when I was using the flashdrive...)
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       80325   976771119   488345397+   7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo mount/dev/sda2 /mnt/
sudo: mount/dev/sda2: command not found
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/
ntfs_mst_post_read_fixup: magic: 0x0008f000  size: 4096  usa_ofs: 0  usa_count: 65535: Invalid argument
Actual VCN (0x20) of index buffer is different from expected VCN (0x0).
ntfs_mst_post_read_fixup: magic: 0x0008f000  size: 4096  usa_ofs: 0  usa_count: 65535: Invalid argument
Actual VCN (0x20) of index buffer is different from expected VCN (0x0).
ntfs_mst_post_read_fixup: magic: 0x0008f000  size: 4096  usa_ofs: 0  usa_count: 65535: Invalid argument
Actual VCN (0x20) of index buffer is different from expected VCN (0x0).
ubuntu@ubuntu:~$

---

### Post by JustMyAlias on 2011-12-08
also (dumb) question...
if my hard drive were truly bad (and yes, there is obviously an issue - this is why I am in Ubuntu again trying to get to my files...)
but if the hard drive were bad
how can a different os still work???  it still needs to access the same drive, right?
too confused...

---

### Post by JustMyAlias on 2011-12-08
still not able to mount the drive - anyone have any ideas?

---

### Post by JustMyAlias on 2011-12-08
now it seems... if I double-click on the OS - the little triangle symbol comes up and show 'mounted', bu I don't see anything...
this is utter badness, isn't it??

---

### Post by oldos2er on 2011-12-08
If an NTFS partition is not shut down cleanly, Ubuntu will not mount it in an attempt to preserve data.

If you can boot Windows, run 'chkdsk' on it.

---

### Post by JustMyAlias on 2011-12-08
I cannot boot the PC - so no Windows...
I am getting a Disk Read Error
then "Press Ctrl+Alt+Del to reboot"
No luck.
This is why I am trying Ubuntu - I wanted to try to save the files if possible...

---

