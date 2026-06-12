---
title: "Running an app as root vs user"
date: 2017-06-05
forum: New to Ubuntu
---

### Post by automate-stuff on 2017-06-05
I have noticed that running gedit as root gives you more options in the menus vs running it as user....when I run it as root it is more complete...For example, When you run Gedit 3.18 as root , it gives you a menu bar with all the options, when you run it as user, the menu bar is gone...


is this the case fort all apps in Ubuntu ?

---

### Post by wildmanne39 on 2017-06-05
I am not sure if there is more options when running all apps as root because I have never done that, and it is very very dangerous it will leave your system vulnerable to attacks and if you make a mistake as root you will break your system or totally wipe it out, we do not allow discussing how to enable root on the forum for that reason but you can discuss the differences or dangers of doing so.

The way to get root privileges for installing apps in the terminal is by using sudo in front of the command and to open say gedit for example the safe way with root privileges the command is sudo -H.

---

### Post by LastDino on 2017-06-05
There is no difference with gedit when run as root or simple user for me at least. 

+1 to wildmanne

It is highly dangerous to run apps with root privileges, there is a reason as to why Ubuntu by default does not allow root privileges unless you request for it by "sudo" or "gksudo" for temporarily.

---

### Post by vasa1 on 2017-06-05
> **wildmanne39 said:**
> ... it is very very dangerous it will leave your system vulnerable to attacks and if you make a mistake as root you will break your system or totally wipe it out ...
Another +1.

I see your [other thread]("https://ubuntuforums.org/showthread.php?t=2362979") is also about using elevated privileges. And concern has been expressed there as well.

Anyway, all the best.

---

### Post by deadflowr on 2017-06-05
The difference in design is that Ubuntu is built to be run as a normal user and so it's menu system is called global where all the app menus are placed in the top panel of the desktop.
When running as root you lose that global menu system and thus the menus show in the app.

---

### Post by Impavidus on 2017-06-05
The menu bar should always be there, but when running it as ordinary user it may end op in the global menu at the top of your screen (I think, I use Xubuntu, so that's neither gedit nor global menu). But the global menu is run by the normal user, so it doesn't work for root applications, so that's why root gedit gets the menu back.

edit: Ninja'd. I type too slow.

---

### Post by deadflowr on 2017-06-05
> **Impavidus said:**
> The menu bar should always be there, but when running it as ordinary user it may end op in the global menu at the top of your screen (I think, I use Xubuntu, so that's neither gedit nor global menu). But the global menu is run by the normal user, so it doesn't work for root applications, so that's why root gedit gets the menu back.

edit: Ninja'd. I type too slow.

Yeah, I don't think anything outside of Ubuntu with the unity desktop has this feature.
Gnome shell has a sort of global menu, but it's fairly limited in design as most menu's consist of a few items such as quit and that's all.

---

### Post by vanillalumina on 2017-06-07
Not sure how to explain this easily, but sudo basically allows you to run more things because it is the root user, the administrator, most of the time you are running Ubuntu you are running in normal privileges (which are restricted), similar to Microsoft Windows UAC system except better of course ;)

It's like that for security reasons, and it's pretty effective. ^^

---

