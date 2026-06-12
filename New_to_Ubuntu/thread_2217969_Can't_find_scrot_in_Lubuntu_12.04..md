---
title: "Can't find scrot in Lubuntu 12.04."
date: 2014-04-19
forum: New to Ubuntu
---

### Post by cheapodonuts on 2014-04-19
Previously running Ubuntu 13.1 but now I'm using Lubuntu 12.04 live disk due to an upgrade crash. I want to take screenshots to post on the forums but can't find 'scrot'. :confused:  Synaptic says it's installed but Software Centre doesn't list it as installed or available. :confused:

Thanx for any help you guys.

---

### Post by bapoumba on 2014-04-19
Do not know about the live session, but here is where you can find it on a regular install :)

---

### Post by cheapodonuts on 2014-04-19
Thanx bapoumba, but it isn't there.

---

### Post by bapoumba on 2014-04-19
Would
```
scrot scrot.png
```
work ? You'll have a full desktop screenshot in your /home. You can refine the options, see ```
man scrot
```

---

### Post by cheapodonuts on 2014-04-19
Woohoo! Thank you bapoumba, you are a :KS !! Interestingly, it made two images, one with the terminal in the middle and one without. But it'll do for me.

Have several donuts! :D

[[IMG]http://i81.photobucket.com/albums/j226/chashugh/donuts-3.jpg[/IMG]]("http://s81.photobucket.com/user/chashugh/media/donuts-3.jpg.html")

---

### Post by bapoumba on 2014-04-19
Thanks much, breakfast here, so donuts are most appreciated!

---

### Post by cheapodonuts on 2014-04-20
I didn't have any strawberries. :)

---

### Post by bapoumba on 2014-04-20
> **cheapodonuts said:**
> I didn't have any strawberries. :)

No worries :)

---

### Post by bapoumba on 2014-04-27
If you want donuts _with_ strawberries, I found this :
[http://ubuntuforums.org/showthread.php?t=1521606&p=9552908#post9552908](http://ubuntuforums.org/showthread.php?t=1521606&p=9552908#post9552908)

The icon path was not correct, I edited the /usr/share/applications/mtpaint-grab.desktop file a bit :

```
Desktop Entry]
Encoding=UTF-8
Name=Grab screenshot
Exec=mtpaint -s
Icon=camera
Type=Application
Terminal=false
Categories=Application;Graphics;
```

And included it in the Panel Application Launch Bar. It grabs the whole desktop, but then you can easily resize it to your needs.

---

