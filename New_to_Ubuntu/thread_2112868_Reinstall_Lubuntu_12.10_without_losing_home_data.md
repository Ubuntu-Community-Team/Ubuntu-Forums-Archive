---
title: "Reinstall Lubuntu 12.10 without losing /home data"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by stevesy on 2013-02-05
I'm having trouble getting Lubuntu 12.10 to boot up from a dual boot setup on my Inspiron 910.  It boots into a black screen and sometimes there's text output printed off down the screen followed by (or mixed in with) the lubuntu splash screen for a couple of secs, and then back to black screen.  I can only get out of it by doing a forced shutdown with the power button.

Before all this happened the session i was in had become sluggish, programs freezing and needing to close, error messages and so on.  I'd a fair bit open but this seemed odd.  It was at the point where I decided to install gimp and it said it was having problems writing such and such a file to disk for space reasons that i decided to shutdown, checked my diskspace on windows (which was ~1GiB) and booted up again  to see if the problem sorted itself out.  It didn't though..

I've no idea what i did/what went wrong and i've been extremely cautious using lubuntu so far, no crazy commands or deletions etc, so its very frustrating  :frown: 

Anyway, I tried repairing packages in ubuntu recovery mode which did nothing so i  left it at that as I'm unfamiliar with it.

I'm considering uninstalling ubuntu in windows and reinstalling it but I'd like to hang on to some of the data i've got in /home if possible, just some bookmarks and documents really and a package or two.  Most of my important data is on my external hd.. 

I read in a forum post that wubi can save a copy of /home data if you're reinstalling. Had a look at the wubiguide but am still not sure if this is possible.  When i click on the the wubi installation file it tells me that a previous installation has been detected and needs to be uninstalled, but it doesn't mention saving a copy of /home files and settings or anything, and i only have the option to uninstall or cancel.

Any light you can shed would be great, thanks.

---

### Post by bcbc on 2013-02-06
You're right that reinstalling will delete you current install completely. You can backup /home yourself beforehand.

Note that Wubi uses a fixed virtual disk so even if you have enough space on the host windows partition, you might still be low on space in the lubuntu install. Running df -h will show the space remaining on /dev/loop0 (that's the virtual disk).

There is a way to increase the space for Wubi, but if you're already short on space you may need to free up some first: see [http://askubuntu.com/a/107476/14916](http://askubuntu.com/a/107476/14916)

For the resize see: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk) or [https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)

PS if you need to force shutdown use Alt+SysRq R-E-I-S-U-B.

---

### Post by stevesy on 2013-02-06
> **bcbc said:**
> You're right that reinstalling will delete you current install completely. You can backup /home yourself beforehand.

Note that Wubi uses a fixed virtual disk so even if you have enough space on the host windows partition, you might still be low on space in the lubuntu install. Running df -h will show the space remaining on /dev/loop0 (that's the virtual disk).

There is a way to increase the space for Wubi, but if you're already short on space you may need to free up some first: see [http://askubuntu.com/a/107476/14916](http://askubuntu.com/a/107476/14916)

For the resize see: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk) or [https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)

PS if you need to force shutdown use Alt+SysRq R-E-I-S-U-B.

That's brilliant bcbc, thank you very much. : ]  I've only got a 15GiB internal hd so I might just do a full install from liveusb.  For now I'm going to try to workout how to backup /home.  I'll mark this thread solved as soon as I can.

---

### Post by bcbc on 2013-02-06
You can backup /home (you'll need to use tar to keep all the permissions etc.) and then reinstall and restore from the backup, overwriting /home. But it's best to play with it to make sure you get it right (unless you can find a good howto as it's not trivial). I tested it a while back in a virtual machine and have some commands from that somewhere (in an old thread).

But the nice thing you can do with Wubi is just to copy the entire root.disk to an external drive. You can always mount it and copy /home directly off it later. Or there's an option to migrate from the root.disk assuming it's fully functional (in other words, just short on space, not corrupt): [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)  (see the --root-disk= option).

Good luck.

---

