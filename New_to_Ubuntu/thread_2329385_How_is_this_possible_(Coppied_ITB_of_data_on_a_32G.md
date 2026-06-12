---
title: "How is this possible? (Coppied ITB of data on a 32GB USB)"
date: 2016-07-01
forum: New to Ubuntu
---

### Post by sim085 on 2016-07-01
Hello, I have a 1TB hard disk which I wanted to clone. This only had around 20GB of data used. So I did the following;

Connected a USB stick
Mounted this to /mnt/usb
Use dd command to copy /dev/sdb to /mnt/usb/sdb.img
Left it running over night

In the morning when I did ls -ah I see that in /mnt/usb, sdb.img is 1TB! 

How is that possible!??

dd command I used is as follows:

```

root@data:/mnt/usb# dd conv=sparse if=/dev/sdb of=/mnt/usb/sdb.img bs=1024
976762584+0 records in
976762584+0 records out
1000204886016 bytes (1.0 TB) copied, 7449.56 s, 134 MB/s
root@data:/mnt/usb# ls -lh
total 16G
drwx------ 2 root root  16K Jun 30 19:50 lost+found
-rw-r--r-- 1 root root 932G Jul  1 04:16 sdb.img

```

---

### Post by sudodus on 2016-07-01
I have not used ***dd*** with the conv=sparse token to image a huge drive like you did.

My first impulse, when I read your post was: 'It does not work, you will never be able to restore a working drive from that image.' But after a second or two, I thought, that maybe it works. So I would be very interested in your result, if you try with a target 'third drive', a drive of at least the same size as the orginal one, 1TB, and expand from the image file.

-o-

When I make a corresponding image, I do not use the conv=sparse token. Instead I

- overwrite the unused space with zeroes (to make it compress better)
- pipe the output from dd through a file compression program, gzip (fast) or xz (slow but better compression).

Then I can restore by reversing the process. This is how I create the compressed image files described at the following link:

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

-o-

But particularly with huge amounts of data, you have 20 GB, it is much more efficient to use ***Clonezilla*** to create an image. Clonezilla is also much safer compared to dd, which is nick-named 'disk destroyer' because it does what you tell it to do without questions, even if you tell it to wipe your family pictures. 

A Clonezilla image is a directory with a number of files, the big ones are compressed, and you can expect that the image is smaller than the original amount of data, in your case probably between 10 and 15 GB (depending on what files you have).

A big advantage with Clonezilla is that it processes only the used data blocks (and skips unused blocks), and keeps track of it, so that it can restore a working copy of the original system. Clonezilla needs a target 'third drive' of at least the same size as the original drive. See the following link:

[clonezilla.org/](clonezilla.org/)

***Edit:*** Back to the question about seeing a 1TB file in a 32 GB pendrive (and a 16 GB directory).

The system might be confused, and after unmounting, unplugging and replugging the pendrive, you might see something else with ***ls -lh***

---

### Post by fdrake on 2016-07-01
could you provide output for :
```

du --apparent-size -h * && du -h *

```

---

### Post by mikodo on 2016-07-01
How?

Sparce files are only a* representative *of what is read on disk using metadata. There are no bits written to that area.

So, in your case the empty space was converted to sparce metadata that reads as real data.

An example of sparce file usage is  space to be read as used so the file system didn't write to it to, save the space for a vm to use if/when needed. A process that saves actual disk space usage.

Probably how a container like lxc will use only the disc space it needs but, can grow as needed.

[https://en.wikipedia.org/wiki/Sparse_file](https://en.wikipedia.org/wiki/Sparse_file)

---

### Post by fdrake on 2016-07-01
i am still curious to know what is the exact size of the image since he said there were about 20gb of used storage and he was able to create an image on a 16gb usb drive

---

### Post by sudodus on 2016-07-01
Trying to address the question about seeing a 1TB file in a 32 GB pendrive (and a 16 GB directory) ...

The system might be confused, and after unmounting, unplugging and replugging the pendrive, you might see something else with

```
ls -lh
```

You might even need a reboot for the kernel to see the real thing.

-o-

But the main question for me is if the data in that image file is useful.

---

### Post by sim085 on 2016-07-01
I must have deleted the file :(
I switched pc again and the file is not on UBS after mounting. 

I will try that again...

How would I know if data in image file is usefull. I tried to load it in Virtual Box but seems not to be supported.

---

### Post by sudodus on 2016-07-01
The hard way via trial and error: The data in the image is useful if you can restore it to a partition which becomes a clone of the original one, nor if you can loop-mount the file and access the files in the directory (should be possible with kpartx, if the image is good).

-o-

But if you are primarily interested in backing up your data or cloning/porting your drive to another computer, we can discuss how to do that. In that case I would recommend ***Clonezilla***, as described in my first post (post #2).

-o-

```
http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux


Mounting a hard disk image including partitions using Linux
	

A while ago I thought it would be a good idea to make a backup of my Linux server by just dumping the complete disk to a file. In retrospect,
it would have been much easier had I just dumped the individual filesystems.

When I finally got around to using this backup, long after the 10GB disk had perished I realized that to use the loopback device to mount a
filesystem it actually needs a filesystem to mount. What I had was a disk image, including partition table and individual partitions.
To further complicate matters the data partition was also not the first partition inside this image.

For reference, I created this image using the Unix ‘dd’ tool:

# dd if=/dev/hda of=hda.img
30544113+0 records in
30544113+0 records out
# ls -lh
-rw-r--r-- 1 root    root  9.6G 2008-01-22 14:12 hda.img

I followed the instructions on http://www.trekweb.com/~jasonb/articles/linux_loopback.html to try and mount the partitions inside the disk
image, but ran into two problems.

To mount a partition inside the disk image you need to calculate the offset of where the partition starts. You can use fdisk to show this
information to you, but you need to specify the number of cylinders if you are using a disk image.

You then also need to multiply the start and end numbers with the calculated sectors to get a byte offset.

I found another tool more useful for this task, called parted. If you are using Ubuntu, you can install it with ‘apt-get install parted’

# parted hda.img
GNU Parted 1.7.1
Using /data/rabbit/disk_image/test2
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit
Unit?  [compact]? B
(parted) print
Disk /data/rabbit/disk_image/test2: 10262568959B
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start        End           Size         Type     File system  Flags
1      32256B       106928639B    106896384B   primary  ext3         boot
2      106928640B   1184440319B   1077511680B  primary  linux-swap
3      1184440320B  10256924159B  9072483840B  primary  ext3
(parted) quit

Now we have the offsets and we can use those to mount the filesystems using the loopback device:

#mount -o loop,ro,offset=32256 hda.img /mnt/rabbit

That mounted the first partition, the ‘boot’ partition, but this didn’t have the data on it that I was looking for. Lets try to mount partition number 3.

#umount /mnt/rabbit
#mount -o loop,ro,offset=1184440320 test2 /mnt/rabbit
#mount: wrong fs type, bad option, bad superblock on /dev/loop0,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

Oops, that doesn’t look right. According the article referred to above if you are using a util-linux below v2.12b then you cannot specify an offset
higher than 32bits. I’m using util-inux 2.13 which shouldn’t have that problem, and besides, my offset is well below the 32bit limit.

The article also offers an alternative loopback implementation that supports mounting partitions within an image, but that requires patching and
recompiling your kernel which I would rather not do.

Instead I decided to extra ct the filesystem from the image which would then allow me to mount it without specifying an offset.
Doing this is quite straightforward with ‘dd’. You need to give ‘dd’ a skip count, or, how far into the source to start copying, and a count, how
much to copy.

Here you can either use the single byte offsets retrieved with parted or divide them by 512 and let ‘dd’ use 512 byte blocks. Copying just one
byte at a time takes a very long time, so I suggest using a larger block size.

Here is the command I used to extract my filesystem. Skip is 2313360 (1184440320/512) and Count is 17719695 (9072483840/4)

#dd if=hda.img of=hda3.img bs=512 skip=2313360 count=17719695
17719695+0 records in
17719695+0 records out
9072483840 bytes (9.1 GB) copied, 485.679 seconds, 18.7 MB/s

After extracting the filesystem I was able to mount it without any problems.

# mount -o loop hda3.img /mnt/rabbit/
# df -h /mnt/rabbit
Filesystem            Size  Used Avail Use% Mounted on
/data/rabbit/image/hda3.img
8.4G  6.3G  1.7G  80% /mnt/rabbit

--------------
unclean system
--------------
Anonymous January 28, 2009 at 6:10 am	

All useful information – just a followup. If your ext3 partition has been uncleanly unmounted (or you took a dump from a live system, say
running as a VM) then you won’t be able to mount it directly as the journal is unclean. Follow the “dd” instructions above to extract just the
partition, then run

“fsck.ext3 hda3.img”

to repair the filesystem before mounting.

------
kpartx
------
Mikko Rantalainen October 1, 2011 at 11:16 am	

One word: kpartx

For example: http://perbu.livejournal.com/1157.html

fess January 26, 2012 at 8:10 am	

    Do not miss @mikko’s answer! kpartx creates the device files for your image file so you can use the partitions just like a real disk.

    kpartx -a hda.img
    mount /dev/mapper/hda.img3

    Thanks mikko.

```

---

