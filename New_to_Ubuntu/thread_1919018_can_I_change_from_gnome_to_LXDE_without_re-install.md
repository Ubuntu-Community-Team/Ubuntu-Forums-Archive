---
title: "can I change from gnome to LXDE without re-installing?"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by chickenPie4breakfast on 2012-02-02
I have ubuntu 10.10 with gnome and would like to have LXDE for a lighter running sytem - can I change quite easily or do I have to download another distro that comes with LXDE

---

### Post by lisati on 2012-02-02
You don't need to follow the convoluted advice in response to your question in the other thread. This should do the trick instead:
```
sudo apt-get install lubuntu-desktop
```
When you do that and log out, you will have the option of logging in useing lxde.

---

### Post by arochester on 2012-02-02
...and if you subsequently want to get rid of the Gnome bits and pieces look here: [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

---

### Post by chickenPie4breakfast on 2012-02-02
Thanks guys - never thought it would be that easy.

---

### Post by chickenPie4breakfast on 2012-02-02
hmm - but before I do that one more question!  
will my existing programs work or will they not be recognised by the LXDE environment - so I will have to re-install a lot of apps like g-note/qBittorent/xpad etc etc

---

### Post by kevdog on 2012-02-02
They will work since no part of the gnome packages were uninstalled.

---

### Post by chickenPie4breakfast on 2012-02-02
ok I did use the command advised 
```
sudo apt-get install lubuntu-desktop
```
but it started to also install a lot of programs like Abi-word etc etc  I just wanted the absolute basics of LXDE for it to work so I stopped it

---

### Post by anaconda on 2012-02-02
Yep. the lubuntu-desktop packake installs all applications that would come with the ubuntu lxde-cd  (is it lubuntu-cd ?)

---

