---
title: "Deleting files in a mounted system doesn't go to trash"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by dnns123 on 2008-06-22
When I try to delete a file in my mounted harddrive, it says it can't locate the trash can and asks to permanently delete it. It wasn't like this is Fiesty and Gutsy. How do I make it like Gutsy again which makes a folder named .trash-dnns or something, or atleast move it to the Trash Applet. BTW, when I make a folder named .Trash-dnns it still doesnt move the deleted files there.

---

### Post by AndThenWhat on 2008-06-23
Will it work if you drag the file to the trash applet?

---

### Post by mevets on 2008-06-23
Sometimes this happens when the folder is really big. Does the same thing happen when you try deleting smaller files?

---

### Post by dnns123 on 2008-06-23
@AndThenWhat

No

@mevets

Yes

---

### Post by AndThenWhat on 2008-06-23
I believe this is because the files aren't located in the Ubuntu filesystem and therefore Ubuntu doesn't send them to its trashcan.  The only fix for that would be to drag the files to Ubuntu (your desktop for instance) and THEN drag them to the trash.

---

### Post by sisco311 on 2008-06-23
> **dnns123 said:**
> When I try to delete a file in my mounted harddrive, it says it can't locate the trash can and asks to permanently delete it. It wasn't like this is Fiesty and Gutsy. How do I make it like Gutsy again which makes a folder named .trash-dnns or something, or atleast move it to the Trash Applet. BTW, when I make a folder named .Trash-dnns it still doesnt move the deleted files there.
[http://ubuntuforums.org/showpost.php?p=5048171&postcount=4](http://ubuntuforums.org/showpost.php?p=5048171&postcount=4)

---

### Post by kaibob on 2008-06-23
> **dnns123 said:**
> When I try to delete a file in my mounted harddrive, it says it can't locate the trash can and asks to permanently delete it. It wasn't like this is Fiesty and Gutsy. How do I make it like Gutsy again which makes a folder named .trash-dnns or something, or atleast move it to the Trash Applet. BTW, when I make a folder named .Trash-dnns it still doesnt move the deleted files there.

Is this an NTFS or VFAT partition? If so, you can try the following:

1) Backup fstab.

2) Backup fstab

3) Add uid=1000,gid=1000 as options to the partition's fstab entry (see example below). 

4) Create a directory named .Trash-1000 in the partition's root.

5) Restart the computer.

Upon completion of the above, deleted files SHOULD be placed in a directory named files within the .Trash-1000 directory, and your Ubuntu desktop trash icon should show the deleted files. A panel trashcan does not always display reliably with this workaround. 

~~~

Example fstab entry
UUID=44B5-9621 /media/store vfat defaults,utf8,umask=007,uid=1000,gid=1000 0 1

---

### Post by ukripper on 2008-06-23
> **dnns123 said:**
> When I try to delete a file in my mounted harddrive, it says it can't locate the trash can and asks to permanently delete it. It wasn't like this is Fiesty and Gutsy. How do I make it like Gutsy again which makes a folder named .trash-dnns or something, or atleast move it to the Trash Applet. BTW, when I make a folder named .Trash-dnns it still doesnt move the deleted files there.

can you do this in terminal:
```
ls -al | grep .Trash*
```

you can try this as well:
> ls ~/.Trash | wc -l

if your trash exists

---

