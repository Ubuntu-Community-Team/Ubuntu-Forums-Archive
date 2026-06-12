---
title: "[SOLVED] Annoying apps"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Java Geek on 2008-08-11
Hello, I previously installed windows programs with wine onto my computer with sudo, however, upon uninstalling it (again with sudo) the programs remain listed in the applications/other menu. The folders that once contained it are gone. Is there a way to make the menu option go away as well

thanks.

---

### Post by ZeldaFan on 2008-08-11
I am plagued by this problem too. It's almost haunting the way the stay in my applications list, lol. I've completely uninstalled WINE, physically removed the directories that WINE used, and whenever I end up reinstalling WINE those program entries come back. The programs do not reinstall, they just remain there as entries...its kinda annoying.

---

### Post by Crafty Kisses on 2008-08-11
There should be an option if you right click on the menu, you can edit the menus and you can uncheck anything you don't want to show up.

---

### Post by Java Geek on 2008-08-11
So... There is no way... That is very annoying. What about synaptic. Will that do anything?

---

### Post by Java Geek on 2008-08-11
> **Codename said:**
> There should be an option if you right click on the menu, you can edit the menus and you can uncheck anything you don't want to show up.

ummm.. no you cant. I have tried that because i am peviously a windows user. I use the XFCE Desktop and Xubuntu. You might be able to do that in GNOME though...

---

### Post by Java Geek on 2008-08-11
I have unistalled wine and deleted its folder (.wine) but the applications still show. any help?

---

### Post by mc4100 on 2008-08-11
First, press ALT+F2 ... and then type this:
```
alacarte
```
Then, on the left you will see the list of menus, click on the "other" menu and, on the right, un-check the stuff you want not to appear in the menu.

Edit: oops, just saw the info about you being a xubuntu user (and it was *obvious* ;)) so in that case, I don't know how to edit the menus!

---

### Post by drawhole on 2008-08-11
i'm not going to say i have a soltion but i mite be able to point ya in the right direction .... when i was looking thru dir's .... i found several .wine or wine.conf files/dir ... i don't remember where and i have to go back to work now on my break .... but i'll have a look when i get home ... i remember removing them somehow ... i had this issue as well...

---

### Post by Java Geek on 2008-08-11
alacarte did not work with xubuntu on ANY menu item.

---

### Post by vikramaditya on 2008-08-11
Sorry I can't help :( but this is precisely why I chose not to "import" any of my xp settings during installation & also why WINE will NEVER touch my lips.

I do think **drawholé** is probably on the right track.

---

### Post by unutbu on 2008-08-11
Perhaps one of these pages gives the answer: [http://forum.xfce.org/index.php?topic=2658.0](http://forum.xfce.org/index.php?topic=2658.0)
[http://ubuntuforums.org/showthread.php?t=418814](http://ubuntuforums.org/showthread.php?t=418814)

---

### Post by Java Geek on 2008-08-11
> **unutbu said:**
> Perhaps one of these pages gives the answer: [http://forum.xfce.org/index.php?topic=2658.0](http://forum.xfce.org/index.php?topic=2658.0)
[http://ubuntuforums.org/showthread.php?t=418814](http://ubuntuforums.org/showthread.php?t=418814)

The second one did it. ~/.local/share/applications/wine/Programs and delete what you dont want. Thanks!

---

### Post by txcrackers on 2008-08-12
Try looking in *$HOME/.config/menus/applications-merged*, as well.

---

### Post by b9k9kiwi on 2008-08-12
> **Java Geek said:**
> So... There is no way... That is very annoying. What about synaptic. Will that do anything?

The previous post from Codename pointed you in the right direction.

Right-click on the menus panel (Applications Places System) on the left hand side of the top panel.  Choose 'Edit Menus' from the pop-up dialogue and you can bring up and edit the Wine Menu so as to delete any now redundant entries.

---

### Post by drawhole on 2008-08-12
ok so i think this is the spot cant be sure as right now i do not have the problem but delete the links from ~/.local/share/applications/wine as su probally the same but for root /root/.local/applications/wine but i'm not 100% worth a shot..

---

### Post by aimpau on 2008-08-12
go to your home folder, press ctrl+h and /home/(your username)/.local/share/desktop-directories

and delete whatever you want to delete.

---

### Post by Java Geek on 2008-08-12
Thank you all, but my last post was the answer to the problem. The .locals file in $HOME held the problems I was experiecing. I pressed CTRL-H to access it. Then i went into WINE software. This post is SOLVED

---

