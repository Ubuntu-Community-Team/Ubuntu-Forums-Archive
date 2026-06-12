---
title: "How to &quot;cd&quot; to a usb drive in ubuntu"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by ironhand41 on 2013-08-20
I'm trying to delete a locked folder on a very large usb drive that I use to back up a dual-boot (ubuntu/win7) pc. I need to delete the oldest back-up folder on this usb drive to obtain enough space to do another back-up.  I can open the terminal, but have no idea how to "cd" over to the usb drive. The usb drive is mounted because I can open it from the desktop and see the folders and I can open the folders too. But I have no idea how to "cd" to the usb drive so I can change permissions. I'm no stranger to command lines (cut my teeth on CP/M) but the Linux directory structure has me baffled. Perhaps I've posted this message in the wrong forum or whatever, so please forgive my protocol violation.  Thanks. Richard.

---

### Post by Cheesemill on 2013-08-20
I've moved this to it's own thread as it's a support issue.

USB drives are mounted in different locations depending on what version of Ubuntu you are using, you can get a list of all currently mounted partitions by running the command...
```
mount
```

You'll probably find your device mounted under /media somewhere.

---

### Post by TVTrukChik on 2013-08-21
Try "cd /media" then "ls".  That should show your USB drive. Then you can "cd" to it.

---

### Post by coldraven on 2013-08-22
You could run Nautilus in root mode then right click, select "Properties" then "Permissions".
Or try just right click then "Delete".
```
gksu nautilus
```

Edit: It would be better to select the folder and press the "Shift+Delete" keys. This will bypass the Trashcan and permanently delete the folder.
       Make sure that you select the correct folder, after this there is no un-delete !

---

### Post by nerdtron on 2013-08-22
This command will should you disk partition and the directory on where a particular drive is mounted.
```
lsblk
```
It has an output like this.
```
NAME             MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb                8:16   1   7.5G  0 disk 
&#9492;&#9472;sdb1             8:17   1   7.5G  0 part /media/kenneth/224a0502-0aa2-4584-91d2-4dade0ce6db5

```
That is my flash drive mounted on /media/kenneth/

---

