---
title: "Error unmounting external hard drives"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by jrsc109 on 2008-10-08
Hi all

I have two external hard drives.  I am able to mount them and use them as I want to.
However, I cannot unmount them.

If I try to unmount them using the context menu (i.e. right click and Unmount Volume) I get this error:

Error trying to unmount - org.freedesktop.DBus.Error.UnknownMethod.

If I switch the hard drives off, and re-mount them, additional icons are added to the desktop.

It's very confusing!

TIA for your help.

---

### Post by kpkeerthi on 2008-10-08
Not sure how to fix the dbus error. 

Meanwhile you may use command-line method to safely unmount the drives:
```
sudo umount <mount-point>
```

To find out <mount-point> type```
mount
```

E.g: if my drive is mounted to /media/disk, I would use ```
sudo umount /media/disk
```

---

### Post by vanadium on 2008-10-08
Do you have an up-to-date Ubuntu installation? There have been issues with removable drives like you describe (don't remember if it was Hardy or Gutsy), but these have been solved.

---

### Post by jrsc109 on 2008-10-09
Less than a month - Hardy Heron LTS - so I would expect it to be OK.  The command line works ok though.
Would be nice to be able to use the context menu as a simpler method.

---

