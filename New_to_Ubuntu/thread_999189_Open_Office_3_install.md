---
title: "Open Office 3 install"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by WorriedMan on 2008-12-01
hello.world

there, now thats out of the way, I am currently running Ubuntu 8.10 on my work laptop. This is not my first taste of linux but this is my first time really using it.

I added the repository in "software sources" for openoffice, but thus far it has not shown any available updates.  Currently the system has O O 2.4 which of course came default.

Can anyone give me any suggestions?  I'm not afraid of command line if thats what it takes to get this moving.

---

### Post by LowSky on 2008-12-01
in terminal type
sudo apt-get update && sudo apt-get upgrade

---

### Post by aztektum on 2008-12-01
If you used this repo

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

there are no packages for it right now. They pulled them because they were too buggy. Supposedly it will be updated with the 3.0.1 release of OO3, but like many things on the internet, that could be mere speculation.

You could try it this method:
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/")

---

### Post by binbash on 2008-12-01
there are no repos for intrepid for openoffice 3. you have to manually download debs and install them

---

