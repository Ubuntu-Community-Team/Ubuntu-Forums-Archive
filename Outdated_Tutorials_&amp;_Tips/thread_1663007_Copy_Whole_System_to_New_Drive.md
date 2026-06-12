---
title: "Copy Whole System to New Drive"
date: 2011-01-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Tybion on 2011-01-09
[COLOR="Blue"][Warning:  With any low level procedure like this, there is risk.  You are advised to backup any important data before you start and then keep the original disk aside for at least a week before re-using it, to ensure that the new system is working fine.  Then if there is a problem, the original disk can then be put back, and the system will be as it was.][/COLOR]

I have used this procedure on a couple of PCs, and it has worked very nicely.  If you buy a larger disk for your PC, you may want to replace the older disk completely - the older disk might be slower, less energy-efficient, or you might only have room or a cable for the new disk.

Download and burn a _[Gparted Live CD]("http://gparted.sourceforge.net/download.php")_.  This is a very nice CD and is better for this type of work than the Ubuntu Live CD.

Connect both the new and old hard disk to the PC, but also arrange to boot off the Gparted Live CD or Gparted Bootable USB Stick.  Sometimes this will involve unplugging the PC's CD-reader and using that cable for the disk. In that case you will need a portable USB CD-reader for the Live CD or a GParted 'Live USB' stick - see the _[GParted Live CD]("http://gparted.sourceforge.net/download.php")_ site for details on that.

Now that the hard part is done, boot the system off the Gparted Live CD.  You will be asked for your keyboard type, language and video type - I just accepted the defaults.  Gparted will start automatically, and using that you will be able to see how the 2 drives have been named (eg. /dev/sda, /dev/sdb) - these will be in the drop-down list at the right.  *Note that the disk names do not end with a digit - eg. /dev/sda - not /dev/sda1.*

Start a terminal, by double-clicking on the 'Terminal' icon.  Then enter the following.
sudo dd if=*olddiskname* of=*newdiskname* bs=100M
This copies **everything** from the old disk to the new disk - master boot record, partition table, all partitions and all data - so everything is set up on the new disk when this is finished.  The 'bs=100M' specifies that 100 megabytes of data should be read then written at a time.  If you do not type this, 512 bytes is used, and that would slow the process.

On my PC the terminal command was ..
```
sudo dd if=/dev/sda of=/dev/sdb bs=100M

```

The dd command only prints out errors, so it might appear that nothing is happening - but it is.  To find out how far the copy has proceeded, open up another Terminal.  First find out the PID of the dd process like so ..

```
ps aux | grep -i "dd"
root      3652 11.8 20.3 105748 102996 pts/0   D    15:02   0:11 dd if=/dev/sda of=/dev/sdb bs=100M
user      3914  1.6  0.1   3296   704 pts/0    D+   15:04   0:00 grep -i dd
```

In the above example the PID of the dd process is 3652.

Now, carefully enter a command like so (but use the PID that you have determined).  Note this does not kill the process - it just sends it a signal that prompts dd to print out the current status.

```
sudo kill -USR1 3652
```

*In the terminal where dd is running*, after a couple of seconds, you will see output like ..

```
77+0 records in
76+0 records out
7969177600 bytes (8.0 GB) copied, 169.075 s, 47.1 MB/s

```

Any time you want a progress update, re-enter the kill command.

When this process is finished, you can check the new disk using the GParted program that will still be running.  It should have identical partitions to the old disk.  Turn off the PC, remove the old disk, and insert the new disk in its place.  When you turn on the PC, it should behave exactly the same as with the old disk.  When you are happy that the new system is working fine, you can use the GParted program to create new partitions or grow existing partitions to utilize the extra space that is available on the new disk.

---

### Post by LiveWireBT on 2011-01-10
Attention, this method has some drawbacks that one should be aware of:

**UUID's of the filesystems**
Of course all the UUID's of the filesystems on both drives are identical too, which will cause trouble if you want to use both drives in one computer. To change the UUID of the filesystem containing the operating system, you will have to edit some files manually.

/boot/grub/grub.cfg
/etc/fstab
/etc/initramfs-tools/conf.d/resume

Then boot from that the drive and run [FONT="Lucida Console"]sudo update-grub[/FONT] and [FONT="Lucida Console"]sudo update-initramfs -k all -u[/FONT].

Please note that this is by no means complete, I'm just pointing out some things to take care of.


**Solid State Drives (SSD's)**
This method is really bad for migrating from HDD to SSD, especially for those that drives support TRIM. You are not only copying all your files from your old drive to the new drive, but copying files that have been marked as deleted, but are still on the drive. TRIM, if enabled, will do it's magic ;) (it will corrupt the filesystem after some time, because it can't determine which files can be discarded and which not). Creating a new filesystem on the SSD and using rsync instead is recommended.

Hint: The simplest way to defragment a drive/filesystem is to create a new filesystem and copy the data onto the new filesystem. ;)


@author this is not meant to be an insult or any such thing, please feel encouraged to write more tutorials.

---

