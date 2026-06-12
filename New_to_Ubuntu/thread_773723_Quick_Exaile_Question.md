---
title: "Quick Exaile Question"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by westyonfire on 2008-04-29
Hey everybody,
I've recently discovered the tag editor Ex Falso; So, naturally I have been going through my music library re tagging music with a vengeance. The only problem is exaile does not remove the old songs linked to filenames that no longer exist. All my music is on an external hard drive so I've tried removing the hard drive from the library and then reimporting it but it still contains the old songs. How do I get rid of the old songs en mass? Is there a library file I can delete so i can import my hard drive music from scratch?
any help would be much appreciated.

---

### Post by alexandremrj on 2008-05-19
You can always delete the .exaile folder and as such delete all customization of it. When you next load it it will be like the first time and then you can import all library.

---

### Post by westyonfire on 2008-05-19
Would that not delete exaile? If programs arn't stored in files such as .exaile where are they stored?

---

### Post by RequinB4 on 2008-05-19
Go to Tools --> rescan collection.

May take a little bit depending on your library size

---

### Post by AndyCooll on 2008-05-19
If rescanning the collection doesn't work delete the music.db file in your .exaile folder

```
rm ~/.exaile/music.db
```
That doesn't remove Exaile it simply deletes the database which Exaile has compiled when you asked it to list your music. You can then rescan your collection again and it will compile a completely fresh database.
You could delete the whole .exaile folder but that will delete any plugins you've installed and settings you've applied too. Deleting the music.db just deletes the music database.

:cool:

---

### Post by westyonfire on 2008-05-19
Thank you! that worked. I now no longer have duplicates of songs that don't work. thanks again,.

---

### Post by Paqman on 2008-05-19
> **westyonfire said:**
> Would that not delete exaile? If programs arn't stored in files such as .exaile where are they stored?

The .exaile folder in your /home will only contain the config files. That's why a separate /home partition is such a popular way to set up your machine. It separates the user's data from the system files.

---

### Post by westyonfire on 2008-05-19
Sweet. So If I had another user on my computer we could potentially have different music libraries on exaile. I get it. But what folder is the system data held in then?

---

### Post by alexandremrj on 2008-05-21
When you open synaptic and select a package you can right-click in properties and see where the package installed files. In the case of exaile you can see them in (cut for the sake of the post):

/usr/share/applications/exaile.desktop
/usr/share/locale (where there are several installed because of the different languages)
/usr/share/exaile
/usr/lib
/usr/lib/exaile
/usr/lib/exaile/python2.5
/usr/lib/exaile/python2.5/mmkeys.so
/usr/bin
/usr/bin/exaile
/usr/lib/exaile/exaile.py

---

