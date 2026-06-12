---
title: "Several doubts in Ubuntu 5.04"
date: 2005-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Peter Alien on 2005-05-10
Hello,

can someone take me some doubts:

Can i access WinXP Pro FAT32 partitions with Ubuntu 5.04 ?

I wanted to install a new pack of cursors in Ubuntu and i read that i have to install them in /.icons , but this directory doesnt appear to me. What the . before the name of the directory means ? It's a hidden directory ?

What is the difference between the Terminal ans the Konsole ?

can someone tell me if Knemo exists for Ubuntu 5.04 ?


Many many thanks guys  :smile:

---

### Post by the_clown on 2005-05-10
How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write?
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

Next time post in another section, this is only for tutorials

---

### Post by Peter Alien on 2005-05-10
Ok the_clown, it was my first post, and oopppsss i posted in the wrong Section.

Many thanks for the Tip ;-) 

Dont you know the rest ?

---

### Post by Klin'Targ on 2005-05-10
> **Peter Alien]
Can i access WinXP Pro FAT32 partitions with Ubuntu 5.04 ?
[/QUOTE]
Yes, you can. Add this code to your /etc/fstab file```
/dev/<windows partition>     /mnt/windows    vfat    rw,umask=000     0   0
```<windows partiotion> is the location of your windows partition. You can change /mnt/windows to wherever you want the windows partition mounted (make sure this directory exists said:**
> I wanted to install a new pack of cursors in Ubuntu and i read that i have to install them in /.icons , but this directory doesnt appear to me. What the . before the name of the directory means ? It's a hidden directory ?
All directorys/files which start with a . are hidden. To show them, choose "show hidden files" in your filebrowser of choice, or use the command ```
ls -a
```/.icons is probably referring to ~/.icons (which resolves to /home/<your username>/.icons). /.icons is not normally a valid directory.
[QUOTE=Peter Alien]
What is the difference between the Terminal ans the Konsole ?
[/QUOTE]
Both are terminal emulators. Konsole uses QT, KDE widgetset (so it will have your kde theme). Terminal uses GTK2, the gnome widgetset (so it will have your gnome theme).
[QUOTE=Peter Alien]can someone tell me if Knemo exists for Ubuntu 5.04 ?[/QUOTE]
Yes, it does. It is in the universe repository. If you don't have that repository enabled, see the guide on repositories here: [http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

---

### Post by Peter Alien on 2005-05-10
Many many thanks Klin'Targ   :grin:  :grin: :grin:

***** stars

---

