---
title: "The external HDD gets assigned a new label sometimes/often, work around?"
date: 2013-11-21
forum: New to Ubuntu
---

### Post by neo1599 on 2013-11-21
Hi,

I have just started using Xubuntu. Still getting used to it. Have a feeling Its the Start of a beautiful friendship albeit difficult to begin.

I have set up some torrents to download to an external HDD, now when I try plug-in this HDD sometimes/often it gets assigned a different label for example, 1st time it was: ABC next ABC1. 

Is there any work around so that it always mounts the same? 

Would greatly appreciate your help.

Cheers

---

### Post by newb85 on 2013-11-21
I suggest you look into adding the drive to your fstab.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by bab1 on 2013-11-21
> **neo1599 said:**
> Hi,

I have just started using Xubuntu. Still getting used to it. Have a feeling Its the Start of a beautiful friendship albeit difficult to begin.

I have set up some torrents to download to an external HDD, now when I try plug-in this HDD sometimes/often it gets assigned a different label for example, 1st time it was: ABC next ABC1. 

Is there any work around so that it always mounts the same? 

Would greatly appreciate your help.

Cheers

This happens when you don't unmount the external drive properly.  The original mount is still listed in the udev rules.  When you reinsert the usb cable it thinks it is a new mount and gives it a new name.  Either leave the drive installed or unmount it properly each time you unplug it.

---

### Post by neo1599 on 2013-11-21
Thanks. :) Will take care of the unmount part. Reading the Fstab. :)

A follow up question, I am trying to change the permission on the drive to make it accessible to Plex, but it wont change just switches back. Please guide me on this. 

Thanks for all the help

Cheers

---

### Post by bab1 on 2013-11-21
> **neo1599 said:**
> Thanks. :) Will take care of the unmount part. Reading the Fstab. :)

A follow up question, I am trying to change the permission on the drive to make it accessible to Plex, but it wont change just switches back. Please guide me on this. 

Thanks for all the help

Cheers

Using fstab to mount the drive will make it harder to remove it.  If it is in the fstab but not attached you may get errors.

The reason you can't change the permissions is because it is formatted NTFS.  This format does not use Linux style permissions.  You can provide the initial permissions of your chose when mounting the partition (what you call the drive).  If you leave it to automagically mount then you are the owner and group owner.

---

### Post by newb85 on 2013-11-21
> **bab1 said:**
> Using fstab to mount the drive will make it harder to remove it.  If it is in the fstab but not attached you may get errors.


The nobootwait option should prevent such errors--if the drive isn't present, the fstab entry is ignored.


I don't know what Plex is.  Is it an application?  (Perhaps your bittorrent client...)  Or a username?

---

### Post by ant2 on 2013-11-21
I had the same permissions problems with an 'internal' ntfs HDD and [Plex]("http://www.plexapp.com/"). I solved the problem by adding it to my fstab. 

Trying the nobootwait option mentioned by newb85 may be the way to go.

---

### Post by bab1 on 2013-11-21
> **ant2 said:**
> I had the same permissions problems with an 'internal' ntfs HDD and [Plex]("http://www.plexapp.com/"). I solved the problem by adding it to my fstab. 

Trying the nobootwait option mentioned by newb85 may be the way to go.

Just using *nobootwait *can cause problems with Ubuntu distros.  See here for additional information: [http://techmonks.net/nofail-and-nobootwait-mount-options-in-fstab-prevent-boot-problems/]("http://techmonks.net/nofail-and-nobootwait-mount-options-in-fstab-prevent-boot-problems/")

---

### Post by bab1 on 2013-11-21
> **newb85 said:**
> 
I don't know what Plex is.  Is it an application?  (Perhaps your bittorrent client...)  Or a username?
Plex is a Media Player for HTPC's.

---

### Post by neo1599 on 2013-11-22
Thanks guys. Still trying to figure out the permissions part.

Vary of using the fstab method since I am new and sure to mess it up. Anyone willing to give me a step-by-step guide to go about this? Would give it a go if I knew the exact commands :)[COLOR=#000000]

[/COLOR]

---

### Post by neo1599 on 2013-11-22
bab1,

I saw you post regarding setting the permissions when mounting the drive, I suspect NTFS might very well be the problem.

I am absolutely new to this, would you be kind enough to tell me how to go about mounting the disk and setting permissions at that point? Willing to learn, if it won't be too much of a bother. 


On a separate note, think I read somewhere that setting a folder on Desktop as link to the disk might help solve the permissions part. Might be wrong, this was after a 12 hour work-day and 5 hours of trying to get plex and other stuff to work. 

Cheers

(loving the community)

Will try to set-up a FreeNas after this is up and running

---

### Post by bab1 on 2013-11-22
> **neo1599 said:**
> bab1,

I saw you post regarding setting the permissions when mounting the drive, I suspect NTFS might very well be the problem.

I am absolutely new to this, would you be kind enough to tell me how to go about mounting the disk and setting permissions at that point? Willing to learn, if it won't be too much of a bother. 


On a separate note, think I read somewhere that setting a folder on Desktop as link to the disk might help solve the permissions part. Might be wrong, this was after a 12 hour work-day and 5 hours of trying to get plex and other stuff to work. 

Cheers

(loving the community)

Will try to set-up a FreeNas after this is up and running
FreeNAS is a Distro itself.  Are you going to incorporate the Plex with the FreeNAS storage?  Or are you just thinking out loud.  :-)

