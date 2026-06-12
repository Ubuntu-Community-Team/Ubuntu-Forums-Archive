---
title: "[SOLVED] ext2 or ext3?"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-07-08
I plan on using an external hdd for backups. I want to use rsync, but I don't know what one to use. Should I use ext2 or 3? After I format the drive into the format, what else do I need to do?

---

### Post by mcduck on 2008-07-08
Ext3. There really aren't much reasons I could even imagine for using Ext2 instead of Ext3. :)

(Of course they are basically the same, only that ext3 adds journaling which makes it more fail-proof.. If the journaling would ever break Ext3 would just become Ext2, and then you could create the journal again and it would become Ext3 again..)

---

### Post by bryncoles on 2008-07-08
when i formatted my external drive to ext3, i had to give myself read/write permissions to it. this should be as simple as opening the terminal and typing 

```
chmod u+rw -R <filepathtoexternaldrive>
```

where <filepathtoexternaldrive> is... well... the filepath to your external drive. you can get this by simply dragging and droping the folder icon for your external drive into the terminal.

if that doesnt work, try opening the terminal and typing 

```
gksudo nautilus
```

to open the file browser as root, then navigate to your external drive mount point (in the /media folder probably) and right click, and go to the permissions tab and give yourself access there. 

be careful with 'gksudo nautilus', as you will have root access to your whole system, and can delete some very very important files, causing yourself no end of problems!

---

### Post by ptn107 on 2008-07-08
Ext3 supports journaling, ext2 doesn't.

---

### Post by Inxsible on 2008-07-08
> **mcduck said:**
> Ext3. There really aren't much reasons I could even imagine for using Ext2 instead of Ext3. :)The only time i use EXT2 is when I don't need the journalling :) for eg. in my /boot partition. The data there is not going to change much often, so there may not be as much fragmentation. I don't think there is need for journalling there.

As for the crashing..its just a 128MB partition..so the fsck would also be quite fast - if needed.

I think filesystems should be chosen according to the usage. I use reiserfs for my /var partition because it is good for large number of small files - which is what /var contains usually.

---

### Post by articpenguin on 2008-07-31
ext3 also has Htrees which help in directorys. Ext2 uses a linked list which is very inefficent for directorys with more than 2k files.

---

