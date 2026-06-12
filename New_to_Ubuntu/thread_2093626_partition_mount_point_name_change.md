---
title: "partition mount point name change"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by unibroker on 2012-12-11
I got an error message when I tried to backup a file to an external hard drive.  I noticed that the mount point now has 2 identical names, with one having a trailing underscore.  When I looked at the properties of the original one (without the underscore)```
Contents: unreadable
```.  I can successfully backup to the one having an underscore.

Can I safely delete the original?  Is this the product of some kind of recovery?

---

### Post by redmk2 on 2012-12-11
> **unibroker said:**
> I got an error message when I tried to backup a file to an external hard drive.  I noticed that the mount point now has 2 identical names, with one having a trailing underscore.  When I looked at the properties of the original one (without the underscore)```
Contents: unreadable
```.  I can successfully backup to the one having an underscore.

Can I safely delete the original?  Is this the product of some kind of recovery?
These 2 mount points are not the same.  The underscore makes them different!  How did you mount the external drive?  If the mount point was created automatically, then I would just leave it for now.  The system should delete it.  I would be more interested in how it got created in the first place.  Do you have 2 drives that have the same label name?

---

### Post by unibroker on 2012-12-11
> **redmk2 said:**
> These 2 mount points are not the same.  The underscore makes them different!  How did you mount the external drive?  If the mount point was created automatically, then I would just leave it for now.  The system should delete it.  I would be more interested in how it got created in the first place.  Do you have 2 drives that have the same label name?

One ext. drive, two partitions (1 for WinXp, 1 for Ubuntu).  Each partition has the original name and the underscore as shown in nautilus.  Gparted only shows the underscore one which is the one mounted.  The drive is rarely disconnected from the system so I assume it is automatically mounted/unmounted on each daily startup/shutdown.

My research this morning points toward a bug as far back as the Hardy release.

---

### Post by oldfred on 2012-12-11
If it is a removeable drive it may be getting mounted twice, the second is the underscore.

Are you mounting with fstab?
Possible work around. But I think this was for permanent drives mounted to /home or /media.
       not sure if it's related to this or not, but the work around there was to replace UUID=xxxx with
/dev/disk/by-uuid/xxxx

    
But it may then just be better to use labels on partitions on your external drive and let the system auto mount via the labels? Only if you do not want default settings may it make sense to mount in fstab.

I also used to have two entries for some of my partitions, but changed to mount in /mnt so they do not show in Nautilus at all. I think link folders into /home so I have easy access.

---

### Post by unibroker on 2012-12-11
> **oldfred said:**
> If it is a removeable drive it may be getting mounted twice, the second is the underscore.

Are you mounting with fstab?
Possible work around. But I think this was for permanent drives mounted to /home or /media.
       not sure if it's related to this or not, but the work around there was to replace UUID=xxxx with
/dev/disk/by-uuid/xxxx

    
But it may then just be better to use labels on partitions on your external drive and let the system auto mount via the labels? Only if you do not want default settings may it make sense to mount in fstab.

I also used to have two entries for some of my partitions, but changed to mount in /mnt so they do not show in Nautilus at all. I think link folders into /home so I have easy access.
Attached are 2 gparted screenshots containing an information window for each subject underscored partition.  Maybe this will be useful instead of my feeble explanation.

---

### Post by oldfred on 2012-12-11
Do you have anything is fstab or is this just the standard mount. It seems to be just using the UUID. I much prefer to add labels to every partition. It is easier to type and understand. I usually try to remember to add labels with gparted when formatting a new partition, but often forget and then use Disk Utility as that works well for labels. You also can use command line.

       Set Labels for external devices gparted, Disk Utility or command line
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

    
       ls -l /dev/disk/by-label/
       sudo blkid -c /dev/null -o list
    
    
```
fred@fred-Precise:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    (not mounted)  04B05B70B05B6768
/dev/sda2  ext3    backup   (not mounted)  13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdc2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69
/dev/sdc3  swap             (not mounted)  00c4e383-cf30-4b54-9a9f-d46953e3966e
/dev/sdc4  ext4    MavData  (not mounted)  431ba9e5-c72c-41c2-ba82-d8ee052336ff
/dev/sdd1  ext3    grub     (not mounted)  9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f
/dev/sdd2  ntfs    Shared   /mnt/shared    44332FD360AA9657

```

---

### Post by unibroker on 2012-12-11
> **oldfred said:**
> Do you have anything is fstab or is this just the standard mount. It seems to be just using the UUID. I much prefer to add labels to every partition. It is easier to type and understand. I usually try to remember to add labels with gparted when formatting a new partition, but often forget and then use Disk Utility as that works well for labels. You also can use command line.

       Set Labels for external devices gparted, Disk Utility or command line
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

    
       ls -l /dev/disk/by-label/
       sudo blkid -c /dev/null -o list
    
    
