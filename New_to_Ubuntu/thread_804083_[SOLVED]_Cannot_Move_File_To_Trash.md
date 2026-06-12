---
title: "[SOLVED] Cannot Move File To Trash"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by thornate on 2008-05-22
Since upgrading to Hardy, whenever I try to delete a file from my second hard drive I get the message "Cannot move file to trash, do you want to delete it immediately". I imagine this is a mounting problem but I can't work out what to put in fstab to fix it.

The line in fstab currently is:
```
UUID=4712-AB28	/media/OS-SHARED	vfat	iocharset=utf8,umask=000	0	0
```

---

### Post by drs305 on 2008-05-22
You are asked if you want to permanently delete it because vfat doesn't support ubuntu's trash system. Once it's gone, you won't be able to find it in a linux trash can.

---

### Post by PPAAUULL on 2008-05-22
You may not be able to find it in the linux trash but if I seem to recall correctly it will place it in a trash folder on that harddrive.

---

### Post by noynac on 2008-05-22
I had the same problem and enabled the trash function for ntfs and vfat partitions that are mounted by fstab as follows:

1) Backup fstab.

2) Add uid=1000,gid=1000 as options to the partition's fstab entry (see example below). 

3) Create a directory named .Trash-1000 in the partition's root.

4) Restart the computer.

Upon completion of the above, deleted files will be placed in a directory named files within the .Trash-1000 directory, and your Ubuntu desktop trash icon will show the deleted files.

~~~

Example fstab entry
UUID=44B5-9621 /media/store vfat defaults,utf8,umask=007,uid=1000,gid=1000 0 1

---

### Post by PPAAUULL on 2008-05-22
Ok but when you have those files there I don't think you can actually "Delete" delete them if you know what I mean. They will just get moved to that directory then you have to go on the directory in the windows or whatever and delete them there or the folder its self.

---

### Post by noynac on 2008-05-22
> **PPAAUULL said:**
> Ok but when you have those files there I don't think you can actually "Delete" delete them if you know what I mean. They will just get moved to that directory then you have to go on the directory in the windows or whatever and delete them there or the folder its self.

I have a fat32 partition on my internal hard drive; it mounts as /media/store. When I delete a file on that partition, it is moved to

/media/store/.trash-1000/files

and the trash icon on my Hardy desktop shows that items are in the trash. If I click on the trash icon, I see the files that were deleted on the fat32 partition. If I empty the trash, the files in the above trash directory are emptied.

---

### Post by thornate on 2008-05-22
Yes, that is what happened under Gutsy and Edgy. 

Thanks for the help noynac, I'll try that.

EDIT: Yup, it worked. You know, the one thing I will never understand is all the mount options and what each of them do.

---

### Post by victor.zamanian on 2008-05-26
I solved the problem by adding the option "user" to my mount options. I don't know about what drs305 said, since it's working for me.

Edit: "user" enables regular users to mount the volume, not just the super user.

---

### Post by drs305 on 2008-05-26
When you mount the partition with 'user', I believe what you are doing is similar to what noynac recommended, in that if you are the user with the uid of 1000 you are doing the same thing with that command.

It appears that in hardy at least we now have a way of viewing the trash and even integrating it with nautilus. That's a good thing.  :D

---

### Post by victor.zamanian on 2008-05-27
> **drs305 said:**
> When you mount the partition with 'user', I believe what you are doing is similar to what noynac recommended, in that if you are the user with the uid of 1000 you are doing the same thing with that command.

That is true, and I am indeed the user with UID=1000, however my group is not 1000, and I want any user to be able to mount the drive. For that purpose, I propose the options "user", "noauto", "gid=plugdev" (most users are a part of the plugdev group, I believe) and "umask=00X" where X is... an arbitrary no. 1..7, depending on your preferences.

This is in any case how my setup is... set up. :o)

---

### Post by all2ez on 2008-08-20
> **noynac said:**
> 
1) Backup fstab.

2) Add uid=1000,gid=1000 as options to the partition's fstab entry (see example below). 

3) Create a directory named .Trash-1000 in the partition's root.

4) Restart the computer.


Thanks, this basically worked for me.  But I already had gid=username so I tried adding uid=username and that worked just as well.

---

### Post by yct on 2008-09-05
I did not have to edit my fstab, all I did to fix this was create the .Trash-1000 on the root dir of the drive, and chown -R it to myself.

---

### Post by seul on 2008-09-09
> **noynac said:**
> 
2) Add uid=1000,gid=1000 as options to the partition's fstab entry (see example below).

3) Create a directory named .Trash-1000 in the partition's root.

4) Restart the computer.
Worked for me. I don't see a »thank you«-button next to your post, so this'll have to do: Thanks a lot, noyanc.

> **yct said:**
> I did not have to edit my fstab, all I did to fix this was create the .Trash-1000 on the root dir of the drive, and chown -R it to myself.
Somewhere I read vfat wasn't chownable?

---

### Post by drs305 on 2008-09-09
> **seul said:**
> Somewhere I read vfat wasn't chownable?
This is true. vfat partitions do not support normal linux permissions and ownership. The permissions are set at the time of mounting and once set the mountpoint ownership cannot be changed. 

If you try to run a "sudo chown" command on a fat32 partition once it is mounted you will get an 'operation not permitted' message. You can set ownership in a mount command, but once set it will remain owned by that uid/gid until unmounted.

---

### Post by Saibot Sivad on 2009-02-14
This worked for me, thanks a lot!

I will add: I am using "psydm", which is "System > Administration > Storage Device Manager" once installed. This is basically a graphical front-end to editing the fstab.

