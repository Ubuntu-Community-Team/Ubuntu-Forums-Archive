---
title: "Firefox 3 Acting up"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by rab4567 on 2008-06-23
A few day ago ff3 final version pack up and cashed the only way i could run it was threw  root, so I uninstalled reloaded it again and now it won't remember  my home page or  addon settings. I'm running hardy on a  HP 2DDR 500GBHD nivida 6150LE.

before and after

---

### Post by Silpheed2K on 2008-06-23
CTRL+0
which is the shortcut for View > Zoom > Reset
check your zoom size to make sure it's normal

---

### Post by bikeboy on 2008-06-23
I would check the permission on your Firefox profile directory. A starting point would be as follows.
```
ls -la /home/USERNAME/.mozilla/firefox/
```Where USERNAME is *your* username.

---

### Post by rab4567 on 2008-06-23
total 24
drwxr-xr-x 3 rab rab 4096 2008-05-26 19:29 .
drwxr-xr-x 4 rab rab 4096 2008-06-20 18:36 ..
-rw------- 1 rab rab 6164 2008-06-16 10:50 pluginreg.dat
-rw-r--r-- 1 rab rab   94 2008-05-05 11:22 profiles.ini
drwxr-xr-x 7 rab rab 4096 2008-06-23 05:49 vkuuxfit.default

OK did that now what do I do?

---

### Post by bikeboy on 2008-06-23
Your permissions seem to be intact, so that's not the problem.

---

### Post by rab4567 on 2008-06-23
Every time I use ff3 I have to reset my home page and aeon clouds art work won't be saved.

---

### Post by bonzodog on 2008-06-23
Delete your ~/.mozilla dir. The default profile is corrupt, which happens sometimes when upgrading Firefox.
You will lose all bookmarks and any extensions you have, but firefox will run properly now.

---

### Post by quanumphaze on 2008-06-23
Don't remove the .mozilla directory, back it up!

use ```
mv ~/.mozilla ~./mozilla-bak
```

Then in the new profile you can import the bookmarks from the old one

Edit: This should be in general help, not the Café

---

### Post by Sef on 2008-06-23
Moved to Absolute Beginners.

---