We should check what the type of file system and what the UUID the external HDD uses.  With the HDD mounted, post the output of this command```
sudo blkid -c /dev/null -o list
```

I suggest you change the mount point to a more appropriate location.  I use /srv for mounting storage drives (partitions).  Since you are using this for plex storage maybe the directory should be /srv/plex

I don't use Plex myself.  Describe the file permissions problem you are experiencing.  If you have Plex instructions post those links here for me to read.  There is no way to change permissions using a desktop link.  

With that information it is fairly easy to create an entry in fstab to allow the HDD to be mounted consistently.

---

### Post by neo1599 on 2013-11-22
Thanks for the reply bab1.

haha....Was just thinking out loud about the FreeNAS set-up, have a feeling I am way off from it at the moment.

The output from the command you said is in screenshot.[ATTACH=CONFIG]248008[/ATTACH]

The problem I am facing: another screenshot[ATTACH=CONFIG]248009[/ATTACH]

It will not allow me to change the Group and Other permission to Read & Write.

I tried creating a dir on the desktop and copying some media files from the disk to the folder set the permissions and then it would play/get added to Plex.

Ummm...regarding the last part about Plex links, I am very new to it as well. I used this:[http://www.engadget.com/2013/02/14/setting-up-a-plex-environment/](http://www.engadget.com/2013/02/14/setting-up-a-plex-environment/) to set it up. 

Not sure which other link to give. 

Thanks a ton

Sid

---

### Post by bab1 on 2013-11-22
> **neo1599 said:**
> Thanks for the reply bab1.

haha....Was just thinking out loud about the FreeNAS set-up, have a feeling I am way off from it at the moment.

The output from the command you said is in screenshot.[ATTACH=CONFIG]248008[/ATTACH]

The problem I am facing: another screenshot[ATTACH=CONFIG]248009[/ATTACH]

It will not allow me to change the Group and Other permission to Read & Write.

I tried creating a dir on the desktop and copying some media files from the disk to the folder set the permissions and then it would play/get added to Plex.

Ummm...regarding the last part about Plex links, I am very new to it as well. I used this:[http://www.engadget.com/2013/02/14/setting-up-a-plex-environment/](http://www.engadget.com/2013/02/14/setting-up-a-plex-environment/) to set it up. 

Not sure which other link to give. 

Thanks a ton

Sid

Let's try again.  When I ask for the output of a command.  I want you to copy the text from the terminal and paste it to the editor INSIDE the ```
 tags.  The [code] tag icon is the [SIZE=3]#[/SIZE] and it is located at the upper right of the editor.  The output looks like this[CODE]Inside the code tags
```

I can then use your supplied information to create the next set of commands.  :-)  

I see two NTFS partitions on the HDD (sdb).  Which one is the partition you want to use?  What is the other one?  Since we have confirmed that it is a NTFS partition, you have no choice other that setting the owner and permissions at mount time.  You can't change it after that.  This is because NTFS does not understand Linux style permissions.  The NTFS driver emulates the permissions and it only allows the setting at mount time.

You need to be able to use the command line to effectively manage a Linux OS.  Struggling along with the GUI will just be frustrating.  I'll give you the commands and explain them at the same time.

I need to see the mounted partitions.  Post me the output of this command```
df -h
```...this reports the file system disk usage in human readable terms.  

FYI:  Any command we use has a manual page (man page).  You can read about the command *df* by using this command ```
man df
```

---

### Post by squakie on 2013-11-22
[This thread]("http://ubuntuforums.org/showthread.php?t=2184382&p=12843482#post12843482") contains a link to another thread that went all over this - mounting a NTFS file system and setting ownership, permissions, etc.  It might be a good read for you.  And please, ignore my ignorant replies in that thread - as the last post shows I found out I was wrong all along but didn't know it.

Also, since this is a USB device, you cannot guarantee what device it will assigned - one time it could be /dev/sdb1, another time it could be /dev/sdc1.  It depends not only on a dismount, but more importantly it's the nature of a hot-plug USB file system.  You should always use the UUID of the partition in any form of mount for it.  The option to ignore if not present at boot has been working for me, but if you don't want to do that be aware that at boot it will wait for you to answer "s" to skip the mount if the drive isn't plugged in.



EDIT:  forgot to put the link in - duh!

---

### Post by neo1599 on 2013-11-22
haha..had no idea how people got that Code: formatting. Now I know (I hope).

```
 sudo blkid -c /dev/null -o list

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext2             /boot          d4119b6d-3f41-4d66-a589-834556f77da0
/dev/sda5  LVM2_member      (in use)       nOAPDV-VvDn-O7C9-KyYq-Q2WC-cXBS-yIUc15
/dev/mapper/xubuntu--vg-root
           ext4             /              5530b8cd-ba7a-4167-b041-3aba6b858bdc
/dev/mapper/xubuntu--vg-swap_1
           swap             <swap>         1ff1271e-9217-4784-972c-67c39808487c
/dev/sdb1  ntfs    GMS      /media/sid/GMS 01CEE3B513324390
/dev/sdb2  ntfs             /media/sid/01CEE3B518EB1B90 01CEE3B518EB1B90


```


```
~$ df -h

Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/xubuntu--vg-root   36G  4.7G   30G  14% /
none                          4.0K     0  4.0K   0% /sys/fs/cgroup
udev                          334M  8.0K  334M   1% /dev
tmpfs                          69M  972K   68M   2% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          343M  240K  342M   1% /run/shm
none                          100M   28K  100M   1% /run/user
/dev/sda1                     236M   35M  189M  16% /boot
/dev/sdb1                     612G  562G   51G  92% /media/sid/GMS
/dev/sdb2                     321G  7.5G  313G   3% /media/sid/01CEE3B518EB1B90





```

The 321G, is a partition on the external disk. Havent been able to label it. :(

I will go through the command list and start reading. Thx for pointing out the command to start knowing how to utilize linux. :)

Thanks for the effort, so much help is rare. :)

Cheers to both of you.

---

### Post by neo1599 on 2013-11-22
@squakie: Thanks mate, will read through it. :) First time with linux, every little bit helps.

---

### Post by bab1 on 2013-11-22
> **neo1599 said:**
> haha..had no idea how people got that Code: formatting. Now I know (I hope).

```
 sudo blkid -c /dev/null -o list

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext2             /boot          d4119b6d-3f41-4d66-a589-834556f77da0
/dev/sda5  LVM2_member      (in use)       nOAPDV-VvDn-O7C9-KyYq-Q2WC-cXBS-yIUc15
/dev/mapper/xubuntu--vg-root
           ext4             /              5530b8cd-ba7a-4167-b041-3aba6b858bdc
/dev/mapper/xubuntu--vg-swap_1
           swap             <swap>         1ff1271e-9217-4784-972c-67c39808487c
/dev/sdb1  ntfs    GMS      /media/sid/GMS 01CEE3B513324390
/dev/sdb2  ntfs             /media/sid/01CEE3B518EB1B90 [COLOR="#FF0000"]01CEE3B518EB1B90
[/COLOR]

```


```
~$ df -h

Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/xubuntu--vg-root   36G  4.7G   30G  14% /
none                          4.0K     0  4.0K   0% /sys/fs/cgroup
udev                          334M  8.0K  334M   1% /dev
tmpfs                          69M  972K   68M   2% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          343M  240K  342M   1% /run/shm
none                          100M   28K  100M   1% /run/user
/dev/sda1                     236M   35M  189M  16% /boot
/dev/sdb1                     612G  562G   51G  92% /media/sid/GMS
/dev/sdb2                     321G  7.5G  313G   3% /media/sid/01CEE3B518EB1B90





```

The 321G, is a partition on the external disk. Havent been able to label it. :(

I will go through the command list and start reading. Thx for pointing out the command to start knowing how to utilize linux. :)

Thanks for the effort, so much help is rare. :)

Cheers to both of you.
From now on we will ID the partition you want to use as: 01CEE3B518EB1B90

This is the UUID (see the red above).  At the present time it is mounted at: /media/sid/01CEE3B518EB1B90  This is how it automagically mounts if you just plug it in.  We can use the UUID in the fstab file to mount the partition in a more understandable manner.

Post the output of the /etc/fstab file using this command```
cat /etc/fstab
```...the command *cat *was originally created to join 2 file together and show them on the screen.  If there is only one file then only that is shown.

I have done a little reading on Plex.  It appears that Plex creates a user and group named *plex*.  We can confirm that using the following commands```
getent passwd plex

getent group plex
```...the first one gets the entry of the user *plex* from the file *_passwd_*.  The second one gets the entry *plex* from the file *[I]group*[/I]

If the user/group plex is there, we can mount the partition with plex as the group owner and add you to the plex group.  This way you as the admin will always have access without needing to use sudo or gksudo while allowing the Plex user access also.

Post the info and we will move to the next step.  

Both getent and cat are part of the man pages```
man getent

man cat
```

---

### Post by neo1599 on 2013-11-23
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/xubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=d4119b6d-3f41-4d66-a589-834556f77da0 /boot           ext2    defaults        0       2
/dev/mapper/xubuntu--vg-swap_1 none            swap    sw              0       0

```

```
getent passwd plex
plex:x:116:125::/var/lib/plexmediaserver:/bin/bash

getent group plex
plex:x:125:



```

bab1, as always, thanks. :) 

Thanks for reading up on my behalf on plex, I also want to mount the GMS one so I can use it with Plex.

Sid

---

### Post by bab1 on 2013-11-23
> **neo1599 said:**
> ```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/xubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=d4119b6d-3f41-4d66-a589-834556f77da0 /boot           ext2    defaults        0       2
/dev/mapper/xubuntu--vg-swap_1 none            swap    sw              0       0

```

```
getent passwd plex
plex:x:116:125::/var/lib/plexmediaserver:/bin/bash

getent group plex
plex:x:125:



```

bab1, as always, thanks. :) 

