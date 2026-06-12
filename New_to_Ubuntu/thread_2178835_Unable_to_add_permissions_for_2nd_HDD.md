---
title: "Unable to add permissions for 2nd HDD"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by Matt_Jackson on 2013-10-05
Hi all, 

I couldnt find a welcome section so hello :) 

Im new to Ubuntu and the world of Linux, my last adventure into this world wasnt great with errors from install years ago. Ive tried again with a new build to see what its like and so far loving it but having some niggles.

Im currently trying to apply full permissions to a partition which i setup with gparted. Currently the partition of media/Storage 1 is owned by root, the hdd is /sda on ext 3. 

I have tried some of the commands on terminal to change permissions like below but to no avail. Permissions show are root and options are greyed out to create new folder in directory.

> sudo chmod o+rw /media/Storage 1
sudo chmod o+rw /media
sudo chown -R mj:mj /media/Storage 1


I had problems at first with partition then with mounting from start up but now shows in folder directory and is mounted from start too. 

Ive tried reading other threads and following but unfortunately no avail.

---

### Post by philinux on 2013-10-05
In the past when I had a similar problem, I used the app Disks and used quick format but made sure I ticked "take ownership".

---

### Post by Matt_Jackson on 2013-10-05
Thanks for the info. 

I formated with Disk Utility and then created the new partition through the same tool, ticked on "Take Ownership" when its started to partition a warning is shown of "Warning the partition is misaligned by 512 bytes" 

I left the Size as default of 2000.399GB. Type EXT 4 . Changed Volume to Storage 1, and take ownership.

Im guessing the 2000.399GB is the problem ?

---

### Post by oldfred on 2013-10-05
No, I suspect the space is the problem. 
That often causes issues with Linux and you have to either put it into quotes or "escape" it with / or /040 so system knows it is a space.
I found it just easier to stop using spaces with anything Linux. I even stopped in Windows when running it.
So I just use CamelCase, under_score or justonename.
Try Storage1 or Storage_1 and then your chown and chmod commands will work. They might also work with quotes or escape.

 I recently learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 
#is better than this:
sudo chmod 775 /mnt/data
sudo chown -R $USER:$USER /mnt/data
#where $USER should be your login name
#or to see user
echo $USER

---

### Post by Matt_Jackson on 2013-10-05
I have deleted the Storage 1 Partition
Tried Disk Utility and entered Storage_1 - Comes up with Warning Partition is misaligned by 512 bytes
Deleted that partition and used gparted to create a new partition with the Storage_1 name.
I ran sudo chmod -R a+rwX /media/Storage_1 then checked the permissions on the folder and still shows root. 
rebooted and ran the same command and still shows root
Tried to apply mj in pysdm and still again shows root
Ive deleted that partition and doing a new partition in gparted with name Storage1 as we speak. Then will try sudo chmod -R a+rwX /media/Storage1

---

### Post by oldfred on 2013-10-05
Until you run chown it will be root. 
chmod is permissions.

I do not recommend pysdm as it still uses device and has not been updated for ages. Better to use UUID.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

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

---

### Post by Matt_Jackson on 2013-10-05
Phew..... after re reading your post guys and other areas finally got it sussed.

Drive mounted and can now add folders etc . Cheers all

---

### Post by Crinkle on 2013-10-05
Can someone advise on this? I have the same issue but theres no "take ownership" option in gparted for me?

---

### Post by oldfred on 2013-10-05
Read back thru thread. I have never used a take ownership with gparted. That may depend on format of partition as you cannot have ownership of Windows formats except as the defaults you use when mounting with fstab or manually mounting.

---

