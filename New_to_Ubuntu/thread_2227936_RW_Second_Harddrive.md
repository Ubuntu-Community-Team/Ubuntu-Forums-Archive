---
title: "RW Second Harddrive"
date: 2014-06-04
forum: New to Ubuntu
---

### Post by digitalpure on 2014-06-04
Sorry if I missed a thread on this already, I did search :(

I have a Intel 530 mounted on sda and a Crucial 500 mSATA mounted at sdb.    When I installed I set everything to the Intel drive, and only formated the Crucial drive.   I would like to use the crucial drive, and if I click on it in the sidebar (using xubuntu right now) it mounts to /media/david/labelname but it is mounted with root so I can write to it only read.   How can I solve this?    I have tried using the same mount statements that I use to mount my NAS drive just swapping out the cifs for ext4 but that did not work.   I tried copy the route path that it auto mounts at, and then mapping that to a folder in my home folder and again same root issue.

Here is the mount statement that I tried to use, and the auto mount statement that the distro is using.  this is from the "mount" command in the terminal, and it added the ( ) parts.

/dev/sdb1 on /media/david/Virtual Machines type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb1 on /home/david/VirtualMachines type ext4 (rw,username=David,password=david1,sec=ntlm,file_mode=0777,dir_mode=0777,rsize=4096,wsize=4096)

I am sure it is something simple that I am missing but I cannot seem to figure it out.   This is my leaving OSX and WIN behind 100% so I am learning as I go.   Lots of formatting, but I learn something each time.  Looking forward to learning here.

Second question, if I format the machine again should I mount this drive to /usr/local so that it will be auto mounted by fstab?

Thank you in advance for you help

David

---

### Post by marbew on 2014-06-04
in fstab, try to use the **uid** and** gid** that you can find with the command **id** like this example.

UUID="THEUUID0123456789" /media/Data ext4 auto,uid=1000,gid=1000,umask=0022 0 0

---

### Post by Bashing-om on 2014-06-04
digitalpure; Hi !

Piece of cake ( once you know how ).

My favorite method ( hey there are others) to do this:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

The hard drive must be partitioned, and a file system set up on it.
Then it is but a matter of how you want it mounted -- on demand, or automounted.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-06-05
I follow this to add mounts in fstab.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

      
 fstab entry For ext4, copy & paste into fstab with correct UUID & mount point:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2


 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab


 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

I prefer to use /mnt/data as my mount, so it does not show again in Nautilus. But I link all the folders in /mnt/data into my /home so all the folder show up in /home as if they were there.

---

### Post by bab1 on 2014-06-05
> **digitalpure said:**
> Sorry if I missed a thread on this already, I did search :(

I have a Intel 530 mounted on sda and a Crucial 500 mSATA mounted at sdb.    When I installed I set everything to the Intel drive, and only formated the Crucial drive.   I would like to use the crucial drive, and if I click on it in the sidebar (using xubuntu right now) it mounts to /media/david/labelname but it is mounted with root so I can write to it only read.   How can I solve this?    I have tried using the same mount statements that I use to mount my NAS drive just swapping out the cifs for ext4 but that did not work.   I tried copy the route path that it auto mounts at, and then mapping that to a folder in my home folder and again same root issue.

Here is the mount statement that I tried to use, and the auto mount statement that the distro is using.  this is from the "mount" command in the terminal, and it added the ( ) parts.

/dev/sdb1 on /media/david/Virtual Machines type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb1 on /home/david/VirtualMachines type ext4 (rw,username=David,password=david1,sec=ntlm,file_mode=0777,dir_mode=0777,rsize=4096,wsize=4096)

I am sure it is something simple that I am missing but I cannot seem to figure it out.   This is my leaving OSX and WIN behind 100% so I am learning as I go.   Lots of formatting, but I learn something each time.  Looking forward to learning here.

You're on the right  track.  You need to mount the drive to a mount point that has you as the owner.  I would create a mount point  and change the ownership to your user account.  Then mount then you mount the drive there with something like this```
sudo mount UUID=<some-long-number>  /path/to/mount-point 
```
To find the correct UUID you use this command```
sudo blkid -c /dev/null -o list
```

Read the man page for fstab and mount for more information```
man fstab

man mount
```
> 

Second question, if I format the machine again should I mount this drive to /usr/local so that it will be auto mounted by fstab?

The directory  /usr stands for Unix System Resources ( not user).  The /usr/local directory is for non standard local apps and scripts.  You are mounting this partition for data I suppose.  I would mount this partition at something like /mnt/<some-dir> or /data or /srv.  

See [here]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for the standard Linux file system names and uses.

Fstab needs to be manually configured so that partitions are mounted when the host is booted up.  I think you know that, but I just remind you.  ;-)

---

