---
title: "Change ownership on external hard drive"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by trooperchix on 2012-07-25
I have an external hard drive that mounts with root as owner making it impossible for me to put more information on the hard drive let alone delete or update files on it.  I'm sure there is a simple answer for this.  I need to change the ownership of the drive and all the files on it.  

I've never had this trouble before, though I think it might have something to do with my doing a fresh reformat and install of Ubuntu on my laptop.  It's the only difference I can think of.  Your help would be much appreciated.  

Oh, I need as simple instructions as possible, I really have no clue.  I've tried the option on another post, and it did not work.  :(

Thanks.
trooperchix.

---

### Post by HiImTye on 2012-07-25
is it mounted in fstab or do you only plug it in when needed?

if it's in fstab then you just change the owner in the flags spot


if it's plugged in on the fly then you'll need to find its' mount point (most likely in /media/) and chown it

---

### Post by d4m1r on 2012-07-25
Make the change in your fstab file, [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by ranger1021994 on 2012-07-25
> **trooperchix said:**
> I have an external hard drive that mounts with root as owner making it impossible for me to put more information on the hard drive let alone delete or update files on it.  I'm sure there is a simple answer for this.  I need to change the ownership of the drive and all the files on it.  

I've never had this trouble before, though I think it might have something to do with my doing a fresh reformat and install of Ubuntu on my laptop.  It's the only difference I can think of.  Your help would be much appreciated.  

Oh, I need as simple instructions as possible, I really have no clue.  I've tried the option on another post, and it did not work.  :(

Thanks.
trooperchix.

>Ubuntu local user permissions dont work on external drives.
>You need to use terminal with sudo command so as to execute commands related to external drives.
OR
you can use :
```
gksudo nautilus
```
and browse your external :)

---

### Post by trooperchix on 2012-07-25
This is a drive plugged in occasionally via usb.  I don't know what mounted in fstab means nor do I know how to chown something.  Could you help? 

[IMG][[IMG]http://i46.photobucket.com/albums/f115/Trooperchix/th_screenshot-2.png[/IMG]](http://s46.photobucket.com/albums/f115/Trooperchix/?action=view&current=screenshot-2.png)[/IMG]

The bugger is that this worked beautifully on my system until the most recent upgrade to Precise.  I had all the permissions done correctly before.  Bugger...

---

### Post by ajgreeny on 2012-07-25
Plug in the drive and you should see it appear as a folder in /media, which you will be able to see either using nautilus or with command ```
ls /media
```Make a note of the folder name (/media/*name)* and then run the command in terminal ```
sudo chown *username:username* /media/*name*
``` Change username:username for your own username, of course.

What filesystem is the drive's partition formatted as, fat32, ntfs or ext3/4?

---

### Post by Bufeu on 2012-07-25
> **trooperchix said:**
> This is a drive plugged in occasionally via usb.  I don't know what mounted in fstab means nor do I know how to chown something.  Could you help? 

[IMG][[IMG]http://i46.photobucket.com/albums/f115/Trooperchix/th_screenshot-2.png[/IMG]]("http://s46.photobucket.com/albums/f115/Trooperchix/?action=view&current=screenshot-2.png")[/IMG]

The bugger is that this worked beautifully on my system until the most recent upgrade to Precise.  I had all the permissions done correctly before.  Bugger...Did you run Nautilus as root (*gksudo nautilus*)?

---

### Post by dandandrums on 2012-08-07
> **ajgreeny said:**
> Plug in the drive and you should see it appear as a folder in /media, which you will be able to see either using nautilus or with command ```
ls /media
```Make a note of the folder name (/media/*name)* and then run the command in terminal ```
sudo chown *username:username* /media/*name*
``` Change username:username for your own username, of course.



Worked perfectly for me, thank you! One note though, I don't understand why you gave username:username as an example when simply username would work.

For example, I used the command sudo chown myusernamehere /media/name. I assumed you meant the code to be sudo chown username:myusername /media/name.

Other then that, thanks! :):o

---

### Post by Kalanac on 2012-08-07
username:username changes the group too I think (usually the same name as username).  Saves having to do a chgrp.  It'll most likely work fine without changing the group.

---

### Post by mdba on 2013-05-03
You need to add -R recursive, the command will be this way: *sudo chown -R username:username /media/mount-point*(drive name).

---

