---
title: "&quot;Documents&quot; and Dual Boot"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by spotteddog on 2008-05-09
Questions about sharing a "Documents" folder between Hardy and Vista.

I have 3 hhd, dual boot. "C" has Vista, "F" has Hardy and "E" is used for backups and misc stuff.

My plan would be to make a folder on "E" called something like "SharedDocuments" and keep my documents there. That way I could work on Documents with either Vista or Hardy and would not have to worry about syncing the folders. "E" is NTFS. I have tried this with some small test documents and it seems to work OK.

Will this work out OK, until I feel confident enough to completely switch to Ubuntu? At any point where I decide to stay with Hardy or go back the Vista, I could just copy "SharedDocuments" back to the original "Documents" folder.

Is there something I am unaware of that could cause problems down the road? 

Is there a better way to do this?

Thanks,
Spot

---

### Post by hyper_ch on 2008-05-09
That would work fine... although I'd rather make it as ext3 instead of ntfs and use the ext2/3 drivers in Windows... but that's a personal preference.

---

### Post by Prestige08 on 2008-05-09
I wouldn't worry about the backup plan you have.  In fact, I personally like the idea you have.  Ubuntu, or other linux systems, are capable of accessing FAT/FAT32 and NTFS drives pretty easily, so don't worry.

---

### Post by newbuntuxx on 2008-05-09
Thats what I have at the moment as a back up scheme. Two ntfs partitions and an linux one. One of the ntfs is for windows, the second one is for back-up and it is being shared between ubuntu and xp. 

Hardy auto-mounts my two ntfs partitions. I didn't need to configure anything.

---

### Post by spotteddog on 2008-05-09
Thanks All. 

Sounds like I'll keep that configuration and forge forward with Hardy. Love it.  :)

---

