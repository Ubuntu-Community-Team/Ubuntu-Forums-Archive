---
title: "How to create a Launcher"
date: 2011-07-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by doppel.ganger on 2011-07-30
How do you create a launcher in 11.10 Alpha 2? Is there a terminal command I can use?:confused:

---

### Post by 23dornot23d on 2011-07-30
gedit test.desktop


cut and paste the code below into it .....

```

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=gnome-panel-launcher
Name[en_US]=compiz --replace
Exec=compiz --replace
Name=compiz --replace
Icon=gnome-panel-launcher

```save the file to your desktop .....

right click on the icon ,,,,
change permissions to executable ......

Then it will become a Launcher ..

____________________________

What are they doing removing the right click on the desktop to create launcher 

The above makes life so easy now ..... progress . :confused:

---

### Post by jbicha on 2011-07-30
```
gnome-desktop-item-edit ~/.local/share/applications/ --create-new
```

---

### Post by VinDSL on 2011-07-30
> **23dornot23d said:**
> What are they doing removing the right click on the desktop to create launcher. 

The above makes life so easy now ..... progress . :confused:
My "*right click on the desktop to create launcher*" feature has been broken for quite a while.

I *assume* that they removed it from the desktop, until they have time to fix it - but, that's just a *guess*.

The way I used to do it was...

[LIST]
[*]Right-click on the desktop
[*]Choose create launcher
[*]Test the launcher on the desktop
[*]Once it works, move it from the desktop to /.local/share
[*]Then drag a copy from /.local/share to the Launcher Panel
[/LIST]

Hopefully, it will return soon...  ;)

---

### Post by walt.smith1960 on 2011-07-30
The cheatin' easy way at least on Gnome Classic no-effects.

Click applications, pick your app.  Click and _hold_ the mouse button. You should be able to drag to icon to the top bar a la Gnome 2.
[ATTACH]198883[/ATTACH]

---

### Post by jbicha on 2011-07-30
The explanation is in the changelogs. If you're going to be running the development release, it's good to read them. The menu item was confusing, wouldn't work in the default install, and upstream has removed it.

