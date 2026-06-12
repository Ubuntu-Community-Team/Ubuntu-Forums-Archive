---
title: "How to access my video files from windows through the videos folder on Ubuntu"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by Haecceity420 on 2012-02-03
So I just installed Ubuntu 11.10 to dual boot with my window 7. I've found the folder that contains all my videos by going to the file systems and then host folder, but I would like to access these videos simply by clicking the Main video folder. I allocated about 30 GB of space for the Ubuntu installation so transferring all the files to that folder wouldn't work because it will not fit.

Also, would it be possible to add this folder (called my DATA drive in windows 7) to my Devices in my Home Folder?

Thanks

---

### Post by thomasw_lrd on 2012-02-03
I think you need a symlink

ln -s 'location to link to' 'name of symlink'

First google search result

[http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html](http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html)

---

