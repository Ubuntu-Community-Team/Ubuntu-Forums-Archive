---
title: "File paths / permissions really stoopid question"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by päikese on 2008-06-24
OK, I plug in a usb harddrive, "bing" there it is on the desktop. No worries. But when I want to paste to it or delete from it I get the whole "you aint allowed cos you dont have permission" thing.
However a second harddrive plugs in fine and I have complete permissions.
I have tried all sorts of sudo chmod 777 stuff to give myself permissions (which I shouldn't have to do because its my ***** harddrive and I should automatically have permission to use it. I paid for the **** thing!)
But using /media/External HD as the path doesn't work. 
So how do I find the correct path to a device and how can I have permission to use my HD automatically when it gets plugged in?
Please.
Please.
I did say it was a stupid question.

---

### Post by quinnten83 on 2008-06-24
is it an ntfs, ext3 or fat32 system.
I had a similar problem, and I installed ntfs-3g and it worked. I had some more tweaking to do with things that were in the fstab, but it cleared itself out and is now working.

---

### Post by päikese on 2008-06-24
I dont know, i right clickedproperties and it was about as helpful as a rubber spanner. How can I find out? It would be so easy with xp but its too late for that now....

---

### Post by hyper_ch on 2008-06-24
```

sudo fdisk -l

```

---

### Post by päikese on 2008-06-24
Ok that worked, I now know it is /dev/sdb1 and that it is ntfs. But sudo chmod 777 /dev/sdb1 still hasn't given me the ability to write or delete to it. What do I need to do next?

---

### Post by bluepowder7 on 2008-06-24
try "sudo chown -R paikese: /dev/sdb1"

---

### Post by Stefanie on 2008-06-24
```
sudo chown -R username:username /media/disk
sudo chmod -R 755 /media/disk
```

this worked for me. if your external hdd is not mounted to /media/disk but to another location you should change that of course. you can see the location in your address bar in the file browser.

---

