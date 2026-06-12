---
title: "Installing properly so all hard drives mount on start."
date: 2013-06-22
forum: New to Ubuntu
---

### Post by osc1882 on 2013-06-22
So I have done many Ubuntu installs but one thing I have never understood is how to install Ubuntu in such a way that after it is installs all extra hard drives in the computer automaticly mount as storage and show up properly. There's most likely something simple that I am not doing.

Thank you everyone for your time.

---

### Post by capscrew on 2013-06-22
A simple answer is that the installer has to recognize all the drives first.  You need to select the manual configuration of the partitions in the install routine.  Then you need to select the partition on those drives (i.e. sdb1 or sdc1 or sdb2) as the partition to mount at a particular mount point (e.g /mnt or /srv or /data).

Edit:  This will configure the /etc/fstab file so these partition are mounted at boot time.

---

### Post by oldfred on 2013-06-23
I do not mount all partitions with fstab, but do label them when I create them in gparted or later with Disks or Disk utility. So then I know what partition is what.

But the ones I use a lot I mount with fstab. Best to just manually add a line for each partition depending on format.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
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

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

You may also need ownership & permissions. Manual mount and setting ownership & permissions:

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo fdisk -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown $USER:$USER /mnt/data




 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

