---
title: "How to set new image desktop background on ubunutu 11.10 by command"
date: 2011-10-16
forum: Programming Talk
---

### Post by sompoch on 2011-10-16
By the past version of ubuntu (<11.04),i can change image desktop background  by command line :

gconftool-2 -t string -s /desktop/gnome/background/picture_filename "$PICTUREDIR$NEWBACKGROUND"  

So,today after upgrade ubuntu to 11.10 that command not work and not respond anything.
:p

---

### Post by Hairy_Palms on 2011-10-16
gconf is deprecated for gsettings now, the new way is
```
gsettings set org.gnome.desktop.background picture-uri file:///some/path/to/picture.png
```

---

### Post by sompoch on 2011-10-16
> **Hairy_Palms said:**
> gconf is deprecated for gsettings now, the new way is
```
gsettings set org.gnome.desktop.background picture-uri file:///some/path/to/picture.png
```

Thank you , It's work

---

### Post by wreckedred on 2012-01-07
I am trying to use this command in cron and it fails...works great from my terminal but just will not run from cron. I have tried several things and wondered if you might have a suggestion

---

