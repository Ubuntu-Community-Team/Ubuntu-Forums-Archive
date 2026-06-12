---
title: "[SOLVED] Cant emty file from Trash....permision denied"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2008-07-23
I have 1 file that I cant remove from trash.it comes up with a "permission denied" error. It is a big (400Mb) PDF file with multiple directories. Even if I go into the individual directories, I am unable to delete the individual files....

I have no trouble in deleting other files in trash, just this  one

---

### Post by Joeb454 on 2008-07-23
You could hit Alt+F2 and enter ```
gksudo nautilus
``` then browse to the trash directory and delete it.

Using that command gives you root privileges in the file browser (until you close it). So take care!!

---

### Post by pastalavista on 2008-07-23
That happened to me once. I restored the file to its original location and then deleted it from there, by-passing the trash, [shift-del]. It worked for me, but then, I'm lucky like that haha.

---

### Post by Rolcol on 2008-07-23
Another solution would be to change the permissions of your trash folder.


(This is if you have Hardy)
```

cd ~/.local/share/
sudo chown -R $USER Trash/
```

---

### Post by iaculallad on 2008-07-23
Or use your terminal to empty the Trash:

User's Trash:

```
sudo rm -rf ~/.local/share/Trash/*
```

Root's Trash:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by Rolcol on 2008-07-23
> **iaculallad said:**
> Or use your terminal to empty the Trash:

User's Trash:

```
sudo rm -rf ~/.local/share/Trash/*
```

Root's Trash:

```
sudo rm -rf ~/.local/share/Trash/files/*
```
That would also delete the two folders that make up the trash.  The info folder and the files folder.  Would the user need to recreate the trash folders after?

---

### Post by drs305 on 2008-07-23
> **Rolcol said:**
> That would also delete the two folders that make up the trash.  The info folder and the files folder.  Would the user need to recreate the trash folders after?

No, they automatically are restored when new trash is created.

---

### Post by Ducatiboy Stu on 2008-07-23
> **Joeb454 said:**
> You could hit Alt+F2 and enter ```
gksudo nautilus
``` then browse to the trash directory and delete it.

Using that command gives you root privileges in the file browser (until you close it). So take care!!

This caused a big hang in nautilus......


sudo rm -rf ~/.local/share/Trash/*


That worked..

Thanks

---

