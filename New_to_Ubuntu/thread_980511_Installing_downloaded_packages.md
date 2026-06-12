---
title: "Installing downloaded packages"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by POWMS on 2008-11-12
Total newbie here. I have downloaded QCAD zip file at work and I wish to install it on my Xubuntu notebook at home.
Do I unzip the tar file and use terminal to install?
If so what would I type into the terminal for it to find the unzipped folder?

---

### Post by jimmy the saint on 2008-11-12
Delete that file.  Open a terminal and use commands

```
sudo apt-get update
```

then

```
sudo apt-get install qcad
```

if it asks you if you want to proceed press "y" and enjoy qcad

edit:  Alternately you can use synaptic, but I cannot remember the xubuntu menu system so I can't tell you where it is.  Under System I think.

---

### Post by POWMS on 2008-11-13
Thanks Jimmy. I now have everything I need to work off Xubuntu.
If I do want to install a package from a downloadd zip (tar) file, how would I generally do that?
Unzip if first and install thru terminal?

---

