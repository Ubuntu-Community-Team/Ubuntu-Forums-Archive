---
title: "Why? drive locations of sd[bcde]1 change after reboot?"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by agentofcode on 2013-04-14
I have a RAID5 set up with my OS on sda1 and the RAID made up of sd[bcde]1. I created labels with the sd*1  along with the drive serial # to affix them to the drives for quick reference while working in the case. I double checked my work prior to affixing them. Then when I powered the server back on I realized that the drive locations changed.

**sda1** is now assigned to a drive that is in the RAID
**sdb1** now contains the OS
**sdc1**, **sdd1 **and** sde1** are still in the RAID but doesn't match the serial numbers I put on my labels

**What is the deal with the drive locations changing?**

---

### Post by redmk2 on 2013-04-14
> **cbfannin said:**
> I have a RAID5 set up with my OS on sda1 and the RAID made up of sd[bcde]1. I created labels with the sd*1  along with the drive serial # to affix them to the drives for quick reference while working in the case. I double checked my work prior to affixing them. Then when I powered the server back on I realized that the drive locations changed.

**sda1** is now assigned to a drive that is in the RAID
**sdb1** now contains the OS
**sdc1**, **sdd1 **and** sde1** are still in the RAID but doesn't match the serial numbers I put on my labels

**What is the deal with the drive locations changing?**

The ***device name*** (/dev/sd*) is enumerated at boot time by the O/S.  This can change as you have seen.  These should only refer to the device, not the partition you will be mounting via the fstab file.  I believe that the RAID array uses it's own methods of assembling the array (e.g with superblocks)  

Since the fstab should not use the device names to mount partitions, it is advised that you use UUID's in the fstab file.  This will provide the consistency you are expecting.  Post the output of ```
cat /etc/fstab
```

Also post the output of ```
sudo blkid -c /dev/null -o list
```

---

### Post by agentofcode on 2013-04-15
Thanks for the response! Here is the requested output[B].

sudo cat /etc/fstab[/B] Results
> 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=20d379b8-c134-4bd6-ba56-92146c6bef4b /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/md0 during installation
#UUID=cc88869d-9bc0-4689-88ff-d88c8b5a57c6 /home           ext4    relatime        0       2
# swap was on /dev/sda5 during installation
#UUID=8e88359b-73e5-48e3-a504-1aea6f4312bf none            swap    sw              0       0
/dev/md0        /storage        ext4    defaults        0       0

**sudo blkid -c /dev/null -o list** Results
> 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              20d379b8-c134-4bd6-ba56-92146c6bef4b
/dev/sda5  swap             (not mounted)  8e88359b-73e5-48e3-a504-1aea6f4312bf
/dev/sdb1  linux_raid_member Animus:0 (in use) fe7a9d30-dab8-e9f3-0d9d-4d865cbd1531
/dev/sdc1  linux_raid_member Animus:0 (in use) fe7a9d30-dab8-e9f3-0d9d-4d865cbd1531
/dev/sdd1  linux_raid_member Animus:0 (in use) fe7a9d30-dab8-e9f3-0d9d-4d865cbd1531
/dev/sde1  linux_raid_member Animus:0 (in use) fe7a9d30-dab8-e9f3-0d9d-4d865cbd1531
/dev/md0   ext4             /storage       31115950-ca7a-4ef8-994f-5dc3d67a84a4


---

### Post by redmk2 on 2013-04-15
Hmmmm,  It looks pretty good right now.  Post the output of these 2 commands and then I will comment on what you have.

```
df -h
```

and 

```
mount
```

---

### Post by agentofcode on 2013-04-15
**df -h** Results
> Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        52G  3.0G   47G   7% /
udev            1.7G  4.0K  1.7G   1% /dev
tmpfs           690M  964K  689M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.7G  4.0K  1.7G   1% /run/shm
/dev/md0        5.5T  1.2T  4.3T  21% /storage

**mount **Results
> /dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/md0 on /storage type ext4 (rw)


---

### Post by redmk2 on 2013-04-16
The results don't show what you stated in your first post.

But the fstab isn't exactly correct.  looking at the fstab...```
# /etc/fstab: static file system information.
#
[B][COLOR="#FF0000"]# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).[/COLOR][/B]
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
[COLOR="#008000"]UUID=20d379b8-c134-4bd6-ba56-92146c6bef4b[/COLOR] / ext4 relatime,errors=remount-ro 0 1
# /home was on /dev/md0 during installation
#UUID=cc88869d-9bc0-4689-88ff-d88c8b5a57c6 /home ext4 relatime 0 2
# swap was on /dev/sda5 during installation
#UUID=8e88359b-73e5-48e3-a504-1aea6f4312bf none swap sw 0 0
[COLOR="#0000FF"]/dev/md0 /storage ext4 defaults 0 0 [/COLOR]
```

The point highlighted in red above is important in some cases.  You may have had a USB storage device inserted when you observed the device names changing.

The last line in this file (highlighted in blue) is a problem.  But we can cure that with the info you provided.

We can see that all is mounted correctly right now by the following blkid listing```

