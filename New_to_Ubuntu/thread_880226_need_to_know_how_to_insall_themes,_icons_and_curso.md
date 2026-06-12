---
title: "need to know how to insall themes, icons and cursor"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by jooking on 2008-08-04
can anyone help me on installing themes icons and cursors? ive been told just to drop it into the theme manager, but i dont know what to do. i need the details in everything, because i just started learning this. i have emerald as well as compiz, so i dont know what to do exactly. also, is it possible to use an ipod on ubuntu? for ex. putting music in it and running itunes and other things that r needed for an ipod. thanks for the help

---

### Post by Victormd on 2008-08-04
There are several types of themes (i.e. GDM, emerald) and each one is installed a different way. You can find the different themes [here]("http://www.gnome-look.org/index.php?xcontentmode=100"). Post back with the type of theme you want to install so we can give you step-by-step instructions... :)
As for using ipod, try Amarok...

```
sudo apt-get install amarok
```

---

### Post by jooking on 2008-08-04
ok i have the .tar.gz on my desktop, but there is also a .tar.gz.part for some reason. what do i do with the tar? the theme is for gnome.

---

### Post by SunnyRabbiera on 2008-08-04
> **jooking said:**
> ok i have the .tar.gz on my desktop, but there is also a .tar.gz.part for some reason. what do i do with the tar? the theme is for gnome.

If there is a .part file then its a file that is still downloading.
Make sure its download process finished.

---

### Post by jooking on 2008-08-04
is gtk the default theme thingy? if the file is gz, then do u go from system to preferences to appearance to install it?

---

### Post by SunnyRabbiera on 2008-08-04
> **jooking said:**
> is gtk the default theme thingy? if the file is gz, then do u go from system to preferences to appearance to install it?

Yes, GTK engines are what will change your theme.
But be warned some themes have source code only in them, just because a theme looks nice doesnt mean it will be easy to install.
and yes thats how you install themes, but also you can right click your desktop and select "change desktop background"
go to the "theme" tab and that is how you change your theme.
GTK mainly stands for The Gimp toolkit, its a graphical front end engine if you are wondering, in linux you will learn there are others too like QT.

---

### Post by cdaringe on 2008-08-04
i'll help address some of your other questions.
*to install cursors: 
-browse to your home folder.
-hold ctrl, and hit h. this displays all of the hidden files (to make any file or folder hidden, simply add a . to the beginning of it.)
-open the .icons folder (mine is at /home/cdaringe/.icons)
-drop your icon/cursor folders into here.
-menu, system, preferences, appearance, themes tab, customize button, and you should see your icons or cursors under their respective tabs

iTunes is not currently compatible with gnu/linux OSs, or with wine.  however, MANY PLAYERS DO OFFER IPOD SUPPORT.  Rythmbox offers many ipod features, and is very similair to itunes.  ive been able to transfer music, share my music library, etc w/ my friends ipods on my computer.  so you can definitely do it.

To activate it (if it's not activated by default)
-menu, sound and video, rythmbox
-Edit menu, plugins
-check DAAP support, mtp portable (particularly the ipod one :) ), and any other cool plugin thats not already checked...'cause there are a few
-plug your ipod into your computer, and it will show up in the left panel in rythmbox

---

### Post by Victormd on 2008-08-04
Hey jooking, just got back to this post. Looks like you should be good to go. Let us know if you run into any problems...

---

