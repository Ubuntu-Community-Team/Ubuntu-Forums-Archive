---
title: "HOWTO: Change your KDM Theme."
date: 2005-05-13
forum: Outdated Tutorials &amp; Tips
---

### Post by bored2k on 2005-05-13
This is a quick and simple guide explaining how to change your KDM theme. The only requirements for this howto are:
[indent]a) KDM (duh!)
b) Konsole or any terminal window (duh![size=1]*x2*[/size])
c) A nice KDM theme to install (this is rocket science hard, leave now!)[/indent]

KDM themes are available at [**[color=green]KDE[/color] [color=orange]Looks**[/color]](http://kde-look.org/index.php?xcontentmode=40). 

Allright so let's get down to bussiness. I'll work using [[color=darkblue]**BlueTheme**[/color]](http://kde-look.org/content/preview.php?preview=1&id=21124&file1=21124-1.jpg&file2=21124-2.png&file3=21124-3.jpg&name=BlueTheme+KDM+Theme) as an example. Its available [**[highlight]here**[/highlight]](http://kde-look.org/content/download.php?content=21124&id=1).

1) KDM themes usually comes in .tgz or .bz2 packages. You unpack these using the tar command as follows:
[indent]* For .tgz, the command is ```
tar xzf themename.tgz
```
* For .bz2, the command is ```
tar xjf themename.bz2
```In our case, it's a .bz2 so we 
```
tar xjf 21124-BlueTheme-0.2.tar.bz2
```[/indent]

2) You can use the theme in your current directory or any you desire, but we are moving ours to /usr/share/apps/kdm/themes/
[indent]```
sudo mv BlueTheme /usr/share/apps/kdm/themes/ 
```[/indent]

3) We are now going  to edit the file that points kdm to the right theme direction with KWrite editor.
[indent]```
sudo kwrite /etc/kde3/kdm/kdmrc
```
Ok so go to Line 48 and 49. They read
[indent]> Theme=/usr/share/apps/kdm/themes/kubuntu[/indent]
UseBackground=true
You change "kubuntu" for your BlueTheme (or your theme name), and that is it :D ("UseBackground" must be set to **true**).[/indent]

 *** Another method is found **[here](http://www.kde-apps.org/content/show.php?content=22120)**

[CENTER][[IMG]http://img79.echo.cx/img79/1592/282fo.th.gif[/IMG]](http://img79.echo.cx/my.php?image=282fo.gif)  -----> [[IMG]http://img86.echo.cx/img86/1205/2112418xj.th.jpg[/IMG]](http://img86.echo.cx/my.php?image=2112418xj.jpg) [/CENTER]

---

### Post by hammett111 on 2005-06-09
No use background on mine bud just kubuntu. How do I stop that kubuntu screen from loading in the background when it goes from the login screen to the desktop?

---

### Post by pdk001 on 2005-06-09
thanks for an useful tip

---

### Post by loboc on 2008-02-04
> **hammett111 said:**
> No use background on mine bud just kubuntu. How do I stop that kubuntu screen from loading in the background when it goes from the login screen to the desktop?
 
In Gutsy (7.10) you can disable the splash screen by going to KMENU>System Settings>Splash Screen and then select none.

By the way the package kdmtheme is supposed to do all this graphically but version 1.2 is broken apparently.

---

### Post by chritoph on 2008-04-21
Cross-Topic-Link where the solution may be found:
[http://ubuntuforums.org/showthread.php?p=4760073#post4760073](http://ubuntuforums.org/showthread.php?p=4760073#post4760073)

---

