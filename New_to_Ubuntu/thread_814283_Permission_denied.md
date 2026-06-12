---
title: "Permission denied"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-05-31
im tryin to move a skin into the directory /usr/share/amsn/skins for amsn but i keep gettin an error telling me that "Permission denied" is denied. can someone please help me overcome this??

---

### Post by WRDN on 2008-05-31
To copy the file, you need root priviledges, so in the terminal, type

```
sudo cp [file] [location_to_copy_to]
```

e.g. sudo cp /home/user/Desktop/file.txt /usr/share

This example would copy file.txt to the share folder.

---

### Post by shifty_powers on 2008-05-31
or alt-f2 and then type

```
gksudo nautilus
```

to do it with nautilus ;)

---

### Post by betterthanjordan79 on 2008-05-31
ok well i want to copy a full folder which is called Futurosoft and is on my desktop to the destination /usr/share/amsn/skins...what would i put in for that??

---

### Post by sisco311 on 2008-05-31
Open your file browser as super user. Press Alt+F2 and type:```
gksu nautilus
```
For more info:[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Ripfox on 2008-05-31
gksu nautilus will give you root permissions temporarily to move or copy that folder. Like he said.

---

### Post by dracayr on 2008-05-31
sudo cp ~/Desktop/Futurosoft /usr/share/amsn/skins
or
gksudo nautilus

---

### Post by betterthanjordan79 on 2008-05-31
> **shifty_powers said:**
> or alt-f2 and then type

```
gksudo nautilus
```

to do it with nautilus ;)

thats man-that works perfect :)

---

### Post by sisco311 on 2008-05-31
> **betterthanjordan79 said:**
> ok well i want to copy a full folder which is called Futurosoft and is on my desktop to the destination /usr/share/amsn/skins...what would i put in for that??
```
sudo cp -r ~/Desktop/Futuresoft /usr/share/amsn/skins
```

---

### Post by shifty_powers on 2008-05-31
np's. glad to help :D

---