I am using an NTFS drive, and the options in psydm to set up are as follows:
1) Check the following boxes on the "Mounting" tab:
  Owner user of the filesystem uid= (put in: 1000)
  umask for file permissions in octal   umask= (put in: 000)
  Owner group of the filesystem  gid= (put in: 1000)

psydm has one annoying "bug": Whenever you open the "Assistant" it always resets the "Mount file system in read-only mode" to true. I unchecked it, but the next time I edit it, it reverts to checked. If this is something that matters to you (it does), then be sure to double check it.

Note also that psydm enables a default which I prefer to change: When you double-click a document in Nautilus (probably others as well) a pop-up asks you if you want to run the file or open it. This is annoying to me when I am trying to open .rtf and .doc files. To make files automatically open, do this: In psydm, under the "Special Files" tab, uncheck the "Permit execution of binaries" button.

---

### Post by drs305 on 2009-02-15
Saibot,

I wrote a tutorial a while back on pysdm. The app is a bit dated but still can be useful. I will incorporate your observations/recommendations into the tutorial.

Thanks for the input and welcome to the ubuntu forums.

---

### Post by vroegahh on 2009-06-23
Hi,

I've been trying and searching to solve this problem for about an hour now.. Didn't work on other pages...

Can somebody help me out with the commands I have to execute? I'm very new in Ubuntu.

I can't find the turorial as well.. :(

Thanks :P

---

### Post by drs305 on 2009-06-23
vroegahh, welcome to the Ubuntu forums!

You may need to restate exactly what problem you are having. Then we can provide help.

If the tutorial link you can't find is the one to pysdm, here it is if you want to take a look. Although I wrote the guide, pysdm has it's limitations. You might look at one of the last posts in the thread where a user gives a simple command line set of instructions that essentially do the same thing as pysdm:

[http://ubuntuforums.org/showthread.php?t=872197]("http://ubuntuforums.org/showthread.php?t=872197")

---

### Post by vroegahh on 2009-06-23
Thank you.


I've been playing around with it. After I did some wrong settings in the tutorial i messed up really good. I'm glad that i backed it up. Then I applied this website's codes:

[http://salonen.wordpress.com/2009/06/14/ubuntu-trash-can-support-on-ntfs-volumes/#comment-13](http://salonen.wordpress.com/2009/06/14/ubuntu-trash-can-support-on-ntfs-volumes/#comment-13)

Now it works. 

Perhaps also useful for other beginning users.


Thanks a lot :P

---

### Post by hunterm4573r on 2010-01-06
I had the same problem and could not delete files into Trash; but, actually all I did to solve it was open a small security wormhole in time.  

```
stav@reaper:/$ df ~ /var/www/
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda9             16840248  10523336   5461456  66% /home
/dev/sda8              9614116   5816160   3309584  64% /

``````
stav@reaper:/$ ll -d /
drwxr-xr-x 24 root root 4096 2010-01-06 13:27 /

```I edited / with write permissions for my user:

```
stav@reaper:/$ sudo chmod 775 /; sudo chgrp stav /; ll -d /
[sudo] password for stav: 
drwxrwxr-x 24 root stav 4096 2010-01-06 13:27 /

```Then I deleted a file on the root partition with Nautilus which created the proper directory tree:

```
stav@reaper:/$ ll -d /.Trash-1000/; tree /.Trash-1000/
drwx------ 4 stav stav 4096 2010-01-06 13:25 /.Trash-1000/
/.Trash-1000/
|-- files
`-- info

```Then I changed permissions back to root and was able to delete files into the Wastebasket just fine.

---

### Post by calbaker on 2010-11-10
> **noynac said:**
> I had the same problem and enabled the trash function for ntfs and vfat partitions that are mounted by fstab as follows:

1) Backup fstab.

2) Add uid=1000,gid=1000 as options to the partition's fstab entry (see example below). 

3) Create a directory named .Trash-1000 in the partition's root.

4) Restart the computer.

Upon completion of the above, deleted files will be placed in a directory named files within the .Trash-1000 directory, and your Ubuntu desktop trash icon will show the deleted files.

~~~

Example fstab entry
UUID=44B5-9621 /media/store vfat defaults,utf8,umask=007,uid=1000,gid=1000 0 1


This worked for me.  Thanks.

---

### Post by tonolmo on 2010-12-25
Great!

Tried and working on an Ubuntu 10.04 (lucid).

Thank you, noynac.


> **noynac said:**
> I had the same problem and enabled the trash function for ntfs and vfat partitions that are mounted by fstab as follows:

1) Backup fstab.

2) Add uid=1000,gid=1000 as options to the partition's fstab entry (see example below). 

3) Create a directory named .Trash-1000 in the partition's root.

4) Restart the computer.

Upon completion of the above, deleted files will be placed in a directory named files within the .Trash-1000 directory, and your Ubuntu desktop trash icon will show the deleted files.

~~~

Example fstab entry
UUID=44B5-9621 /media/store vfat defaults,utf8,umask=007,uid=1000,gid=1000 0 1

---

### Post by sergius248 on 2011-10-22
Yes changing  Add uid=1000,gid=1000 as options to the partition's fstab entry. Than Create a directory named .Trash-1000 in the partition's root and Restart the computer. Has been working for me too (Lucid on NTF partition). Thanks

---

### Post by lakeshore17 on 2012-08-17
Hi,
I am extremely new to Ubuntu. How do I do this, step by step would be great. 
Thanks

---

### Post by oldos2er on 2012-08-17
Hi lakeshore17, please start a new thread for your question. This one's four years old.

---

