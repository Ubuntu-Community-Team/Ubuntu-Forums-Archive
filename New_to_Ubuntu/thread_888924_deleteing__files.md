---
title: "deleteing  files"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by moondoggy17 on 2008-08-13
alright on my hard drive theres is a recovery partition i´ve got it all copied but theres one folder i can´t delete
[IMG]http://i105.photobucket.com/albums/m201/goemon17/Screenshot-1.png[/IMG]

---

### Post by Ryadt on 2008-08-13
Open nautilus as root```
gksudo nautilus
``` and delete it from there.

---

### Post by Sycron on 2008-08-13
type on a terminal
```
$ gksudo nautilus
```
go to your partition and delete it. Make [COLOR="Red"]SURE[/COLOR] you wont delete anything except that otherwise you may break your ubuntu box...

---

### Post by moondoggy17 on 2008-08-13
ty ty

---

### Post by moondoggy17 on 2008-08-13
ok ran into another deleting prob i´m trying empty my trash and the same files say ACCESS DENIED

---

### Post by Shazaam on 2008-08-13
BE VERY CAREFUL WHILE USING NAUTILUS AS ROOT!
gksudo nautilus again. Go to /home/yourusername/.local/share/trash/Files. Delete the recovery file(s). Then go to /root/.local/share/trash/Files. Delete the recovery file(s). If it makes a copy and doesn't delete anything highlight the file(s) and hit your Shift+Delete keys.
When you delete while root it is GONE! So be careful.

---

### Post by lukjad on 2008-08-13
Go to the terminal and type:
```
sudo rm -r ~/.local/share/Trash/files/
```

That way you don't have to do any drilling or opening of nautilus. Any, you can't make any misteaks. ;)

---

### Post by LeChacal on 2008-08-13
Not being mean but you know that you are deleting your winodws restore image right? And if you really want to do that it would be easier to just do an fdisk on that partition  and then reformat the partition with what ever file system you want on it.

---

### Post by moondoggy17 on 2008-08-13
well i made a copy of the restore disk on a dvd

---

