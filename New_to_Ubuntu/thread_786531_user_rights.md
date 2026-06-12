---
title: "user rights"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by fmpfmpf on 2008-05-08
i am using Ubuntu 8.04

i have a problem creating a new folder in Computer/Filesystem/etc/opt
i right click, and the "Create Folder" is grey in colour (unclickable)

is there a command i have to type in terminal so that i can create a new folder?
or is there any other methods?

thank you

---

### Post by TeoBigusGeekus on 2008-05-08
```
sudo mkdir /etc/opt/nameoffolder
```

---

### Post by fmpfmpf on 2008-05-08
thankkk yyoouuuu
:D:D:D

---

### Post by billgoldberg on 2008-05-08
It's easier to type:

```
sudo nautilus
```

this opens the file manager as root so you can create, delete, copy, paste as you please.

---

### Post by fmpfmpf on 2008-05-08
is there any command that gives me 100% power to do what ever i want to the system?

---

### Post by Tatty on 2008-05-08
sudo / gksu gives you superuser rights and this allows you to do whatever you want to the system.

You use sudo with text based operations, and you use gksu for graphical applications.  You do not have superuser powers all the time, you simply invoke them whenever you need to use them.  This is for security purposes - it stops malware/hackers from doing things to your system without you knowing.

I recommend you read this : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by fmpfmpf on 2008-05-08
i used sudo and created a new folder
then i copied smoe files into that new folder
the problem now is, i cant read the files in the new fodler
it says i hv no rights

---

### Post by Tatty on 2008-05-08
If you open a terminal and type ```
gksu nautilus
``` then it will open a version of nautilus (the file browser) with superuser powers.  

If you right click on a file and choose properties you can set read and write access.

---

### Post by hyper_ch on 2008-05-08
why do you want to create a folder there???

---

### Post by aysiu on 2008-05-08
It should be ```
gksudo nautilus
``` or ```
gksu nautilus
``` instead of *sudo nautilus*

---