Thanks for reading up on my behalf on plex, I also want to mount the GMS one so I can use it with Plex.

SidI think at this point we should just mount the partition manually and see what happens.  But first we need to add your login user to the group plex.  We do that with this command```

sudo gpasswd -a <user> plex

```...substitute your login where it says <user>

Then we check that it was successful with this command```
getent group plex
```...it should show your user name in the group.

Now we need to make a mount point for the partition we are going to mount.  Since you are used using /media/UUID  as the point we will create the mount point at /media.  We do that with this command```
sudo mkdir /media/plex
```...you can see the mount point with this command```
ls -l /media
```...or you can use the GUI to see it.  It is really just a directory.  You mount partitions to the directory.  Actually you are mounting the file system on the partition to the local file system at that directory, so it's not all that hard to understand.

If you plug in the USB HDD it will mount automatically, so you  need to unmount it.  You can use the GUI, but DO NOT the shortcut on the desktop to "safely remove" the drive.  Right click and 'Unmount" the drive.  The reason we are doing this is because "safely remove" unmounts and turns off the drive.  There is no way to mount the drive (partition) without you re-inserting it.  So we just need to unmount the device so we can remount it manually for testing.

To remount (mount) the partition we use this command```

sudo mount -t ntfs UUID=01CEE3B518EB1B90 /media/plex -o uid=1000,gid=125,umask=002,nls=utf8

```...I have used this very command with my UUID and my uid and gid so I know it works. [COLOR="#0000FF"]Edit:  After I removed the space before the nls parameter.[/COLOR]

