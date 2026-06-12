---
title: "Cleaning the garbage out of ubuntu?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-03
Hi folks, 

(One more). 

... In Windows I used to use the app CCleaner to get rid of all the garbage (cache files/temp files/etc and the like). Is there any such application for Ubuntu or way to do it? Is it even necessary?

-'Mage

---

### Post by SunnyRabbiera on 2008-05-03
well if you use firefox it does have a built in cache cleaner/ cookie cleaner, what applications do you use to browse the net?
as for extra junk lets go down the list first.

---

### Post by UnWarierMage224 on 2008-05-03
I use firefox to browse the web.. I do have all the cleaning options enabled. It clears all my stuff every time I close FF. 

However, when you download a file and auto-open it (like a PDF for example) in FF, where does FF stick the temp file? Does it delete it when it's through?

---

### Post by Oldsoldier2003 on 2008-05-03
> **UnWarierMage224 said:**
> Hi folks, 

(One more). 

... In Windows I used to use the app CCleaner to get rid of all the garbage (cache files/temp files/etc and the like). Is there any such application for Ubuntu or way to do it? Is it even necessary?

-'Mage

bootclean runs on boot and clears out your /tmp 
```
sudo apt-get clean
``` will clear out your package cache
clear out your thumbnails once in awhile if you have a lot of graphics. you can do it manually by clearing out the .thumbnails folder in your home ```
dir.find ~/.thumbnails -type f -atime +7 -exec rm {} \;
```will kill any thumbnails over 7 days

you can also clean out any logs you are not interested in keeping. they are stored in /var/log and its safe to delete the gzipped logs. 
```
cd /var/log
sudo rm -r *.gz
```

---

### Post by UnWarierMage224 on 2008-05-03
Ah, that's very useful information! Thanks! 

-'Mage

---

### Post by SunnyRabbiera on 2008-05-03
that should do it, there is no "temporary internet files" to worry about if you keep on cleaning your cache.

---

