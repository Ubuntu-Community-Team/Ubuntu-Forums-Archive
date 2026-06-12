---
title: "Download onto /home partition not / root partition"
date: 2015-06-03
forum: New to Ubuntu
---

### Post by hwangjk012 on 2015-06-03
Hi everyone, I am new to Vivid Vervet Ubuntu. 
I have about 10 gb for a / partition and about 120 gb for /home partition.
I am trying to install Matlab but there isn't enough space on the / partition.
How do I change the download path, and direct all future downloads to the /home path where there is tons of space?
Thanks!
-JC

---

### Post by yancek on 2015-06-03
The /home partition is meant to store personal files/data and the / partition for system files and software.  If you read the official Ubuntu documentation for Matlab at the link below, you will see that there is a default location for the install "/usr/local/MATLAB/R2014a".  I expect there will be libraries and dependencies needed which expect it to be in this location.  It might be possible to install it elsewhere and perhaps someone more familiar with this particular software will have a suggestion or two.  10GB seems like a small system partition in this day and age with the size of operating systems getting larger all the time.  It may be possible to resize the / partition.

---

### Post by grahammechanical on 2015-06-03
Downloads usually go in the Downloads folder on /home. It is the installation of the application that puts libraries in different folders in /. It is the way Linux does things.

Regards.

---

### Post by buzzingrobot on 2015-06-03
When you download something with a browser, the file is deposited in the directory the browser is configured to use for downloads.  It usually defaults to the 'Downloads" directory in your home folder.   (Every user on a Linux system -- there can be more than one -- has a 'home' directory located in the /home directory.  I.e., user "John" would have /home/John" as his home directory, with Firefox defaulting to putting downloads into /home/John/Downloads.

On the other hand, when packages are installed, their components are installed throughout the system file hierarchy that begins at /. Altering the location of your Downloads directory will not affect that.

---

### Post by leunam12 on 2015-06-04
Please post the results of ```
lsblk
```and```
sudo fdisk -l
```

Now, based on the information that you have given so far I can tell you that the recommended thing to do here is to extend your system partition to 20 or more GB. 10 GB is too small in my opinion. Parted Magic is your friend. 

This is what I would do, it may not be the correct procedure but I have done it many times.

1- Backup the whole disk using clonezilla. You need a clonezilla bootable DVD or USB. (VERY IMPORTANT. DO NOT SKIP THIS STEP)
2- Boot Parted Magic and Backup the Home partition. (I use rsync for this).
3- Open the partition editor in Parted Magic and delete the home partition.
4- There is going to be a chunk of unallocated space now next to System on the right side
5- Extend the system partition to the desired size. 
6- Create a new Home partition on the remaining free space.
7- Restore your data to your Home partition.

Before you do anything let's see the results of those two commands and wait for further advice if needed.
8- Reboot.

If you feel uncomfortable doing all this or if you are not sure, ask all the questions that you need to ask before doing anything.

---

### Post by Bucky Ball on 2015-06-04
Presuming your / partition comes first and your /home partition is next to it. (For instance, sda1=/ and sda2=/home) ...

Boot from live media, disk or USB> 'Try Ubuntu'> when at the desktop launch Gparted> Unmount and shrink the /home partition from the beginning, leaving unallocated space to expand (from the end) your / partition into. 10Gb would be ok if you were using a minimal install with not much added, but a regular install these days I'd be imagining 15 or 20Gb, and I don't use Matlab. (I do use a minimal install with a few things added. :))

Unless your / and /home partitions aren't butted up next to each other it shouldn't be necessary to clone your entire disk, your /home partition, delete /home, then re-create things, although it is definitely a good idea to make a backup of important data before resizing partitions, as suggested.

Attach a snapshot of your Gparted as it now is if you need to.

PS: Shrinking /home from the beginning, or the end, will take a while, especially if you have a lot of data on there. Apply that shrink only first, make sure all went well and there are no exclamation marks or anything else worrying, then expand the / partition into the unallocated space created.

---

### Post by hwangjk012 on 2015-06-04
Hi everyone,
Thanks for all the great advice! I was able to manipulate the swap partition and move around some space next to ext4 and extend the root partition by another 10 gb while booting from a live usb. 
-JC

---

### Post by Bucky Ball on 2015-06-04
Great news. Thanks for marking as solved. Good luck and enjoy. ;)

---

