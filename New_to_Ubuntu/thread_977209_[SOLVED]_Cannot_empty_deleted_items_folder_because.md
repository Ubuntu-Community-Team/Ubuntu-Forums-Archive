---
title: "[SOLVED] Cannot empty deleted items folder because of permissions"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by corkscrew on 2008-11-10
I have a couple of folders in my deleted items folder which contain jpg files. I cannot remove them because of the permissions. How do i navigate to the trash folder change the permissions and delete them?

---

### Post by Ryadt on 2008-11-10
Do ```
gksu nautilus
``` and go in the trash folder and delete the files.
Or do```
sudo rm -rf  ~/.local/share/Trash/*
```

---

### Post by corkscrew on 2008-11-10
Hey thanks a million this has driving me nuts!!
could'nt delete with nautilus but your second answer fixed it
why is it in nautilius that it shows the location as 
[ trash:///]

---

