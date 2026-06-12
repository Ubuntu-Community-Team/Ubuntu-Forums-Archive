---
title: "Is there anythin in  Ubuntu that will fix my problem?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by guyos3n1 on 2008-06-25
We have a computer running windows 98 with a hard drive that was partitioned into several partition drives.  We used C drive only for system files.  All our data and picture files were on the other partition drives.  We developed a problem within the system files and formatted C drive and reloaded windows 98 to it but now we cannot see or get to the other partition drives.  Is there anything in Ubuntu that would help us recover the data on these partition drives? [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by MasterSander on 2008-06-25
You can use the live cd and ubuntu will be able to mount those partitions, so yes.

---

### Post by snowpine on 2008-06-25
MasterSander is correct. The only thing I would add is that, if your computer is older and has 256mb or less of RAM, you will have trouble running the Ubuntu Live CD. If that is the case, you will need to try a lighter-weight distro that runs off of live CD, for example DSL or Puppy. Good luck! If you get stuck, keep posting details so we can help you.

---

### Post by bijeeshvs on 2008-06-25
get a live cd of any linux version, ( a cd that can start os without installing it )
if you are short on RAM use a light weight version of linux ( mentioned in the above post, if want help to find it try googling the mentioned names ) then put the cd in the cd drive change the boot device to cd drive ( in BIOS ) reboot the system , it will show you options to install or start the system, select to start system, linux wiil boot into a fully operable system , then you can check your missing hard drives

---

### Post by bumanie on 2008-06-25
If you are not used to command lines and shells etc., it would be best to use puppy linux as it mounts drives/partitions via GUI and can be run from ram, leaving your cd/dvd-rom free for transfering data to if you don't have an extrnal hard drive/usb pendrive etc. It loads into ram via a live cd - once 'installed' into ram, the live cd can be removed from the cd-rom tray and puppy will keep working.

---

### Post by dwhitney67 on 2008-06-25
There's always the option to remove the HDD, connect it to an external HDD-enclosure, then plug the USB cable into the working system that hosts Ubuntu.  Each partition on the HDD should get automatically mounted.

---

### Post by bumanie on 2008-06-25
Another solution could be to burn a gparted live cd and if you have available external hard drive space, gparted is able to copy whole partitions/drives. It would also give a good indication as to whether the partitions you can't see are still there or not.

---

### Post by Jerry N on 2008-06-25
I see no reason at all that Win98 should not see your partitions IF they are primary partitions.  Are you absolutely sure you didn't reformat the whole drive?  If your partitions were logical partitions within a primary partition, you may be SOL.  Since you appear to be using an older machine, like others I would try Puppy Linux.  If there are primary partitions on the drive Puppy should see them and allow you to copy your data to thumbdrives or CDs.  

Jerry

---

### Post by jr48 on 2008-06-25
I imagine the reason Win 98 can't see the other partitions is simply because the 'new' Win 98 install has performed it's usual trick of overwriting the Master Boot Record. If so the information is still safe in it's partition and a Live session CD will be able to access it as noted in earlier posts.

---

