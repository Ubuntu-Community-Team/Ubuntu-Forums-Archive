---
title: "wastebasket directory??"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by raedbenz on 2008-07-29
hi, what is wastebasket's directory in order to be accessed from command line??
coz i have some file in it that cant be deleted it says about error in permission,
thanks

---

### Post by PmDematagoda on 2008-07-29
The directory you want is:-
```
~/.local/share/Trash
```

---

### Post by philinux on 2008-07-29
username/.local/share/Trash/files

There is also a folder called info in Trash.

---

### Post by raedbenz on 2008-07-29
neither in "info" of "files" i can see what is inside my wastebasket.
hints???
thanx

---

### Post by PmDematagoda on 2008-07-29
> **raedbenz said:**
> neither in "info" of "files" i can see what is inside my wastebasket.
hints???
thanx

Can you post the output of:-
```
ls -la
```
inside the files directory.

---

### Post by raedbenz on 2008-07-29
hi,,

```
raed@raed-laptop:~/.local/share/Trash/files$ ls -al
total 8
drwx------ 2 raed raed 4096 2008-07-29 12:07 .
drwx------ 4 raed raed 4096 2008-07-16 11:55 ..

```
```
raed@raed-laptop:~/.local/share/Trash/info$ ls -al
total 8
drwx------ 2 raed raed 4096 2008-07-29 12:07 .
drwx------ 4 raed raed 4096 2008-07-16 11:55 ..
-rw-r--r-- 1 raed raed    0 2008-07-25 19:53 disk.trashinfo
-rw-r--r-- 1 raed raed    0 2008-07-26 10:19 etch.trashinfo
-rw-r--r-- 1 raed raed    0 2008-07-21 09:27 mod.trashinfo
-rw-r--r-- 1 raed raed    0 2008-07-16 23:58 tmp.sEiQeR5585.trashinfo

```
and here is my basket:[ATTACH]79335[/ATTACH]
cheers

---

### Post by jjlido on 2008-07-29
when I have empty wastebasket there are no files in Trash/info folder.
Try to move what you have in the info folder somewhere and see if this fix.
I say move somewhere so you can step back in case of need.

---

### Post by Malta paul on 2008-07-29
Some times you can't delete a file from your trash bin because they are read only. You may find also that you can't change the file from 'read only' to 'write'!.

You don't need to use the terminal to remove them from the trash bin.

There are two trash bins located at:
User Trash:  /home/>username</.local/share/trash  
Root Trash:  /root/.local/share/trash

Both these trash directories contain two directories 'files' and 'info'
delete the items in these files, but DO NOT delete the two directories.

To access the Root trash use 'Alt+F2' type in >gksudo nautilus<
(also now be careful as you are permanently in root)  

Hope this helps:)

---

### Post by BDNiner on 2008-07-29
There are also hidden trash folders on your other harddrives. I can see that you have other drives mounted in nautilus. So you can open nautilus as root and browse to the other drives and display hidden files you should see another trash folder. there should be one for each mount point.

---

### Post by Ghliofris on 2008-08-20
I had to go in through terminal and chmod 777 to all the directories and sub directories before they could be deleted.

---

### Post by nynoah on 2008-08-20
easier way to do it would be to sign in using alt-f2 *gksudo nautilus*

---

