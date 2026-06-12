---
title: "upgrade help"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by DarinB on 2008-04-28
i upgraded didn't finish
no desktop icons they do flash then disappear
when try to upgrade run partial upgrade
then when i try can't upgrade gutsy to hardy with this tool

---

### Post by bobplano on 2008-04-28
If you want to do a network upgrade to hardy heron, the command 
```
gksudo "update-manager -c -d"
``` might work, although in your case, it sounds like there's some issue. 

go to your sources.list 

```
gksudo gedit /etc/apt/sources.list
```and change all the places where it says gutsy to hardy, then update normally

---

### Post by Jammin80503 on 2008-04-28
If that doesn't work, you can try installing with the CD. instructions are at the bottom of this page: [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

---

### Post by DarinB on 2008-04-28
what do you mean change??

---

### Post by bobplano on 2008-04-28
example of what I meant: 

(a sample from my own sources)

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) **gutsy**-security main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) **gutsy**-security main restricted universe

to 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) **hardy**-security main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) **hardy**-security main restricted universe

this is to tell it to update the packages from the hardy servers rather than the gutsy ones.

---

