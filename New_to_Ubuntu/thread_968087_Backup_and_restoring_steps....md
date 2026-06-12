---
title: "Backup and restoring steps..."
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Innernet on 2008-11-02
From an older post, learned that to backup my 7.10 compfuser to a DVD I can go :

Places > Home folder > Ctrl H > Places > CD/DVD creator > Drag and drop all the home folders whose names start with a dot (if I want to backup the system only; all of them if I want to backup data too) and click "write to disk"

Questions:  Can someone check if I have it exactly right ?, and
If I end with a valid DVD backup; when I install a **blank** new hard drive in my machine, what will be the exact steps to transfer back the DVD contents to it, to end with an equally performing compfuser ?

Sorry, am not as skilled as you :(
Miguel

---

### Post by Paqman on 2008-11-02
> **Innernet said:**
> 
Questions:  Can someone check if I have it exactly right ?


Sounds pretty good.

One main point: this obviously won't back up anything outside of home that you've set up. This includes files like /etc/fstab, which is the list of what drives/partitions to mount, and can be handy to keep a copy of.

> 
If I end with a valid DVD backup; when I install a **blank** new hard drive in my machine, what will be the exact steps to transfer back the DVD contents to it, to end with an equally performing compfuser ?


You'll need to reinstall the system from the LiveCD as per usual. Re-create your user accounts in the exact same order as before. Or at least, make sure they have the same user id (UIDs can be seen in System > Admin > Users and Groups > User > Advanced, and you can set it yourself when you create a user)

Then just transfer all the backed-up folders/files into the user's /home. If you strike problems, double check that the user owns all files you've transferred in. Wrong file ownership is really the only thing that will trip you up here.

There are some automated backup solutions, like sbackup that can sort this all out for you.

Another good reinstalling tip is that Ubuntu can [create a list of all installed packages](http://ubuntuforums.org/showthread.php?t=261366) and reinstall them all in one step.

---

