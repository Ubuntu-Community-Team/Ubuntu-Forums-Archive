---
title: "Issues with Grsync"
date: 2016-10-28
forum: New to Ubuntu
---

### Post by anbu-s on 2016-10-28
I have a folder where i store all my photos and videos worth about 80GB and growing.
I want to copy the contents of this to a 1TB usb drive connected to my router. I've been trying Grsync without much success. While it copies files, it randomly fails at various points - sometimes after a few folders and other times after copying for more than 20mins. 

Essentially, i really can't trust the grsync.

So I would like to see whether i can use rsync command via a script and make it run as a cron job so that whenever the contents of my source folder changes, it copies the changes to the network drive. (may be using smb mount for the usb drive?)

Obviously, in the beginning of the copy, if the file exists in destination i want to ignore it.

Can someone please help me create the script and tell me how to run it as a cron job - I'm using gnome ubuntu 16.04.

---

### Post by kurt18947 on 2016-10-28
I'm not at all familiar with text based rsync though that's the most flexible and powerful.  I have tried 3 apps that are graphical front ends for rsync - Grsync, Lucky Backup and Unison. They all have their strengths & weaknesses. Lucky Backup will do either backups or sync. Unison appears to sync either locally or remotely and seems pretty straightforward to use. I don't see a way to implement rsync switches in Unison-gtk.  Lucky Backup does support adding rsync switches.

---

### Post by Dennis N on 2016-10-28
**cp -ru** may do the job. **-u** is the update option, which only copies files from the source that are newer (based on time stamp) than those on the destination, or that don't exist yet on the destination. 

Example:
```

cp -ru ~/photos/* /<path-to-destination>/
```

---

