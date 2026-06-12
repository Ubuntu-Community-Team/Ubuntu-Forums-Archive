---
title: "Classic is better for me"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by nolyfeking on 2013-05-17
I'm not new to linux or ubuntu. I have used it quite frequently, and recently decided to upgrade from 8.4 to 12.10, and im not liking the new desktop layout (especialy the unity bar). Is there a guide somewhere that i can follow to get the old task-bar set up back?

---

### Post by SuperFreak on 2013-05-17
If you go to login screen and click on the circle (or Ubuntu symbol?) it will give you a choice of opening different desktop Environments. One of them, I think Classic Gnome may give you an interface more to your liking. Alternatively you could install XFCE or Cinnamon

---

### Post by holycow131415 on 2013-05-17
Install xfce or mate DEs

---

### Post by nolyfeking on 2013-05-17
Thank you

---

### Post by SuperFreak on 2013-05-17
Cinnamon can be installed in terminal
```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon nemo
```


To install XFCE see [HERE]("http://www.ubuntukiller.com/2013/05/how-to-install-xfce-40-in-ubuntu.html")

---

### Post by uzumakifahim on 2013-05-17
I think you'll be much more comfortable with MATE desktop. To install MATE on ubuntu 12.10 just open the terminal and enter the following commands

```
sudo add-apt-repository "deb http://packages.mate-desktop.org/repo/ubuntu quantal main"
sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update
sudo apt-get install mate-core
sudo apt-get install mate-desktop-environment
```

For more details see [HERE]("http://www.noobslab.com/2012/11/install-mate-14-desktop-in-ubuntu.html").

---

