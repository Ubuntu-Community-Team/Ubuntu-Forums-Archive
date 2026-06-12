---
title: "Unity won't load, terminal doesn't work"
date: 2015-08-12
forum: New to Ubuntu
---

### Post by flex567 on 2015-08-12
After Installing Oracle VM virtualbox 5.0 ffrom official site, I can loggin to ubuntu 14.04 but it won't load unity and ctrl+t won't show terminal. How can I solve this problem?

---

### Post by v3.xx on 2015-08-12
Try a different desktop, add "Flashback".

Go to console (r-ctrl + F1) at the login screen and ..

```
sudo apt-get install gnome-panel
```

Reboot and choose flashback at the login screen by clicking on the icon at top right of screen.

See if that gets you anywhere.

---

### Post by flex567 on 2015-08-13
I just reinstalled ubuntu

Is there a more stable version of Oracle VM virtualbox in repo?

---

### Post by howefield on 2015-08-13
Think the one in the Trusty repository is 4.3.10.

Is it more stable ? <shrug> if 5.0 isn't doing it for you, you could try 4.3.30 from the virtualbox website. Btw, may have been a typo but it is Ctrl+Alt+t for terminal.

---

### Post by flex567 on 2015-08-21
> Think the one in the Trusty repository is 4.3.10. I didn't find it in Ubuntu software centre. How can I download it?

Here is one way to install but instructions for Ubuntu 15.04 which I have are missing?

[http://www.howopensource.com/2013/04/install-virtualbox-ubuntu-ppa/](http://www.howopensource.com/2013/04/install-virtualbox-ubuntu-ppa/)

---

### Post by howefield on 2015-08-21
From a terminal..

```
sudo apt-get update
```
```
sudo apt-get install virtualbox
```

should do it.

Make sure you uninstall the previous version first though.

---

