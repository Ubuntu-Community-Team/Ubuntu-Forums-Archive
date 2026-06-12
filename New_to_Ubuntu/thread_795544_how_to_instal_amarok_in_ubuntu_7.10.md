---
title: "how to instal amarok in ubuntu 7.10"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by antoniusmeliala on 2008-05-15
i am using ubuntu 7.10, and when i try to install amarok, i always fail
when i type
      $ sudo apt-get install amarok
then it will display
      E : invalid operation amarok
i had download amarok 1.4.9.1 to my home directory, but still don't know how to make it work...

---

### Post by nowshining on 2008-05-15
double-click on the .deb file or if it's ins ource u'll have to install it..

u should be able to download it thru the repos...

in the menu find something called software  sources and from there check mark every repository except for source - click close and reload when asked to.

u can also use the TAB completion for names after install

u may have to TAB twice.

---

### Post by forestpixie on 2008-05-15
Open softweare sources in system admin menu - check the multiverse, universe and restricted repos, close and reload.

Try to install again
```
sudo apt-get install amarok
```

---

### Post by FreewheelinFrank on 2008-05-15
Add Midibuntu then Amarok's in Add/Remove.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