device     fs_type label mount point       UUID
-------------------------------------------------------------------------------
[B][COLOR="#008000"]/dev/sda1 ext4              /                    20d379b8-c134-4bd6-ba56-92146c6bef4b
[/COLOR][/B]
[B][COLOR="#0080ee"]]/dev/sdb1 linux_raid_member Animus:0 (in use) fe7a9d30-dab8-e9f3-0d9d-4d865cbd1531
/dev/sdc1 linux_raid_member Animus:0 (in use) fe7a9d30-dab8-e9f3-0d9d-4d865cbd1531
/dev/sdd1 linux_raid_member Animus:0 (in use) fe7a9d30-dab8-e9f3-0d9d-4d865cbd1531
/dev/sde1 linux_raid_member Animus:0 (in use) fe7a9d30-dab8-e9f3-0d9d-4d865cbd1531[/COLOR][/B]

**[COLOR="#800080"]/dev/md0    ext4         /storage                 31115950-ca7a-4ef8-994f-5dc3d67a84a4[/COLOR]** 
```

The green shows the device sda1 mounted to /  (Note the UUID in the fstab is the same as what we see here)

The RAID members are not mounted (as it should be) and are shown in light blue.

The device md0 is mounted at /storage.  Note the UUID here, it should be used in the fstab instead of md0.  The use of the UUID is more a definitive label of the partition you wish to mount, rather than the device, which may or may not be the same at each boot.

If you look at ***mount*** you can see the current device to mount points.  All looks good right now.  The same is true of ***df -h***.

My advice is to edit the fstab and replace this```
[COLOR="#0000FF"]/dev/md0 /storage ext4 defaults 0 0 [/COLOR]
```...with this```

