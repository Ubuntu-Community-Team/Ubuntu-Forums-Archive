---
title: "unneeded packages"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by hammeraxe on 2008-07-29
when i install a program lots of dependencies are installed as well. now that i decide to remove a program only the program package is removed, but what about the other ones? i have a feeling that my harddisk is gradually filling up with unneeded stuff. is there a way to detect/remove the unneeded packages?

---

### Post by eightmillion on 2008-07-29
The program deborphan can get help you find unneeded dependencies for you.

---

### Post by tuxxy on 2008-07-29
If you are remving from command line, simply add a * to the command and it will remove the dependant file.  Example below.

> sudo apt-get remove firefox*

If your in synaptic it should do this for you.

---

### Post by SunnyRabbiera on 2008-07-29
also the command sudo apt-get autoremove is good too

---

### Post by hammeraxe on 2008-07-29
hey, thanks for the quick responses

---

### Post by Potatoj316 on 2008-07-29
also if you add and remove all your packages with aptitude (works the same as apt-get just substitute aptitude where you normally use apg-get) it will automatically remove unneeded packages.

---

### Post by hyper_ch on 2008-07-29
and you also might want to delete the downloaded .deb files. I think synaptic has an option somewhere.

---

### Post by Nepherte on 2008-07-29
> **hyper_ch said:**
> and you also might want to delete the downloaded .deb files. I think synaptic has an option somewhere.
I believe either
```
sudo apt-get clean
```
or
```
sudo apt-get autoclean
```
would do the trick.

---

