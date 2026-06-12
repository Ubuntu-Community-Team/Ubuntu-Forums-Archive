---
title: "Cannot get my DVD/CD drive to read"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by Sully_3118 on 2011-10-24
OK,
I have tried to read as many posts as possible so that I do not bother guys, but I can't find anything that truly identifies what I am having an issue with. Although, I am sure its in this forum somewhere, I'm just so new to both this forum and Ubuntu its ridiculous. I have installed software to allow me to watch a video; and rip it, but I am getting an error that the destination is invalid. How do I install my DVD/CD drive? Please bare with me, I am very new at GNOME/Debian OS's. Thanks in advance....

Sully

---

### Post by waynefoutz on 2011-10-24
try these commands in the terminal, then reboot:


```
sudo apt-get install libdvdread4
```



```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