I want to see directories and files in /media/plex.  What is the output of ```
ls -l /media/plex
```

You should be able to run Plex and see all the files.  Tell me what errors you get.  If all is well we can add the entry to the fstab file for automatic or user directed mounting.

---

### Post by neo1599 on 2013-11-23
Added user to group plex, worked. Cross-checked with the command as told by you.

```
sudo mkdir /media/plex
```

Done and Checked with command as instructed.

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo mount -t ntfs UUID=01CEE3B518EB1B90 /media/plex -o uid=1000,gid=125,umask=002, nls=utf8[/FONT][/COLOR]
```

Got output:

```
~$ sudo mount -t ntfs UUID=01CEE3B518EB1B90 /media/plex -o uid=1000,gid=125,umask=002, nls=utf8 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

Output of: 

```
ls -l /media/plex
```

```
~$ ls -l /media/plextotal 0
~$ 



```


Dont think it worked. :(

---

### Post by bab1 on 2013-11-23
What's this???

```
~$ ls -l /media/plextotal 0
```

How did you get this?

---

### Post by neo1599 on 2013-11-23
> **bab1 said:**
> What's this???

```
~$ ls -l /media/plextotal 0
```

How did you get this?

Uhh..not sure. Just ran the command again. Output:

```

sid@BOX:~$ ls -l /media/plex
total 0
sid@BOX:~$ 





```

---

### Post by bab1 on 2013-11-23
> **neo1599 said:**
> Added user to group plex, worked. Cross-checked with the command as told by you.


Post the output so I can see it.
> 

```
sudo mkdir /media/plex
```

Done and Checked with command as instructed.

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo mount -t ntfs UUID=01CEE3B518EB1B90 /media/plex -o uid=1000,gid=125,umask=002, nls=utf8[/FONT][/COLOR]
```

Got output:

```
~$ sudo mount -t ntfs UUID=01CEE3B518EB1B90 /media/plex -o uid=1000,gid=125,umask=002, nls=utf8 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

Output of: 

```
ls -l /media/plex
```

```
~$ ls -l /media/plextotal 0
~$ 



```


Dont think it worked. :(
This is because one of the parameters is wrong.   It is either the UUID or the uid or the gid.

---

### Post by bab1 on 2013-11-23
> **neo1599 said:**
> Uhh..not sure. Just ran the command again. Output:

```

sid@BOX:~$ ls -l /media/plex
total 0
sid@BOX:~$ 





```
Yes, we're good with that.

---

### Post by Morbius1 on 2013-11-23
> [COLOR=#000000][FONT=Ubuntu Mono]sudo mount -t ntfs UUID=01CEE3B518EB1B90 /media/plex -o uid=1000,gid=125,[/FONT][/COLOR][COLOR=#0000cd][FONT=Ubuntu Mono]umask=002, nls=utf8[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR]
I think it's the space(s) after the last comma and before nls=utf8 that's the problem. Of course it's also possible that at my age I'm not seeing that correctly.

---

### Post by bab1 on 2013-11-23
> **Morbius1 said:**
> I think it's the space(s) after the last comma and before nls=utf8 that's the problem. Of course it's also possible that at my age I'm not seeing that correctly.

Yes indeed.  Remove the space and try it again.

---

### Post by neo1599 on 2013-11-23
> **bab1 said:**
> Post the output so I can see it.

This is because one of the parameters is wrong.   It is either the UUID or the uid or the gid.


Ok, used:

```
sudo mount -t ntfs UUID=01CEE3B518EB1B90 /media/plex -o uid=1000,umask=002,nls=utf8


```

Output of: 

```
ls -l /media/plex
```

```
sudo mount -t ntfs UUID=01CEE3B518EB1B90 /media/plex -o uid=1000,umask=002,nls=utf8


```

```
sid@BOX:~$ getent group plex
plex:x:125:sid
```

Fingers crossed. Checking and will post result of whether it works with plex now.

Umm..since I have taken so much time already one last thing, bab1, do I mount the other partition the same way?

Thanks Morbius for pointing out the extra space. Deleted it. :)

Appreciate all the help

---

### Post by neo1599 on 2013-11-23
Great :) :D

It works with plex now. 

Thank you. 

Will keep asking and learning here. :)

