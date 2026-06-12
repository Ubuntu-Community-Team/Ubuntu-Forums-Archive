---
title: "FAT Support"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by takuhii on 2008-06-08
What can I re-install to fix my FAT support in ubuntu hardy heron (8.04).

Any ideas, as at the moment, I cannot mount any FAT devices.

---

### Post by kellemes on 2008-06-08
> **takuhii said:**
> What can I re-install to fix my FAT support in ubuntu hardy heron (8.04).

Any ideas, as at the moment, I cannot mount any FAT devices.

More info please.. how are you trying to mount? You get error messages or something?

---

### Post by bumanie on 2008-06-08
As above, plus is there any reason you particularly need FAT partitions/drives? Ubuntu now has read/write support to ntfs - with ntfs, you don't have the limitations FAT produces.

---

### Post by takuhii on 2008-06-08
i'm just pluggin the FAT formatted memory pens in, and it's giving me an error. "Invalid mount options"

---

### Post by bumanie on 2008-06-08
This a walkk-through from [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668") What you are describing seems to be a known bug in 8.04 that hasn't been fixed yet. Hope this helps.
Hi fellers,

To baby those who are onlookers in desperate search of a solution (i'm running Hardy)...

open a terminal.
type "gconf-editor"
click your way to "/system/storage/volumes/_org_freedesktop_Hal_devices_..."
you should now see mount point, and its value

You can do something here and get your drive to work, yes. However, if you have programs with calls to that drive before you got a bunch of wacko underscores (_), you'd probably like to return your drive to its original mount point. If you dont, click the value field, and just erase the text. Plug your drive back in and you are golden. exit out of your terminal and rock on. if you do want to get things back to their original state...

In my /media directory existed:
/CDback
/CDback_
/CDback__
/Mint
/Mint_
/Mint__

In my drive, I have two partitions. I would like to see them always mount to /CDback and /Mint.

Be careful here. I did a quick "gksudo thunar" (or gksudo nautilus), and erased ONLY those mount directories which were related to my drive. you dont want to erase your standard hard drive's mounting point, or your CD-ROM etc etc etc (sda,hda,cdrom,cdrom0,etc). Many a folk will likely scold me for even mentioning doing this. a sudo rm MOUNT-DIRECTORY would suffice for each sloppy underscored directory as well. return to gconf-editor and remove the text from the 'value' field.

You may have to read the whole thread and 'bug' to get the full gist of it.

---

### Post by takuhii on 2008-06-10
didn't work. I have had to re-format my memory pen to NTFS and use that. All FAT support is broken...

> **bumanie said:**
> 
click your way to "/system/storage/volumes/_org_freedesktop_Hal_devices_..."


This doesn't exist in 8.04 anymore, all these "fixes" seems aimed at 7.10 and below. Some people found that eliminating USEFREE in relation to VFAT fixed the problem. other found that re-adding it fixed the problem. Go figure, the "bug" seems to be quite temporamental in being fixed...

NTFS all the way baby!!

---

### Post by mde123 on 2008-06-10
i have the same problem.
in linux mint

---

