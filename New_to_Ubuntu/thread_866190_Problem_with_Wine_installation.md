---
title: "Problem with Wine installation"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by pkj on 2008-07-21
Hi,
i had installed wine but somehow it has got deleted..
Now when i am trying to install it again via synaptic packet manager, i am getting this error
Following packages have unresolved dependencies.Make sure that all required repositories are added and enabled in the preferences

wine:
  Depends: libasound2 (>1.0.14) but 1.0.13-1ubuntu5 is to be installed
  Depends: libgphoto2-2 (>=2.4.0) but 2.3.0-0ubuntu4 is to be installed
  Depends: libgphoto2-port0 (>=2.4.0) but 2.3.0-0ubuntu4 is to be installed
 Depends: libldap-2.4-2 (>=2.4.7) but it is not installable
  PreDepends: dpkg (>=1.14.12ubuntu3) but 1.13.24ubuntu6 is to be installed

Need help to resolve this problem

pkj

---

### Post by Nano Geek on 2008-07-21
Try running this:```
sudo apt-get install libldap
```

---

### Post by Potatoj316 on 2008-07-21
try going to the wine website (winehq.com I think) and adding their repository to your list and trying to instal from that.  I dont know if it will work though

---

### Post by pkj on 2008-07-21
tried running sudo apt-get install libldap
but got this error

Couldn't find package libldap

pkj

---

### Post by Nano Geek on 2008-07-21
Sorry, try this instead. 
```
sudo apt-get install libldap2
```

---

### Post by pkj on 2008-07-22
the command works. However, installing wine still gives the same errors as stated in my earlier mail.

pkj

---

### Post by tech0007 on 2008-07-22
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

sudo apt-get update
sudo apt-get install wine

---

### Post by pkj on 2008-07-22
and if someone can tell me what this error line means

libasound2 (> 1.0.14) but 1.0.13-1ubuntu5 is to be installed

pkj

---

### Post by pkj on 2008-07-22
Thanks to Tech0007

Problem resolved and wine installed

thanks once again

pkj

---

