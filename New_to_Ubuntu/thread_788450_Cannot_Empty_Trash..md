---
title: "Cannot Empty Trash."
date: 2008-05-09
forum: New to Ubuntu
---

### Post by noahTHEpurdy on 2008-05-09
I have two folders in my trash bin that were originally extracted from .rar's. When I empty the trash, they are not deleted, and when I chose to delete the individual directories, it gives me an error and says that I do not have the permission to do so. Any ideas?

---

### Post by TeoBigusGeekus on 2008-05-09
In Gutsy:
```
sudo rm /home/yourusername/.Trash/*
```

In Hardy:
```
sudo rm /home/yourusername/.local/share/Trash/files/*
```

---

### Post by gn2 on 2008-05-09
Press Alt+F2 then type ```
gksudo nautilus
``` and press enter.
You will now be able to empty the trash.

***This opens the file browser with full root privileges so be very careful what you edit or delete and close it immediately you are finished.***

---

### Post by tjwoosta on 2008-05-09
i had this problem a wile back and i had to use 
```
sudo rm -rf
```
instead of 
```
sudo rm
```

the -rf means
  -r for recursively (use this to delete directories rather than files)
and -f for force (it will force the deletion despite any errors)

to learn more about how to use any commands (including the rm command)  just do this
```

man <command>

```

where <command> is replaced by the command you are looking up (for instance)
```

man rm

```

hope this helps

---

### Post by nowshining on 2008-05-09
or 

sudo chown -R username:username pathtofolder

u don't need to insert the * part.

change username to ur username

or just chown ur /home/username/ folder.

---

### Post by noahTHEpurdy on 2008-05-10
> **tjwoosta said:**
> i had this problem a wile back and i had to use 
```
sudo rm -rf
```
instead of 
```
sudo rm
```

the -rf means
  -r for recursively (use this to delete directories rather than files)
and -f for force (it will force the deletion despite any errors)

to learn more about how to use any commands (including the rm command)  just do this
```

man <command>

```

where <command> is replaced by the command you are looking up (for instance)
```

man rm

```

hope this helps

Thanks bud!

---

