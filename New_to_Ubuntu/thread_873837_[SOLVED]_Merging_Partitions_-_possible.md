---
title: "[SOLVED] Merging Partitions - possible?"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by JoneYee on 2008-07-29
Last night, I finally removed the last vestiges on my NTFS partition that contained WinXp.

I used Gparted and then shrunk its size down leaving an area of unallocated space that I formatted ext3.

Now i would like to make this new partition part of the Ubuntu partition.  

Is this possible?  I don't think gparted can do it.  

Partition Table:
[1000MB] - [56000MB ext3] - [60000MB ext3 (ubuntu0)]

I know Ubuntu is at the end, but thats the remenants of a dual boot system.  I truly don't want to backup all of my home and then recopy it to a full hard drive install.  

Are the any *faster* options for merging the partitions?

I am not in front of this machine right now (at work) so requests for terminal output will be delayed several hours.

---

### Post by Darkchef on 2008-07-29
i don't think this is possible without deleting all of your data, so I would seriously consider backing up your data before you try it.

EDIT : But it is possible to merge your partitions, despite loss of data

---

### Post by Elfy on 2008-07-29
you could delete the new partition and then resize the exisitng installation this could take some time, alternatively you could have a seperate /home and migrate your exisitng to it or use it as a data partition and add it to fstab to mount on boot

personally I would have a seperate partition for use as data - eventually you'll likely reinstall or upgrade at which point it would be useful to havea seperate home

---

### Post by JoneYee on 2008-07-29
> **forestpixie said:**
> you could delete the new partition and then resize the exisitng installation this could take some time, alternatively you could have a seperate /home and migrate your exisitng to it or use it as a data partition and add it to fstab to mount on boot

personally I would have a seperate partition for use as data - eventually you'll likely reinstall or upgrade at which point it would be useful to havea seperate home

The latter is likely, sadly the entire reason I decided to drop the hammer on the ntfs partition was because I ran out of disk space in my root partition trying to get nwn platinum to work (which I still have not done *frustrated*)

So I need to finally learn fstab.  Thanks for the information.

---

### Post by Elfy on 2008-07-29
fstab's bark is worse than it's bite

however if the reason for it is to make / bigger then I don't see much option really - delete the old ntfs and resize the exisiting install partition - it really could take a long time - by that I mean hours or more, so do not be tempted to turn it off.

But it could be foolhardy not having backups - is the warning.

---

### Post by drs305 on 2008-07-29
> **JoneYee said:**
> So I need to finally learn fstab.  Thanks for the information.

If you want to take it slow there is a graphical fstab program called PySDM (it might be in your menu at System, Admin, Storage Device Manager). I've just written a tutorial on how to use it. The "3 Minute Guide" section is probably all you'd need. It's linked in my signature. Good luck with the partitioning.

---

### Post by JoneYee on 2008-07-29
> **forestpixie said:**
> fstab's bark is worse than it's bite

however if the reason for it is to make / bigger then I don't see much option really - delete the old ntfs and resize the exisiting install partition - it really could take a long time - by that I mean hours or more, so do not be tempted to turn it off.

But it could be foolhardy not having backups - is the warning.

My backups take place weekly to a Samba file server running on Ubuntu 8.04 Server 64.  Its just my last backup is Saturday Night and I am pressed for time this week and don't want to lose a day's time.  

I have no issue with mounting the empty ext3 partition in the media folder and using it as part of the file system.  Actually just needed my brain jogged on the subject.  I know that Linux doesn't differentiate along partition lines like Windows does, I just forgot about telling fstab to mount the partition to a specific location.

From what I read, Ubuntu can be told to mount the partition in the media directory on boot, so I'm all good with that, as long as the space is usable.

---

### Post by JoneYee on 2008-07-29
> **drs305 said:**
> If you want to take it slow there is a graphical fstab program called PySDM (it might be in your menu at System, Admin, Storage Device Manager). I've just written a tutorial on how to use it. It's linked in my signature. Good luck with the partitioning.

I may have a look should editing fstab prove to be too much for my 3 week old Linux experience.

---

### Post by bodhi.zazen on 2008-07-29
I think resizing your partition is being made to sound harder then it really is.

You need to boot a live CD (you can not resize a mounted partition, thus you need to go with a live CD to resize your root partition).

Use gparted :

Documentation: [Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

I think it is unlikely you will need to edit fstab or menu.lst, but if needed it is quite easy.

For your reference :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

It is also quite simple to make a separate home or data partition.

If you need help , just ask.

---

### Post by JoneYee on 2008-07-29
> **drs305 said:**
> If you want to take it slow there is a graphical fstab program called PySDM (it might be in your menu at System, Admin, Storage Device Manager). I've just written a tutorial on how to use it. The "3 Minute Guide" section is probably all you'd need. It's linked in my signature. Good luck with the partitioning.

Worked like a charm, danke my friend.

---

