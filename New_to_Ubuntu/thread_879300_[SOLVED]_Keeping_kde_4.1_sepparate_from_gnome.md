---
title: "[SOLVED] Keeping kde 4.1 sepparate from gnome?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-08-03
After recently installing the KDE 4.1 and having the hard job of removing everything it installed afterwards, is there anyway i can install it but make sure that i don't see any of the KDE applications from gnome? but to keep them completely separate of each other?

Thanks in advance,

Carl

---

### Post by kamitsukai on 2008-08-04
Thats a no then...?

---

### Post by kaboodle_fish on 2008-08-04
This [http://www.kde-apps.org/content/show.php?content=31025](http://www.kde-apps.org/content/show.php?content=31025) will keep you Gnome applications neat and tidy in KDE and I believe there is one also for keeping KDE applications under a menu heading in Gnome

---

### Post by kamitsukai on 2008-08-05
Thanks!

---

### Post by hyper_ch on 2008-08-05
well, you ahve all the kde4 settings in ~/.kde

So if you want to remove kde 4.1 completely then
(1) delete all the kde applications
(2) delete the ~/.kde folder
and it's gone.

But I guess that's not really what you asked for... :(

---

### Post by cdtech on 2008-08-05
If you use the Gnome desktop (like I do) try this:

Make a backup:
```
mkdir ~/.desktopbackup
cp -R /usr/share/applications/ ~/.desktopbackup
```

On a command line type:
```
for i in /usr/share/applications/kde/*; do echo "OnlyShowIn=KDE;" | sudo tee -a $i; done
```

You could also do the same with KDE by changing it to:
```
for i in /usr/share/applications/*; do echo "OnlyShowIn=GNOME;" | sudo tee -a $i; done
```

Hope this helps.........

---

