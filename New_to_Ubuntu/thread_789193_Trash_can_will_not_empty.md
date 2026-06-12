---
title: "Trash can will not empty?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by kg4tah on 2008-05-10
My trash can appears to be empty because no files show up when I open it however it still says it contains 12 items and the icon will not switch to the empty trash can.  Any suggestions?

---

### Post by SunnyRabbiera on 2008-05-10
your trash applet might be having hiccups, I have bumped into this issue before.
do you have a desktop shortcut to trash though?

---

### Post by dRock1286 on 2008-05-10
Check and see if you have hidden files in it...That's my suggestion.  I had this problem and I have to open it as root to delete them...

---

### Post by SunnyRabbiera on 2008-05-10
also it light help if you logged out and back in again

---

### Post by onestep on 2008-05-10
The "Empty Trash" button does not highlight in mine either. I have to select all item(s) (Ctrl+A) and then press the "Delete" button to remove anything thats in the Trash Folder.

It's Annoying...

---

### Post by anjilslaire on 2008-05-10
Check your ~/.local/share/Trash/ directory. In the info directory, there is a .trashinfo file listed for every item in the trashcan files folder. Sometimes these get out of sync. 

Delete everything in both folders manually, but not the info and files folder themselves. 
Sudo may be needed if there's something wonky.
Then use the Trash icon as usual and Empty Trash if needed to erset the icon.

---

### Post by kg4tah on 2008-05-10
Alright I removed the items in those folders and did a reboot and the problem is fixed...... THANKS a lot!

---

### Post by cr0sh on 2012-08-18
I know this is a long dead thread, but I was experiencing this today on my 10.04 system; both home folders were empty, nothing in /root, etc - here is what I did to get the trash to empty, per this bug post:

[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/569724](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/569724)

Basically - if you used a usb drive (or other removable drive - heck, maybe any previously mounted but writable drive?) - and you deleted files off that drive, but -didn't- immediately empty the trash, then unmounted the drive - the trash icon will show the number of files left to delete (on that drive) - even though the "local" trash is empty.

To empty the trash icon - you have to plug that drive back in, mount it up, then empty your trash. I noticed on the drive I last was using that there was something like a /.Trash-100 in the root of the drive. I ended up deleting that directory off the drive because there isn't a good reason to leave it behind on the drive. I suspect that is where the trash on mounted drives goes to (and not on the local system - I wonder if there is a way to change this?).

So - by not emptying the trash immediately - the count gets out of sync (because it is reporting what was deleted on "other" now-unmounted drives, of course). What would be nice to know is -where- the count is stored on the system, to zero it out. Even better, would be some way to set a flag to move trashed files to the local trash file area, and not on the drive itself.

Hope this helps someone out there! Good luck!

:)

---