[https://launchpad.net/ubuntu/+source/nautilus/+changelog](https://launchpad.net/ubuntu/+source/nautilus/+changelog)

[HTML]nautilus (1:3.1.4-0ubuntu1) oneiric; urgency=low

  * New upstream version
  * debian/control.in:
    - don't Build-Depends on gir binaries which are pulled in by the libraries
    - drop libdbus-glib requirement, it uses gdbus
    - updated glib requirement
  * debian/patches/12_remove_create_launcher_on_desktop.patch:
    - dropped, the change is in the new version
 -- Sebastien Bacher  Mon, 25 Jul 2011 16:53:10 +0200

nautilus (1:3.1.3-0ubuntu3) oneiric; urgency=low

  * debian/patches/12_remove_create_launcher_on_desktop.patch:
    - remove the "create launcher" entry from desktop right-click. It's depending 
on a gnome-panel binary, confusing the user when unity is running and default 
upstream sessions don't have even nautilus drawing the icons on the desktop. 
Do the same for other places as well. (LP: #723861)
 -- Didier Roche  Mon, 25 Jul 2011 11:44:24 +0200[/HTML]

---

### Post by VinDSL on 2011-07-30
> **jbicha said:**
> ```
gnome-desktop-item-edit ~/.local/share/applications/ --create-new
```
Whoa!  Sweet!

It's back...  :D

Had to install it, but no big deal.

```

$ gnome-desktop-item-edit ~/.local/share/applications/ --create-new
The program 'gnome-desktop-item-edit' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-panel
$ sudo apt-get install gnome-panel
[sudo] password for vindsl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alacarte evolution-data-server gir1.2-panelapplet-4.0 gnome-applets
  gnome-applets-data gnome-panel-data gnome-session-fallback libebackend-1.2-1
  libedata-book-1.2-10 libedata-cal-1.2-12 libgweather-3-0 libgweather-common
  libpanel-applet-4-0
Suggested packages:
  evolution evolution-data-server-dbg gnome-netstatus-applet deskbar-applet
  cpufrequtils epiphany-browser desktop-base
The following NEW packages will be installed:
  alacarte evolution-data-server gir1.2-panelapplet-4.0 gnome-applets
  gnome-applets-data gnome-panel gnome-panel-data gnome-session-fallback
  libebackend-1.2-1 libedata-book-1.2-10 libedata-cal-1.2-12 libgweather-3-0
  libgweather-common libpanel-applet-4-0
0 upgraded, 14 newly installed, 0 to remove and 1 not upgraded.
Need to get 3,023 kB of archives.
After this operation, 19.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y

```

Thanks!

I'm gonna go play with it for a while...  ;)

---

### Post by VinDSL on 2011-07-30
> **jbicha said:**
> The explanation is in the changelogs. If you're going to be running the development release, it's good to read them.
True!

If there were 52 hours in a day, 24 days in a week, and 365 weeks in a year, I would read everything ever written.

I love to read and write (and code), but...

You're right.  We should prioritize our time more wisely.  ;)

---

### Post by VinDSL on 2011-07-30
Worked like a lucky charm...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/Screenshot at 2011-07-30 14:05:54(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot at 2011-07-30 14:05:54.png")[/INDENT]


Guess what the first Launcher I made was!?!?!?!

"Create Launcher"  :D

I had to changed the path slightly:

```

gnome-desktop-item-edit **[COLOR="Red"]/home/vindsl[/COLOR]**/.local/share/applications/ --create-new

```

The tilde (~) wasn't doing it for me.


I digress...


You might notice that I'm running Opera Next in the background.

I've been trying-to-like Opera since well into the last century - and I think they finally hooked me.

Been running Opera 12.00 pre-alpha for the last day, and they finally got it right.  LoL!

If you're reading this post, you're probably into pre-alphas, et cetera.

If so, you might want to give Opera 12 a whirl.  I have a *feeling* it's going to be a winner.

---

### Post by mc4man on 2011-07-30
> **VinDSL said:**
> 

I *assume* that they removed it from the desktop, until they have time to fix it - but, that's just a *guess*.

Hopefully, it will return soon...  ;)

I'd be surprised if they do, gnome/nautilus 3 doesn't 'see' much use in custom commands, most likely users will have to deal with themselves from the opposite dir.
Instead of 'use a custom command' or 'create  launcher' making a .desktop with a command of your choice, you'll just need to create the .desktop yourself.

(for real junkies of _desktop launchers_ you can simply make a launcher to open 'Create Launcher'

---

### Post by walt.smith1960 on 2011-07-31
> **jbicha said:**
> ```
gnome-desktop-item-edit ~/.local/share/applications/ --create-new
```

It may just be my install but when i try the above, I get a message that "gnome-panel must be installed".  Gnome-panel was removed when I did the latest update today and I cannot re-install.  A change not for the better.

---

### Post by drs305 on 2011-07-31
> **walt.smith1960 said:**
> It may just be my install but when i try the above, I get a message that "gnome-panel must be installed".  Gnome-panel was removed when I did the latest update today and I cannot re-install.  A change not for the better.

It's not just you. When I saw the list of packages that would have to be installed to run the command I decided I'd just modify existing launchers.

By the way, a lot of the default launchers are in /usr/share/applications

If you wanted to change the default icon of a major system app, for instance, you could make the change in the desktop file found in this folder. ** See *jbicha's* comment in next post.

---

### Post by jbicha on 2011-07-31
walt.smith, what specifically is the error you get when you try to install gnome-panel? Because it works just fine here.

drs305, I wouldn't recommend editing the .desktop files in /usr/share/applications directly. I believe when any of those apps are updated, you'll lose your changes. It's better to copy the .desktop to ~/.local/share/applications and edit the copies there. You don't need admin privileges either to do that.

I forgot to mention **alacarte**, the Gnome Menu editor. It also depends on gnome-panel but lets you change the categories and hide/show launchers in the menus (or in the Gnome Shell/Unity application lists).

---

### Post by mc4man on 2011-07-31
> **jbicha said:**
> 

I forgot to mention **alacarte**, the Gnome Menu editor. It also depends on gnome-panel but lets you change the categories and hide/show launchers in the menus (or in the Gnome Shell/Unity application lists).
I believe for many alacarte will not run, it seems to need an applications and settings .menu's in ~/.config/menus first
By default now that dir. is empty

(if alacarte crashes then copying those 2 files from a 11.04 install will allow alacarte to run

walt.smith - as mentioned, normally gnome-panel shouldn't be removed by anything, nor remove anything when installing...

Edit: after a bit of testing it would be better if those 2 menus where in /etc/xdg/menus
Then when alacarte is run as a user they will be created in /.config/menus
So this is another issue w/ gnome-menus

re-edit:
alacarte will be updated to not need a settings.menu

---

### Post by walt.smith1960 on 2011-07-31
> **jbicha said:**
> walt.smith, what specifically is the error you get when you try to install gnome-panel? Because it works just fine here.

drs305, I wouldn't recommend editing the .desktop files in /usr/share/applications directly. I believe when any of those apps are updated, you'll lose your changes. It's better to copy the .desktop to ~/.local/share/applications and edit the copies there. You don't need admin privileges either to do that.

I forgot to mention **alacarte**, the Gnome Menu editor. It also depends on gnome-panel but lets you change the categories and hide/show launchers in the menus (or in the Gnome Shell/Unity application lists).

I solved the problem via another thread. I lost Gnome-panel after an update this morning.  When I went to reinstall, Gnome-panel wouldn't install by itself.  When I installed Gnome-session-fallback (as I recall) Gnome-panel installed as one of three packages.  I don't know why it wouldn't install by itself but I now have Gnome 3, Gnome classic and Gnome classic no-effects on the start menu once again. These seems like a nice alternatives for the "I-hate-Unity" crowd.

---

### Post by mc4man on 2011-08-01
> **mc4man said:**
> I believe for many alacarte will not run, it seems to need an applications and settings .menu's in ~/.config/menus first
Blah, blah


A lot of things getting fixed today - as far as alacarte - 
"This bug was fixed in the package alacarte - 0.13.2-2ubuntu3"

---

