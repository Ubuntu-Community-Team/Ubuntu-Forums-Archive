---
title: "Removing wine"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by ozbolt on 2008-07-26
There is no problem removing wine with sudo apt-get remove wine, but when I remove it there still remains those programs and I still cen't use space they use. So I want to remove it completly. I also have problems removeing by normal with wine.

---

### Post by wishyjr on 2008-07-26
firstly, you could try a 'complete removal' in synaptic.

also, wine creates a fictional C: drive under your home directoy (/home/name/.wine/) - note the period (.) before the folder, this makes it a hidden folder.

try deleting that folder also, that might free up the space you are looking for.

---

### Post by stevoo on 2008-07-26
well everything shoulb be in ~/.wine

if you remove wine the directory  should have been removed as well.
If not you can delete it yourself.

---

### Post by northern lights on 2008-07-26
Run ```
sudo apt-get autoremove
```to rid yourself of packages that have become unnecessary.

You could have unistalled wine with autoremove, i.e. ```
sudo apt-get autoremove wine
```and not only wine but also all dependencies (that are not required for other packages as well) would have gotten removed.

Further,```
sudo aptitude purge wine
```removes all related files.

As for those in your /home directory, you have to manually delete 'em (note: hidden).

---

### Post by pmlxuser on 2008-07-26
open home folder /home/<username>
vie hidden files [Ctrl+h]
delete .wine [folder in which wine programes are installed]

of you they go into recycle bin all out of your life 
if you use shift + del ;)

---

### Post by ozbolt on 2008-07-26
TNX all for help, that worked.

---

