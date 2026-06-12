---
title: "ntfs mount for 10.04"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by ZombeApocalips on 2012-05-26
I've had a little trouble with this in a couple different versions of Linux.  Here's a thought:
What file system is the drive/partition containing the folders in question formatted in?  

I've mostly seen this behavior with NTFS.  If that is the case, try installing NTFS Mount and running.  You can use that to edit some of the permissions.  That has solved some of my problems in the past.

That being said, I'm now on Ubuntu 10.04 (I downgraded because some programs I need to run are incompatible with newer versions) and I can't find ntfs mount for 10.04.  I found a package named ntfs-cfg-3 or something to that effect, but can't seem to locate an interface for it.  

Can someone point me in the right direction here? I've tried all of the above mentioned solutions without success.

---

### Post by oldos2er on 2012-05-26
Post moved to its own thread.

---

### Post by ZombeApocalips on 2012-05-26
I've come across mount manager but any time I change the properties (i.e. who can mount this partition) it says that the configuration file was overwritten successfully.  Unfortunately if I close Mount Manager and restart all the properties are back to default.  I even tried saving the configuration file and overwriting /etc/fstab (after a backup of course).  No dice.  I'd be happy to format my drives to XFAT or something but the media takes up too much space and I have nowhere to store it while I format.  I even downloaded a few partition managers in the hope of creating a new partition from the free space and using that to store some data and resizing each partition as I move media.  Unfortunately the option to resize a partition is grayed out.

---

### Post by ZombeApocalips on 2012-05-26
sudo apt-get update
sudo apt-get install ntfs-config

find it under system.  Once again someone already solved the problem and I couldn't find it until 10 hours after posting the same question.  I'm a genius.

---

