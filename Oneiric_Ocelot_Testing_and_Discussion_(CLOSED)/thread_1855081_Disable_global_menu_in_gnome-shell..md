---
title: "Disable global menu in gnome-shell."
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by praveenthivari on 2011-10-05
I am testing oneiric and have installed latest updates available and have added ricotz ppa for gnome-shell. 

When I log into gnome-shell I notice a global menu running in background of top bar of gnome-shell. 

It looks ugly. How do I disable it?

Have attached a screenshot which explains everything.
(Am using elementary viper theme)

---

### Post by cjnucette on 2011-10-06
I'm having the same issue, anyone?

---

### Post by cjnucette on 2011-10-06
Ok, Andrew from webupd8 told me this:

"As far as I know, the only way to do it for now is to disable Nautilus from handling the desktop (from GNOME Tweak Tool)."

And it worked but now handling files on the desktop is not posible anymore.

---

### Post by crdlb on 2011-10-06
You can also remove the appmenu-gtk3 package, but that will affect unity too, of course.

---

### Post by Jesus_Valdez on 2011-10-06
Try closing from System Monitor anything Unity related.

---

### Post by 23dornot23d on 2011-10-06
*I have removed global menus ...... I can now use my system again .... made it easier.*


[B]sudo apt-get remove  [indicator-appmenu]("https://launchpad.net/ubuntu/+source/indicator-appmenu")

________________________________

[/B][I]I do this as I mainly run Gnome-Shell  ....

but if you need them on UNITY ..... it will mean constantly adding and removing this ......[/I]

---

### Post by jbicha on 2011-10-06
...or just don't use a transparent themed top bar in GNOME Shell.

---

### Post by praveenthivari on 2011-10-08
Thanks for all your responses.
I am planning to send a bug report for this. Which package should it best be reported against?

---

### Post by Bowmore on 2011-10-08
There is already a bug reported on this issue:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/826771](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/826771)

---

### Post by P-I H on 2011-10-08
In my installation with an AMD Radeon graphic card, the problem was corrected by installing Catalyst 11.9. To install fglrx I used the method described on this page: [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

---

### Post by praveenthivari on 2011-10-08
@Bowmore. Thanks. I should have searched launchpad first. Anyway I subscribed to that bug and voted for it.

---

