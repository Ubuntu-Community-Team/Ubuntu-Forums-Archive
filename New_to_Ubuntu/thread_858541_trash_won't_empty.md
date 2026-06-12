---
title: "trash won't empty"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by alien8predator on 2008-07-13
I have a folder in my trash that won't delete when I empty my trashcan. how can I delete it or if I log in with root,where is the trash folder exactly located? so I can delete the folder out of my trash?

---

### Post by drs305 on 2008-07-13
> **alien8predator said:**
> I have a folder in my trash that won't delete when I empty my trashcan. how can I delete it or if I log in with root,where is the trash folder exactly located? so I can delete the folder out of my trash?

In hardy, the trash is in ~/.local/share/Trash/files

In earlier versions, it's in ~/.Trash

As you guessed, login with "gksu nautilus" and browse to those folders to delete.

If you think there is other trash, you can do a search all of ubuntu with:
```
sudo find / -type d -iname Trash
```

---

### Post by Rallg on 2008-07-14
More than that: In recent updates to hardy, there is a problem emptying the trash under certain circumstances (particularly if a file is owned by root). It's a bug, reported. Symptom: CPU usage, lockup, slow response.

---

