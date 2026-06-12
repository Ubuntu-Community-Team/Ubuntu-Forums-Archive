---
title: "[SOLVED] Weird Home Folder and Amarok problem"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by marko_4454 on 2008-11-04
So I have this weird problem that if I click Places-> Home folder, Amarok randomly starts playing some music. I dont really know why this happens. I started looking online and I found someone with the same problem:
[http://bugs.kde.org/show_bug.cgi?id=151968](http://bugs.kde.org/show_bug.cgi?id=151968)
Any help

---

### Post by marko_4454 on 2008-11-07
I still have this problem. Does anyone know? 
Thanks

---

### Post by marko_4454 on 2008-11-08
So the solution is the following:
[http://ge.ubuntuforums.com/showthread.php?t=964930](http://ge.ubuntuforums.com/showthread.php?t=964930)

1) Run;
```
sudo gedit ~/.local/share/applications/mimeapps.list
```

2) Replace the inode/directory=.... with:
```
inode/directory=nautilus-folder-handler.desktop;
```

---

