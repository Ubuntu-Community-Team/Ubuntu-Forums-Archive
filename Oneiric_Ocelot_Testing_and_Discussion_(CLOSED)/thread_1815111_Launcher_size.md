---
title: "Launcher size"
date: 2011-07-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tajreed on 2011-07-30
Can't seem to change the launcher size with compiz.

Anyone able to do that? Or is there a bug?

Thanks

---

### Post by drs305 on 2011-07-30
In compiz config settings manager (ccsm) go to Desktop and enable Ubuntu Unity Plugin. Do you have that option?

In the Experimental tab there is a laucher size slider. The min size is 32.

---

### Post by mc4man on 2011-07-30
While the launcher itself is only half functional, all of the settings in compiz > ubuntu unity plugin work fine here on 2 installs and todays iso in live session.

Can you change anything else like hide, backlight modes, panel opacity, ect.

If not, then are you sure you're in the unity session, not unity-2d instead?

---

### Post by tajreed on 2011-07-30
Yes, I've tried the Unity plug-in to change icon size to no avail. And when I log into OO, I use Unity. So I assume I have the 3-d version. I'm also testing in Virtual Box.

---

### Post by fjgaude on 2011-07-30
If you can rearrange the launcher icons then you are in 3D, if not then 2D. It is only in 3D that the size can be changed.

Ubuntu selects 2D if it detects the lack of sufficient video power to do Unity 3D.

---

### Post by tajreed on 2011-07-30
That's the problem. I'm in 2d even though I log in as Unity. Couldn't get 3d to work in natty either under VB.

Thanks to all for your responses.

---

### Post by philinux on 2011-09-13
> **drs305 said:**
> In compiz config settings manager (ccsm) go to Desktop and enable Ubuntu Unity Plugin. Do you have that option?

In the Experimental tab there is a laucher size slider. The min size is 32.

I'd prefer this to go smaller than 32. Anyone else think so?

I'm using a 22" wide screen monitor by the way.

---

### Post by drs305 on 2011-09-13
> **philinux said:**
> I'd prefer this to go smaller than 32. Anyone else think so?

I'm using a 22" wide screen monitor by the way.

+1 to both paragraphs.

---

### Post by Quackers on 2011-09-13
Use gnome-shell :-)
If you put enough launchers in there they go smaller

---

### Post by mc4man on 2011-09-13
> **philinux said:**
> I'd prefer this to go smaller than 32. Anyone else think so?

I'm using a 22" wide screen monitor by the way.
I believe there is a tech reason that they can't go smaller than 32, it was explained once in a natty bug on this.

---

### Post by lucazade on 2011-09-13
> **mc4man said:**
> I believe there is a tech reason that they can't go smaller than 32, it was explained once in a natty bug on this.

the tech reason is probably the overlay number when pressing windows/super botton and the progressbar on launcher tiles. They need some space to be enough big and readable.

in unity-2d tiles are hardcoded to 48px.. to get a 32px launcher i had to tweak some sources. (hope this and backlight control will land in unity-2d soon)

---

### Post by mc4man on 2011-09-13
> **lucazade said:**
> 

in unity-2d tiles are hardcoded to 48px.. to get a 32px launcher i had to tweak some sources. (hope this and backlight control will land in unity-2d soon)
if you ever get a chance to post which src file(s) are involved would be useful
I'd consider using 2d if that could be done (maybe..
(I think compiz is still several months + from being able to perform at a high level 'nicely'

---

### Post by lucazade on 2011-09-13
> **mc4man said:**
> if you ever get a chance to post which src file(s) are involved would be useful
I'd consider using 2d if that could be done (maybe..
(I think compiz is still several months + from being able to perform at a high level 'nicely'

of course... here you are.
the tar contains only different files from original one, it is based on 3.8.16 but it still work for newer release (both gtk2 and gtk3).
there are also the .png of the tiles reworked to look better when downscaled.

ps in Launcher.qml  I've commented some special launchers on the sidebar.. remove comments if you like them back
```
        items.appendModel(applications);
        /*items.appendModel(workspaces);
        items.appendModel(visiblePlaces);
        items.appendModel(devices);*/
        shelfItems.appendModel(trashes);
```

---

### Post by mc4man on 2011-09-13
> **lucazade said:**
> of course... here you are.
the tar contains only different files from original one, it is based on 3.8.16 but it still work for newer release (both gtk2 and gtk3).
there are also the .png of the tiles reworked to look better when downscaled.
Well that was/is interesting - 
!st - there is a .c file inc. that's no longer in source, (/panel/applets/indicator/indicator.c
Important?

Anyway - using the rest did get the smaller launcher, though with quite unexpected results, only 1 icon, Imgburn, that was actually 'Home Folder'
The rest were there but invisible - scr1
Did a debdiff, there seemed to be quite a # of changes.

Then just picked a few from a guesstimate perspective & things seem ok - scr.2
(excluded the artwork for the moment in both

If curious am attaching both debdiffs, interested as to what you think...

Additionally - if wanting to do a 36px. vs. current 32px.  are there any other values that need to be adjusted? (+4 ?

---

### Post by lucazade on 2011-09-14
> **mc4man said:**
> Well that was/is interesting - 
!st - there is a .c file inc. that's no longer in source, (/panel/applets/indicator/indicator.c
Important?

for oneiric not important, in natty was useful to override iconset for indicators (from ubuntu-mono-dark to faenza-dark).

> Anyway - using the rest did get the smaller launcher, though with quite unexpected results, only 1 icon, Imgburn, that was actually 'Home Folder'
The rest were there but invisible - scr1
Did a debdiff, there seemed to be quite a # of changes.

Then just picked a few from a guesstimate perspective & things seem ok - scr.2
(excluded the artwork for the moment in both

If curious am attaching both debdiffs, interested as to what you think...

Yep, those files in the tar were good for 3.8.16 so some things changed for recent revisions but more or less the files involved are the same.
in the changelog there was a better description of changes I made:

  /launcher/LauncherItem.qml (sourceSize.width: 32 from 48 )
  /launcher/LauncherList.qml (tileSize: 38 from 54)
  /launcher/Launcher.qml (blacklist workspace switcher, lenses, media)
  /libunity-2d-private/src/launcherclient.cpp (MaximumWidth = 50 from 66)
  /panel/applets/homebutton/homebutton.cpp (width: 45 from 61)  (only gtk2)
  /panel/applets/indicator/indicator.c (Faenza-Dark from ubuntu-mono-dark)  (only gtk2)
  resized png tiles for launchers

> Additionally - if wanting to do a 36px. vs. current 32px.  are there any other values that need to be adjusted? (+4 ?

just add +4 to the values mentioned above :)
happy hacking

---

### Post by lucazade on 2011-09-29
Refreshed the modded unity-2d launcher for natty, now it is in sync with daily ppa.
As soon as Oneiric will be released i'll tweak it and push as well into my [testing ppa]("https://launchpad.net/~lucazade/+archive/testing")

[URL="http://dl.dropbox.com/u/1338581/varie/Schermata.png"][IMG]http://dl.dropbox.com/u/1338581/varie/Schermatap.png[/IMG]
[/URL]
p.s. trashbin at the bottom looks strange.. 
edit: added unity-asset-pool in ppa with modified trash icon

---

### Post by lucazade on 2011-10-02
resized launcher also for unity-2d in oneiric.. it is available in my ppa as well ;)

[[IMG]http://dl.dropbox.com/u/1338581/varie/oneiricp.png[/IMG]]("http://dl.dropbox.com/u/1338581/varie/oneiric.png")

---

