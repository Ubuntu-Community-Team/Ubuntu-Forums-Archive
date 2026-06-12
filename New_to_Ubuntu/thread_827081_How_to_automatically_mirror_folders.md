---
title: "How to automatically mirror folders"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by macpuppy on 2008-06-12
Hello,  I'm looking to install ubuntu and jump in the world of Open Source.  I will be putting together a system that will serve one purpose - store data that we create using other computers (Win2k, WinXP).  Currently the server I use for this is filling up, and I am replacing it.  I have it set up so that when I save a file on the C drive, it automatically makes a copy on the D drive.  This is done with a utility called mirrorfolder.  It's an easy painless system.

Is there a simple way to do this with ubuntu?  I'd prefer not use a nightly backup system and instead do it in real time.  I have zero experience in unix, but hope to get up an running soon.

I'd like to know that I can do this before installing ubuntu and going any further.  Thanks for your help.


Art

---

### Post by ukripper on 2008-06-12
> **macpuppy said:**
> Hello,  I'm looking to install ubuntu and jump in the world of Open Source.  I will be putting together a system that will serve one purpose - store data that we create using other computers (Win2k, WinXP).  Currently the server I use for this is filling up, and I am replacing it.  I have it set up so that when I save a file on the C drive, it automatically makes a copy on the D drive.  This is done with a utility called mirrorfolder.  It's an easy painless system.

Is there a simple way to do this with ubuntu?  I'd prefer not use a nightly backup system and instead do it in real time.  I have zero experience in unix, but hope to get up an running soon.

I'd like to know that I can do this before installing ubuntu and going any further.  Thanks for your help.


Art

You got mother of all sync in GNU/linux world called rsync

[http://samba.anu.edu.au/rsync/documentation.html](http://samba.anu.edu.au/rsync/documentation.html)
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

and ofcourse unison which syncs multiple machines

if you want something gui - go for grsync```
sudo apt-get install grsync
```

---

### Post by louieb on 2008-06-12
Just curious was looking a the rsync documentation. Doesn't look to me that it can be set up to real time mirror.   I guess you could set up cron job to run rsync every so often.  

Might look  into using **dmraid or mdadm **and setting up a **raid1** array.
Might be that mirroring a couple of partitions on different hard drives would do what you need.

---

### Post by decoherence on 2008-06-12
rsync is just a syncing tool. it's up to you to watch for file changes and update them. simply put rsync in an infinite while loop with an appropriate amount of sleep. if no files have changed, rsync won't do anything.

while true
do rsync [source-folder] [destination-machine:folder]
sleep 5
done

there is probably a way to trigger rsync to run when there is a change in a directory, rather than having it poll. upstart? dbus? not my field of expertise...

---

### Post by defrex on 2008-06-12
To use that code, you need to make a shell script.

```
#!/bin/sh

while true
do rsync [source-folder] [destination-machine:folder]
sleep 5
done
```

Put that in a text file. Right click > Properties > Permissions > Allow executing file as a program. Then call it from System > Preferences > Sessions to have it start at boot.

---

