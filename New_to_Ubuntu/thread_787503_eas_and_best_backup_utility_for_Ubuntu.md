---
title: "eas and best backup utility for Ubuntu?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by TMcKSmith on 2008-05-08
So in the past month I've had a laptop stolen, and a hard drive die on me.  Are there any simple programs out there in the Ubuntu repositories that are a quick and easy way to back up my hard drive?  Preferably something that'd let me plug in my laptop to my 750gb external drive and have it copy an image or something of my entire laptop drive that could easily be restored on a new computer?  Any suggestions would be very helpful

---

### Post by inportb on 2008-05-08
If you want disk images, dd seems to be a nice solution:

dd if=/dev/hda of=/path/to/file

restore:

dd if=/path/to/file of=/dev/hda

(where /dev/hda is your harddrive)

---

### Post by Tatty on 2008-05-08
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

try those links.  Or there is Ghost for Linux: [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

But i have never used any of these myself, so i cant offer any advice on the merits of each one

---

