---
title: "Fix for Gui / applications"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by pragmatic on 2012-09-08
Ok so you have installed 12.04 LTS and you want to get rid of the daft way that file, edit, view, history etc etc are missing from the application windows and for some insane reason are located in the top panel where sometimes they decide to appear and at other times not.   if like me you want to do something productive with this version open terminal and copy and paste the line of text ( posted below)  into the terminal and resolve this nonsense by returning to the way the previous versions of ubuntu worked which were disability /visually impaired friendly  anybody from the development team please note this. 12.04 fails the useable GUI test on VI suitability.

here is the comand line to resolve the issue ( better still it should be an option in the settings page )   starts here --->```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```<--ends here  copy everything between the arrows and then press return in terminal and then reboot  job done !

regards  Pragmatic

PS make sure also to disable the add on in firefox =  global menu bar integration !

---

### Post by vasilbelarus on 2012-09-08
If some body dislike new scroll-bars type it into gnome-terminal:
sudo apt-get remove overlay-scrollbar
then
sudo apt-get autoremove

---

### Post by Frogs Hair on 2012-09-08
[http://www.liberiangeek.net/2012/04/disable-the-global-menu-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/disable-the-global-menu-in-ubuntu-12-04-precise-pangolin/)

[http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html)

---

### Post by Epodx64 on 2012-09-08
I really couldn't find much I liked about Unity. KDE is the way to go IMO.

---