**[COLOR="#5500FF"]UUID=31115950-ca7a-4ef8-994f-5dc3d67a84a4  /storage ext4 defaults 0 0[/COLOR]** 
```

It won't change anything from the way it is running right now.  You only have / and /storage and are currently showing only 2 real devices (sda1 and md0).  but in the future if you use a usb flash drive, usb hard drive or add a new eSATA drive they will be enumerated first and things will change.

Remember that the physical hard drive and the device name do not have to match.  The partition UUID must always match and be mounted to the same place.  The physical  drives making up the RAID array are ID'd internally by the RAID software (via super blocks) the partition on the md0 device has the unique ID (UUID) only.

---

### Post by agentofcode on 2013-04-16
I made the changes. Thanks!

**A couple more things.**

Is  it safe to say I can delete the two commented lines from fstab  referring to /home? This is where my RAID5 was set up initially until it  crashed. When I set it up the second time I set it up on the new  directory of /storage.

Also what is the deal with that swap sda5? I'm assuming that is on my OS drive but its commented out, do I need that? For that matter, do I need any of it aside from the RAID?

---

### Post by redmk2 on 2013-04-16
> **cbfannin said:**
> I made the changes. Thanks!

**A couple more things.**

Is  it safe to say I can delete the two commented lines from fstab  referring to /home? This is where my RAID5 was set up initially until it  crashed. When I set it up the second time I set it up on the new  directory of /storage.

Also what is the deal with that swap sda5? I'm assuming that is on my OS drive but its commented out, do I need that? For that matter, do I need any of it aside from the RAID?
You need at least **[SIZE=2]/ [/SIZE]**([COLOR="#008000"]UUID=20d379b8-c134-4bd6-ba56-92146c6bef4b[/COLOR] / ext4 relatime,errors=remount-ro 0 1).   This is where the OS resides.  I assumed that you also had /home on this partition.  If not then the system should not boot.  Do you have an /home directory on this partition?

You need /storage.  I assume this is where the data is stored.

I appears as if you are not using any swap right now.  I have always configured a swap space on the hard drive.  It is not mounted anywhere, but it is used.  I would uncomment this line (#[COLOR="#800080"]**UUID=8e88359b-73e5-48e3-a504-1aea6f4312bf none swap sw 0 0**[/COLOR]).

In the end you should have at minimum / and swap and /storage.  You should have a /home directory in use.  It can be on its own partition or on /. 

Look at the users file (/etc/passwd) to see where you have the home directories.  You can see a typical account with this command```
getent passwd|grep 1000
```...mine looks like this```
bab:x:1000:1000:Administrator,,,:**[COLOR="#ff8000"]/home/bab[/COLOR]**:/bin/bash
```

Post the output back here.

---

### Post by agentofcode on 2013-04-16
Hmmm...What had happened was...

Since I rebuilt the RAID on /storage I figured I no longer need /home. I do remember deleting my account in webmin and then needing to recreate it. Was experimenting with permissions and obviously screwed something up.

**getent passwd|grep 1000** Results
```
cbfannin:x:1000:27::/storage:/bin/sh

```

---

### Post by bab1 on 2013-04-16
msispost

---

### Post by redmk2 on 2013-04-16
> **cbfannin said:**
> Hmmm...What had happened was...

Since I rebuilt the RAID on /storage I figured I no longer need /home. I do remember deleting my account in webmin and then needing to recreate it. Was experimenting with permissions and obviously screwed something up.

**getent passwd|grep 1000** Results
```
cbfannin:x:1000:27::/storage:/bin/sh

