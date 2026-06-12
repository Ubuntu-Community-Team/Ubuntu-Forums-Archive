---
title: "Set up dedicated &quot;Data&quot; partition to share data between multiple distros"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by lucasreece on 2011-09-27
Hi,

I've installed L(Ubuntu) with / (sda3), swap (sda2) and /home (sda11) partitions.

I'd now like to use sda10 as a dedicated "Data" partition to shared among other distros (common data) that everyone can access.

Can someone offer a solution how to do this please. Are there any good easy to follow guides out there on how to accomplish this.

I've googled but not found anything (not sure I'm searching the correct search terms).

Hope I've posted to the correct forum.

Many thanks.


PARTITION TABLE LAYOUT (using fdisk -l)...

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9aaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3917    31457280    7  HPFS/NTFS
/dev/sda2            3917        4178     2097152   82  Linux swap / Solaris
/dev/sda3            4178        5483    10485760   83  Linux
/dev/sda4            5484       14594    73178113    5  Extended
/dev/sda5            5484        6789    10485760   83  Linux
/dev/sda6            6789        8094    10485760   83  Linux
/dev/sda7            8095        9400    10485760   83  Linux
/dev/sda8            9400       10706    10485760   83  Linux
/dev/sda9           10706       12011    10485760   83  Linux
/dev/sda10          12011       13317    10485760   83  Linux
/dev/sda11          13317       14594    10257408   83  Linux

---

### Post by Lisiano on 2011-09-27
A easy way to make the partition available on boot, the easiest would be to add the partition to fstab.

---

### Post by ninjaaron on 2011-09-27
I do something similar.  You will have to repeat these steps for all distros that you want to use the partition.

1.  figure out where you want to mount your data partition and create the directory. I mount mine in '/data'. You could also mount it in your home folder, like '/home/USERNAME/data.'  I used to do this, but bad stuff happened, so I don't do that anymore.  I just have links to my home folder.

In a terminal type:
```
sudo mkdir /data
```

You can replace '/data' with whatever name you like, but I'm going to keep on referring to it as '/data'.

2. next command:
```
sudo blkid
```

This will give you a list of drives with information about there UUID and lables, as well as their formatting.  You need this information for the next step.

3. next command:
```
gksu gedit /etc/fstab
```
BE CAREFUL EDITING THIS FILE!  Don't change anything that is already there.

to the bottom of the list add a line like this 
```
/dev/sda10      /data      ext4    nodev,nosuid     0     2
```

Your line may be different:
a)  It will be better if, in place of /dev/sda10, you use the UUID that the "blkid" command gives you.  Partition devices can change, but the UUID will stay the same unless the partition is reformated.  If the partition has a label you can also use "LABEL=[your label]"
b) Where I have '/data' is the mount point.
c) 'ext4' is the filesystem type.  I use ext4, but you may have formatted it another way.  The blkid command tells you what the type is.  If you want to share the data with Windows, you should have formatted the partition to NTFS or FAT32, and you may have to reformat  the partition and start over if this is your goal (as I can see that you did not do this originally).
d) 'nodev,nosuid'  these are the normal options you want for a shared data partition.  Stick with that.
e)  the numbers have to do with dumps and disk checks.  What I have here will be fine.

4.  Save and quit.  Your data should be mounted in '/data' or wherever if you entered all of the correct information in /etc/fstab.

5.  Make links to the folder/s in your home folder wherever you want them, assuming you are not already mounting the partition inside of your home folder.

I don't use Windows at all, so I'm not sure how to mount partitions under that system.  Someone else here might know, or you could ask wherever people go to get support for Windows.  These steps will get the partition mounted in any Linux system, so that's at least half of your answer.

---

### Post by lucasreece on 2011-09-27
> **Lisiano said:**
> A easy way to make the partition available on boot, the easiest would be to add the partition to fstab.

Thanks for that but can you advise how to do this please?

Also, do I have to set file/folder permissions in order for everyone to have access to read/write?

Many thanks.

---

### Post by Morbius1 on 2011-09-27
This can get complicated depending on what your definition of "shared" is and the other distro's involved. 

If you create an fstab entry for /dev/sda10 in all your distros and then chmod to 777 then the user on any distro will be able to add to and remove from that partition. But the user on DistoB may not be able to edit a file added by the user on DistoA even though you are using the same user name because your uid's are different.

For example suppose you have 2 distros: Fedora and Ubuntu and you have the same user name: bob.

When bob on Ubuntu adds a file to "Data" it will save as owner = bob but bob will have a user id number (uid) of 1000. User bob on Fedora has a uid of 500. The 2 are not the same to the system. It's my understanding that Fedora will be moving to the Debian way of numbering uid's starting in Fedora 16 so this may not be an issue. It's also not an issue if all your distros are Debian based.

There are ways around this that can become very complicated to pull off. One easy way is to use something called bindfs. An example of bindfs:

Mount the partition as normal in fstab:
```
UUID=f7927995-b098-42be-ada0-987857f5177a /mnt/Data ext4 defaults,noatime 0 2
```Then "remount" the partition using bindfs - first temporarily from the terminal so you can see what it does:
```
sudo bindfs -o perms=0666:+X /mnt/Data /mnt/Data
```[COLOR=Blue]*Note: to unmount:*[/COLOR]
```
sudo umount /mnt/Data
```All of the folders/files will change from permissions of 755/644 to 777/666. Any new files or folders added by any user on any distro will also save to the new permissions. It essentially makes your common Linux partition look like a common NTFS partition - sort of ;)

Then you can either add that same bindfs command  ( without the sudo ) to rc.local, if your system uses upstart you can create an upstart job ( my favorite ), or you can add it ( modified a bit ) to fstab itself. This will make it so it does it at every boot.

---

### Post by Morbius1 on 2011-09-27
You can start off just mounting the partition the standard way and use the fstab entry I posted above as a template:

[1] If you have the sda10 partition mounted manually unmount it.

[2] Run the following command to get the right UUID number and filesystem:
```
sudo blkid -c /dev/null
```[3] Create the mount point:
```
sudo mkdir /mnt/Data
```[4] Add the following line with the corrected UUID number and filesystem to the end of /etc/fstab:
```
UUID=f7927995-b098-42be-ada0-987857f5177a /mnt/Data ext4 defaults,noatime 0 2
```[5] Run the following command which will test for errors and mount the partition without a reboot:
```
sudo mount -a
```[6] Change permissions on the mounted partition to allow access:
```
sudo chmod 0777 /mnt/Data
```You will have repeat steps [3], [4], and [5] on all your other distros. 

Try that first and if there's a problem with access we can explore bindfs or if anyone has another method.

---

### Post by lucasreece on 2011-09-28
> **Morbius1 said:**
> You can start off just mounting the partition the standard way and use the fstab entry I posted above as a template:

[1] If you have the sda10 partition mounted manually unmount it.

[2] Run the following command to get the right UUID number and filesystem:
```
sudo blkid -c /dev/null
```[3] Create the mount point:
```
sudo mkdir /mnt/Data
```[4] Add the following line with the corrected UUID number and filesystem to the end of /etc/fstab:
```
UUID=f7927995-b098-42be-ada0-987857f5177a /mnt/Data ext4 defaults,noatime 0 2
```[5] Run the following command which will test for errors and mount the partition without a reboot:
```
sudo mount -a
```[6] Change permissions on the mounted partition to allow access:
```
sudo chmod 0777 /mnt/Data
```You will have repeat steps [3], [4], and [5] on all your other distros. 

Try that first and if there's a problem with access we can explore bindfs or if anyone has another method.

Superb. Thanks very much for your help on this. Marked as solved.

---

