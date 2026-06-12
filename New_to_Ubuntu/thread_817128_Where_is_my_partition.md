---
title: "Where is my partition??"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by germantechie on 2008-06-03
I wanted a dual booted system of VISTA and **Hardy Heron** which i successfully did. My partitions are:
Vista - 15 Gb (Primary)
/     - 15 Gb (Primary)
/home - 30 Gb (Primary)
Fat32 - 30 Gb (Logical) - wanted to have common space for
                          Movies/Music
Fat32 - 20 Gb (Logical) - same for photos and other data
/tmp  - 20 Gb (Logical) - i was forced to(it asked for a 
                          mount point)
/usr  - 19 Gb (Logical) - i was forced to(it asked for a 
                          mount point)
/swap - 6  Gb (Primary)    

On my Ubuntu, i see an icon for Vista listed as 15.4 Gb drive and one icon listed as "FileSystem".
First of all what is this "FileSystem" which lists all the default folder in linux?

Second, why isnt it listing the different partitions as my partition table?? i want sepearte partition as seperate icon. how to do that?

The first Fat32 of 30 Gb has a mount point as /dos and the other Fat32 has /windows.

What are these /dos and /windows mount points?

Please suggest a better Partiton table if mine is not correct.

---

### Post by _sphinx_ on 2008-06-03
Please post the ouput of following
```
sudo fdisk -l
```

---

### Post by ibuclaw on 2008-06-03
FileSystem is your [SIZE="5"]/[/SIZE] root directory. It is the top of the filesystem tree that is your Linux Filesystem and Mounted Partitions.

It seems strange that the installation of Ubuntu forced you to have a separate partition for your /tmp and /usr directories.
By default Ubuntu installs itself into one partition, but does give you the option to have a separate /home partition (which is highly recommended).

Hmm... I'm thinking that you probably chose to manually partition?
Not the most wise idea if you don't know what you are doing.
But, oh well. It is done now.

A better place to your Windows partitions would be in your /media directory, as it is the most common place to mount them.

ie:
```

from **/dos** to **/media/music**

from **/windows** to **/media/photos**

```
And the partitions should show themselves up on the Desktop now once you make the change too.

This can be done by editing your fstab file, this can be opened and edited by pressing **Alt+F2** and typing
```
gksu gedit /etc/fstab
```
Locate the partitions, and change the mount point accordingly with great care.



Also, if you want to change the naming convention of the hard drives (ie: from "54GB Hard Drive" to a more meaningful name, such as "My Music Drive") then read this very useful howto [here]("https://help.ubuntu.com/community/RenameUSBDrive").

Regards
Iain

---

