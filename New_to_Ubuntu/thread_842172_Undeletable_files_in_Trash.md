---
title: "Undeletable files in Trash?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by raccoonone on 2008-06-27
I have a folder in my Trash, synce-gnome-0.11, that I can't delete. When I click on Empty trash I get a permission denied error, and when I look at the file permissions I see that it's owned by root. How can I delete this folder? I tried searching the file system for the folder, but I can't figure out where the trash is stored, and hence I can't chown it to my username. I also tried running nautilus as root using "gksudo nautilus," but after doing that nautilus hangs if I try to click on the trash can.

---

### Post by iaculallad on 2008-06-27
> **raccoonone said:**
> I have a folder in my Trash, synce-gnome-0.11, that I can't delete. When I click on Empty trash I get a permission denied error, and when I look at the file permissions I see that it's owned by root. How can I delete this folder? I tried searching the file system for the folder, but I can't figure out where the trash is stored, and hence I can't chown it to my username. I also tried running nautilus as root using "gksudo nautilus," but after doing that nautilus hangs if I try to click on the trash can.

Try this using your terminal:

For User Trash:

```
sudo rm -rf /home/your_username/.local/share/Trash
```

or

For Root Trash:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by _sphinx_ on 2008-06-27
you can try he following command:
```
sudo rm /home/<user name>/.local/share/Trash/files/<filename>
```

---

### Post by raccoonone on 2008-06-27
Thanks! That's fixed it.

---

### Post by roswellgreens on 2009-06-17
EXCELLENT.... that worked like a charm--- UBUNTU 8.10 & 9.04

---

### Post by Nkosi on 2009-08-02
[quote=iaculallad;5271577]Try this using your terminal:
For User:
```
sudo rm -rf /home/your_username/.local/share/Trash
```or

 I tried several other tips elsewhere first, but your little bit of command line nailed my trash can problem in a flash. 50 Megs of junk are gone for the first time in 3 weeks. Awesome.

---

### Post by credobyte on 2009-08-02
> **Nkosi said:**
> [quote=iaculallad;5271577]Try this using your terminal:
For User:
```
sudo rm -rf /home/your_username/.local/share/Trash
```or

 I tried several other tips elsewhere first, but your little bit of command line nailed my trash can problem in a flash. 50 Megs of junk are gone for the first time in 3 weeks. Awesome.

Are you sure that *file* and *info* folders will be regenerated ?

---

### Post by cb951303 on 2009-08-02
they should figure out something about this whole permissions and trash thing. few days ago I've noticed my Trash directory is 20gb eventhough it's empty, turns out, all the files with messed up permissions stays in ".local/share/Trash/expunged" ...

---

### Post by cb951303 on 2009-08-02
> **credobyte said:**
> [quote=Nkosi;7721359]

Are you sure that *file* and *info* folders will be regenerated ?

yes, they are instantly regenerated.

---

### Post by credobyte on 2009-08-02
> **cb951303 said:**
> [quote=credobyte;7721433]

yes, they are instantly regenerated.

Ok, thnx ( haven't really dealt with these directories .. always using Nautilus ) :)

---

