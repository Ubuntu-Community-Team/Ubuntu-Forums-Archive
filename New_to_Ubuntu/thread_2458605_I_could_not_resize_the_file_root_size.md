---
title: "I could not resize the file root size"
date: 2021-02-28
forum: New to Ubuntu
---

### Post by mmursithakram on 2021-02-28
I have tried to increase my fileroot size with gparted but could not resize at it's not allowing me to adjust the size
Plz help me to sort out this issue

Note:
/dev/sda9   - Fileroot
/dev/sda14 - Newly created partition

---

### Post by Impavidus on 2021-02-28
The screenshot doesn't really look like gparted. Anyway, what may be the problem is that you cannot change a partition when it's mounted. So you have to boot a live disk and do your changes from there.

---

### Post by CelticWarrior on 2021-02-28
> [COLOR=#000000]The screenshot doesn't really look like gparted.[/COLOR]
It isn't. It's (Gnome) Disks.

---

### Post by grahammechanical on 2021-02-28
Keep in mind also that to make one partition bigger you need to make another partition smaller. There has to be unallocated (free) space before or after the partition to be resized. From the dialog of the Disks utility there is not any free space. When the disks utility firsts opens we get a layout of the disk showing all the partitions and their sizes and some information about what the partition is used for. Please take a screen shot of the layout and post it in this thread. If we do not have full and correct information about the drive and its partitions any advice we give might be inaccurate and damaging.

Regards

---

### Post by mmursithakram on 2021-03-01
This is actually taken from my Ubuntu and even when I tried with a live disk I could not resize it . Let me share those screenshots too

Yeah with the live boot disk I tried to resize the fileroot size but I could not adjust the size so I created a new partition called "New" (ex4) that you can see in the screen the shots. Afterwards I'm really stuck what to do next

Yeah I have shared the gparted screenshots ... Plz have a look at those

---

### Post by CelticWarrior on 2021-03-01
Again, you need unallocated space right after the partition you want to expand and right next to the partition you apparently want to expand there's a swap partition.

---

### Post by Impavidus on 2021-03-01
14 partitions? No wonder you've some difficulty managing that. But the important bits have been said: partition must be unmounted and unallocated space must be adjacent.

---

### Post by mmursithakram on 2021-03-01
Thank you so much , I got the point but if you could tell me how can I achieve in my case?

Yeah I have dual boot so that's why many partitions

Yeah I have dual boot that's why many partitions

I have 8 GB ram and Is it okay to swap off and use that partition to increase the fileroot size ? Is it a safe way to achieve this ?  in case if I used swap partition , can I re-create the swap memory when my physical runs of ram?

---

### Post by yancek on 2021-03-01
You can turn swap off then delete the swap partition.  That will give you less than 2GB of additional space.  You can't use the unallocated space or the New partition (sda14) because you have a 100+GB partition between the them.  You have a data partition, not sure what that is for but you could copy personal data there which would reduce the amount of space used on the / filesystem partition.

---

### Post by mmursithakram on 2021-03-01
Thank you so much , So can I use my sda12 (which is home directory of my Ubuntu partition - You can see in the screen shot which is next to swap space) to increase the fileroot if I delete my swap space? Is it possible to increase my sda12 when I delete the swap size (sda12 size + swap size becoming newly extended sda12) and then use the newly extended sda12  ( Which will be next to the fileroot )to get my fileroot size increased ? moreover if I need swap size , would I be able to create in case I delete it ?

---

### Post by Impavidus on 2021-03-01
> **mmursithakram said:**
>  Is it possible to increase my sda12 when I delete the swap size (sda12 size + swap size becoming newly extended sda12) and then use the newly extended sda12  ( Which will be next to the fileroot )to get my fileroot size increased ? 
No, to make your root partition larger you need unallocated space next to it. Partitions can only be extended into unallocated space. So you can extend sda12 that way, but that isn't useful.

35GB, the current size of sda9 (your root partition, if I get this right), should be enough for a root partition. You've got a separate /home partition, so you don't need that root partition for your documents. It may be a better idea to see if you can clean some things up in the root partition. I don't know what's in your sda10 and sda13. sda14 is new and appears quite useless. Maybe you can move files to those partitions or sda12 to get more room in sda9. Removing old logs, archives and snaps may help too. It should work automatically, but maybe something's wrong there.
```
sudo apt clean
journalctl --disk-usage
```

You don't really need swap, but it may be best to have some anyway. When you run out of ram (which will happen one day), it's better if things slow down than if random applications crash.

---

### Post by grahammechanical on 2021-03-01
My suggestion would be to first delete that partition that you call New. What do you need it for? Will deleting that New partition increase the size of the unallocated space?

Where is the Ubuntu root partition that you want to expand? Is it the partition after sda6 (119GB)? If it is then as sda6 is a NTFS partition use Windows tools to move sda6 to the left to take up the unallocated space. Then you can use GParted to expand the Ubuntu root partition into the unallocated space that is now to the left of the Ubuntu root partition.

If the Ubuntu root partition is after sda5 (81GB NTFS entertainment) then which one of the two ext4 partitions is the Ubuntu root partition?

If the first ext4 partition after sda5 is the Ubuntu root partition and the second ext4 partition after sda5 is the NEW partition. Then deleting the NEW partition will bring the Ubuntu root partition right up against the unallocated space. Now you should be able to expand the Ubuntu root partition to the right using up unallocated space. Do this with GParted from a Ubuntu live session.

I am having to guess which partition is which as the screen shot does not label all the partitions and you do not help us by telling us which partition is the Ubuntu root partition and where it is in that GParted display.

The swap partition is very small. Deleting it will not do much to solve your problem. Besides, sda12 is between that small swap partition and which ever partition is your Ubuntu root partition. 

Introducing additional questions into a thread is not only a distraction but it can cause confusion as to what you really want help for. Each additional question should be put into its own post.

Ubuntu 20.04 uses a swap file if my memory is correct. You can turn swap off but deleting a swap partition will slow down the Ubuntu boot process as the OS looks for a swap partition that is not there. Expect an increase of time by almost 2 minutes. Please do not ask me how I know.

Creating a new partition and calling it swap will not make it a swap partition as detected by the OS. More work would need to be done to get Ubuntu recognising a new partition as swap.

Do you remember your original question? That was solved by the information that we cannot resize ext4 partitions if the are mounted (in use) as the Ubuntu root partition was at the time. 

regards

---

### Post by mmursithakram on 2021-03-02
Yeah it's very clear and I really got it .... Thank so much

---

### Post by TheFu on 2021-03-02
If you were using LVM, increasing the size of an LV from other places on the disk would be easy, assuming they were all in the same VG. Alas, LVM use needs to be selected at install-time for OS increases.

OTOH, with all the partitions you seem to be using, learning LVM really would make your storage management life easier.  LVM can be added to any empty data partition. Generally, you'd have maybe 3 partitions on a system (/boot/, /boot/EFI/, everything else for LVM), then break up the everything else as a single PV and single VG, with as many LVs as you like, sized however you need.  When expanding any LV, the space doesn't need to be adjacent, just within the same VG.  The real power with LVM is to only allocate storage to LVs when it is needed.  Some of my LVM setups use less than 50% of the total storage in the system.

Sorry, the fonts aren't readable to my eyes in the images.  
**parted -l** and **lsblk -e 7 -o name,size,type,fstype,mountpoint** would be useful AS TEXT.
Here's an example of some LVM coolness:
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
sr0                       1024M rom              
vda                         30G disk             
&#9500;&#9472;vda1                     512M part vfat        /boot/efi
&#9500;&#9472;vda2                       1K part             
&#9492;&#9472;vda5                    29.5G part LVM2_member 
  &#9500;&#9472;vgubuntu--mate-root     17G lvm  ext4        /
  &#9500;&#9472;vgubuntu--mate-swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu--mate-home     12G lvm  ext4        /home
vdb                         10G disk             
&#9492;&#9472;vdb1                      10G part LVM2_member 
  &#9492;&#9472;vgubuntu--mate-root     17G lvm  ext4        /

$ sudo parted -l

Model: Virtio Block Device (virtblk)
Disk /dev/vdb: 10.7GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  10.7GB  10.7GB                     lvm


Model: Virtio Block Device (virtblk)
Disk /dev/vda: 32.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  538MB   537MB   primary   fat32        boot
 2      539MB   32.2GB  31.7GB  extended
 5      539MB   32.2GB  31.7GB  logical                lvm


```
See how the "root" LV is made up of storage from two different disks (vda and vdb)?  Those are actually virtual disks. The storage is really on the same SSD.

LVM is very powerful.  It is helpful in creating clean backups too.

---

