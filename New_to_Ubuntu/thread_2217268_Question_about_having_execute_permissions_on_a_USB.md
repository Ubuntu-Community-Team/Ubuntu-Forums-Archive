---
title: "Question about having execute permissions on a USB"
date: 2014-04-16
forum: New to Ubuntu
---

### Post by Freeze145 on 2014-04-16
Hello
I am reasonably new to Ubuntu, and I have downloaded 13.10 Saucy onto my Chromebook as a dual boot
I have downloaded Steam onto it but I want to download a game onto a USB stick
I tried to set a steam library to the USB but it needs to be on a _filesystem with execute permissions._
How do I make it so?

Things I have already tried:

Changing it by right clicking the USB drive and changing permissions from read only to create and delete files (for group); it would not change at all

Running *sudo gedit /ect/fstab *when I do this, it shows /ect/fstab as completely empty, and if I only type in /ect/fstab it says that there is no such file or directory.


Any other ideas?

P.S. apologies in advance if it takes me a while to reply.

---

### Post by Impavidus on 2014-04-16
Usb flash drives usually have a FAT32 file system, which doesn't support Linux permissions. One possible solution is formatting your usb drive ext4, but then you can't use it any more on Windows or Mac systems. The other solution is setting different mount options. Mount options can be set from /etc/fstab (not /ect/fstab, which doesn't exist). Usb drives are rarely put in fstab, as they can be automounted. I don't know how to add execute permission when automounting, but it may be possible.

---

### Post by bab1 on 2014-04-16
> **Impavidus said:**
> Usb flash drives usually have a FAT32 file system, which doesn't support Linux permissions. One possible solution is formatting your usb drive ext4, but then you can't use it any more on Windows or Mac systems. The other solution is setting different mount options. Mount options can be set from /etc/fstab (not /ect/fstab, which doesn't exist). Usb drives are rarely put in fstab, as they can be automounted. I don't know how to add execute permission when automounting, but it may be possible.

There is no reason you can't mount a USB connected disk via fstab.  The auto mount of that drive is not attempted as it is already mounted when the auto mount routine scans for attached USB devices.

---

### Post by Freeze145 on 2014-04-16
Alright, so I have entered in the command sudo gedit /etc/fstab and it has come up with a file with only the line
# UNCONFIGURED FSTAB FOR BASE SYSTEM
in it. I added
/dev/sdc1 /media/FREEZE vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
which was told to me by another source, but it still doesn''t have the execute permissions. 
Now, when I go to add my steam library, there is nothing in /media , but there is in /var/host/media
Have I got the wrong place?

One more thing, I see to be able to read the files, but everytime I put the USB in it comes up with 'unable to mount FREEZE'

*EDIT* When I try adding the Steam Library to /media it says it is read only.

---

### Post by bab1 on 2014-04-16
> **Freeze145 said:**
> Alright, so I have entered in the command sudo gedit /etc/fstab and it has come up with a file with only the line
# UNCONFIGURED FSTAB FOR BASE SYSTEM
in it. I added
/dev/sdc1 /media/FREEZE vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
which was told to me by another source, but it still doesn''t have the execute permissions. 
Now, when I go to add my steam library, there is nothing in /media , but there is in /var/host/media
Have I got the wrong place?

One more thing, I see to be able to read the files, but everytime I put the USB in it comes up with 'unable to mount FREEZE'

*EDIT* When I try adding the Steam Library to /media it says it is read only.

Well...After carefully reading your description of your situation,  I'm going to back up a bit here.  If you mount a partition via fstab you should not remove the drive or reinsert it after booting up.  In addition, I'm not so sure you edited the correct fstab file.  When I search on  the terms "# UNCONFIGURED FSTAB FOR BASE SYSTEM" or "/var/host/media" All I get are references to Chromebook and SSD installations.  Not Ubuntu at all.

Most likely the directory /media/FREEZE does not exist unless the USB drive is auto mounted.  Remove the drive and the directory is deleted automatically.

I have mounted flash drives with the command [FONT=Courier New][SIZE=2]sudo mount ...[/SIZE][/FONT] and you can craft that.  You need to create your own mount point.  One last point; since the vFAT driver is what is controlling the file permissions, it is entirely possible that the drive is not equipped to handle executables at all.  You could try NTFS formatting for the drive.  Both Windows and Linux understand that format.

---

### Post by Freeze145 on 2014-04-16
> **bab1 said:**
> Well...After carefully reading your description of your situation,  I'm going to back up a bit here.  If you mount a partition via fstab you should not remove the drive or reinsert it after booting up.  In addition, I'm not so sure you edited the correct fstab file.  When I search on  the terms "# UNCONFIGURED FSTAB FOR BASE SYSTEM" or "/var/host/media" All I get are references to Chromebook and SSD installations.  Not Ubuntu at all.

Most likely the directory /media/FREEZE does not exist unless the USB drive is auto mounted.  Remove the drive and the directory is deleted automatically.

I have mounted flash drives with the command [FONT=Courier New][SIZE=2]sudo mount ...[/SIZE][/FONT] and you can craft that.  You need to create your own mount point.  One last point; since the vFAT driver is what is controlling the file permissions, it is entirely possible that the drive is not equipped to handle executables at all.  You could try NTFS formatting for the drive.  Both Windows and Linux understand that format.


Thank you so much, I have formatted it to NTFS like you said, 
BUT
Can you please tell me how to mount it with the specific permissions, and make sure it mounts everytime I put it in? I don''t know how, I'm relatively new to linux and ubuntu.

I am on a Chromebook by the way, so maybe it hasn''t been mounted at all. 

*EDIT* If I right click it it will say it has read-write permissions but it does not seem to exist for steam unless I go the long way (/var/host/media) and at which it will still not have execute permissions.

---

### Post by bab1 on 2014-04-17
> **Freeze145 said:**
> Thank you so much, I have formatted it to NTFS like you said, 
BUT
Can you please tell me how to mount it with the specific permissions, and make sure it mounts everytime I put it in? I don''t know how, I'm relatively new to linux and ubuntu.

I am on a Chromebook by the way, so maybe it hasn''t been mounted at all. 

*EDIT* If I right click it it will say it has read-write permissions but it does not seem to exist for steam unless I go the long way (/var/host/media) and at which it will still not have execute permissions.

It seems like you have multiple issues.  If you are logged in to Chrombook then Ubuntu is not being used at all.  Chromebook is Linux distro and may work similarly to Ubuntu, but as we have seen with with the fstab location and content, it is not exactly the same.

If you are using Ubuntu then the the method to manually set the ownership and permissions for NTFS partitions is described [here]("http://ubuntuforums.org/showthread.php?t=1604251").  All the options for mounting using fstab are described [here]("https://help.ubuntu.com/community/Fstab").  Pay attention to the ***noauto *** option.

---

### Post by Freeze145 on 2014-04-18
> **bab1 said:**
> It seems like you have multiple issues.  If you are logged in to Chrombook then Ubuntu is not being used at all.  Chromebook is Linux distro and may work similarly to Ubuntu, but as we have seen with with the fstab location and content, it is not exactly the same.

If you are using Ubuntu then the the method to manually set the ownership and permissions for NTFS partitions is described [here]("http://ubuntuforums.org/showthread.php?t=1604251").  All the options for mounting using fstab are described [here]("https://help.ubuntu.com/community/Fstab").  Pay attention to the ***noauto *** option.

Thank you, but why would I wan''t it not to auto mount every time? 
I am using Ubuntu 13.10 dualboot with Chrome OS (if I wasn't clear before) but the main thing is that there are no lines in /etc/fstab other than the one I added (UUID=C64C10144C0FFE3D /media/freeze ntfs-3g defaults,auto,uid=1000,gid=1000,umask=000 0 0) and this:

# UNCONFIGURED FSTAB FOR BASE SYSTEM

What's more, is that if I try to type in the command *mount -a *it comes up with this:

Mount is denied because the NTFS volume is already exclusively opened. The volume may already be mounted or another software may use it which could be identified for example by the help of the 'fuser' command.

I try *sudo fuser *and aside from telling me what a lot of commands (such as -a and -m) do, it says that there are no process specification given.

Any ideas?

Thank you so much for helping this far.

---

### Post by Mark Phelps on 2014-04-18
> Thank you, but why would I wan''t it not to auto mount every time? 

Because, if it's not inserted prior to boot, booting will HANG waiting for the device to be found, prompting you to do something to continue.

---

### Post by bab1 on 2014-04-18
> **Freeze145 said:**
> Thank you, but why would I wan''t it not to auto mount every time?

You can't control the file and directory ownership and permissions when you allow automounting.
> 
I am using Ubuntu 13.10 dualboot with Chrome OS (if I wasn't clear before) but the main thing is that there are no lines in /etc/fstab other than the one 
I added (UUID=C64C10144C0FFE3D /media/freeze ntfs-3g defaults,auto,uid=1000,gid=1000,umask=000 0 0) and this:

# UNCONFIGURED FSTAB FOR BASE SYSTEM


Dual boot is fine, but which OS are you logged into?  No Ubuntu that I know of uses anything but a /etc/fstab.  It should look like this
```

[COLOR="#0000FF"]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0[/COLOR]
# / was on /dev/sda1 during installation
UUID=c4807753-7a09-4d0a-8052-bf96c1f81d40 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=46a258bf-6ace-4d52-b4d7-db47e7b3de7b /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=69e4c9c7-a439-416d-85a9-c79162983068 none            swap    sw              0       0

```
Note the header in blue.
> 
What's more, is that if I try to type in the command *mount -a *it comes up with this:
```
Mount is denied because the NTFS volume is already exclusively opened. The volume may already be mounted or another software may use it which could be identified for example by the help of the 'fuser' command.

```
I try *sudo fuser *and aside from telling me what a lot of commands (such as -a and -m) do, it says that there are no process specification given.

Mount -a can only be used by the root user (via sudo or su).  You should not have gotten the denied message anyway.
> 

Any ideas?

Are you really logged into Ubuntu?  Post the output of this```

lsb_release -a

```

---

### Post by Freeze145 on 2014-04-18
No, I am definitely logged into Ubuntu
lsb_release -a basically says Ubuntu 13.10 Saucy

Also, I can tell you right now that the /etc/fstab contains nothing but:
# UNCONFIGURED FSTAB FOR BASE SYSTEM
UUID=C64C10144C0FFE3D /media/freeze ntfs-3g defaults,auto,uid=1000,gid=1000,umask=000 0 0

The second line being the one I added. 

I'll try adding noauto to it and see if it works.

---

### Post by Freeze145 on 2014-04-18
No, I obviously have not made proper use of it but it seems to not make a difference.

---

### Post by bab1 on 2014-04-18
> **Freeze145 said:**
> No, I obviously have not made proper use of it but it seems to not make a difference.
I'm not at all convinced that you can do what you want to do.  I'm also not sure we are using some terms the same way.

To my way way of thinking, automount is the mounting of a USB based partition via udisks with NO CONFIGURATION in fstab at all.  When you configure a partition to be mounted via fstab you have a configured mount.  These are two different things.  Which is it that you are attempting to do?

---

### Post by Freeze145 on 2014-04-18
> **bab1 said:**
> I'm not at all convinced that you can do what you want to do.  I'm also not sure we are using some terms the same way.

To my way way of thinking, automount is the mounting of a USB based partition via udisks with NO CONFIGURATION in fstab at all.  When you configure a partition to be mounted via fstab you have a configured mount.  These are two different things.  Which is it that you are attempting to do?

I am trying to mount the USB with execute permissions.

---

### Post by bab1 on 2014-04-19
> **Freeze145 said:**
> I am trying to mount the USB with execute permissions.

Since auto mounting the partition will not allow you to have control over user permissions you can't use auto mount at all.  

This means you have to mount the partition (the USB drive) via fstab.  No mounting "when I insert the drive".  You will need to use *noauto*  as one of options to prevent auto mounting.  This is because the auto mount routines scan the USB connection when you inset the device unless there is an entry for the device in the fstab file.   

NTFS doesn't seem to work for you.  I recommend you change the partition formatting to the Linux native format.  That would be EXT4.  This will allow you to manage the permissions and set executables just like any other place in the system.

Then all that is needed is for you to script the mount and dismount or the partition when you need it mounted.

In summary you would need to do this
[LIST]
[*]Format the USB drive to EXT4 (Note:  You will have a new UUID because of the new formatting)
[*]Create a mount point for the new partition
[*]Mount the partition at that mount point and set the permissions you need
[*]Create the mount configuration in the fstab file
[*]Create a script to run to mount and unmount the partition
[/LIST]

Do you need specifics for any of this?

---

### Post by Freeze145 on 2014-04-20
> **bab1 said:**
> Since auto mounting the partition will not allow you to have control over user permissions you can't use auto mount at all.  

This means you have to mount the partition (the USB drive) via fstab.  No mounting "when I insert the drive".  You will need to use *noauto*  as one of options to prevent auto mounting.  This is because the auto mount routines scan the USB connection when you inset the device unless there is an entry for the device in the fstab file.   

NTFS doesn't seem to work for you.  I recommend you change the partition formatting to the Linux native format.  That would be EXT4.  This will allow you to manage the permissions and set executables just like any other place in the system.

Then all that is needed is for you to script the mount and dismount or the partition when you need it mounted.

In summary you would need to do this
[LIST]
[*]Format the USB drive to EXT4 (Note:  You will have a new UUID because of the new formatting)
[*]Create a mount point for the new partition
[*]Mount the partition at that mount point and set the permissions you need
[*]Create the mount configuration in the fstab file
[*]Create a script to run to mount and unmount the partition
[/LIST]

Do you need specifics for any of this?

Sorry I haven't been able to reply (Easter is  busy for me)
So, a few things:

How do I format it?
Is creating a mount point just making a folder (e.g. /media/freeze)?
I am assuming I mount through fstab. Am I right? If I am, does the fact my fstab file is almost empty (except fot the unconfigured fstab note)
How do I create a script?

Thanks in advance

---

### Post by bab1 on 2014-04-20
> **Freeze145 said:**
> Sorry I haven't been able to reply (Easter is  busy for me)
So, a few things:

How do I format it?
Is creating a mount point just making a folder (e.g. /media/freeze)?
I am assuming I mount through fstab. Am I right? If I am, does the fact my fstab file is almost empty (except fot the unconfigured fstab note)
How do I create a script?

Thanks in advance
I took the time today to format to EXT4  a spare USB flash drive.  I learned something myself.  The drive **can** be auto mounted and you can make your files executable.  So in the end you only loose the ability to use the drive in a Windows or Apple machine.  EXT4 is native to Linux only.
 
You can format the partition using the GUI app *Disk Utility*.  The Disk Utility is located at:  Applications>>Accessories>>Disk Utility on my machine.  Move all of the files on the flash drive to a safe place as the formatting will delete them.

Select the USB Flash Drive and then select the volume (partition) on that drive.  Unmount the volume.  Then you click on the button that says **Format Volume**.  Select a name for the volume and select EXT4 for the type.   Then move all the files back.

At this point I found the flash drive will mount at /media/<Drive_Label> and I was able to run executables.

---

### Post by Freeze145 on 2014-04-21
When I got into Disk Utility (I used the gksu gnome-disks command in terminal because I can't seem to find it anywhere else, but the partitions listed to format to did not include EXT4. I tried installing GParted but it would not let me change the partition.

Thank you for taking the time to do this but if you feel it is getting to the point where it just won't work don't hesitate to say so.

---

### Post by bab1 on 2014-04-21
> **Freeze145 said:**
> When I got into Disk Utility (I used the gksu gnome-disks command in terminal because I can't seem to find it anywhere else, but the partitions listed to format to did not include EXT4. I tried installing GParted but it would not let me change the partition.

Thank you for taking the time to do this but if you feel it is getting to the point where it just won't work don't hesitate to say so.

II don't know what gnome-disks is.  The utility I'm speaking of is named **palimpsest**.  Try that from the command line.  No gksu needed (or wanted).   See if that works.  Remember that you are looking for the physical device (drive) and then the partition (volume).

The volume is what you format.  The type of format is ext4.

---

### Post by Freeze145 on 2014-04-22
> **bab1 said:**
> II don't know what gnome-disks is.  The utility I'm speaking of is named **palimpsest**.  Try that from the command line.  No gksu needed (or wanted).   See if that works.  Remember that you are looking for the physical device (drive) and then the partition (volume).

The volume is what you format.  The type of format is ext4.

That's the point, that command (palimpsest) is, from what I have looked up, outdated. It certainly does not work for me with or without gksu. From other research gnome-disks was the new command for opening it, but it still won't let me format it to ext4.

---

### Post by bab1 on 2014-04-22
> **Freeze145 said:**
> That's the point, that command (palimpsest) is, from what I have looked up, outdated. It certainly does not work for me with or without gksu. From other research gnome-disks was the new command for opening it, but it still won't let me format it to ext4.
Hmmm...  It turns out that palimpsest and gnome-disks are for the same app.

The underlying formatting command is ```
sudo mkfs -t ext4 /dev/<sdxn>
```...where xn = device partition.  You can try that.  Make sure you have the correct partition before issuing the command.

---

### Post by Freeze145 on 2014-04-24
> **bab1 said:**
> Hmmm...  It turns out that palimpsest and gnome-disks are for the same app.

The underlying formatting command is ```
sudo mkfs -t ext4 /dev/<sdxn>
```...where xn = device partition.  You can try that.  Make sure you have the correct partition before issuing the command.

Sorry I haven''t replied recently (school)
When I do that it says :
/dev/sdb1 is mounted, will not make a filesystem here!

Any other ideas? 

Otherwise I'll try something else.

---

### Post by bab1 on 2014-04-24
> **Freeze145 said:**
> Sorry I haven''t replied recently (school)
When I do that it says :
/dev/sdb1 is mounted, will not make a filesystem here!

Any other ideas? 

Otherwise I'll try something else.
It means you have to unmount the filesystem that is on the USB drive.

It also means, in a practical sense you should be trying something a bit more user friendly.  I have used the Disk Manager to format a couple of USB flash drives so I know it works.  You seem to have problems using that user friendly interface.  I think you should look for an alternative to using a flash drive for your Steam needs.

---

### Post by Freeze145 on 2014-04-26
> **bab1 said:**
> It means you have to unmount the filesystem that is on the USB drive.

It also means, in a practical sense you should be trying something a bit more user friendly.  I have used the Disk Manager to format a couple of USB flash drives so I know it works.  You seem to have problems using that user friendly interface.  I think you should look for an alternative to using a flash drive for your Steam needs.

Yeah
Ubuntu on a Chromebook is definitely not without its problems. 
Thanks for all your help

---

### Post by adgsfuzwe on 2015-01-25
I'm another user with the same problem. The solution is easy: You have  to mount a partition with "exec". I didn't wanted to change my old  partitions or the fstab-file, so I created a new partition with ext4.  BTW the old partition I used for Steam games was NTFS. I use Ubuntu  14.10 64-bit and the newest Steam. After I created a partition with the  GUI of gnome-disk-utility (a really great program [http://wiki.ubuntuusers.de/Laufwerksverwaltung](http://wiki.ubuntuusers.de/Laufwerksverwaltung)),  I clicked on the partition, then on these 2 circles, then on mounting  options edit, then in the first line I switched the button to OFF. There  is a line which contains "nosuid,nodev,nofail,noauto,x-
gvfs-show", just  add ",exec" and click ok. Then use Steam.

---

