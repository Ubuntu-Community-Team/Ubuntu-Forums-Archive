---
title: "Second (windows) partition seems to be inactive at Startup"
date: 2013-09-08
forum: New to Ubuntu
---

### Post by sebas2 on 2013-09-08
Hey,
I just installed my first Linux (Ubuntu 12.04) and I am actually quite happy with it. The only problem I'm having at the moment is a minor, but still kind of annoying one. At startup, a few things wouldn't work, for example my desktop background wouldn't appear or Dropbox couldn't find its folder. From what I've seen, the problem seems to be that these files (the picture, and the dropbox folder) are not on the Linux partition but on the parallel Win7 partition I still have. This partition seems to be inactive/unmounted at startup, and only becomes active as soon as I click on it for the first time. (Similarly, for instance all the bookmarks to picture folders only pop up after that). Is there any way I can change this, which does not require me to move it to the Linux partition?
Thanks, Sebas

---

### Post by carlwsnyder on 2013-09-08
Have you added your Windows partition to your /etc/fstab file?  This is the recommended manner to mount partitions/drives prior to reaching the desktop.

---

### Post by deadflowr on 2013-09-08
Did you try just installing dropbox onto the Ubuntu partition?
It is available for you in the software center.
And I don't know if just having the dropbox folder mounted from the Windows partition will do anything useful, like sync, since that's probably tied to the Windows OS.
And why not just move some pictures you like in your Ubuntu pictures folder?

It'll save you the neat and nifty adventure of trying to get The Windows partition set up in fstab.

---

### Post by Impavidus on 2013-09-09
In case you want to try the fstab route, here is some documentation: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Mark Phelps on 2013-09-09
IF you DO add the Windows partition to fstab, be sure to mount it read-only.  Mounting the Windows partition read-write and then making any change to it risks corrupting the filesystem.  And if that happens, Windows is likely to not boot after that.

---

