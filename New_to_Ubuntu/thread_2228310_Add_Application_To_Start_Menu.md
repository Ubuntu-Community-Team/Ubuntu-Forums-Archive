---
title: "Add Application To Start Menu"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by Duke Nukem on 2014-06-06
OK, I give in, I've installed an app in Lubuntu 14.04 and I'd like to open it from the "start" menu (yes, I'm a Windows weenie).

I'm aware of [http://wiki.lxde.org/en/Main_Menu](http://wiki.lxde.org/en/Main_Menu) and [https://help.ubuntu.com/community/Lubuntu/Windows](https://help.ubuntu.com/community/Lubuntu/Windows) but it still does not work.

I've created a file in /usr/share/applications called Aptana.desktop:-

[Desktop Entry]
Version=3.0
Name=Aptana
Comment=Aptana Studio 3
GenericName=Aptana
Keywords=Internet
Exec=/usr/share/Aptana_Studio_3/AptanaStudio3
Terminal=false
Type=Application
Icon=/usr/share/Aptana_Studio_3/icon.xpm
Categories=Internet
StartupNotify=true

I've used cut 'n paste to set the exec and icon entries. I've compared it against Firefox.desktop (firefox does appear on start menu) and even re-arranged the order of my file entries to exactly match that used by firefox. Indeed, if I open a file explorer I can see my file, it has picked up the correct icon and if I double click on it then it launches the correct application. I'm therefore expecting it to appear on the start menu under "internet" but no sign of it in that menu or indeed any menu.

I have of course logged out and back in after the change (in fact done complete reboot).

TTFN,
   Jon

---

### Post by deadflowr on 2014-06-06
My categories all have
Categories=Place**;**
instead of 
Categories=Place
Don't know if that matters or not.

---

### Post by Duke Nukem on 2014-06-07
Ah, thought it was just a separator character. So I added the ';' to the end of the categories - and 'fraid it still doesn't work.

For a laugh, I took a copy of (and renamed) the firefox.desktop and edited the "Name" field and rebooted. Sure enough I saw my "new" item appear in the main menu under "internet" so I'm in the right folder. Just my own file that it ignores.

So next I cut and paste Categories and Keywords from firefox to my own :-

Keywords=Internet;WWW;Browser;Web;Explorer
Categories=GNOME;GTK;Network;WebBrowser;

Yay ! Now my item appears in the menu. So question is, what *should* I use for this app - it sure 'aint a WebBrowser as stated in my Categories ?

Also, what is the Keywords enty ? The documentation says this is "menu categories" but my menu does not have WWW, Browser, Web or Explore in it, so I'm confused.

TTFN,
   Jon

---

