---
title: "myspace music and now youtube sound"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-05-28
neither are working, youtube video plays fine but not myspace and i get error loading xml document with myspace youtube is just muted can i fix this?

---

### Post by SteveNorman on 2008-05-28
Probably need a flash plugin, you can try this


[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Select .tar.gz for linux

Do "Save file" versus open with Archive manager

right click the icon on your desktop and do "extract here"

double click the install_flash_player_9_linux icon

double click flashplayer_installer

select run in terminal

follow the instructions (answer yes to all)

---

### Post by diablo75 on 2008-05-28
Try this in terminal:

```
sudo apt-get install libflashsupport
```

---

### Post by AlucardXXVII on 2008-06-16
> **diablo75 said:**
> Try this in terminal:

```
sudo apt-get install libflashsupport
```

I was having the same error, this fixed mine.

Thanks

---

