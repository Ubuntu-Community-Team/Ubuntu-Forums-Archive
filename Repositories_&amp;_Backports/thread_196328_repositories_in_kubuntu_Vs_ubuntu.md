---
title: "repositories in kubuntu Vs ubuntu"
date: 2006-06-14
forum: Repositories &amp; Backports
---

### Post by rowck001 on 2006-06-14
I switched from ubuntu to kubuntu

I guess now I will be using adept for package management.
Do I need to replace all references to ubuntu with kubuntu in sources.lst

Can I still use apt-get in kubuntu?

---

### Post by aysiu on 2006-06-14
Ubuntu and Kubuntu use the same repositories.

You can use apt-get in Kubuntu. In fact, if you install Synaptic, you can use that instead of Adept.

---

### Post by bailout on 2006-06-15
Adept now seems to be working very well so there is no need to use synaptic in kubuntu.

---

### Post by aysiu on 2006-06-15
You mean Adept now warns you if it's going to remove packages?

---

### Post by bailout on 2006-06-15
The bar along the bottom shows how many packages are going to be added/updated/removed and if you click the Preview changes button on the toolbar it tells you exactly what it is going to do.

---

### Post by dresnu on 2006-06-17
You may want to insert the latest KDE 3.5.3 repository [http://kubuntu.org/announcements/kde-353.php](http://kubuntu.org/announcements/kde-353.php)
and amarok 1.4 [http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php) in your sources.list. These are official repos of the Kubuntu team.
You can also just add these lines```
## Latest KDE
deb http://kubuntu.org/packages/kde-latest dapper main

## Latest Amarok
deb http://kubuntu.org/packages/amarok-latest dapper main
``` in your sources.list which assures you to have the latest versions without having to re-edit the list everytime a new KDE or Amarok comes out.

Note: if you decide to upgrade KDE do an apt-get dist-upgrade because there's going to be alot of new packages, or even better use aptitude ;-)

---

