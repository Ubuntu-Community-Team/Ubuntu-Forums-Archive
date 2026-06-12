---
title: "How to remove using  'apt-get autoremove '"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Peterfc on 2008-07-03
I have been trying to get Realplay working and on a previous post it mentioned about going to a terminal and typing the following. 

sudo apt-get install helix-player mozilla-helix-player

I did this and got the following that i have pasted into this post. I now need to remove using apt-get. HOW

Thanks for reading this post.


peter@peter-desktop:~$ sudo apt-get install helix-player mozilla-helix-player
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
helix-player is already the newest version.
mozilla-helix-player is already the newest version.
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-core python-twisted-web
  libaccess-bridge-java python-bluez python-pgm python-avahi python-mutagen
  libgif4 python-daap tzdata-java python-pylirc libpigment0.3-4
  python-setuptools python-pkg-resources python-gpod python-twisted-bin
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
peter@peter-desktop:~$

---

### Post by iaculallad on 2008-07-03
On your terminal:

```
sudo apt-get remove helix-player mozilla-helix-player
sudo apt-get autoremove
```

---

### Post by Elfy on 2008-07-03
> **iaculallad said:**
> On your terminal:

```
sudo apt-get remove helix-player mozilla-helix-player
sudo apt-get autoremove
```

Why did you get the op to remove what he was trying to install - but already was, now he won't have helix player

> helix-player is already the newest version.
mozilla-helix-player is already the newest version.

should have been just 

```
sudo apt-get autoremove 
```

to get rid of the others :)

---

