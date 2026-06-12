---
title: "Problem while installing Ubuntu Restricted Extras (13.04)"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by ranjank on 2013-05-06
Hi,

I tried to install Ubuntu Restricted Extras packages via Terminal. While installing Microsoft EULA agreement page came. But I accidentally closed the terminal. Now when I try to install any pacakge or remove the following message comes. I can't install anything using Software Center too.Please help me to fix this problem

[ATTACH=CONFIG]242256[/ATTACH]
[ATTACH=CONFIG]242258[/ATTACH]

---

### Post by Cheesemill on 2013-05-06
Try doing...
```
sudo apt-get -f install
```

To accept the EULA in a terminal just hit TAB until the OK button is highlighted then hit ENTER.

---

### Post by ranjank on 2013-05-06
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it.
user@user-pc:~$

Getting same message sir.

---

### Post by wildmanne39 on 2013-05-06
Please try:
```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```
Thanks

---

### Post by ranjank on 2013-05-06
This is the output.

> user@user-pc:~$ sudo apt-get install --reinstall ttf-mscorefonts-installer
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it.
user@user-pc:~$ 



Not working :-(.

---

### Post by wildmanne39 on 2013-05-06
Check that multiverse, universe and restricted repositories are enabled, not sure where the fonts are located.

---

### Post by ranjank on 2013-05-06
Every repos are enabled. Can someone help me fix this via TeamViewer?.

---

### Post by varunendra on 2013-05-06
Just download the package from here : [http://packages.ubuntu.com/raring/all/ttf-mscorefonts-installer/download](http://packages.ubuntu.com/raring/all/ttf-mscorefonts-installer/download)
Then double-click to install.

If you are connected to internet, dependencies should be automatically taken care of. Otherwise you can individually download them from here : [http://packages.ubuntu.com/raring/ttf-mscorefonts-installer](http://packages.ubuntu.com/raring/ttf-mscorefonts-installer)

---

### Post by ranjank on 2013-05-06
Fixed on my own. The culprit was the Indian update server. After changing to to Main Server. It got installed automatically.

---

### Post by varunendra on 2013-05-06
> **ranjank said:**
> Fixed on my own. The culprit was the Indian update server. After changing to to Main Server. It got installed automatically.

Great! Please mark the thread as [SOLVED] now, it helps others looking for a similar problem. Thanks!

---

