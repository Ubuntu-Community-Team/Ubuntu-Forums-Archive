---
title: "how to enable repository"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by SchrodingerCat on 2013-09-13
How to 
[LIST=1]
[*]Enable the Universe and Multiverse repositories (for bumblebee and nvidia packages respectively ) by terminal?
[/LIST]

---

### Post by plucky on 2013-09-13
> **SchrodingerCat said:**
> How to 
[LIST=1]
[*]Enable the Universe and Multiverse repositories (for bumblebee and nvidia packages respectively ) by terminal?
[/LIST]

```
sudo nano /etc/apt/sources.list
``` and remove the # from the front of the respective lines.

Good Luck

Do what Mastablasta recommends for command line.

---

### Post by mastablasta on 2013-09-13
firstly don't use sudo with gedit use gksu instead
secondly gedit is a GUi applicaiton. if oyu are no in desktop bu tonly in terminal use nano instead. in that case it can be 
```
sudo nano /etc/apt/sources.list
```

---

### Post by Mephisto Pheles on 2013-09-13
For more info please read

Repositories/Ubuntu
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by deadflowr on 2013-09-13
> **SchrodingerCat said:**
> How to 
[LIST=1]
[*]Enable the Universe and Multiverse repositories (for bumblebee and nvidia packages respectively ) by terminal?
[/LIST]


Enabling either of those won't help get nvidia drivers.
You need to enable the restricted repos for that.
Easy way is to open software sources and check the restricted repos.
Or through terminal uncomment the lines for restricted.

And unless you're running Saucy(as of now the development branch of Ubuntu)
Bumblebee is available through a ppa and not part of the default repo system.
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

