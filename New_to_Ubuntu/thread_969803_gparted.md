---
title: "gparted"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Skyker on 2008-11-03
I just installed gparted and opened it.  It shows I have two paritions, one is fat32 and one is 'extended' which is further subdivided.

The fat32 one is my XP parition, is there a way to integrate this partition with my xubuntu partition?  (as in, format xp) 

I also get this error message: 
Failed to mount "10G Volume".

---

### Post by Skyker on 2008-11-03
I right click on the fat32 icon and click 'format to..'  do i want to format it to an ext2? or ext3?

And can I integrate it with my othe parition?  Or should I delete it and just make my other parition bigger?

---

### Post by logos34 on 2008-11-03
You'll have to do it from the ubuntu live cd.  

System>admin>partition editor (Gparted).  If it activates the swap partition inside the extended partition, unmount it. (otherwise you won't be able to do anything).

Delete the fat32 XP partition.  

Grow the extended partition into the empty space.

Now you can expand the / partition inside

---

### Post by sneeks on 2008-11-03
or use the gparted live cd,may be eaiser for you

---

### Post by Skyker on 2008-11-03
so I can't do anything from the program I've just installed? -_-;

---

### Post by pyromanic123boom on 2008-11-03
so you have one big drive, and that is split into two different partitions:  fat and ext?  Because you won't be able to delete a partition if you are *running* on the drive itself.  Just get your version's live cd, and then do it from there. the img files are on [www.ubuntu.com](www.ubuntu.com)

---

### Post by kansasnoob on 2008-11-03
Someone should ask:

What is the FAT 32 partition? Is it a Windows operating system? If so do you really want to get rid of it?

Second thing is that grub gets fiddly with no primary partition at the beginning of the drive.

---

### Post by pyromanic123boom on 2008-11-03
> The fat32 one is my XP parition, is there a way to integrate this partition with my xubuntu partition? (as in, format xp) 

Maybe you should read more closely.  He wants to format his XP partition...and make ubuntu his primary partition...

---

### Post by kansasnoob on 2008-11-03
> **pyromanic123boom said:**
> Maybe you should read more closely.  He wants to format his XP partition...and make ubuntu his primary partition...

Okey dokey! I'll count on you straightening this out when the OP ends up with nothing but an Extended Partition and can't boot!

---

### Post by pyromanic123boom on 2008-11-03
Yes, well, not exactly my point. I would suggest installing clean to make the necessary partitions. Copy data to a external drive or some other way of backup (if possible,) and then install new. Otherwise, ask someone who knows more about partitioning.

---

### Post by logos34 on 2008-11-04
> **pyromanic123boom said:**
> I would suggest installing clean to make the necessary partitions.

That shouldn't be necessary.

[QUOTE]> **kansasnoob said:**
> Second thing is that grub gets fiddly with no primary partition at the beginning of the drive.

And that's not true.  

At most you might need to rewrite grub to the MBR and edit 'root' line in menu.lst (but even here you may not have to because the deletion will not renumber the logical partitions, which is where / is)

I just got done doing this very same thing--I've grown my extended partition (containing all my ubuntustudio partitions) to take up the entire hard disk.  Works perfectly, no boot problems.

good luck

---

