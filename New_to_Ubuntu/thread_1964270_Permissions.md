---
title: "Permissions"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by GuitarHero on 2012-04-23
I'm trying to install plugins for MuseScore.  I'm supposed to copy the .js files to /usr/share/mscore-1.2/plugins but when i drag and drop them it says I don't have permission.  How do I accomplish this?

---

### Post by Paqman on 2012-04-23
All the folder outside your home folder are owned by root. So you need to copy the files as root.

To open the file browser as root, hit Alt-F2 and:
```
gksudo nautilus
```
Or you could open a terminal (Ctrl-T) and use the mv command:
```
sudo mv /origin /destination
```

---

### Post by audiomick on 2012-04-23
The folder /usr belongs to root, so you wont be able to copy into there as your normal user. The way to do this using the GUI is to start an instance of the file manager, Nautilus, with root privileges. To do this, do the following in a terminal

```
gksudo nautilus
```

You will be asked for your password. Type it in, the one you use to  log on, and hit enter. The file manager will open. Copy the file to where it has to go, and then close that instance of Nautilus. Be aware that this instance of Nautilus is able to delete system files and all sorts of other destructive things, so don't mess around in there. Just use it for what you opened it for, then close it.

---

### Post by GuitarHero on 2012-04-23
Thanks guys! Worked like a charm.

---

### Post by audiomick on 2012-04-23
Cool. Have fun with it. ;)

---