```
Ah ha! I understand what happened,

As it stands right now the system will work because you have declared your home directory to be /storage. This will cause problems down the road if you try and add new users. It would have been better to have either selected your home directory to be /storage/cbfannin or to have created a /home/cbfannin for a home directory.

So what to do? How much data to you have at /storage. Is it all your home directory data? If so, I would recreate the /home/cfbannin directory, copy the data there and configure that as your home directory again. Then the RAID array is strictly for storage for all users. As this would make the /home on the same partition as the OS (i.e /). This means the fstab file would not need to be altered at this time.

Of course the best thing would be to back up the data to a safe place and reinstall the O/S while creating a separate partition for home. You could then reconstitute the RAID array and the /storage mount point.

Thoughts or questions...

---

### Post by agentofcode on 2013-04-18
I have roughly 2tb of data on /storage w/ nowhere to back it up to since it is my storage and backup. To make sure I understand clearly by recreating the /home/cbfannin directory this is only for user information, correct? I can and should leave /storage for storage only and /home/cbfannin for user data? With that said, all I should need to do is move my user files over to /home/cbfannin and be all set?

I suppose it would be very helpful to request step-by-step of how I should go about accomplishing this, Thanks!

---

### Post by redmk2 on 2013-04-18
> **cbfannin said:**
> I have roughly 2tb of data on /storage w/ nowhere to back it up to since it is my storage and backup. To make sure I understand clearly by recreating the /home/cbfannin directory this is only for user information, correct? I can and should leave /storage for storage only and /home/cbfannin for user data? With that said, all I should need to do is move my user files over to /home/cbfannin and be all set?
You need to have a backup copy of all of your data on a separate removable device.  This can be a s simple as a USB hard drive.  If the 2 RAID array fails, you run the risk of loosing ALL of your data.  RAID was not designed to provide protection against loss of data.  It's primarily for high availability of data.  At work we run RAID and backup the data daily.  At home I don't run RAID, but I do backup my data every night.  I have no high availability requirements at home.  If the drive fails I install another one and restore the data.  At work we can't just shut down the system.  RAID provides us the ability to *plan the downtime* when we observe a disk failure.

The /home can be on the same partition as /.  The only reason to move /home to a separate partition is for ease of re-installation of  the O/S.  There are lot's of variations to this (separate hard drives (spindles) vs separate partitions on the same spindle)

The main things is think about is data safety, how to allow some scalability (adding users), and consistency with Linux standard practices (home directory location)> 

I suppose it would be very helpful to request step-by-step of how I should go about accomplishing this, Thanks!

I will post some instructions for this later today.  Think long and hard about getting a backup device (HDD or SDD or tape drive, etc.).

Ask questions if you don't completely understand.  :-)

[COLOR="#0000FF"]Edit: Some thoughts about how to correct your file system.  Below is the listing of what you have now[/COLOR]```
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 52G 3.0G 47G 7% /
...
/dev/md0 5.5T 1.2T 4.3T 21% /storage 
```

You have more than enough room on the / partition (sda1) for a /home/ <user> directory We can worry about the swap drive later.  For now I suggest we first create a new home directory at its proper position on the / partition.  Let's see what is there now.  What is the output of ```
ls -l /home

ls -ld /home
```

I'm curious how much data at: /storage is really your home directory and how much is general data.  How do you keep it separated.  What is the output of ```
ls -l /storage
```

After we create the now /home/cbfannin directory we can edit the /etc/passwd file using usermod or directly.  I edit the /et/passwd file directly myself.  We can then reboot to see of that works...or if we can separate your home directory we can use the tool ***usermod***  to move the contents of your home directory and reassign $HOME to /home/cbfannin.

Note:  I'm being vague on purpose.  I want to see what you have *before* we start altering the file systems.

---

### Post by agentofcode on 2013-04-22
**ls -l /home** Returns
>  total 0
**ls -ld /home** Returns
> drwxr-xr-x 2 root root 4096 Mar 17 17:40 /home
**ls -l /storage** Returns
>  total 28
drwxr-xr-x  20 cbfannin sudo 4096 Apr 14 16:31 Charles
drwxr-xr-x   5 cbfannin sudo 4096 Apr 14 16:31 Heather
drwxr-xr-x  10 cbfannin sudo 4096 Apr 14 16:44 Home Videos
drwxr-xr-x 164 cbfannin sudo 4096 Apr 17 16:57 Movies
drwxr-xr-x   4 cbfannin sudo 4096 Apr 14 19:15 Music
drwxr-xr-x   4 cbfannin sudo 4096 Apr 14 16:08 OS Image BUs
drwxr-xr-x  18 cbfannin sudo 4096 Apr 14 16:11 Photos

---

### Post by capscrew on 2013-04-22
miss post

---

### Post by redmk2 on 2013-04-22
It appears the /home directory exists on the / partition (sda1).   This is good.  This means we can create the /home/**cbfannin** directory there.

I notice that the /storage directory has some irregularities.  Specifically; the user group is *sudo*.  Why did you use the group [I]sudo[/I?] This is not the default and probably should not be used in this way.  Did you do this on purpose?  Also some of the default directories are missing (not including the hidden files).   Is this a Desktop or Server edition of Ubuntu?  Did you remove the following directories?```