```
fred@fred-Precise:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    (not mounted)  04B05B70B05B6768
/dev/sda2  ext3    backup   (not mounted)  13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdc2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69
/dev/sdc3  swap             (not mounted)  00c4e383-cf30-4b54-9a9f-d46953e3966e
/dev/sdc4  ext4    MavData  (not mounted)  431ba9e5-c72c-41c2-ba82-d8ee052336ff
/dev/sdd1  ext3    grub     (not mounted)  9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f
/dev/sdd2  ntfs    Shared   /mnt/shared    44332FD360AA9657

```

Terminal output had too much whitespace that I couldn't figure out how to get rid of so I've attached text file.

---

### Post by redmk2 on 2012-12-11
> **unibroker said:**
> Terminal output had too much whitespace that I couldn't figure out how to get rid of so I tried to upload as a text file but got an error.  Suggestions?What's the error?  How did you create the text file?

To create a file I would do this```
sudo blkid -c /dev/null -o list > blkid.txt
```

You then should be able to upload the file *blkid.txt* from you home directory.

---

### Post by dannyboy79 on 2012-12-11
i've had this happen to me with an external fat32 usb drive. not sure why it happens but when I notice it upon a computer restart, i'll unmount the one with the underscore and unplug it (usb plug or turn the power off), check the contents of the folder without the underscore, it's always empty, then i'll delete that folder, then i'll just either plug it back in or flip the power switch and it gets mounted to a automatically created folder without the underscore.

I dont know why it happens but it does randomly

---

### Post by unibroker on 2012-12-11
> **redmk2 said:**
> What's the error?  How did you create the text file?

To create a file I would do this```
sudo blkid -c /dev/null -o list > blkid.txt
```

You then should be able to upload the file *blkid.txt* from you home directory.

I'm actually not completely comfortable with my terminal skills so I mix resources.  I copy the terminal output, paste/save it in a text editor.  I get the error from this forum when I try to upload the attachment.  Maybe it's because I didn't append txt to the filename.

---

### Post by redmk2 on 2012-12-11
> **unibroker said:**
> I'm actually not completely comfortable with my terminal skills so I mix resources.  I copy the terminal output, paste/save it in a text editor.  I get the error from this forum when I try to upload the attachment.  Maybe it's because I didn't append txt to the filename.
Just cut command (right click>>copy) and paste in the open terminal at the prompt (Use *shift-insert* to past the command). Then hit *enter*. The file will be created in you home directory.  Try and upload that file.

---

### Post by redmk2 on 2012-12-11
> **dannyboy79 said:**
> i've had this happen to me with an external fat32 usb drive. not sure why it happens but when I notice it upon a computer restart, i'll unmount the one with the underscore and unplug it (usb plug or turn the power off), check the contents of the folder without the underscore, it's always empty, then i'll delete that folder, then i'll just either plug it back in or flip the power switch and it gets mounted to a automatically created folder without the underscore.

I dont know why it happens but it does randomly

Nautilus creates a mount point for all the USB connected drives that are not mounted via fstab.  If the drive is not cleanly unmounted (power cut, unplugged, etc.) it leaves the mount point.  If you label the partition then Nautilus uses that label as the name of the directory created and used as the mount point.  If not it should use the UUID.

---

### Post by unibroker on 2012-12-11
> **redmk2 said:**
> Just cut command (right click>>copy) and paste in the open terminal at the prompt (Use *shift-insert* to past the command). Then hit *enter*. The file will be created in you home directory.  Try and upload that file.

I appended ".txt" and it uploaded.  I edited that response.

---

### Post by redmk2 on 2012-12-11
> **unibroker said:**
> I appended ".txt" and it uploaded.  I edited that response.

Attached to ???  I don't see any attachment.  Possibly somewhere else?

Edit:  I see it now.

---

### Post by unibroker on 2012-12-11
> **redmk2 said:**
> Attached to ???  I don't see any attachment.  Possibly somewhere else?

The original post where I asked for suggestions.  The resulting text file still gives me headaches just looking at it.  Data isn't even showing up under the proper column heading.

---

### Post by oldfred on 2012-12-11
Someone else had the same issue with too much white space. I think he never really resolved it but later it worked. Must be some difference in versions?

just run this but it is harder to read. But if you have not labeled anything then it really does not matter. I was just trying to show labels.

sudo blkid

---

### Post by redmk2 on 2012-12-11
> **oldfred said:**
> Someone else had the same issue with too much white space. I think he never really resolved it but later it worked. Must be some difference in versions?

