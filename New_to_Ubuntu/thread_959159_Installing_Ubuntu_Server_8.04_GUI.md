---
title: "Installing Ubuntu Server 8.04 GUI"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by manuleka on 2008-10-26
i've just installed Ubuntu Server 8.04 - first time to go to server and i'm also a newbie to Linux... i get a comman line interface which i have no idea on the how-to... how can i get to GUI interface? like Gnome/KDE etc...

does Gnome come on the Installation CD? or is there a way of activating it if it's already installed? 

cheers for any help

---

### Post by louieb on 2008-10-26
No gui on the server edition.
to add
```
sudo aptitude update
sudo aptitude  full-upgrade
sudo aptitude install ubuntu-desktop
```

Have fun!

---

### Post by billgoldberg on 2008-10-26
I would recommend using apt-get instead of aptitude.

---

### Post by aggalitsas on 2008-10-28
I know you might laugh but i'm completely new.
Will installing ubuntu desktop the way you described format the hard drive? or there will be no effect? 

Thank you

---

### Post by linuxisevolution on 2008-10-28
> **aggalitsas said:**
> I know you might laugh but i'm completely new.
Will installing ubuntu desktop the way you described format the hard drive? or there will be no effect? 

Thank you

No, It will just add some apps and the fancy gui. Just like installing any application.  Good luck ;)

---

### Post by aggalitsas on 2008-10-28
> **linuxisevolution said:**
> No, It will just add some apps and the fancy gui. Just like installing any application.  Good luck ;)

thank you :)

---

### Post by Iowan on 2008-10-28
Depending on how much "stuff" you want, there is a "core" method (I've forgotten exact name) that installs the GUI without all the extra desktop accessories - like OpenOffice, Firefox, etc.

---

### Post by louieb on 2008-10-29
> **Iowan said:**
> Depending on how much "stuff" you want, there is a "core" method...
```
sudo aptitude install xorg gdm gnome-core
```

> These are the core components of the GNOME Desktop environment, an intuitive and attractive desktop.

This package depends on a basic set of programs, including a file
manager, an image viewer, a text editor, a sound recorder and other
useful tools.

> **billgoldberg said:**
> I would recommend using apt-get instead of aptitude.

:confused:

---