Desktop
Documents
Downloads
PDF

```

To get a better view we should have looked at the hidden files too.  We can do that by you posting the output of this```
ls -al /storage
``` 

If this is a CLI only host (no X-server) then life is a little easier.  But we will still have to manually move selected files to your /home/cbfannin directory.  There is a tool for automating moving home directories but you have a large amount of  data that shouldn't be in your home directory because we won't have the space there.

Slowly we are getting there.  Have patience.

---

### Post by agentofcode on 2013-04-22
Sudo was not on purpose, not sure how/why its like that. This is a server edition of Ubuntu and I've never noticed any default directories in /storage.

**$ ls -al /storage** Returns
> total 52
drwxr-xr-x  10 cbfannin sudo 4096 Apr 14 19:12 .
drwxr-xr-x  24 root     root 4096 Apr 15 20:47 ..
-rw-r--r--   1 cbfannin sudo  220 Apr 14 16:05 .bash_logout
-rw-r--r--   1 cbfannin sudo 3486 Apr 14 16:05 .bashrc
drwx------   2 cbfannin sudo 4096 Apr 14 16:06 .cache
drwxr-xr-x  20 cbfannin sudo 4096 Apr 14 16:31 Charles
drwxr-xr-x   5 cbfannin sudo 4096 Apr 14 16:31 Heather
drwxr-xr-x  10 cbfannin sudo 4096 Apr 14 16:44 Home Videos
drwxr-xr-x 164 cbfannin sudo 4096 Apr 17 16:57 Movies
drwxr-xr-x   4 cbfannin sudo 4096 Apr 14 19:15 Music
drwxr-xr-x   4 cbfannin sudo 4096 Apr 14 16:08 OS Image BUs
drwxr-xr-x  18 cbfannin sudo 4096 Apr 14 16:11 Photos
-rw-r--r--   1 cbfannin sudo  675 Apr 14 16:05 .profile

P.S. I'm patient, I appreciate you being patient with my wicked awesome methods of setting this up :)

---

### Post by redmk2 on 2013-04-22
I need to know the version of Ubuntu you are using.  We can see that with this command```
lsb_release -a
```

Lets see who is in the following 3 groups```
getent group sudo

getent group users

getent group adm
```

We will need to make your new home directory.  Using this info```
cbfannin:x:1000:27::/storage:/bin/sh
```
...we create the directory like this```
sudo mkdir /home/cbfannin
```

What is the output of this now ```
ls -l /home
```

---

### Post by agentofcode on 2013-04-23
**lsb_release -a** Results
> No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:        12.04
Codename:       precise

**getent group sudo** Results
> sudo: x:27:
**getent group users** Results
> users: x:100:
**getent group adm** Results
> adm: x:4:
**ls -l /home** Results
> total 4
drwxr-xr-x 2 root root 4096 Apr 23 06:46 cbfannin


---

### Post by redmk2 on 2013-04-23
It's troubling to see **no users** in the 3 groups you listed.  For instance the group **sudo** should have at least your user login included.  This allows you to use the tool sudo.  My sudo group has 2 users and looks like this```

getent group sudo
sudo:x:27:**[COLOR="#FF0000"]bab[/COLOR]**,bill
```


Do you use **su ** to assume root powers?  I noticed that you made the /home/cbfannin directory correctly.

What is the output from this```
groups cbfannin
```  

Here is what I get```
groups bab
bab : bab adm cdrom sudo dip plugdev users sambashare lpadmin smbusers www-content
``` 

Some of these groups I created for my use, but the majority you should have by default.

---

### Post by agentofcode on 2013-04-23
**groups cbfannin** Results
> cbfannin : sudo

Like I mentioned before, this is all a result of me messing with permissions through webmin and ending up deleting my originally created account and then recreating it. So anything you see was not intentional and why I am trying to fix it.

---

