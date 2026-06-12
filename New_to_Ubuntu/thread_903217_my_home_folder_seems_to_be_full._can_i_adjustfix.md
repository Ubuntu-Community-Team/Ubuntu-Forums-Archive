---
title: "my home folder seems to be full. can i adjust/fix?"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by danny_galaga on 2008-08-28
i noticed this when i couldnt get openoffice to save, and bookmarks, forward/back buttons stopped working in firefox. at that point the disk usage analyser told me my home folder usage was 100% at 2.4 GB. i deleted my mame roms folder to see what would happen. everything is working now, but the disk usage analyser now says home folder is 100% at 1.1 GB. what does this actually mean then? how do i find out how much space i have left for Linux? i partitioned the drive for dual boot with XP. all i remember is that i added a little extra than recommended for the Linux partition (i think something like 12 GB was recommended minimum, and i made it 15). Surely it's not full already? 

As a note, any non linux required files i download (music or whatever) goes to a secondary hard drive...

edit: system monitor tells me 'system status: available disk space: 0 bytes

---

### Post by SunnyRabbiera on 2008-08-28
well how did you partition may I ask?
how much room did you give to each partition?
by the way, I am the master, you will obey me :D

---

### Post by dinostabOMG on 2008-08-28
Assuming nothing else is wrong, actually the "available space" will tell you how much space is left on the entire partition - which can all be allocated to any particular directory on that partition. Try emptying the trash once you've deleted some stuff.

---

### Post by danny_galaga on 2008-08-28
thats funny! i went out of system monitor and back in. i guess it needed to refresh. now it tells me available space is 1.1 GiB. which is probably about the difference between when 'home' was 2.4 GB and when i deleted the mame folder and emptied the trash.

still, this seems rather a small amount of space to play with. i did a standard dual boot install but i dont remember the specifics. just trying to find the original guide on the net i used to see if it jogs an memories. might have to boot back to Xp to find the link!

---

### Post by louieb on 2008-08-28
Please post the disk usage. to do that:
Open Accessories>Applications>Terminal and run
```
df  -h 
```

Cut and paste the output in your next post.

---

### Post by danny_galaga on 2008-08-28
Filesystem            Size Used Avail Use% Mounted on
/dev/sda5              12G   10G  1.2G  90% /
varrun                502M  120K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   60K  502M   1% /dev
devshm                502M   12K  502M   1% /dev/shm
lrm                   502M   39M  463M   8% /lib/modules/2.6.24-19-generic/volatile
overflow              1.0M   36K  988K   4% /tmp
gvfs-fuse-daemon       12G   10G  1.2G  90% /home/danny/.gvfs
/dev/sdb1             150G   38G  112G  26% /media/New Volume
/dev/sda1              25G   19G  6.0G  77% /media/disk

---

### Post by jpds on 2008-08-28
> **danny_galaga said:**
> Filesystem            Size Used Avail Use% Mounted on
/dev/sda5              12G   10G  1.2G  90% /

You don't have your /home folder on a separate partition - which is usually a recommended thing to do.

Instead you have all your Ubuntu files (which take up some space) and your personal documents all on the same partition.

See the buttom of this page: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) - for reasons on why a separate /home partition is a good idea.

---

### Post by danny_galaga on 2008-08-28
> **SunnyRabbiera said:**
> 
by the way, I am the master, you will obey me :D

ha! would you believe i only just got that! and i call myself a doctor who fan...

---

### Post by danny_galaga on 2008-08-28
> **jpds said:**
> You don't have your /home folder on a separate partition - which is usually a recommended thing to do.

Instead you have all your Ubuntu files (which take up some space) and your personal documents all on the same partition.

See the buttom of this page: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) - for reasons on why a separate /home partition is a good idea.

thanks for that. now the big question is- can i adjust it? i see in the linked page it says

 "If you want to resize a partition or add more space to an existing partition, keep in mind that you can add only to the end of a partition, not to the beginning of it. "

which implies it can be done.

edit: oops, i guess what i should be asking is 'can i add a partition'...

---

### Post by danny_galaga on 2008-08-28
i found this thread:

[http://ubuntuforums.org/showthread.php?t=898032&highlight=add+partition](http://ubuntuforums.org/showthread.php?t=898032&highlight=add+partition)

does this sound like the right way to going about it?

---

### Post by sameerds on 2008-08-28
> **danny_galaga said:**
> "If you want to resize a partition or add more space to an existing partition, keep in mind that you can add only to the end of a partition, not to the beginning of it. "

which implies it can be done.

Yeah, you can extend the partition, but the only thing to look out for is that another partition might start just after it. Then you don't have any space to grow the earlier partition.

> **danny_galaga said:**
> 
edit: oops, i guess what i should be asking is 'can i add a partition'...

You can add a partition using a partition editor tool. This is preferably done from a live CD instead of a running system. For your problem about insufficient space in /home, you could move your entire /home to a new partition. Refer to [this post]("http://ubuntuforums.org/showthread.php?p=5619971#post5619971") for a general idea about how to do that. Although the post is about moving /usr, the same steps can be used to move /home to a different partition.

---

### Post by sh4d0w808 on 2008-08-28
Maybe U can try these commands also:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

Description of the above commands are [here]("http://ubuntuforums.org/showthread.php?t=592141").

---