---

### Post by bab1 on 2013-11-23
> **neo1599 said:**
> Great :) :D

It works with plex now. 

Thank you. 

Will keep asking and learning here. :)
So now we need to mount it permanently.  If you leave the drive connected it will revert to the original mount when you reboot.

---

### Post by bab1 on 2013-11-23
> **Morbius1 said:**
> I think it's the space(s) after the last comma and before nls=utf8 that's the problem. Of course it's also possible that at my age I'm not seeing that correctly.

I was doing three things at the same time.  I didn't even notice that it was you that replied.  Thanks for the catch!  I have corrected my error.  :-(

---

### Post by neo1599 on 2013-11-23
> **bab1 said:**
> So now we need to mount it permanently.  If you leave the drive connected it will revert to the original mount when you reboot.

Ok. How to do this?

Also, do I mount the other partition i.e. GMS the same way to the same location? 

Guess mounting both permanently would be great.

As usual, thanks mate.

---

### Post by bab1 on 2013-11-23
> **neo1599 said:**
> Ok. How to do this?

Also, do I mount the other partition i.e. GMS the same way to the same location? 

Guess mounting both permanently would be great.

As usual, thanks mate.

If you are not going to move the external drive we can mount it using fstab.  We can't mount 2 partitions at the same place (/media/plex) but we can easily make a new mount point.  What are you using the other partition for?

So is the HDD going to be always connected to this machine?  What do you want to name the other mount point (lower case)?

---

### Post by neo1599 on 2013-11-24
Hey,

The external drive isn't going to be always connected. I use it to take back-ups of a few things from work computers. The other partition will be the one with all the media files for plex. I think I will move all the back-ups etc to the partition we have mounted as its smaller.

The other mount point can be "downloads" or any other name no specific name in mind. :)

Thanks bab1

Sid

(Oh..Great, now plex has started using/counting towards my internet data cap. :( Another question coming up, would this be an xubuntu, windows, plex or networking. Damn I am a noob)

---

### Post by neo1599 on 2013-11-24
Tried mounting the other partition using the commands as guide. Seems to have mounted with correct permissions. :)

```
sid@BOX:~$ sudo mount -t ntfs LABEL=GMS /media/plex2 -o umask=002,nls=utf8
```

I omitted the uid, gid didn't know how to get them or risk going wrong. Fingers crossed

---

### Post by bab1 on 2013-11-24
> **neo1599 said:**
> Hey,

The external drive isn't going to be always connected. I use it to take back-ups of a few things from work computers. The other partition will be the one with all the media files for plex. I think I will move all the back-ups etc to the partition we have mounted as its smaller.

