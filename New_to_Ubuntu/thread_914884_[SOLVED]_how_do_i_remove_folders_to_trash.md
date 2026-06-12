---
title: "[SOLVED] how do i remove folders to trash"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by hazman on 2008-09-09
i recently tried install a program but it failed and left me with a folder on my desktop i can not remove [something about root permissions] when i looked in properies

---

### Post by sisco311 on 2008-09-09
open a terminal (Applications -> Accessories -> Terminal)
and run the following command to change the owner of the folder:
```
sudo chown -R $USERNAME: ~/Desktop
```then try to remove the folder.

---

### Post by clive littlewood on 2008-09-09
Hi

right click the file and go to properties.

In properties click the permissions tab and make sure the create and delete option is used.

This will allow you to the delete the file

Hope this helps

cl

---

### Post by hazman on 2008-09-09
in the properties box that option is not allowed as i'm not the owner tried sisco's way and says the directory does not exist plus my terminal seems to be broke since up grading to 8.10

---

### Post by bumanie on 2008-09-09
In terminal > gksudo nautilusYou should then be able to go to Places --> Filesystem (double click) and navigate to your desktop. gksudo is root in graphical mode - it should allow you to remove the folder. If not, post back.

---

### Post by elmoosecapitan on 2008-09-09
In the terminal if you are in the local directory containing the folder:
```
$ rm -r ./foldername
```
If you do not have permission:
```
$ sudo rm -r ./foldername
```or
```
$ chmod u+w ./foldername
$ rm -r ./foldername
```
If you have folders in the trash that you are trying to get rid up but do not have write permission:
```
$ cd ~/.local/share/Trash/files/
$ chmod u+w ./foldername
$ rm -r ./foldername
```

cheers

---

### Post by clive littlewood on 2008-09-09
He cannot get into the terminal

---

### Post by sisco311 on 2008-09-09
> **bumanie said:**
> In terminal You should then be able to go to Places --> Filesystem (double click) and navigate to your desktop. gksudo is root in graphical mode - it should allow you to remove the folder. If not, post back.
In xubuntu the default file manager is Thunar.
To start it as root press Alt+F2 and type:
```
gksu thunar
```

---

### Post by hazman on 2008-09-09
thanks sisco311 thats removed it but wheres it gone to cos it not in trash

---

### Post by bumanie on 2008-09-09
The -r operator removes the file from the filesystem without going to trash. I was only going to give you that sort of code as a last resort as if you make a mistake with that type of code the file you remove is not retrievable eg if you accidentally removed a system file, you would have to reinstall.

---

