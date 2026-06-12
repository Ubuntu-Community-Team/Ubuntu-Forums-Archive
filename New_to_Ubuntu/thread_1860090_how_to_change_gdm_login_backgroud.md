---
title: "how to change gdm login backgroud"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-10-14
there is a program to change the lightdm login background works great however i cant log in under lightdm(another thread i started)okay so using gdm how to i change the login backgroud. ubuntu tweak has an option that worked well in 11.04 but no longer works in 11.10. been searching for a couple of hours and cant find any answers. tks

---

### Post by crazy bird on 2011-10-14
Yes, there is a tool for it called gdm2setup. You can find it here: [https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)

---

### Post by sikander3786 on 2011-10-14
The simple old method might still work. I haven't tested it with Oneiric though:

[http://www.tuxgarage.com/2011/05/customize-gdm-plymouth-grub2.html](http://www.tuxgarage.com/2011/05/customize-gdm-plymouth-grub2.html)

Neither this one:

[http://www.tuxgarage.com/2011/08/changing-desktop-login-lock-backgrounds.html](http://www.tuxgarage.com/2011/08/changing-desktop-login-lock-backgrounds.html)

So, if you come to try any of these methods, please let us know if it still works.

Thanks.

---

### Post by rburkartjo on 2011-10-14
sik tried the second one get this error message -step4


ray@ray-GC660AA-ABA-SR5123WM:~$ sudo rm /usr/share/applications/desktop.*.cache
[sudo] password for ray: 
ray@ray-GC660AA-ABA-SR5123WM:~$ sudo sh -c "/usr/share/gnome-menus/update-gnome-menus-cache /usr/share/applications/ > /usr/share/applications/desktop.${LANG}.cache"
sh: /usr/share/gnome-menus/update-gnome-menus-cache: not found
ray@ray-GC660AA-ABA-SR5123WM:~$ 

note even though i get the above error it runs as suppose to however does change login screen

---

### Post by sikander3786 on 2011-10-14
> **rburkartjo said:**
> sik tried the second one get this error message -step4


ray@ray-GC660AA-ABA-SR5123WM:~$ sudo rm /usr/share/applications/desktop.*.cache
[sudo] password for ray: 
ray@ray-GC660AA-ABA-SR5123WM:~$ sudo sh -c "/usr/share/gnome-menus/update-gnome-menus-cache /usr/share/applications/ > /usr/share/applications/desktop.${LANG}.cache"
sh: /usr/share/gnome-menus/update-gnome-menus-cache: not found
ray@ray-GC660AA-ABA-SR5123WM:~$ 

note even though i get the above error it runs as suppose to however does change login screen
And what about the first one? That doesn't work either?

I would try to find a fix to it tomorrow possibly and would update you.

---

### Post by rburkartjo on 2011-10-14
sik didnt try the first. let me know if you find a fix. think it has something to do where 11.10 stores default login window. as stated before ubuntu tweak option use to work in 11.04 but not in this current release.tks
know there has to be a simple answer .

---

### Post by gordderp on 2011-10-14
> **sikander3786 said:**
> The simple old method might still work. I haven't tested it with Oneiric though:

[http://www.tuxgarage.com/2011/05/customize-gdm-plymouth-grub2.html](http://www.tuxgarage.com/2011/05/customize-gdm-plymouth-grub2.html)

Neither this one:

[http://www.tuxgarage.com/2011/08/changing-desktop-login-lock-backgrounds.html](http://www.tuxgarage.com/2011/08/changing-desktop-login-lock-backgrounds.html)

So, if you come to try any of these methods, please let us know if it still works.

Thanks.

I'm finding the way to change login screen, too.
The first method doesn't work either, since there is even no such file gnome-appearance-properties.desktop in 11.10......

---

