---
title: "review fstab entry"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by mike acker on 2012-10-15
ok, after some study I think i'm getting there,...

here's my proposed fstab update:

[B]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c8aaa7f1-28e7-4024-96c3-3fc4d898ad9f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=48eee500-b271-4e27-9e8b-d02e0326f8e4 none            swap    sw              0       0
#
# Proposed addition to fstab
#
/dev/sdb1 /media auto[/B]

I think i understand the device, and maybe the mount point:
it means: the content of /dev/sdb partition 1 will replace /media in my system .

should i create a new subdirectory of /media for this mount ?
do i need to add any options ?

---

### Post by drmrgd on 2012-10-15
The most glaring thing about your entry is that you don't have a legal mount point listed.  /media would be where you would want to set your mount point, but you do need to have a subdirectory in there.  So, I would recommend you change that bit to /media/NewDrive (or whatever you want to call it).  

With regard to the options, I think it all depends on what you need.  If there are other users that might need to mount it, you'd probably want to add 'users' so that they won't need admin rights.  You also might need (or want) some masks in that regard.  If you're the only one on the system, then probably just 'defaults' is enough.  

Here's probably the best fstab guide I've ever seen (even though it's really old), that I use all the time:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by NikTh on 2012-10-15
> **drmrgd said:**
> 

Here's probably the best fstab guide I've ever seen (even though it's really old), that I use all the time:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

+1 

Definitely any user who wants to learn about fstab must read this.

---

### Post by Paqman on 2012-10-15
> **mike acker said:**
> 
should i create a new subdirectory of /media for this mount ?


Yes. Open a terminal (Ctrl-T) and type:
```
sudo mkdir /media/name-of-new-directory
```
> do i need to add any options ?
The most common thing to add options for is controlling permissions on the drive. You can just use "defaults" if you don't need to bother with that.

One tip about making changes to fstab: always check that you've not broken the file after editing it. The command:
```
sudo mount -a
```
will force the system to try and mount everything in fstab, it will spit out errors if you've made any booboos. It's possible to make your system unbootable if you mess up fstab, so it always pays to check.

---

### Post by mike acker on 2012-10-15
> **drmrgd said:**
> The most glaring thing about your entry is that you don't have a legal mount point listed.  /media would be where you would want to set your mount point, but you do need to have a subdirectory in there.  So, I would recommend you change that bit to /media/NewDrive (or whatever you want to call it).  

With regard to the options, I think it all depends on what you need.  If there are other users that might need to mount it, you'd probably want to add 'users' so that they won't need admin rights.  You also might need (or want) some masks in that regard.  If you're the only one on the system, then probably just 'defaults' is enough.  

Here's probably the best fstab guide I've ever seen (even though it's really old), that I use all the time:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Thanks!!!!! this has been most helpful!!!!!
here's my Plan of Action
reading your doc:

[SIZE=1][B]Mount point.
This is where the partition is mounted or accessed within the "tree" (ie /mnt/hda1).
You can use any name you like.
In general

    /mnt Typically used for fixed hard drives HD/SCSI. If you mount your hard drive in /mnt it will NOT show in "Places" and your Desktop.
    /media Typically used for removable media (CD/DVD/USB/Zip). If you mount your hard drive in /media it WILL show in "Places" and your Desktop.[/B][/SIZE]

typically ease of access would be good so I'll plan on mounting sdb1 in /media.

thus i'll need to 
sudo mkdir /media/share1

and then change my mount command to
**/dev/sdb1 /media/share1 auto auto,user,rw 0 0**

this reference:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

is most helpful: it tells me what the option keys are and of what effect
my option string is: auto,user,rw:
[INDENT] partition to be mounted automatically at boot; users may mount the partition and have read/write access
[/INDENT]~~~~~~~~

next step: do the mount -a command test to make sure i've edited fstab properly.

I remember all too well, working with MVT, certain things you could screw up
and the system wouldn't boot.  You had to boot a backup SYSRES and go in and correct your
defugelty ....while the operation manager gave birth to kittens

with Ubuntu,-- I could just load a LIVE CD and being an Old Retired Fellow (ORF)
no one is going to care, not even Mitsi, my little toy beagle

~~~~~
way cool: the drive appears to be properly mounted.  I'll play with the share options tw.

---

### Post by bab1 on 2012-10-16
@mike acker

I would not use the /dev/<some_partition> to mount the partition.  This can change.  Follow the advice listed at the top of the fstab file (that you listed in your first post). ```
# /etc/fstab: static file system information.
#
# Use '[COLOR="Red"]**blkid**[/COLOR]' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
```

To find out what the UUID for your devices are you can do this```
sudo blkid
```

---

### Post by nothingspecial on 2012-10-16
You can make it more readable by using LABEL. You can lable your external drive with gparted then add an option in fstab like so

```
LABEL=media   /mnt/media  ext4  defaults 0    0
```

---

### Post by mike acker on 2012-10-16
> **nothingspecial said:**
> You can make it more readable by using LABEL. You can lable your external drive with gparted then add an option in fstab like so

```
LABEL=media   /mnt/media  ext4  defaults 0    0
```

thanks.

i understand the UUID stuff but unless I re-route the cables or redefine partitions I'm OK, for now anyway

the thing I'm struggling with right now is how access rights are controlled. before i updated fstab it seemed the chmod directive -- i set it to 777 -- allowed any user rw access ( it probably should have been 666 ) .

now that i have the fstab entry set access appears to be 664 -- guests getting read only access.   this is consistent with what i'd noticed earlier using the Dell box --  the "create share" panel from the file directory  offers to allow guest access, -- but fails

i had to fuss around with the security entries in samba,-- equating logons, and listing user id's in the samba access table.

maybe more experiments tw

---

### Post by bab1 on 2012-10-16
> **mike acker said:**
> thanks.

i understand the UUID stuff but unless I re-route the cables or redefine partitions I'm OK, for now anyway

Maybe, maybe not.  The udev names are assigned by order of discovery and that can change, even if you don't move cables or redefine partitions.> 

the thing I'm struggling with right now is how access rights are controlled. before i updated fstab it seemed the chmod directive -- i set it to 777 -- allowed any user rw access ( it probably should have been 666 ).
How exactly did you use chmod?  Do all users have access on the local machine?  You only need eXecute on the directories to access (traverse) that directory.  The files need to have rw only.  The default for 12.04 is 775 on directories and 664 on files.> 
now that i have the fstab entry set access appears to be 664 -- guests getting read only access.   this is consistent with what i'd noticed earlier using the Dell box --  the "create share" panel from the file directory  offers to allow guest access, -- but fails
A remote user (via Samba) is ultimately restricted by the local permissions.  Samba can be more restrictive, but it can't grant permissions that the local filesystem doesn't allow.> 

i had to fuss around with the security entries in samba,-- equating logons, and listing user id's in the samba access table.

What did you do?  What are the permissions on the entire filesystem tree that you are sharing?  How did you set up the Samba share(s)?

Please post the */etc/samba/smb.conf* file and the output of ```
net usershare list -long
```

---

### Post by mike acker on 2012-10-17
my objective is to create a Home Network Share as /dev/sdb1

access by

[LIST]
[*]logging onto the U-box, or
[*]from Home Network using a Windows or another U-box
[/LIST]
right now i have 2 u-boxes, 2 win7, an HP printer, a kindle tablet, and a couple lap tops (win7) that come over sometimes . Cisco wi-fi router WPA2-PSK


they way I've been taught: a shared resource should be "owned" by a group and users are given access by adding them to the group that owns the shared resource


i think using SAMBA for all access -- local sign on as well as wireless is probably my best bet. i may give up trying to figure out how to set up the local sign ons and start over using SAMBA.  

this would suggest mounting /dev/sdb1 on /mnt/share1 rather than at /media/share1


:confused::confused::confused::confused::confused:

---

### Post by bab1 on 2012-10-17
> **mike acker said:**
> my objective is to create a Home Network Share as /dev/sdb1

access by

[LIST]
[*]logging onto the U-box, or
[*]from Home Network using a Windows or another U-box
[/LIST]
right now i have 2 u-boxes, 2 win7, an HP printer, a kindle tablet, and a couple lap tops (win7) that come over sometimes . Cisco wi-fi router WPA2-PSK


they way I've been taught: a shared resource should be "owned" by a group and users are given access by adding them to the group that owns the shared resource


i think using SAMBA for all access -- local sign on as well as wireless is probably my best bet. i may give up trying to figure out how to set up the local sign ons and start over using SAMBA.  

this would suggest mounting /dev/sdb1 on /mnt/share1 rather than at /media/share1


:confused::confused::confused::confused::confused:

It might be helpful if you think of the Samba shares (SMB) as as resources that are accessed remotely.  That is, a user at a client host (computer) requests access to the SMB resource managed by the Samba server.  The Samba server always presents these shares in this form  ```
//COMPUTER_NAME/share_name
```  
The name /dev/sdb1 relates to the local host OS only as does /mnt/share.  In addition that we have *share browsing* (e.g. network neighborhood) that is separate but still a part of Windows style network 

This means there are three concepts to understand for basic Windows (Samba) shares.  sharing experience.  The have 3 components to the puzzle are:
[LIST=1]
[*]Mounting the Partition on the Samba Server
[*]Creating the Samba Share and Allowing Access
[*]Making Shares Available to the Local Network via Browsing
[/LIST]
Samba shares are not *""owned" by a group"*, nor are *"users are given access by adding them to the group"*.  The only group that is used in Samba is the workgroup.  This is only to associate multiple servers and their shares while browsing.  It does not restrict access at all.

The local host that serves the shares (e.g. the server) can use groups to set the underlying permissions that all users must conform to.  All Samba users must be users on the local host (i.e. Ubuntu users) to access the share or the ```
map to guest = Bad User
``` ... parameter must be in the *smb.conf* file.

As far as where you mount the partition that contains the shares on the server is totally up to you.  I have mounted these partitions in the past at these points```
/smb
/share
/data
/home/<user>/data
```...in short; the mount point of the partition has nothing to do with how the share is presented.  You can't tell by **//COMPUTER_NAME/share_name** where the mount point of the partition is.

Share browsing usually works by default as long as the name services for the LAN are working properly.  If you can't browse for shares then name services in some why will need to be configured. 

What have you done as far as setting up shares and users?  What help do you need exactly?

---

### Post by mike acker on 2012-10-18
=What help do you need exactly?

the problem I'm running into is:

If I create a file on the share using my local user log on it ends up with
owner = me
group = me
chmod = ?  

another local user will get read only access.
i think i'll start over and re-mout the /dev/sdb1 partition at /mnt/share1

and then just work with Samba.

if i remember right from my first u-box ( the old Dell ) everyone who had a u-box logon was ok but they had to get at the share via "network".  by mounting the share at /media/share1 the partition appears for everyone in "places" ( not on desk-top ) .

Perhaps if I create a user called "Share" and chown of the partition to Share I can then chmod the partition to 666 and add the local box users to the group share. this might be worth a try

the device is intended as additional storage for large volume stuff, backup, px etc. right now we are using a USB hard drive for that.  my U-box is built from an ANTEC 300 case and has -- I think 4 more empty slots for those 1TB Seagate baracuda drives and the M4A88-M board has lots of un-used SATA ports    the CISCO WiFi router combined with the ANSUS WiFi card is giving 70Mb/sec local net speed

---

### Post by bab1 on 2012-10-19
> **mike acker said:**
> =What help do you need exactly?

the problem I'm running into is:

If I create a file on the share using my local user log on it ends up with
owner = me
group = me
chmod = ?  

another local user will get read only access.
This is easily overcome.  More about this below.> 


i think i'll start over and re-mout the /dev/sdb1 partition at /mnt/share1

and then just work with Samba.

if i remember right from my first u-box ( the old Dell ) everyone who had a u-box logon was ok but they had to get at the share via "network".  by mounting the share at /media/share1 the partition appears for everyone in "places" ( not on desk-top ) .
All users who browse to the share from remote computers will find shares via "places"> 

Perhaps if I create a user called "Share" and chown of the partition to Share I can then chmod the partition to 666 and add the local box users to the group share. this might be worth a try
You don't need to do this quite like you think.  It is easier to chgrp (change the group ownership) to a common group for all users.  Ubuntu already has one for this purpose named *sambashare*.  The trick is to set the group ID (SGID) on the root directory of the share.  This forces all files and directories to inherit the group ownership.  Most folks assume that SGID is the default behavior but it is not so for Ubuntu (or any Debian based distro).> 

the device is intended as additional storage for large volume stuff, backup, px etc. right now we are using a USB hard drive for that.  my U-box is built from an ANTEC 300 case and has -- I think 4 more empty slots for those 1TB Seagate baracuda drives and the M4A88-M board has lots of un-used SATA ports    the CISCO WiFi router combined with the ANSUS WiFi card is giving 70Mb/sec local net speed

This host (ANTEC) should work fine.  For most of this we will be only working with this machine. What is the hostname of this machine?  Can you ping it by hostname from other hosts in the LAN?  Can you add your user to the ***sambashare ***group on this host?  Is there any data on the partition that you have mounted and wish to share?

---

### Post by mike acker on 2012-10-19
> **bab1 said:**
> This is easily overcome.  More about this below.All users who browse to the share from remote computers will find shares via "places"You don't need to do this quite like you think.  It is easier to chgrp (change the group ownership) to a common group for all users.  Ubuntu already has one for this purpose named *sambashare*.  The trick is to set the group ID (SGID) on the root directory of the share.  This forces all files and directories to inherit the group ownership.  Most folks assume that SGID is the default behavior but it is not so for Ubuntu (or any Debian based distro).

This host (ANTEC)
[*] should work fine.  For most of this we will be only working with this machine. What is the hostname of this machine?  Can you ping it by hostname from other hosts in the LAN?  Can you add your user to the ***sambashare ***group on this host?  Is there any data on the partition that you have mounted and wish to share?

first off, thanks so much for the time you have taken to help with this. I will check that group ownership. i think the idea here is to assign the share to samba and then control access via samba

this "works" for me: I don't mind editing the samba config files from my admin key. as long as visitors with windows type devices can get on easily we are All Good .   right now it seems to be working. 

i'll check the owner/ group owner on that share.  it's the inherrited rights that i need: what tends to happen is: if Jen and Lyn are both accessing the share Jen's files end up owned by Jen and Lyn can read but not update

in Linux -- every file, every folder -- has an owner, group owner, and permissions for the owner, group, and guest -- the entire relationship being difficult.
~~~
* just a point of interest-- the computer is built from a case (Antec) ,power supply (ANTEC) ,motherboard (ASUS) ,CPU (AMD Phenom II ) ,RAM (Kingston) ,DASD (Seagate/Baracuda) ,DVD/CD drive (Ansus) ,WiFi card (ANSUS) .  I had a lot of fun building it,-- but now I struggling learning Linux security procedures.  

* after I re-mounted the shared partition on /mnt -- it does not show up in "places" -- just as noted here earlier.  If I've added the user to sambda -- then it can be accessed via the network access option.  if i mount it under /media -- it does show up -- and is easier to get to -- but I can't control permissions

---

### Post by bab1 on 2012-10-19
> **mike acker said:**
> first off, thanks so much for the time you have taken to help with this. I will check that group ownership. i think the idea here is to assign the share to samba and then control access via samba
This is not entirely true.  Access is a combination of Samba access to the SMB resource (the share) and the file permissions of Linux. > 

this "works" for me: I don't mind editing the samba config files from my admin key. as long as visitors with windows type devices can get on easily we are All Good .   right now it seems to be working. 

i'll check the owner/ group owner on that share.  it's the inherrited rights that i need: what tends to happen is: if Jen and Lyn are both accessing the share Jen's files end up owned by Jen and Lyn can read but not update
These are permissions not really ownership in any other way.  If the user is part of a group that has read write and execute permissions then that user has all the permissions to the file.  The owner (creator) has no more or less than that.  Inheritance of permissions are not been set with the usual 777 or 775 or 664 or any other 3 bit combination.> 

in Linux -- every file, every folder -- has an owner, group owner, and permissions for the owner, group, and guest -- the entire relationship being difficult.

It's all rather simple once you know what to do.> 
~~~
* just a point of interest-- the computer is built from a case (Antec) ,power supply (ANTEC) ,motherboard (ASUS) ,CPU (AMD Phenom II ) ,RAM (Kingston) ,DASD (Seagate/Baracuda) ,DVD/CD drive (Ansus) ,WiFi card (ANSUS) .  I had a lot of fun building it,-- but now I struggling learning Linux security procedures. 
It's not really obvious, but as I said it's simple once you see how it's done.>  

* after I re-mounted the shared partition on /mnt -- it does not show up in "places" -- just as noted here earlier. 

 If I've added the user to sambda -- then it can be accessed via the network access option.  if i mount it under /media -- it does show up -- and is easier to get to -- but I can't control permissions
This is because the share has a defined path to the data (/media/<somedir>).  When you move the mount point without re-defining the path to the share Samba cant display it properly.

When do you want to start reconfiguring this?  I will explain as we go along. I think the experience will be more helpful than just me answering your questions.  If you look back at the last few posts you will notice I have asked for data so we could begin to configure your system.  Post that data.  I don't see how we can progress unless we start with that.

---

### Post by mike acker on 2012-10-19
> **bab1 said:**
> When do you want to start reconfiguring this?  I will explain as we go along. I think the experience will be more helpful than just me answering your questions. 

agreed!!

the 2d disk drive is installed as /dev/sdb
the one partition it has is /dev/sdb1 ACKER4V2
(Vol.2 4th machine )

the partition has one share, which is intended to be the pubic transfer area for the home net:

A4SHARE1 :
#
# added 2012-10-15 to FSTAB :
#
/dev/sdb1 /mnt/share1 auto auto,user,rw 0 0


here is LL output:

[B]bill@acker4:~$ cd /mnt
bill@acker4:/mnt$ ll
total 12
drwxr-xr-x  3 root      root       4096 Oct 18 09:51 ./
drwxr-xr-x 24 root      root       4096 Oct 15 12:28 ../
drwxrwxrwx  5 ackerwaa sambashare 4096 Oct 15 12:41 share1/
bill@acker4:/mnt$ cd share1
bill@acker4:/mnt/share1$ ll
total 32
drwxrwxrwx  5 ackerwaa sambashare  4096 Oct 15 12:41 ./
drwxr-xr-x  3 root      root        4096 Oct 18 09:51 ../
drwxrwxrwx  5 ackerwaa ackerwaa   4096 Oct 19 10:20 A4SHARE1/
drwxrwxrwx 21 ackerwaa ackerwaa   4096 Oct 15 12:50 ackerwaa/
drwx------  2 root      root       16384 Oct 13 16:07 lost+found/
bill@acker4:/mnt/share1$ cd A4SHARE1
bill@acker4:/mnt/share1/A4SHARE1$ ll
total 20
drwxrwxrwx 5 ackerwaa ackerwaa  4096 Oct 19 10:20 ./
drwxrwxrwx 5 ackerwaa sambashare 4096 Oct 15 12:41 ../
drwxr-xr-x 4 bill      bill       4096 Oct 19 10:26 music/
drwxr-xr-x 3 bill      bill       4096 Oct 18 11:44 px/
drwxrwxrwx 2 ackerwaa ackerwaa  4096 Oct 19 10:55 test/
bill@acker4:/mnt/share1/A4SHARE1$ 
[/B]
( "Mike" is just my screen name ) .

"ackerwaa" is the admin account; "bill" is an ordinary user

this machine is for learning at this time so we can do anything to it no harm done

---

### Post by bab1 on 2012-10-20
> **mike acker said:**
> agreed!!

The 2d disk drive is installed as /dev/sdb
the one partition it has is /dev/sdb1 acker4v2
(vol.2 4th machine )

the partition has one share, which is intended to be the pubic transfer area for the home net:

A4share1 :
#
# added 2012-10-15 to fstab :
#
/dev/sdb1 /mnt/share1 auto auto,user,rw 0 0

...and the partition formated with ext4?  What does **[COLOR="Red"]acker4v2 [/COLOR]** stand for? 

In the future please format the text using ```
 [/code ] blocks for clarity.  You can just click on the **#** tag on the right side of the formatting icons to create the blocks.  Then the output will look like this

[code]

bill@acker4:/mnt$ ll
total 12
drwxr-xr-x  3 root      root       4096 oct 18 09:51 ./
drwxr-xr-x 24 root      root       4096 oct 15 12:28 ../
drwxrwxrwx  5 ackerwaa sambashare 4096 oct 15 12:41 share1/
```> 

"ackerwaa" is the admin account; "bill" is an ordinary user

I see you have chown'd the directory *share1* to ackerwaa:sambashare.  Have you added these two users to the sambashare group yet?


When you share the *share1 *directory you have shared the whole partition.  If you want to have separate shares in the future (such as share2 or share3) you will not be able to keep them separate.  I always create a directory at the root of the partition (i/e samba or some such) and create sub-directories for the shares.  Just something to think about.

At the end of this *_section_* of the project you should have users that are part of the group sambashare and a directory that is available to share.  If you are happy with  sharing */mnt/share1* and you have added the users to the group sambashare then we are ready for the next step.  Are we there yet?  Post the output of this command```
getent group|grep sambashare
```

---

### Post by mike acker on 2012-10-20
q1: what does acker4v2 stand for?
a1: that is the name that i assigned as the disk volume label using disk utility -- right after i installed the 2d hard drive

q2: what is the result of getent group|grep sambashare?
a2:
```

ackerwaa@acker4:~$ getent group|grep sambashare
sambashare:x:124:ackerwaa
ackerwaa@acker4:~$ 

```( I had used the "create share" option on the file-folder tool to "create a share".  I think that tool changed the group ownership of the folder "share1"

I did use chmod to alter the permissions on share1 to rwxrwxrwx because when i told Samba to allows guests it provided only read access. :-(
~~~
I had hoped to make share1 available to anyone and then to control access by user using Samba.  I used these changes for that

```
sudo smbpassword -a <Bill>
```to add Bill to Samba
and then

```
sudo gedit /etc/samba/smbusers

Bill = "Bill"
```

so that my Windows Logon can assume the same rights that my Ubuntu logon has

this is all very confusing because Samba and Linux seem to conflict.

it was very helpful in knowing that the group ownership rights of the
root folder will be inherited by all of the sub-folders and files
stored -- by any user -- in that root area.
~~~~
i had to install some samba tools too,--
```
sudo apt-get install samba smbfs
```

---

### Post by nothingspecial on 2012-10-20
Removed solved since this thread is ongoing.

---

### Post by bab1 on 2012-10-20
> **mike acker said:**
> 
what is the result of getent group|grep sambashare?
```

ackerwaa@acker4:~$ getent group|grep sambashare
sambashare:x:124:ackerwaa
ackerwaa@acker4:~$

```
You need to add all users that are going to access the directory tree *share1* to the _sambashare_ group.  In your case it means adding the user *bill *to that group.  If the *user bill* is not a member of that group it will not have full access to the date in the share.  Remember, the host OS sets the basic authorization for these files.  **Add all users of the share to the user group *sambashare***> 

( I had used the "create share" option on the file-folder tool to "create a share".  I think that tool changed the group ownership of the folder "share1"
Are you saying that you did not specifically add any user to the *sambashare *group?> 

I did use chmod to alter the permissions on share1 to rwxrwxrwx because when i told Samba to allows guests it provided only read access. :-(
This is not the way to achieve you goal.  It is a security risk and not needed.  Since you are using this host as a test bed you shuld learn the proper way of doing things.> 
~~~
I had hoped to make share1 available to anyone and then to control access by user using Samba.
There are subtleties to this notion.  Can you explain your thought a little more so I can advise,  > 

I used these changes for that

```
sudo smbpassword -a <Bill>
```to add Bill to Samba
and then

```
sudo gedit /etc/samba/smbusers

Bill = "Bill"
```

so that my Windows Logon can assume the same rights that my Ubuntu logon has
Windows hosts pass the login ID to Samba and it is compared with the smbpasswd database.  You don't need to edit the smbusers file if the logins are the same.> 
this is all very confusing because Samba and Linux seem to conflict.
Samba and Linux do not conflict at all.  The basic SMB/CIFS protocol is extremely complex and non-intuitive.  It would be helpful for you to not over think the process.  Just ask questions AFTER we do things. > 
it was very helpful in knowing that the group ownership rights of the
root folder will be inherited by all of the sub-folders and files
stored -- by [COLOR="Red"]any user[/COLOR] -- in that root area.
This should be: [COLOR="Red"]any user[/COLOR]* that is a member of the sambashare group*.  To add users to the sambashare group you can use this incantation ```
usermod -a -G [COLOR="Blue"]groupname[/COLOR] [COLOR="Red"]username[/COLOR]
```

To add the user bill to the sambashare group use this```
usermod -a -G sambashare bill
```

See if you were successful.  Post the output again of this```
getent group|grep sambashare
```

---

### Post by mike acker on 2012-10-28
:)thanks for all the help. I havn't given up on this; I've been busy putting the new machine in service to replace my Win7 box

I've got some issues to resolve related to AppArmor and then I can get back to this.

---

