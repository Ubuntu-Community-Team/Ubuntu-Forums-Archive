---
title: "Rhythmbox Data"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by intense.ego on 2008-11-30
Is the data from Rhythmbox (e.g. song ratings, playlists, etc) stored in your home folder or in the application folder in the root? I am asking because I am about to install Intrepid, but don't want to lose all the playlists, etc. I have a home partition so if it is stored on /home it won't be a problem

---

### Post by BlueSkyNIS on 2008-11-30
I would also like to now this too.

---

### Post by nothingspecial on 2008-11-30
~/.gnome2/rhythmbox/playlists.xml

have a look there.

I`m pretty sure your safe but I`ve not tried it myself. That appears to be where your playlist information is stored.

```
cat ~/gnome2/rhythmbox/playlists.xml
```

to veiw

---

