---
title: "Messed up /home partition"
date: 2018-09-04
forum: New to Ubuntu
---

### Post by namialos on 2018-09-04
Hey,

yesterday I restored a backup from 2016, however, not to replace all new files but just restore it in a new folder. It failed saying there was not enough space left, so I put in a external HDD and put it on there. That finished and everything was fine.

Today anything I did it kept saying no space left on disk so I ran df -h to see what is going on:


```
Filesystem      Size  Used Avail Use% Mounted on
udev             16G   12K   16G   1% /dev
tmpfs           3.2G  1.8M  3.2G   1% /run
/dev/sdc6       199G  190G     0 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none             16G   84K   16G   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sdc2        96M   66M   31M  68% /boot/efi
overflow        1.0M  124K  900K  13% /tmp
/dev/sdb2       1.8T  1.5T  337G  82% /media/home

```
I saw sdc6 seems to be 100% full, but to be honest I had no idea why that parition was my "/" folder. I googled a few things and people told me to start deleting things and change the fstab file etc. I did a lot of things that seem to have messed up more than helped. 

Currently, what is supposed to be my $HOME folder is in /media/home. I noticed that it wasnt in the right place anymore when I tried to run a program and it couldnt find it anymore through the normal search console. When I change the fstab file nothing happens. This is my fstab file:


```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb6 during installation
UUID=0c98d9c3-7872-47a8-b2e7-56daaa9879cb       /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
UUID=5E6D-C4CA  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sdb7 during installation
UUID=50e61bea-a126-4c07-949e-a02dfd3469e0 none            swap    sw              0       0
UUID=2b466ca7-6b9a-4161-a791-371eac20813c   /home    ext4          nodev,nosuid       0       2

```

And these are all harddrives with UUIDs:

```
/dev/sda1: LABEL="SequencingBackUp1" UUID="E69A8EE59A8EB19B" TYPE="ntfs" 
/dev/sdb2: LABEL="NewHome" UUID="2b466ca7-6b9a-4161-a791-371eac20813c" TYPE="ext4" 
/dev/sdc1: LABEL="Windows RE Tools" UUID="D23C20DC3C20BD7B" TYPE="ntfs" 
/dev/sdc2: LABEL="SYSTEM" UUID="5E6D-C4CA" TYPE="vfat" 
/dev/sdc4: LABEL="Windows" UUID="3A9AC2D79AC28F37" TYPE="ntfs" 
/dev/sdc5: LABEL="HP_RECOVERY" UUID="DADEABFFDEABD255" TYPE="ntfs" 
/dev/sdc6: UUID="0c98d9c3-7872-47a8-b2e7-56daaa9879cb" TYPE="ext4" 
/dev/sdc7: UUID="50e61bea-a126-4c07-949e-a02dfd3469e0" TYPE="swap" 



```

As yo ucan see we also have a windows parition on the same computer. SequencingBackUp1 is the HDD that the backup was on. NewHome is the HDD that $HOME was/should be on. And I have no clue what sdc6 is, but currently it is set as "/". 

Could someone help me get it back on track?

---

### Post by TheFu on 2018-09-04
sudo mount -a

That will force the fstab to be looked at and if /dev/sdb2 isn't already mounted, then it will be to the place specified.
Or rebooting should do it.

If that doesn't. then the output from **lsblk**, **blkid** and **df -hT** would be helpful, along with the fstab, if you attempted more changes.

---

### Post by namialos on 2018-09-04
Thanks. sudo mount -a didnt work.

here are the outputs:

