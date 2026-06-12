---
title: "Back-up file system questions."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-08-05
Ok so i searched the fourms and even found a good wiki for how to back up my system. I have my personal files backed-up to an external HDD. About the File-system though: Can i back up just the file-system with all the config files, and applications, so that if in my toying around, i mess somthing up, i can go into recovery mode and cp from the cd/dvd and replace it back into the system? also, where are programs "installed" to? is it in etc?

I found this code in the howto: thread

```
tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys /
```

But "tarballing" it i dont think will be nessary if i can just burn an image to a dvd, since an ubuntu install is less than 4Gb. And then i wouldnt need to unpackage it when i need the data.

I ask, because i find myself creating another copy of config files before i play with them. I feel it would jsut be easier to burn the whole thing to a dvd, and not have two of each config file over time wasting space.

What are your thoughts?

---

### Post by tuxxy on 2008-08-05
[http://ubuntuforums.org/archive/index.php/t-6509.html](http://ubuntuforums.org/archive/index.php/t-6509.html)

---

### Post by tamoneya on 2008-08-05
it sounds like for you a nice way to do it would be with the dd command.  It will make a bit for bit copy of the partition or device.  That way it makes the recovery really easy as no reinstalls are needed and you just need to "dd" in the other direction.

[http://research.att.com/~gsf/man/man1/dd.html](http://research.att.com/~gsf/man/man1/dd.html)

---

### Post by deathvalleyjoker on 2008-08-05
I looked at the dd page. I am little confused by what they mean by block. I am new to linux, so could you provide an example of code to back up say the /dev folder? 

i think a bit for bit copy is exactly what i am looking for. and would like to do that for every folder off of the root except for users. 

As far as your first post, if i were to make an iso image of the folders, could i just cp (or dd) from the disc and into the file system for when i mess up the orignal config file?

thanks!

EDIT: sorry, jsut relized you are two seperate people. i only looked at the avatars, and first letter of your username. sorry for hte mix up.

---

### Post by tamoneya on 2008-08-05
> **deathvalleyjoker said:**
> I looked at the dd page. I am little confused by what they mean by block. I am new to linux, so could you provide an example of code to back up say the /dev folder? 

i think a bit for bit copy is exactly what i am looking for. and would like to do that for every folder off of the root except for users. 

As far as your first post, if i were to make an iso image of the folders, could i just cp (or dd) from the disc and into the file system for when i mess up the orignal config file?

thanks!

EDIT: sorry, jsut relized you are two seperate people. i only looked at the avatars, and first letter of your username. sorry for hte mix up.

A block device is something like /dev/sda or /dev/sdb1.  The simplest version of this command would be ```
sudo dd if=/dev/sda of=/dev/sdb
```
that would backup all of harddrive /dev/sda to harddrive /dev/sdb.  This would be EVERYTHING.

Then to recovery you just pop in the live CD and run:```
sudo dd if=/dev/sdb of=/dev/sda
```

---

### Post by DGortze380 on 2008-08-05
> **tamoneya said:**
> A block device is something like /dev/sda or /dev/sdb1.  The simplest version of this command would be ```
sudo dd if=/dev/sda of=/dev/sdb
```
that would backup all of harddrive /dev/sda to harddrive /dev/sdb.  This would be EVERYTHING.

Then to recovery you just pop in the live CD and run:```
sudo dd if=/dev/sdb of=/dev/sda
```

Take a look at these threads too.

[http://ubuntuforums.org/showthread.php?t=870059](http://ubuntuforums.org/showthread.php?t=870059)
[http://ubuntuforums.org/showthread.php?t=879272](http://ubuntuforums.org/showthread.php?t=879272)

rsync is a lot quicker than dd. 
it's not bit for bit, but you don't necessarily need a bit for bit just for a backup.

---

