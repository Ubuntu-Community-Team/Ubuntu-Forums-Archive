---
title: "permissions and Samba issue"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by karl14 on 2014-05-07
So I installed Samba servers early this morning successfully and was able to access my mounted 2nd hard drive path at (/media/titan1) and I could view sub folders within titan1 including downloads, downloads/movies & downloads/games. Later I installed plex media server and while trying to set it correctly I might have typed some commands to alter permissions.

Now when I connect to my samba server through my windows 7 laptop I can only view the 2 sub folders (movies & games) within downloads but cannot go up a folder or to the root of titan1/ as I was able to do before. Any idea's how I can fix this guys?

Thanks all

---

### Post by dannyboy79 on 2014-05-07
its probably an easy fix, can you tell me what the permissions of the folder are at /media/titan1. open a terminal, then issue the following command
```
ls -la /media/titan1
```
you didn't change anything in your smb.conf file did you?

---

### Post by karl14 on 2014-05-07
I didn't edit any files, just ran two commands that were suggested on plex forums for a similar problems. If I could locate the thread then I would post them. I have used the command you mentioned and this was the output:

drwxrwxrwx 4 karl  karl   4096 May  6 23:15 .
drwxr-xr-x 5 root root  4096 May  6 22:35 ..
drwxrwxrwx 4 karl karl   4096 May  7 16:49 downloads
drwx------ 2 root root 16384 May  6 22:07 lost+found

---

### Post by dannyboy79 on 2014-05-09
ok now this lets see permissions of titan1 and then media
```
ls -la /media/ | grep titan1
```

```
ls -la / | grep media
```

---

