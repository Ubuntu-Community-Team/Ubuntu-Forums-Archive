---
title: "How to automate file syncing w/ Windows"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Contrarian on 2008-06-16
I got MythBuntu installed on a new PC.  I'd like to set up an automated process to copy the audio directory on one of my windows machines to the /var/lib/mythtv/music dir on this MythBuntu system.    

Could someone point me in the direction of how to accomplish this? I'm thinking...

1) share the audio dir on windows
2) find a way to mount it in linux
3) use an rsync program to copy windows dir to local music dir 
4) set up chron job to do #3 periodically

Before you ask why I don't just link to the windows share, by copying it I get a backup on another PC. 

Is rsync the program I'd use to copy files? I don't want to copy ALL files again, only the new or changed ones.

Any help or suggestions is appreciated.

---

### Post by p_quarles on 2008-06-16
Yes, rsync is the program you want to copy only changes. There are also graphical interfaces for it available (grsync, for instance). 

To mount a shared Windows folder on a Linux machine, you can use the smbclient application.

---

