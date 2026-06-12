---
title: "folder persmission QEMU"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by noland on 2008-06-15
all right i am kind of confused.. I have set up, got working a winXP using QEMU, and set up a share folder between host Ubuntu Hardy and guest XP. now, for reasons mentionned in this thread 

[http://ubuntuforums.org/showthread.php?p=5164987#post5164987](http://ubuntuforums.org/showthread.php?p=5164987#post5164987)

i download files using Utorrent in the emulated xp directly in the share folder.  I set up the folder so that i have read/write/execute permissions in Ubuntu, and so that "guests" can read write (i.e. winXP) using the "share" tab in the folder properties.  When i access the share folder in the emulated windows, i have read/write permissions, as was set in host Ubuntu.  When i open the share folder in ubuntu now there is a "lock" on all files downloaded or downloading or put there from windows.  I cannot move nor delete the files when using GUI file browser. But i **CAN** move them in the terminal using the mv command as i please though i cannot delete the files.  To delete from Ubuntu, i need to use sudo.  now i dont understand why i cannot at least move the files from the normal file browser and i can in the terminal WITHOUT using SUDO.  When i have moved the files from the share folder i can then delete the files as i please graphically.  

Now is it me or the permissions are messed up? is that SAMBA? or is the share thing already included in Ubuntu?

Thanks,

Phil

---

