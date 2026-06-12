---
title: "Having two ubuntu OS /home/photos etc point to same data partition"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by codenameSQL on 2013-07-07
Hi gang. Alrighty, I've learned just enough to be dangerous and have managed to get a triple boot system working but need to consolidate and tidy up a little

On the 'buntu side of things, i have these partitions:
 lubuntu 13.04 on sda1, 
lubuntu /home (soon to be moved to) sda6, 
ubuntu 12.04 LTS on sda7, 
12.04 LTS /home already at sda8 during install, 
swap sda5, 
sda9 a large partition (ext4) for data only

Keeping the /home folders for both OS's on their respective partitions, I would like to set the /documents, /downloads, /photos, /videos for each to point to the same folders on the data partition (e.g., one location for photos - I click the "Pictures"  icon in either file manager for either OS - and it goes to the same place on the data partition as if it were still part of the /home directory).

How does one go about accomplishing this task?  I saw a couple of references to "soft links", but no instructions and I'm not sure if that's actually what I need..

Thanks

---

### Post by waynefoutz on 2013-07-07
You use the advanced options in the installer, when you install the first OS, make /home a separate partition. When you install the second OS, do the same thing, but point your /home to the one that already exists.

This guide is old, but the process s pretty much the same. 

[http://www.psychocats.net/ubuntu/installseparatehome]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by codenameSQL on 2013-07-07
Okay, but won't that put the program installs/settings in the same place as well?  I'd like to keep those /home folders for each OS on their isolated partitions and have what is strictly ubiquitous data isolated on it's own partition as well.

---

### Post by monkeybrain2012 on 2013-07-07
I think oldfred probably answered your question
[http://ubuntuforums.org/showthread.php?t=1951526](http://ubuntuforums.org/showthread.php?t=1951526)

BTW, if you are dualbooting why not try another Linux distro than *buntu? Seems like too much repetition to be fun. :)

---

### Post by codenameSQL on 2013-07-08
Repetition is the mother of skill.. or just the mother something.. :P

Yep, that seems to be what I'm looking for.. thanks for the link. It appears straight forward enough.. famous last words..

Not sure what is going on here though.. I created the /mnt/data folder on the data partition and then read up on editing /etc/fstab  and edited it for mounting. Seemed to work for mounting, but now when looking at the direcotory tree I see that something appears to be strange.  I created only /mnt/data


But I see the following:
/mnt/data/lost+found
/mnt/data/mnt/data

where'd the second directory creation come from? I'm quite sure I didn't do it..  so delete 'em and start over? or??  maybe is there a sudo exorcism command lying around somewhere to throw at it?

---

### Post by codenameSQL on 2013-07-08
Okay, I think something *may* have just clicked.. I thought I was indicating the path to follow...but...

does fstab indicate the location IN UBUNTU *from where* the partition will be mounted???  If so, then what is happening makes a little more sense..  SO, if I edit fstab
to uuid=####  /mnt/data       it "puts" the root of the partition at that location in the directory tree... then any folders I created on the partition will show there, i.e. mnt/data..   .. so I can delete the mnt/data folders from the partition and just create /music /videos etc. at the root level of the partition,  rename the ones already in the home folder and *from the home folder* create the new links???


Edit: Yep, that was the ticket.. now everything is working perfectly...

---

### Post by CaptainMark on 2013-07-08
@waynefoutz I wouldn't do that exactly, the problem there is that is if OS1 and OS2 have different version numbers of the same piece of software installed, whichever OS has the older version is likely to have problems reading the config files.

A better way would be to have a single seperate home partition which is mounted to /home only for the 'main' OS, and then for all second/third etc. OS's to have its own home folder containing symlinks for the main data folders on the home partition, so:

/dev/sda1 Ubuntu
/dev/sda2 Data partition mounted at /home on /dev/sda1
/dev/sda3 Fedora with symlinks "/home/mark/Documents > (/dev/sda2)/mark/Documents"
/dev/sda4 Opensuse with symlinks "/home/mark/Documents > (/dev/sda2)/mark/Documents"

Obviously you would need to create symlinks for every main folder within /home on the second and third OS's but me and most people only have 6 or seven so thats not a huge hassel

---

