---
title: "How to prevent automount of USB Flashdrive partitions?"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by alfu on 2012-12-11
Now that USB flash drives are becoming larger, I have put 4 partitions on a flashdrive.  My problem is that they all mount on insertion, cluttering the screen with their windows. Using 'View/Sidebar/Tree', you only need one directory window open anyway, UNLESS you are trying to access unmounted volumes.

I have explored GParted and the Disk Utility to see if there is a flag or other parameter that I can set to prevent the partitions from automounting, but can't find anything.  I simply want them to be listed in the folder Sidebar, but not mounted.

Maybe setting the mount point from 'media' to 'mnt' might do the trick, but I can't find any way to control the mount point, either.

Also, it would be nice not to have to continually mouse up to 'View/Sidebar/Places;Tree' to switch between the mutually exclusive functionality of both of these views.

---

### Post by pqwoerituytrueiwoq on 2012-12-11
in xubuntu i go into the Settings Editor and click on "Removable Drives and Media" it is on the 1st tab

---

### Post by GordThompson on 2012-12-11
> **alfu said:**
> I have explored GParted and the Disk Utility to see if there is a flag or other parameter that I can set to prevent the partitions from automounting, but can't find anything.
On...

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

...I found a reference to automount settings in `dconf-editor`. Give those a try.

---

### Post by alfu on 2012-12-12
Thank you GordThompson and [pqwoerituytrueiwoq]("http://ubuntuforums.org/member.php?u=865458").  I will go into dconf-editor and give it a try.  

But first I am going to do an install of Xubuntu.  I burned a live CD and tried it, and while it does not give me the control I am looking for, at least it doesn't launch a snowstorm of partition windows the way Unity does: everything comes up in the same window, and I don't think you have to switch directory views from the menubar to get full functionality.  It solves some other issues as well that I won't mention here.  Overall, it looks very good.

Oh, and by the way, Xubuntu brings back scrollwheel switching of workspaces that was killed in Ubuntu 12.04!

OK, I have finished the install, and since I kept the mountpoints '/home' and '/usr' on separate partitions, and only formatted '/' during the install, everything is fine. Email and web settings transferred flawlessly.  Slight panic at not having wifi, but hardwired an ethernet connection, then Xubuntu went out and suggested all the drivers I needed.  So far, I like it very much.

---

