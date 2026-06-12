---
title: "[SOLVED] Windows Font?"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Haruki-kun on 2008-10-08
Not a big problem, but... is there any way to import or download the fonts from Windows to Ubuntu?

---

### Post by OutOfReach on 2008-10-08
You can install the ubuntu-restricted-extras (which includes Microsoft fonts).
Or to only get the fonts, install them like so:
```
sudo apt-get install msttcorefonts
```

In a terminal (Applications>Accessories>Terminal)

---

### Post by Haruki-kun on 2008-10-08
It worked. Thanks a lot, OOR!

---

### Post by Locutus_of_Borg on 2008-10-08
insert windows CD
mount windows cd
cd to i386 directory
copy all *.tt_ and *.fo_ files to another directory
cd to i386/lang and repeat previous step
cd to directory you copied the .tt_ and .fo_ files to
mkdir /usr/share/fonts/MSFonts
use cabextract to extract the contents of the directory to /usr/share/fonts/MSFonts
run fc-cache -fv
restart X


or if you are satisfied with msttcorefonts, just use those, but they are not the exact same fonts as what microsoft uses...i believe, plus there are more fonts on the cd than what is in that package

---

### Post by OutOfReach on 2008-10-08
No problem. :)

---

