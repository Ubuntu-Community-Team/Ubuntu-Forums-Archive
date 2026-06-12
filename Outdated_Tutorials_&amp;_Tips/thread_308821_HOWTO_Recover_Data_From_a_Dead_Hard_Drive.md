---
title: "HOWTO: Recover Data From a Dead Hard Drive"
date: 2006-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by kenweill on 2006-11-28
> 
Recover Data From a dead hard drive using ddrescue
by Admin @ 9:07 am.

Like dd, dd_rescue does copy data from one file or block device to another.dd_rescue is a tool to help you to save data from crashed partition. It tries to read and if it fails, it will go on with the next sectors where tools like dd will fail. If the copying process is interrupted by the user it is possible to continue at any position later. It can copy backwards.


dd_rescue Advantages

Imagine, one of your partitions is crashed, and as there are some hard errors, you don’t want to write to this hard disk any more. Just getting all the data off it and retiring it seems to be suitable. However, you can’t access the files, as the file system is damaged.

Now, you want to copy the whole partition into a file. You burn it on CD-Rom, just to never lose it again. You can setup a loop device, and repair (fsck) it and hopefully are able to mount it.

Copying this partition with normal Un*x tools like cat or dd will fail, as those tools abort on error. dd_rescue instead will try to read and if it fails, it will go on with the next sectors. The output file naturally will have holes in it, of course. You can write a log file, to see, where all these errors are located.

The data rate drops very low, when errors are encountered. If you interrupt the process of copying, you don’t lose anything. You can just continue at any position later. The output file will just be filled in further and not truncated as with other Un*x tools.

If you have one spot of bad sectors within the partition, it might be a good idea, to approach this spot from both sides. Reverse direction copy is your friend.

The two block sizes are a performance optimization. Large block sizes result in superior performance, but in case of errors, you want to try to salvage every single sector. So hardbs is best be set to the hardware sector size (most often 512 bytes) and softbs to a large value, such as the default 16k.

Install dd_rescue in Debian

Install ddrescue using the following command

#apt-get install ddrescue

Install ddrescue in Ubuntu

sudo apt-get install ddrescue

This will complete the installation

ddrescue Syntax

dd_rescue [options] infile outfile

Now we will see how to use ddrescue under damaged disk

If you have a damaged hard disk /dev/sda1 and you have an empty space hard disk /dev/sda2 Now if you want to copy data from /dev/sda1 to /dev/sda2 use the following commnd

# dd_rescue /dev/sda1 /dev/sda2/backup.img

If you are using ubuntu linux use the following command

sudo dd_rescue /dev/sda1 /dev/sda2/backup.img

This copies an image of /dev/sda1 to sda2

Now you need to check the backup image consistency this will check for is there any problems with this image.

#fsck -y /dev/sda2/backup.img

If you are using ubuntu linux use the following command

sudo fsck -y /dev/sda2/backup.img

After finishing this checking you need to mount your disk image in to your other hard disk

#mount /dev/sda2/backup.img /mnt/recoverydata

If you are using ubuntu linux use the following command

sudo mount /dev/sda2/backup.img /mnt/recoverydata

This will mount all the data from the backup.img under /mnt/recoverydata now you can try to access the data it should work without any problem.

Restore image

If you want to restore this image use the following command

#dd_rescue /dev/sda2/backup.img /dev/sda1

If you are using ubuntu linux use the following command

sudo dd_rescue /dev/sda2/backup.img /dev/sda1

Copy Disk Image to remote machine using SSH

If you want to copy your disk image to remote machine over ssh you need to use the following command

#dd_rescue /dev/sda1 - | ssh username@machineip ‘cat /datarecovery/backup.img’

If you are using ubuntu linux use the following command

sudo dd_rescue /dev/sda1 - | ssh username@machineip ‘cat /datarecovery/backup.img’

This will be prompetd for password of the username you have menctioned in the above command after entering the password dd_rescue strats copying obviously it will take some time to copy over the network.

Possible Error

If you see the following error at the time of copying you can ignore this error

dd_rescue: (warning): output file is not seekable!
dd_rescue: (warning): Illegal seek

If you want to take this image in compressed format you can use the following command format

#tar zcvf - /dev/sda1 | ssh username@machineip ‘cat@@>/tmp /datarecovery/backup.tar.gz’

If you are using ubuntu linux use the following command

sudo tar zcvf - /dev/sda1 | ssh username@machineip ‘cat@@>/tmp /datarecovery/backup.tar.gz’

If you want to know more available options check dd_rescue man page 


Original Copy From  [Here]("http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html")

---

### Post by JohnPhys on 2007-02-25
does this work with ntfs partitions?  Specifically, the fsck part?

---

