---
title: "placing icons on the desktop"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Nickocosmicfatplanet on 2008-07-12
specifically, the trash icon. i deleted the panel on the bottom so i could use AWN, therefore removing my tiny tiny trash icon. is there any way i can replace it on my desktop? and i have custom icons for it, but they have seperate ones for an empty one and a full one, so does it automatically switch without me having to do anything?

---

### Post by Tim Sharitt on 2008-07-12
The easiest way is to run gconf-editor (hit Alt-F2 and type in gconf-editor). Click on apps --> nautilus --> Desktop and it will show a list of icons you can add and remove from the desktop.

---

### Post by Nickocosmicfatplanet on 2008-07-12
cheers! and what of the second part of my question?

---

### Post by monolux on 2008-07-12
I had the same problem!!!!

---

### Post by BLTicklemonster on 2008-07-13
I was going to say find Ubuntu Tweak and us it. It's easier than gconf-editor to me.

---

### Post by Tim Sharitt on 2008-07-13
I'm not sure about the trash icon. If you change the icon manually, then you will probably have to change it twice (once empty, once full). However, if you are installing an icon theme, everything is taken care of.

---

### Post by fenian on 2008-07-13
If you are using a custom icon set you can replace the trash icons from your home directory.Open your home directory and choose show hidden files from the view menu (or hit ctl+h) go to the folder named .icons ,any third party icon themes should be there.Go to the current theme folder,open the scalable folder,the empty trash icons should be in the places folder and the full trash icons should be in the status folder.

---

### Post by BLTicklemonster on 2008-07-13
Ubuntu Tweak

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Lots of stuff you can do, all in one nice place where it's easy to find.

---

