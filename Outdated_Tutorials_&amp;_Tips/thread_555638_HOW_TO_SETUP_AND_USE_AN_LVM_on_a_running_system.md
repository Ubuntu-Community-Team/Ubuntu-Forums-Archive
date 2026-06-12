---
title: "HOW TO SETUP AND USE AN LVM on a running system"
date: 2007-09-20
forum: Outdated Tutorials &amp; Tips
---

### Post by tagra123 on 2007-09-20
This guide is based on using Feisty, but should work well with Edgy and Gutsy too. The guide originally showed how to use it with an XFS file system but the XFS files system has no tool to shrink it like reiser and ext3. The guide now shows how to use it with a reiser file system. Other file systems can be used.

This guide describes how to set up a LVM  drive  for data on a working system. This can be used, in my case for MythTv to have an expandable volume for recordings.

Parts of this guide were adapted for ubuntu from the following sources.

[http://www.builderau.com.au/program/linux/soa/Set-up-Logical-Volume-Manager-in-Linux/0,339028299,339274722,00.htm](http://www.builderau.com.au/program/linux/soa/Set-up-Logical-Volume-Manager-in-Linux/0,339028299,339274722,00.htm)
[http://www.gentoo.org/doc/en/lvm2.xml](http://www.gentoo.org/doc/en/lvm2.xml)
[http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html)
[http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html)


[B][COLOR="Red"][SIZE="5"]WARNING ---  BEFORE STARTING

First
MAKE A BACKUP OF ANYTHING YOU DO NOT WANT TO LOSE OR CANNOT REPLACE. There are plenty of guides to backing up data here on the forums. If you follow the steps below you should not lose data. It is always a good idea to have backed up your important data before using a tool like parted or gparted which has the ability to wipe out your data in seconds if the wrong partition or drive is deleted or formatted. 

Second 
If you do not understand what parted or gparted does or the difference between hda, hdb, hdc, and hdd STOP NOW and search the forums or google.

Third
This is just a guide. Do not copy the commands without knowing what they are going to do. The commands for your machine will be similar but not exactly the same --- See Second Warning.

Fourth
If you want to be able to easily reduce the size of a file system DO NOT choose XFS.  I originally chose XFS but changed the guide to reiser because it can be easily shrunk or expanded. I would choose ext3 or reiser if you want to shrink the partition.  Reiser may still have some issues with NFS shares on some distributions*.  

 [/SIZE][/COLOR][/B]


NFS and reiser seemed to drop the connection frequently using Feisty.  The final setup of my MYTHTV box ended up being 140GB ext3  and a 120GB reiser.  The steps below explain how to set up either of these. You can divide your LVM into groups and its very similar to partitioning. The steps below should give you a good understanding of how to setup and configure an lvm.


**[SIZE="6"]HOW TO INSTALL AND SETUP THE LVM[/SIZE]**
**Step 1** - Install the necessary utilities.

```
sudo apt-get install lvm2 lvm-common
```



**Step 2** - Fix a bug in Feisty and Edgy

Read more: [https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/96802](https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/96802)

In Feisty and Edgy it is necessary to create a link to the correct library in order for pvcreate to work correctly.

```
 sudo ln -s /lib/lvm-200 /lib/lvm-0
```

**Step 3** - Load the LVM MODULES

```
 sudo modprobe dm-mod
```

**Step 4** - Create or erase a partition for the LVM to use

The following example uses gparted to create a single partition on a Maxtor 40 GB HDD that was installed before booting the machine. The device of this drive is hdd and the partition I created is hdd1. (hdd is the slave on the 2nd ide)

```
 sudo gparted
```
Using gparted create an unformatted partition. (See gparted help or google for gparted)
You do not have to give the whole drive to the lvm. You can have 1 partition for the lvm and another a plain ole ext3.  In this example the entire drive was partioned as hdd1, unformatted, and the entire drive will be given to the lvm
Close gparted when finished.


**Step 5** - Make the partitions available to LVM for use
```
sudo pvcreate /dev/hdd1
```


**Step 6** - Create the volume group named "data"
```
 sudo vgcreate data /dev/hdd1
```

The command above will create a volume group called "data" and assign /dev/hdd1 to it. **_[COLOR="Green"]Another drive, drives, or partitions can be added to the group later. [/COLOR]_** (See ADDING PARTITIONS AND DRIVES)



**Step 7** - Make the new space available.

To obtain information on your volume group, use vgdisplay and the volume group name.

```
sudo vgdisplay data | grep "Total PE"
```

In my case it reported that 9540 extents were available. I want to give the entire space to a volume called mythtv

```
sudo lvcreate -l 9540 data -n mythtv
```


[B][COLOR="Red"]STOP 
At this point you can format the drive to use the file system of your choice. For MythTv I chose reiserfs[/COLOR][/B]



**[SIZE="6"]FORMATTING THE  LVM VOLUME[/SIZE]**

(See HOW TO INSTALL AND SETUP THE LVM Steps 1-7 )

**Step 1** - Format the  mythtv volume (You can think of this similar to a partition)

```
sudo mkfs.reiserfs /dev/data/mythtv
```


**Step 2** - Create a mount point and mount the the newly created volume.

For testing I gave the /mythtv directory full read/write/execute access 777. Adjust these as necessary to the permissions that you prefer.

```
sudo mkdir /mythtv
sudo chmod 777 /mythtv
sudo mount /dev/data/mythtv /mythtv
```

At this point you can use the new volume just like any other drive

**Step 3** - Mount the volume at boot
To do this fstab will need an entry.

```
sudo gedit /etc/fstab
```

Add a line similar to the line below. The line below is for the reiser file system. If you are using ext3, or another file system then adjust the line accordingly.

```
/dev/data/mythtv      /mythtv     reiser     defaults        0      0
```

Save the file and exit the text editor.

**[COLOR="Red"]STOP - At this point if you can start saving data to the file system or if you reboot your computer the file system should be ready to use when booted.[/COLOR]**


**[SIZE="6"]HOW TO ADD ANOTHER DRIVE OR PARTITION TO THE LVM[/SIZE]**
**Step 1** - Prepare a drive or partition as described in HOW TO INSTALL AND SETUP THE LVM - Step 4 (above).

Stop any processes currently using the LVM Volume you are working with and unmount the volume. 

In my case I didn't need mythtv recording any shows while I was working on this.

**[COLOR="Red"]Stop MythTV  ( You can skip this step if you do not have mythtv installed. If the volume is busy you will receive a message when unmounting.)[/COLOR]**
Other items that might be using the drive are samba and nfs. Shut them down too.
```
 
sudo /etc/init.d/mythtv-backend stop
sudo /etc/init.d/samba stop
sudo /etc/init.d/nfs-kernel-server stop

```

Unmount the volume 
 ```
sudo  umount /mythtv
```

**Step 2** - Make the partitions available to LVM for use
```
sudo pvcreate /dev/hdc1
```

**Step 3** Add the drive/partition to the group "data"
The drive I added was about 10 GB and was IDE2-Master (hdc) the partition was hdc1


```
sudo vgextend data /dev/hdc1
```


**Step 4** - Make the new space available.

To obtain information on your volume group, use vgdisplay and the volume group name.

```
sudo vgdisplay data | grep "Total PE"
```

If you want a more detailed report of information use the following. This will show MB per drive and a lot of other information.

```
sudo vgdisplay -v
```

In my case it now reported that 11924 extents were available. I could give the entire space to the volume called mythtv

I know that be looking at "sudo vgdisplay -v" I have 46 GB available.

 In my case I want to leave 2 GB for later use hdd is 36GB and the hdc1 is 10GB
So 36+10-2=44
 44GB is the total new size I want to use for the mythtv volume. (See NOTE for lvextend)

```
 sudo lvresize -L 44G /dev/data/mythtv
```

[I]I could have used  the output of _**sudo vgdisplay data | grep "Total PE"**_ and gave it all available space too by using the following command 
**sudo lvextend -l 11924 /dev/data/mythtv**[/I]


NOTE for man lvextend
 [I] -l, --extents [+]LogicalExtentsNumber
              Extend  or  set  the  logical  volume  size  in units of logical
              extents.  With the + sign the value is added to the actual  size
              of  the  logical volume and without it, the value is taken as an
              absolute one.

   -L, --size [+]LogicalVolumeSize[kKmMgGtT]
              Extend or set the logical volume  size  in  units  in  units  of
              megabytes.  A size suffix of M for megabytes, G for gigabytes or
              T for terabytes is optional.  With the + sign the value is added
              to  the  actual  size  of the logical volume and without it, the
              value is taken as an absolute one.[/I]

Using -L you can specify 10G for 10 gigabytes or 100G for 100 gigabytes. (Easier to work with GB than extents)





**Step 5** - Grow the file system and mount the volume.
NOTE: The method below is for using the reiser file system. If your are using ext3 or another file system the procedure will be similar. In my case I want to leave 2 GB for later use hdd is 36GB and the hdc1 is 10GB
So 36+10-2=44
 44GB is the total new size I want to use.

You can read more about resizing the reiserfs here:

[http://linux.die.net/man/8/resize_reiserfs](http://linux.die.net/man/8/resize_reiserfs)


```
sudo resize_reiserfs -s 44G /dev/data/mythtv
sudo mount /mythtv

```

**[COLOR="Red"]STOP - At this point the newly added space should be ready to use. Your existing files in the volume remain untouched. You can start saving data to the filesystem or if you reboot your computer the file system should be ready to use when booted.[/COLOR]**



**[SIZE="6"]HOW TO REMOVE A DISK FROM THE LVM[/SIZE]**
A follow up how-to will be written on how to remove a disk from the LVM soon.

The links below describes removal and replacement of an LVM drive. I will write up a ubuntu how-to once it has been tested.

[http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html](http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html)

[http://www.linuxjournal.com/article/8874](http://www.linuxjournal.com/article/8874)

---

### Post by be4truth on 2007-09-20
I like the introduction in **[COLOR="Red"]RED[/COLOR]**. How clearer can one be when playing around with partitions..

---

### Post by tagra123 on 2007-09-20
Thanks,

I just wanted to make people aware that they could end up being really mad if they didn't have a backup and made a bad mistake. There's no way to miss it written in giant red letters.:)

I've aleady found **XFS isnt the way to go if you want to be able to shrink a partition late**r. I'll update the howto with that too.

I hope this How to Helps. I coulnd really find any straightforward guide from start to finish and though it might help someone else too.

Reiserfs seems to have some problems with NFS sharing on Feisty.  Ended up splitting the LVM Reiserfor the actual recordings and the other half as ext3 for the samba/nfs server. The ext3 folder is where the processed "nuvexported" video ends up.

---

### Post by troutbum13 on 2008-02-23
just wanted to say thanks for a great write-up and to add that if you are using ext2 or ext3 instead of reiserfs you can use resize2fs to resize the file system...

---

### Post by tagra123 on 2008-03-07
Thanks,

Glad it was of use.

---

### Post by lrochon on 2008-08-25
_Hardy Update_

Works great on hardy with two exceptions:
    1. lvm-common package is not necessary
    2. Symbolic Link bug-fix is not necessary

_Tip for resizing EXT3 partitions_

Firstly, unmount your volume
    ```
sudo umount YOURMOUNTPOINT
```

Then, run a filesystem check:
    ```
sudo e2fsck -f /dev/YOURVGNAME/YOURVOLNAME 
```

Next run the resizing tool in one of 2 ways:

    To resize FileSystem to maximum size of partition:
    ```
sudo resize2fs /dev/YOURVGNAME/YOURVOLNAME
```

    To resize FileSystem to a specific size:
    ```
sudo resize2fs /dev/YOURVGNAME/YOURVOLNAME SIZE 
```
    Where SIZE is something like 40G for 40 Gigabyte. 
    For more info man resize2fs.

[COLOR="Red"]NOTE: In the precedeing examples 
        YOURVGNAME = the name you gave your volume group
        YOURVOLNAME = the name you gave your volume
        YOURMOUNTPOINT = where fstab says to mount your drive
DO NOT JUST COPY AND PASTE IT WON"T WORK.

Aswell ALWAYS remember if in doubt [_RTFM_]("http://en.wikipedia.org/wiki/RTFM").[/COLOR]

---