lsblk:

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   1.8T  0 disk 
&#9492;&#9472;sda1   8:1    0   1.8T  0 part /media/imm_admin/SequencingBackUp1
sdb      8:16   0   1.8T  0 disk 
&#9492;&#9472;sdb2   8:18   0   1.8T  0 part /home
sdc      8:32   0   477G  0 disk 
&#9500;&#9472;sdc1   8:33   0   1.3G  0 part 
&#9500;&#9472;sdc2   8:34   0   100M  0 part /boot/efi
&#9500;&#9472;sdc3   8:35   0   128M  0 part 
&#9500;&#9472;sdc4   8:36   0 229.2G  0 part 
&#9500;&#9472;sdc5   8:37   0    13G  0 part 
&#9500;&#9472;sdc6   8:38   0 201.4G  0 part /
&#9492;&#9472;sdc7   8:39   0  31.9G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom 
``` 

blkid:

```
/dev/sda1: LABEL="SequencingBackUp1" UUID="E69A8EE59A8EB19B" TYPE="ntfs" 
/dev/sdb2: LABEL="NewHome" UUID="2b466ca7-6b9a-4161-a791-371eac20813c" TYPE="ext4" 
/dev/sdc1: LABEL="Windows RE Tools" UUID="D23C20DC3C20BD7B" TYPE="ntfs" 
/dev/sdc2: LABEL="SYSTEM" UUID="5E6D-C4CA" TYPE="vfat" 
/dev/sdc4: LABEL="Windows" UUID="3A9AC2D79AC28F37" TYPE="ntfs" 
/dev/sdc5: LABEL="HP_RECOVERY" UUID="DADEABFFDEABD255" TYPE="ntfs" 
/dev/sdc6: UUID="0c98d9c3-7872-47a8-b2e7-56daaa9879cb" TYPE="ext4" 
/dev/sdc7: UUID="50e61bea-a126-4c07-949e-a02dfd3469e0" TYPE="swap" 

```

df -hT:

```
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs   16G   12K   16G   1% /dev
tmpfs          tmpfs     3.2G  1.8M  3.2G   1% /run
/dev/sdc6      ext4      199G  190G     0 100% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs      16G   84K   16G   1% /run/shm
none           tmpfs     100M   48K  100M   1% /run/user
/dev/sdc2      vfat       96M   66M   31M  68% /boot/efi
overflow       tmpfs     1.0M  172K  852K  17% /tmp
/dev/sdb2      ext4      1.8T  1.5T  337G  82% /home
/dev/sda1      fuseblk   1.9T  190G  1.7T  11% /media/imm_admin/SequencingBackUp1

```


So as you can see sdc6 is 100% full. Im not sure why and I also thought that "/" is supposed to be on the same drive as /home. 

Thank you so much for the quick response!

---

### Post by TheFu on 2018-09-04
```
/dev/sdb2      ext4      1.8T  1.5T  337G  82% /home
```
says home is mounted from the other disk, as I think you intended.

If you didn't clean up the /home BEFORE mounting sdb2, then all that data is still there, using space on sdc6.  Hidden.  this is actually a good way to hide things on a disk if you don't want use encryption.  Just use a small mount over the location.
 The easiest way to clean that up is to boot from a flash drive with ubuntu, mount sdc6 somewhere, /mnt/ is where I'd put it temporarily, and remove everything **UNDER** /mnt/home/.  Be certain to leave the /mnt/home directory.

This is just a guess, BTW.  I have a high belief it is what you need.

Really, / shouldn't be larger than 25G. That is large enough for all the programs and a few DEs to be loaded. Smaller is also easier for backups.

---

### Post by namialos on 2018-09-04
Okay, so I will boot from a usb, mount sdc6, remove the home directory from there. Do I have to unmount anything? Or will everything be sorted when I boot from the HDD without usb?

---

### Post by TheFu on 2018-09-04
> **namialos said:**
> Okay, so I will boot from a usb, mount sdc6, remove the home directory from there. Do I have to unmount anything? Or will everything be sorted when I boot from the HDD without usb?

I specifically said NOT to remove the old /home directory.  That would be bad.  You need to remove all the stuff inside it, but leave the directory. It is a "mount point".  

Be certain you don't touch the 2nd HDD - assuming you've already moved all the data over. If you haven't, get from the /mnt/home/.... storage first.

Yes, that should be it.

---

### Post by namialos on 2018-09-05
Thats right, you wrote "under". My bad. thank you. ill try that today and let you know how it went.

---

### Post by namialos on 2018-09-05
Thank you! That was it, there was a full home folder where there doesnt need to be one. Deleted it and its fine now.

Something else came up now however. Some apps dont run anymore, im guessing there are some permission problems. The main program problem I have is with "R". Usually I could run "R" with no problem, just start it in the terminal by typing "R". Now I get following error:

```
imm_admin@PC3272796:~$ R
Segmentation fault (core dumped)
```

The only way to get around it is by using sudo.

This is a problem because I use "R" with several bash scripts that run Rscript and open several R scripts. Now I get this Segmentation fault. What might be the issue?

---

