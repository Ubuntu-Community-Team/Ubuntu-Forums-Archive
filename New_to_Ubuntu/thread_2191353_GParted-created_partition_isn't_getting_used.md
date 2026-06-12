---
title: "GParted-created partition isn't getting used"
date: 2013-12-02
forum: New to Ubuntu
---

### Post by pdzwig on 2013-12-02
I had a dual boot system which I reconfigured as Ubuntu-only using gparted. That gave me an additional 70 GB of disk which I needed because the system insisted that I was running out of disk space (had less than 1.1 GB). I did this under 12.10. It appeared to run under 12.10 OK.

I upgraded recently to 13.04 and now it tells me that I am running out of disk space again. I have added hardly anything to my disk and have removed quite a few packages.

The original partition /dev/sda3 is almost full and mounted at "/" the new partition /dev/sda1 appears to be mounted at /media/peter/xxx-yyy-zzz. My swap is at /dev/sda4 at about 1.5 GB.

The mount point is odd and I can't see an externally attached 350MB drive at /media.

How can I use sda1 as additional storage automatically available to Ubuntu? Could this be linked to the inability to see the external drive?


I know that gparted is not really "absolute beginners" stuff, but I think that this is something really elementary.

Thanks

---

### Post by Bucky Ball on 2013-12-02
Welcome. Maybe you could start by opening Gparted and taking a screenshot of your disk then attaching it to a post here ('Go Advanced'>Paperclip icon>Attach file).

You could also supply the result of:

```
df -T
```

---

### Post by pdzwig on 2013-12-02
Filesystem     Type         1K-blocks     Used        Available  Use% Mounted on
/dev/sda3      ext3         66048764    61424608       1269084    98%    /
none             tmpfs                  4                0                4      0%    /sys/fs/cgroup
udev             devtmpfs   1003548               12       1003536     1%     /dev
tmpfs            tmpfs          204168             988        203180     1%     /run
none             tmpfs             5120                0            5120     0%     /run/lock
none             tmpfs        1020836             156       1020680     1%     /run/shm
none             tmpfs         102400               40         102360     1%     /run/user
/dev/sda1      ext3        51463780        184268      48665296     1%     /media/peter/50c01980-4d64-4f51-ad71-996da81c128b


OK I tried to pad it but of course copying from one application to another doesn't work ;)

---

### Post by pdzwig on 2013-12-02
.

---

### Post by oldfred on 2013-12-02
Deleted all you text.
You can save a screen shot to your system and then in advanced editor click on paperclip icon to attach that screenshot.

       Guide to Forum features - see #4:
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)
Forum do & don't
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

---

### Post by pdzwig on 2013-12-02
or....



[ATTACH=CONFIG]248284[/ATTACH]

---

### Post by gedakc on 2013-12-02
From the screen shot it appears that the partitions are mounted and in-use.  For GParted to resize partitions, these need to be unmounted.  An easy way to do this is by booting from media (USB flash drive or CD-ROM) containing [GParted Live]("http://gparted.org/livecd.php").

---

### Post by pdzwig on 2013-12-02
...that is what I did under 12.04 (resized the partitions). What I can't see is why the system isn't accessing /dev/sda1 which is free and formatted as ext3 and so accessible.

---

### Post by pdzwig on 2013-12-02
Perhaps I should be asking the question another way round: There is mounted free space and the system isn't using it when it finds itself running low on space. How can I make it use it automatically.

---

### Post by oldfred on 2013-12-02
If Linux formatted you have to specify ownership & permissions. It is not automatic.
Best to set up in fstab so everytime you reboot it is auto mounted.

Unmount from current mount first.
 sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

           
 For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Impavidus on 2013-12-03
When you (or the system) store(s) files, you do so at a specific location in the directory tree. The extra partition is at a specific place in the directory tree too and files will only be stored there if you specifically ask for them to be stored there. There's no way that the system may say: `Hey, that partition if full, let's put that file in a directory over there.'

Your / partition is about 60GB. This is much larger than an Ubuntu system, even if you added a lot of packages. Most files must me user files, which – provided you have a neatly organised system – are in your home directory. Best way to solve this depends a bit on what kind of data you store on your disk. For example, if you have a large music collection (most people do), you may want to move that to the new partition. In any case, use /etc/fstab to mount it automatically. Oldfred has given you some links.

---

### Post by pdzwig on 2013-12-03
I think that probably sorts it.

For the record I edited fstab, unmounted /dev/sda1, and restarted. It came back up OK...now all I have to do is see if it uses it as storage when it needs it.

Thanks.

---

### Post by arubislander on 2013-12-03
As [Impavidus ]("http://ubuntuforums.org/member.php?u=1417721")said, the extra partition will **not** get automatically used. You will have to manually move stuff over to it, to make space on your root partition.

---

### Post by oldfred on 2013-12-03
I link folders in my data partitions back into /home so then they are auto used. The main reason I do this is I have multiple Ubuntu installs and can have the same data in every install I boot.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by arubislander on 2013-12-04
+1

I do the same for my Videos and Music folders.

---

