---
title: "problems installing stuff from the software centre"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by Carnivorum on 2013-03-08
Bs'd

I tried to install some programs, but because of a very slow connection I didn't succeed. 

Now, when I use a normal fast connection, when I want to instal something, flashplayer or VLC, then I get the message:   Previous installation has not been completed.  The installation could have failed bacause of an error in the corresponding software package or it was cancelled in an unfriendly way.  You have to repair this before you can install or remove any further software.

Clicking the "repair" button doesn't help.   What can I do about this?

---

### Post by slickymaster on 2013-03-08
Try these, one at a time:
```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get upgrade -y
```

What they'll do: the first will update your repositories, the second will try to reinstall any pending installations, the third will force install pending installations and the fourth will upgrade the system.

---

### Post by ibjsb4 on 2013-03-08
try

sudo apt-get -f install

---