just run this but it is harder to read. But if you have not labeled anything then it really does not matter. I was just trying to show labels.

sudo blkid

I have reformatted the file myself.  Not so hard to do.

The 2 partitions are on the device sdf.  There is also a swap partition on that device too.  The 2 partitions we are talking about are```
sdf2   ext4  [COLOR="Blue"]**/media/6e9ac323-45f6-4cb0-acca-8277530a3584_**[/COLOR]  **[COLOR="Red"]6e9ac323-45f6-4cb0-acca-8277530a3584[/COLOR]**

sdf5   ntfs   HP Pocket Media Drive  **[COLOR="Blue"]/media/HP Pocket Media Drive_ [/COLOR]** **[COLOR="Red"]08EC8654EC863BC6[/COLOR]**

```

The mount points are blue and the UUID is red.

If these are not mounted in fstab then you can unmount the devices and delete the mount points and new ones will be created.  I agree with *@ oldfred* that the label for the HP Pocket Media drive should be shorter and with no spaces.  Maybe: hp__usb_drive.

We should check first to make sure these are not mounted via the fstab file.  You can provide the output like this ```
cat /etc/fstab > fstab.txt
```
Past that output here.

---

### Post by unibroker on 2012-12-11
> **redmk2 said:**
> We should check first to make sure these are not mounted via the fstab file.  You can provide the output like this ```
cat /etc/fstab > fstab.txt
```
Past that output here.

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=a9320513-c32b-4ce2-b66f-f83f083cedd5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=d4ec1efb-06cd-4472-b540-e5d797f76846 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=d2acd6bd-8ba2-4f5b-bfa8-f268071a6b9a none            swap    sw              0       0
# swap was on /dev/sdf6 during installation
UUID=bdf866d0-4891-4bc7-9595-94069089e763 none            swap    sw              0       0

---

### Post by redmk2 on 2012-12-11
> **unibroker said:**
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=a9320513-c32b-4ce2-b66f-f83f083cedd5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=d4ec1efb-06cd-4472-b540-e5d797f76846 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=d2acd6bd-8ba2-4f5b-bfa8-f268071a6b9a none            swap    sw              0       0
[COLOR="Red"]# swap was on /dev/sdf6 during installation
UUID=bdf866d0-4891-4bc7-9595-94069089e763 none            swap    sw              0       0[/COLOR]

You are not mounting the 2 partitions with fstab.  This means you can **unmount the partition in question** and delete the mount point safely.  The mountpoint will be recreated when you either: enter this command ```
mount -a
```...or you reboot the OS.

I see there is a 2nd swap partition on this removable disk.  Did you do this on purpose?  I have highlighted it in red above.

---

### Post by unibroker on 2012-12-11
> **redmk2 said:**
> You are not mounting the 2 partitions with fstab.  This means you can **unmount the partition in question** and delete the mount point safely.  The mountpoint will be recreated when you either: enter this command ```
mount -a
```...or you reboot the OS.

I see there is a 2nd swap partition on this removable disk.  Did you do this on purpose?  I have highlighted it in red above.

I did not.  The only thing I've done purposely with the external drive is shrink the Windows partion to create the linux partition.  I've never used nor intended to use the external drive to boot from so I was surprised when a swap partition was present.  I'll recapture it when I need the space.

By the way, what does ```
errors=remount-ro 0 1
``` in reference to the root partition of the main hard drive mean?  Thanks for your input today.

---

### Post by redmk2 on 2012-12-11
> **unibroker said:**
> I did not.  The only thing I've done purposely with the external drive is shrink the Windows partion to create the linux partition.  I've never used nor intended to use the external drive to boot from so I was surprised when a swap partition was present.  I'll recapture it when I need the space.

By the way, what does ```
errors=remount-ro 0 1
``` in reference to the root partition of the main hard drive mean?  Thanks for your input today.
There are 3 parts to that.  The first part says "if the disk has errors mount it read only (ro).  The second part ( the 5 field in fstab) says ```
The fifth field, (fs_freq),  is  used  for  these  filesystems  by  the
       dump(8)  command  to determine which filesystems need to be dumped.  If
       the fifth field is not present, a value of zero is  returned  and  dump
       will assume that the filesystem does not need to be dumped.
```

The third part (the 6th field in fstab) says```
The  sixth field, (fs_passno), is used by the fsck(8) program to deter&#8208;
       mine the order in which filesystem checks are done at reboot time.  The
       *[COLOR="Red"]root  filesystem  should  be specified with a fs_passno of 1[/COLOR]*, and other
       filesystems should have a fs_passno of 2.
```

---

