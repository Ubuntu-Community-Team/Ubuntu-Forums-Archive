---
title: "Error message that i hate"
date: 2006-01-31
forum: Repositories &amp; Backports
---

### Post by helrumyc1 on 2006-01-31
whenever i try to install the KDE enviorment (i hate GNOME) i constantly get a message saying there no pub key or something, this also happened with tryingto instal XFCE, which fortunatley i just got working as we speak through apt-get. Also when i use the terminal and i type: sudo apt-get update, it continuously sais i need to like update apt-get. Also, components in kde refuse to be installed, it always sais "Depend: blah blah blah, wont be installed" someone help me please, this is really really annoying

---

### Post by Ld. Ikon on 2006-02-27
u should try to download, the kubuntu iso... and install from there, should not be a big problem.

---

### Post by newuser111 on 2006-02-27
goto [http://www.kubuntu.org](http://www.kubuntu.org) and add the repos for the latest kde which is kde 3.51

the key warning is because you have to import the keys like it says on the site, if you dont then it will still work but you can ignore the complaints

---

### Post by aysiu on 2006-02-27
Sounds as if your sources.list has conflicting repositories.

Follow these directions to clean it up:
[http://www.psychocats.net/linux/sources](http://www.psychocats.net/linux/sources)

After that, do ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

Log out. Select **Session** and then **KDE** and log back in.

Once you've done that, if you really hate Gnome, follow [this tutorial to get rid of it](http://www.ubuntuforums.org/showthread.php?t=96046).

---

