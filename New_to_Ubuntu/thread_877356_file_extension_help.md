---
title: "file extension help"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by steve228 on 2008-08-01
Im new to ubuntu and need help getting a program to work.  I have a program I am trying to use as a default when I download a file from the internet.  For example, I use Azureus and want to open a torrent with it, but I cannot find it when i search for it.  I am used to windows and its executable files (.exe)... What file extension can I look for or how can I get azureus to be the default torrent program through the "open with" dialog?

---

### Post by bks on 2008-08-01
The torrent files themselves should be a *.torrent, I believe.

---

### Post by mikewhatever on 2008-08-01
Executables in Ubuntu don't really have an extension. If you installed Azureus from Synaptic, the executable should be /usr/bin/azureus. To make sure torrent files get opened with Azureus, right click on a torrent file, Open with tab, and add the above path.

Edit: Double post!
[http://ubuntuforums.org/showthread.php?t=877339](http://ubuntuforums.org/showthread.php?t=877339)

---

### Post by bks on 2008-08-01
> **steve228 said:**
> [...]how can I get azureus to be the default torrent program through the "open with" dialog?

I'm not in front of my Ubuntu computer right now, but under System > Preferences there should be a Default Applications (may be called something slightly different) selection. From there you can set all your favorite applications to handle different actions.

---

### Post by kostkon on 2008-08-01
> **steve228 said:**
> Im new to ubuntu and need help getting a program to work.  I have a program I am trying to use as a default when I download a file from the internet.  For example, I use Azureus and want to open a torrent with it, but I cannot find it when i search for it.  I am used to windows and its executable files (.exe)... What file extension can I look for or how can I get azureus to be the default torrent program through the "open with" dialog?
You right click on the file, go to *Properties -> Open With* and then select *Add*. If you don't see the app you want to use in the list, then select *Browse* and search for the app yourself. Most executables are in the */usr/bin* folder.

---