The other mount point can be "downloads" or any other name no specific name in mind. :)

Thanks bab1

Sid

(Oh..Great, now plex has started using/counting towards my internet data cap. :( Another question coming up, would this be an xubuntu, windows, plex or networking. Damn I am a noob)

Since the HDD is moving around you should add the entries to the fstab file but mount them with a simple command.

Make a copy of the fstab file with this command```
sudo cp /etc/fstab /etc/fstab.original
```

I see you created a second mount point, so we will use that. 

Now add these lines to the bottom of the /etc/fstab file```

## NOTE: The following UUID's are different but very similar ##
#large partition 
UUID=01CEE3B513324390 /media/plex ntfs uid=1000,gid=125,umask=002,nls=utf8,noauto 0 0
#lsmall partition 
UUID=01CEE3B518EB1B90 /media/plex2 ntfs uid=1000,gid=125,umask=002,nls=utf8,noauto 0 0

```
To edit the file we can use gedit.  To open the editor with sudo use this command```

gksudo gedit /etc/fstab

```...add the lines.

Now we can mount the partitions with these simple commands
```
sudo mount /media/plex

sudo mount /media/plex2
```

---

### Post by neo1599 on 2013-11-24
```
sid@BOX:~$ sudo cp /etc/fstab.original[sudo] password for sid: 
cp: missing destination file operand after &#8216;/etc/fstab.original&#8217;
Try 'cp --help' for more information.
sid@BOX:~$ sudo cp /etc/fstab /etc/fstab.original
sid@BOX:~$ gksudo gedit /etc/fstab
sid@BOX:~$ gksudo gedit /etc/fstab
sid@BOX:~$ sudo gksudo gedit /etc/fstab
sid@BOX:~$ 

```

Not sure what I am doing wrong. But cant get to the editing part.

Tried:

```

sudo nano /etc/fstab

```

saved the file.

now when i try:

```

sid@BOX:~$ umount /media/plex
umount: /media/plex mount disagrees with the fstab
sid@BOX:~$ 

```

think I messed up somewhere. :(

Tried umount with sudo and it worked.

Now when I try to mount with:

```

sudo mount /media/plex

```

I get 

```

sid@BOX:~$ sudo mount /media/plex
[sudo] password for sid: 
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
sid@BOX:~$ 

```

Shouldn't have tried anything :(

---

### Post by bab1 on 2013-11-24
> **neo1599 said:**
> ```
sid@BOX:~$ sudo cp /etc/fstab.original[sudo] password for sid: 
cp: missing destination file operand after &#8216;/etc/fstab.original&#8217;
Try 'cp --help' for more information.
sid@BOX:~$ sudo cp /etc/fstab /etc/fstab.original
sid@BOX:~$ gksudo gedit /etc/fstab
sid@BOX:~$ gksudo gedit /etc/fstab
sid@BOX:~$ sudo gksudo gedit /etc/fstab
sid@BOX:~$ 

```

Not sure what I am doing wrong. But cant get to the editing part.

Tried:

```

sudo nano /etc/fstab

```

saved the file.

now when i try:

```

sid@BOX:~$ umount /media/plex
umount: /media/plex mount disagrees with the fstab
sid@BOX:~$ 

```

think I messed up somewhere. :(

Tried umount with sudo and it worked.

Now when I try to mount with:

```

sudo mount /media/plex

```

I get 

```

sid@BOX:~$ sudo mount /media/plex
[sudo] password for sid: 
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
sid@BOX:~$ 

```

Shouldn't have tried anything :(
Post the output of these commands```
cat /etc/fstab

ls -l /media

df -h

mount
```

---

### Post by neo1599 on 2013-11-25
> **bab1 said:**
> Post the output of these commands```
cat /etc/fstab

ls -l /media

df -h

mount
```

Hi

Out out:

```
sid@BOX:~$ cat /etc/fstab /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/xubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=d4119b6d-3f41-4d66-a589-834556f77da0 /boot           ext2    defaults        0       2
/dev/mapper/xubuntu--vg-swap_1 none            swap    sw              0       0
## NOTE: The following UUID's are different but very similar ##
#large partition 
UUID=01CEE3B513324390 /media/plex ntfs uid=1000,gid=125,umask=002,nls=utf8,noauto 0 0
#lsmall partition 
UUID=01CEE3B518EB1B90 /media/plex2 ntfs uid=1000,gid=125,umask=002,nls=utf8,noauto 0 0
sid@BOX:~$ ls -l /media
total 32
drwxr-xr-x  2 root root  4096 Nov 22 17:29 backup
drwxr-xr-x  2 root root  4096 Nov 22 17:29 gms
drwxrwxr-x  1 sid  plex 16384 Nov 22 04:27 plex
drwxrwxr-x  1 sid  plex  4096 Nov 25 02:36 plex2
drwxr-x---+ 2 root root  4096 Nov 24 20:08 sid

```
```

sid@BOX:~$ df -h
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/xubuntu--vg-root   36G  9.9G   24G  30% /
none                          4.0K     0  4.0K   0% /sys/fs/cgroup
udev                          334M  4.0K  334M   1% /dev
tmpfs                          69M  992K   68M   2% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          343M  240K  342M   1% /run/shm
none                          100M   24K  100M   1% /run/user
/dev/sda1                     236M   61M  163M  28% /boot
/dev/sdb1                     612G  566G   47G  93% /media/plex
/dev/sdc2                     321G  8.6G  312G   3% /media/plex2
/dev/sdc1                     612G  566G   47G  93% /media/plex

```

```

sid@BOX:~$ mount
/dev/mapper/xubuntu--vg-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot type ext2 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=sid)
/dev/sdb1 on /media/plex type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc2 on /media/plex2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/plex type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
sid@BOX:~$ 



```

---

### Post by bab1 on 2013-11-25
> **neo1599 said:**
> Hi

Out out:

```
sid@BOX:~$ cat /etc/fstab /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/xubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=d4119b6d-3f41-4d66-a589-834556f77da0 /boot           ext2    defaults        0       2
/dev/mapper/xubuntu--vg-swap_1 none            swap    sw              0       0
## NOTE: The following UUID's are different but very similar ##
#large partition 
UUID=01CEE3B513324390 /media/plex ntfs uid=1000,gid=125,umask=002,nls=utf8,noauto 0 0[COLOR="#FF0000"]<--This is the larger 620 GB Partition [/COLOR]
#lsmall partition 
UUID=01CEE3B518EB1B90 /media/plex2 ntfs uid=1000,gid=125,umask=002,nls=utf8,noauto 0 0[COLOR="#FF0000"]<- This is the smaller 320GB partition[/COLOR]

```
 
```

sid@BOX:~$ ls -l /media
total 32
drwxr-xr-x  2 root root  4096 Nov 22 17:29 backup
drwxr-xr-x  2 root root  4096 Nov 22 17:29 gms
drwxrwxr-x  1 sid  plex 16384 Nov 22 04:27 plex [COLOR="#FF0000"]<- The larger partition is mounted here[/COLOR]
drwxrwxr-x  1 sid  plex  4096 Nov 25 02:36 plex2[COLOR="#FF0000"]<-- The smaller partition is mounted here[/COLOR]
drwxr-x---+ 2 root root  4096 Nov 24 20:08 sid

```

```

sid@BOX:~$ df -h
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/xubuntu--vg-root   36G  9.9G   24G  30% /
none                          4.0K     0  4.0K   0% /sys/fs/cgroup
udev                          334M  4.0K  334M   1% /dev
tmpfs                          69M  992K   68M   2% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          343M  240K  342M   1% /run/shm
none                          100M   24K  100M   1% /run/user
/dev/sda1                     236M   61M  163M  28% /boot
/dev/sdb1                     612G  566G   47G  93% /media/plex[COLOR="#FF0000"]<-- Here is 1 of 2 partitions mounted at /media/plex[/COLOR]
/dev/sdc2                     321G  8.6G  312G   3% /media/plex2
/dev/sdc1                     612G  566G   47G  93% /media/plex [COLOR="#FF0000"]<-- This means you mounted another partition on top of the first one![/COLOR]

```
The seems to be your problem.  [COLOR="#dd00dd"]When you mount a second partition on top of the first one you will only see the last one mounted.[/COLOR]> 
```

sid@BOX:~$ mount
/dev/sdb1 on /media/plex type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096) [COLOR="#FF0000"] <-- The first mount ???[/COLOR]
/dev/sdc2 on /media/plex2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/plex type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096) [COLOR="#FF0000"]<- The second mount ???[/COLOR]
sid@BOX:~$ 



```

Hi Sid,
So we have 3 partitions not just 2.  Is this correct?

I think we need to sort the 3 partitions out.  Why don't you tell me what the 3 partitions are for.  We need to make a mount point for each one.  Lets make then names more unique.  We can use plex. but lets not use plex2.  plex2 is too similar to plex.  If you tell me what data you are going to put on each of the partitions I can make suggestions. See my comments in red above.

---

### Post by neo1599 on 2013-11-26
Hi bab1,

There are only 2 partitions as far as I know on the external hard drive. There is an Internal Hard drive which I have exclusively for xubuntu.

I am going to use 1 partition(smaller one) exclusively for taking back-ups and doing some work for office. The larger one if for all kind of Downloads eg, games, movies, program install etc. 

Not sure, but when I just double the partition icons appearing on the desktop they seem to work now with no adjustment required. 

Another output:

```

sid@BOX:~$ sudo umount /media/plex
[sudo] password for sid: 
sid@BOX:~$ sudo umount /media/plex2
sid@BOX:~$ sudo mount /media/plex
[mntent]: line 1 in /etc/fstab is bad
sid@BOX:~$ sudo mount /media/plex2
[mntent]: line 1 in /etc/fstab is bad
sid@BOX:~$ 

```

Output of /etc/fstab in nano:

```

  GNU nano 2.2.6              File: /etc/fstab                                  


 /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/xubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=d4119b6d-3f41-4d66-a589-834556f77da0 /boot           ext2    defaults     $
/dev/mapper/xubuntu--vg-swap_1 none            swap    sw              0       0
## NOTE: The following UUID's are different but very similar ##
#large partition
UUID=01CEE3B513324390 /media/plex ntfs uid=1000,gid=125,umask=002,nls=utf8,noau$
#lsmall partition
UUID=01CEE3B518EB1B90 /media/plex2 ntfs uid=1000,gid=125,umask=002,nls=utf8,noa$






                               [ Read 16 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell



```

Appreciate all the help.

Thanks

Sid :)

---

### Post by bab1 on 2013-11-26
> **neo1599 said:**
> Hi bab1,

There are only 2 partitions as far as I know on the external hard drive. There is an Internal Hard drive which I have exclusively for xubuntu.

I am going to use 1 partition(smaller one) exclusively for taking back-ups and doing some work for office. The larger one if for all kind of Downloads eg, games, movies, program install etc. 

Not sure, but when I just double the partition icons appearing on the desktop they seem to work now with no adjustment required. 

Another output:

```

sid@BOX:~$ sudo umount /media/plex
[sudo] password for sid: 
sid@BOX:~$ sudo umount /media/plex2
sid@BOX:~$ sudo mount /media/plex
[mntent]: line 1 in /etc/fstab is bad
sid@BOX:~$ sudo mount /media/plex2
[mntent]: line 1 in /etc/fstab is bad   [COLOR="#FF0000"]<-- This means "Look at line 1 in the /etc/fstab file[/COLOR]
sid@BOX:~$ 

```

Output of /etc/fstab in nano:

```

  GNU nano 2.2.6              File: /etc/fstab                                  


 /etc/fstab: static file system information.   [COLOR="#FF0000"]<- This needs to have a **#** at the start of the line to make it a comment.[/COLOR]
#  [COLOR="#FF0000"]<<<<<<----This line is just a comment (not executed.  It's for the programmer to leave notes[/COLOR]
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/xubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=d4119b6d-3f41-4d66-a589-834556f77da0 /boot           ext2    defaults     $
/dev/mapper/xubuntu--vg-swap_1 none            swap    sw              0       0
## NOTE: The following UUID's are different but very similar ##
#large partition
UUID=01CEE3B513324390 /media/plex ntfs uid=1000,gid=125,umask=002,nls=utf8,noau$
#lsmall partition
UUID=01CEE3B518EB1B90 /media/plex2 ntfs uid=1000,gid=125,umask=002,nls=utf8,noa$






                               [ Read 16 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell



```

Appreciate all the help.

Thanks

Sid :)

Add a # mark to make the line a comment rather than a line to be parsed (read) at mount time.

I'm not sure how it happened but the OS found 3 devices (sda, adb and sdc).  This may have been because of the uncommented line.

Unmount the 2 partitions (sudo umount...) and try it again after editing the fstab.  After we get it working we can play with the mountpoint names.

---

### Post by neo1599 on 2013-11-26
> **bab1 said:**
> Add a # mark to make the line a comment rather than a line to be parsed (read) at mount time.

I'm not sure how it happened but the OS found 3 devices (sda, adb and sdc).  This may have been because of the uncommented line.

Unmount the 2 partitions (sudo umount...) and try it again after editing the fstab.  After we get it working we can play with the mountpoint names.

After editing:

```

  GNU nano 2.2.6              File: /etc/fstab                                  


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/xubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=d4119b6d-3f41-4d66-a589-834556f77da0 /boot           ext2    defaults     $
/dev/mapper/xubuntu--vg-swap_1 none            swap    sw              0       0
## NOTE: The following UUID's are different but very similar ##
#large partition
UUID=01CEE3B513324390 /media/plex ntfs uid=1000,gid=125,umask=002,nls=utf8,noau$
#lsmall partition
UUID=01CEE3B518EB1B90 /media/plex2 ntfs uid=1000,gid=125,umask=002,nls=utf8,noa$






                               [ Read 16 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```

```

sudo mount /media/plex2
sudo mount /media/plex

```

worked perfectly

Thanks. :)

---

