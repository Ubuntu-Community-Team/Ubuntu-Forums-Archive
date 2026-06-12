---
title: "Ubuntu home shared with windows files missing"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by CachoCh on 2013-04-10
Hello,
I have a pc in dual boot with Ubuntu 12.04 LTS x64 and Windows 7 x64.  I have the /home folder (ubuntu's) in its own ext2 partition and I read and write it with ubuntu and windows.
I access the /home ext2 partition in windows 7 with ext2 volume manager, whenever I boot in ubuntu I can not see the files that were created while in windows.
All files are available whenever I load in Windows.

How can I get access all the files (Windows & Ubuntu created) under Ubuntu ?
Thanks

---

### Post by ajgreeny on 2013-04-10
I wonder if this is a problem of the files made by windows not having any Linux permissions tags on them, windows not recognising the whole business of file permissions as Linux does.  This is just an idea, as I do not have any evidence one way or the other, however, I believe it is possible to set premissions on a folder on an ext2 file system in such a way that it will automatically give all files added to that folder the same general permissions.  See if a search about that gets you anywhere.

I do not have windows to even test the theory, but back in the days when I did use XP I never found the ext2fs driver or whatever it was called, to be very effective or trustworthy, so that may be another reason for the problem.

---

### Post by oldfred on 2013-04-10
It generally is better to create a shared NTFS data partition. The Linux driver works well for NTFS and you avoid all the permission and ownership issues.
Also better to have a journalized file system, in case of file issues, repair may be easier or possible where ext2 and FAT32 may not be repairable.

---

