---
title: "Change permissions on files"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2008-08-23
How can I change permissions on read-only files...such as to add games to a folder for pingus

---

### Post by bobnutfield on 2008-08-23
> man chmod

This is the man page for the chmod command.  Explains it all.

---

### Post by ad_267 on 2008-08-23
Press alt-f2 and run "gksu nautilus" to get a root file browser so you have root permissions.

---

### Post by mali2297 on 2008-08-23
> **ad_267 said:**
> Press alt-f2 and run "gksu nautilus" to get a root file browser so you have root permissions.

Since it's Xubuntu, use
```

gksu thunar

```
instead.

---

### Post by fenian on 2008-08-23
If you download the games to your desktop you can move them to a protected folder using sudo.For example if you had a game named game.x downloaded to your desktop and wanted to move it to a protected folder (I don't know the path to your pingus game folder so I'll just use /usr/share/pingus/games as an example you will need to use the correct path)you could open a terminal and use the command...

> sudo mv ~./Desktop/game.x /usr/share/pingus/games

and it will move the file to the protected folder.

---

