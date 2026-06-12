---
title: "Help backing up files"
date: 2013-07-12
forum: New to Ubuntu
---

### Post by lostonubuntwo on 2013-07-12
I'm new to Ubuntu and trying to learn it.  I can't figure out how to backup a file to a system file.

---

### Post by VMC on 2013-07-13
What version of Ubuntu are you using? Is [Deja Dub Backup Tool]("https://wiki.gnome.org/DejaDup/Screenshots") what your looking for. If so, it can be found under System Settings.  I'm also unsure what your meaning is "file to system file".

---

### Post by sparklyprgs on 2013-07-13
I'd have to also recommend [DirSyncPro]("http://dirsyncpro.com/index.html"). It's pretty easy to setup but still gives you enough power to get a little technical with the way you backup.

The only issue I've seen is the version of Java pre-installed, but only on older Ubunutu versions. As long as you update to the latest version, the program work fine.

---

### Post by lostonubuntwo on 2013-07-13
I'm not really sure the version.  But I want to backup my .bashrc file so that I can change something in it.

---

### Post by oldos2er on 2013-07-13
```
cp .bashrc .bashrc.backup
```

---

### Post by deadflowr on 2013-07-13
You can use right-click options in the file manager(nautilus/home folder).
Simply right click on the file and select copy, then right click on an empty space in the window and select paste.
You'll get, by default, filename(copy). Use rename if a better name fits it for you.
If you want to replace the new file with the old just rename it again and you'll be asked if you want to replace the existing file.
Just say yes.

Sidenote: Because the .bashrc is a hidden file, it most likely won't show up at first.
Use either ctrl+h, or go to view/view options > show hidden files.

---

### Post by leclerc65 on 2013-07-13
Backup one or a few files doesn't mean you are safe.
Sometimes making some simple changes can be deadly (Computer won't boot, freeze, screen goes dark...)
I suggest using Clonezilla to back up whole system.
I keep data on another partition (using symlinks) so system and home partitions together take less than 7G, and 5 minutes to clone.
I also keep data on two partitions, one that I backup occasionally by cloning, the other - expendable - never. In both cases I copy, one shot
deal, to my external HDD files that I want to keep. 
You can download free Parted Magic, that includes Clonezilla and several more ...

---

