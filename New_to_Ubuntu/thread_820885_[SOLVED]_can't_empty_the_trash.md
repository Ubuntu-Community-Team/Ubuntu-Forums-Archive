---
title: "[SOLVED] can't empty the trash"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by ercferret18 on 2008-06-06
i guess i made a mistake, because i trasnferred some files from one user account to another, but those files were still owned by the first user. i moved them to the trash, which was the mistake. because now whenever i try to empty the trash i get a "permission denied" error. I cant take them out of the trash because i still get a permission denied error, and when i run nautilus as root, when i try to enter trash:/// it says that it can't find it. what can i do?

---

### Post by roccivic on 2008-06-06
[http://ubuntuforums.org/showthread.php?t=809237](http://ubuntuforums.org/showthread.php?t=809237)

Rouslan

---

### Post by SunnyRabbiera on 2008-06-06
the trash directory is a bit different now, open nautilus in superuser mode and hit ctrl+h to unhide hidden folders/files and make your way to /root/.local/share/Trash/files
that will have the trashcan data you need to erase.

---

### Post by sayakb on 2008-06-06
```
sudo rm -rf ~/.local/share/Trash/files
```

---

### Post by ercferret18 on 2008-06-06
> **roccivic said:**
> [http://ubuntuforums.org/showthread.php?t=809237](http://ubuntuforums.org/showthread.php?t=809237)

Rouslan

thanx, this worked. btw for LinuxIsInnovation... isn't sudo rm -rf dangerous or something???

---

### Post by sayakb on 2008-06-06
> **ercferret18 said:**
> thanx, this worked. btw for LinuxIsInnovation... isn't sudo rm -rf dangerous or something???

It is dangerous, unless you know what you are deleting! ;)

---

### Post by ercferret18 on 2008-06-06
oh, never mind lol

---

