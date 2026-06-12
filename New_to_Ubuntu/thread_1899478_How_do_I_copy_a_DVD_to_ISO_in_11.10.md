---
title: "How do I copy a DVD to ISO in 11.10?"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by diablo75 on 2011-12-23
I have a DVD a friend made of my recent wedding and I'm trying to rip a copy to ISO for backup.  But there doesn't seem to be a simple way to do this anymore.  I remember I used to be able to right-click on the disc icon and say "Copy to image" or something like that, but I can't remember the last time I did that.  Is that feature still available somehow?  I tried using Brasero but it seems to think the total size of the data on the disc is only 23 MB when it's really almost 1 GB in size.  Ultimately I'd like to copy this to a standard physical sized DVD since you can't stick these 3 inch discs into a PS3.

---

### Post by halitech on 2011-12-23
Unless they've changed it, you could try K3B and use the copy disc option and select the make an image only. Then select where you want to save the image.

---

### Post by diablo75 on 2011-12-23
k3b did the trick.  I had to squint to see the "Copy Image Only" checkbox but it was right under my nose.  Thanks for your help!

---

### Post by GWBouge on 2011-12-23
Seems the feature is still there, but you have to Right-Click on the mounted folder to do it, so you have to be in the /media directory.

Click on the Device in the left pane
Go up one directory.
Right-Click -> Copy Disc
Select -> Image File

May have to click the Properties button and select the ISO image type, mine seems to default to a .toc.  Seems pretty round-a-bout, though ... may just be easier with k3b or a 'cat' command, ha.

---

