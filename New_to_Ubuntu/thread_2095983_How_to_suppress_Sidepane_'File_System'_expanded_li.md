---
title: "How to suppress Sidepane 'File System' expanded listing?"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by alfu on 2012-12-18
Switching to Xubuntu has been an improvement over Ubuntu: I like getting the scrollwheel back to switch workspaces (or just mousing over to one!)

Also, Xubuntu is fully functional in Viewing the Sidepane as 'Tree'.  The humble user does not have to keep switching the view back to 'Places' ('Shortcuts' in Xubuntu) to find unmounted drives.

However, clicking on a drive on the desktop to open its directory window results in a fully expanded view of the 'File System' in the sidepane, which drives the directory of the partition of interest off the bottom of the window (if its name starts with G-Z), whereas the partition of focus is not expanded in the Sidepane.

I have tried turning this off by unchecking 'Default Icons/Filesystem' in 'Right click: Desktop Settings .../Icons' but it only removes the File System icon from the desktop.

---

### Post by audiomick on 2012-12-18
That would be Thunar as the file manager, wouldn't it?

I just had a look. I have it installed here, but don't use it.

Look in the menu that is probably called "view" in English. Mine is in German, so I am not sure. There is an entry for that side bar that offers "bookmark" or "tree". See if that changes things.

Keyboard shortcut is ctrl+b for bookmark, ctr+t for tree. I'm guessing that yours is set to tree.

---

### Post by LewisTM on 2012-12-18
You should try Thunar 1.6
[http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html](http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html)

The new version shows mountable drives on the tree pane and expands them in situ, without traveling to "File system", an genuine annoyance.

Cheers!

---

### Post by alfu on 2012-12-18
Yes, Mick, my view is set to 'tree' as I noted in the first post.  I find Thunar 1.23 allows me to use the 'tree' view for everything I need, but I don't care to look at all the obligatory folders in the File System.  Lewis, Thunar 1.23 does everything you mention in your post -- now if it does that WITHOUT expanding the File System in the sidepane (sidebar) I would upgrade to it. 

I notice that if I double-click 'Home' on the desktop to launch a directory window, the sidepane does NOT expand the File System.  But it DOES if I double click any other platter.

---

### Post by LewisTM on 2012-12-19
To reiterate, Thunar 1.6 doesn't expand the File system tree to display a mountable volume. So you should upgrade.

---

### Post by Frogs Hair on 2012-12-19
Here are the latest Thunar 1.6 features if interested.
[http://forum.xfce.org/viewtopic.php?pid=28190#p28190](http://forum.xfce.org/viewtopic.php?pid=28190#p28190)

---

### Post by alfu on 2012-12-19
OK, LewisTM, I will do so.  One of the update items listed in the link provided by Frogs Hair mentions "Select problems have been fixed."  I hope it does not include the multiselect in the directory listing if you click on the icon instead of the filename.

I thought that feature was a bug, and was incredibly annoyed at it, until I realized how to use it properly!

Update 121219: Upgrade to Thunar 1.6 failed.  After following the instructions in the link kindly provided by LewisTM, a reboot indicated I was still running 1.23, but now Synaptix reported 1.6 as the latest version (previously the installed version and the latest version were both 1.23).  After marking them for upgrade, Synaptix claimed it couldn't find enough of the files in the repositories to do the job, so it did not go through.

Wow, I sure do miss Mac system upgrades pre-OSX.  Backup the Preferences folder, start from a CD, wipe the System folder, drag a new System folder to replace the old one, then drag the old preferences back into the System folder, and reboot: you were done.

---

### Post by LewisTM on 2012-12-19
Did you install the Xfce 4.10 PPA as specified in the linked page? I wouldn't think so since Thunar 1.4 is the version provided by Xfce 4.10 (Thunar 1.23 is the version for Xfce 4.8 in Precise). Thunar 1.6 is actually a preview and will be part of Xfce 4.12.

In other words, in Xubuntu 12.04, you have to jump up two Xfce versions to get the latest Thunar. Progress sure goes fast :)

---

### Post by alfu on 2012-12-21
LewisTM: Ooops.  My bad.  I will go back and jump thru the required hoops.

That said, there is a little part of me that still believes that software with the design intent of making the humble user feel like an idiot is not good software.  I guess that comes from me being an early Macintosh adopter (1984), but the Linux world is slowly beating that out of me.  I will be a Normal in a few years ...

---

### Post by alfu on 2013-02-13
I upgraded to xubuntu 12.1, and the expanded File System problem not only remained, but all partition listings were duplicated both on the desktop and the sidepane!

So I followed the instructions to upgrade to Thunar 1.6 on
[http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html](http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html)
and everything went perfectly. I now have Thunar 1.62, and the *original* problem is solved.:) 

At present, my only gripe is the cursor arrow image on the browser icon in the launchbar: it makes me think I am hovering over it, and launch something else instead!

---

