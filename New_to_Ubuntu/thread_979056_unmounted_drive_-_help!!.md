---
title: "unmounted drive - help!!"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by bmaguire on 2008-11-11
This evening I went to unmount a flash drive before removing it and I seem to have accidentally seriously messed my system up.  I can log in as myself, I get all my applications, but none of the data - including my personal preferences, email, documents, etc.is visible!  

My system is a Zareason Midlap with 4 megs of RAM and a 450 gb hard drive.  I suspect I somehow unmounted one of the hard drive partitions.  What have I done and how can I fix it???

---

### Post by dsurge on 2008-11-11
I'm not too good with this stuff myself yet but I'll try to help. Check gparted partition editor. It'll tell you if you have any unmounted harddrives. If you don't have it installed go to your apps> add remove, type in gparted under universe and install it. if you do, all you have to do is boot up in the live cd mode and mount it.

---

### Post by Arlo012 on 2008-11-11
Unless you somehow completely deleted a partition, you can always boot to the Live CD and try to remount any unmounted partitions. Failing that, you can also access any critical files that you have saved and reinstall Ubuntu.

---

### Post by bmaguire on 2008-11-13
Thanks for the suggestion.  I went in with gparted and didn't really make any progress.  It appears that my user account got messed up somehow.  Luckily my critical material was backed up, so I just restored.
Brian

---

### Post by mapes12 on 2008-11-13
It looks like somehow your /etc/fstab file has become corrupted and your system doesn't know where your /home is (that's where all your files, personal settings, bookmarks and the like are stored).

You may be able to reconfigure it from picking out what you need from here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Might be a good opportunity to make sure you have your partitions set up correctly as well: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by bmaguire on 2008-11-14
Thanks!  I'll check that out.
Brian

---

