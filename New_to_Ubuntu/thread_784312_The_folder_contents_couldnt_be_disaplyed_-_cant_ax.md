---
title: "The folder contents couldnt be disaplyed - cant axx network drives"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Walc on 2008-05-06
Basiclly i cant axx 2nd pc in my network ( vista pc)

There r 2 ways i do it:

1/ places > network : i can see windows network but when clicking it i cant see a thing, it doesnt report back with any errors, just theres nth in that windows network.

2/ i have an desktop launcher too (nautilus smb://komputron). and when clicking it i have this 'folder content couldnt be displayed'

both of the above ways worked for me (from time 2 time, thats the thing)......

---

### Post by Walc on 2008-05-06
bump

---

### Post by Diki on 2008-05-06
I had a similar problem and had to change the workgroup for Ubuntu.
Open up terminal and:

```
sudo gedit /etc/samba/smb.conf
```

Find this and change the "workgroup" to whatever you named your network in Vista:

```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME
```

Save and reboot.

---

