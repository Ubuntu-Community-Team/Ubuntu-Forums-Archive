---
title: "wine c drive: again"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by icegood on 2012-07-25
Trying to browse via menu. Says
file:///home/ice/Docunents/.wine/dosdevices/c has bad location.
Should be file:///home/ice/.wine instead of file:///home/ice/Docunents/.wine
Where to change it? 
In wine config  all options to change drive c properties are unavailable.

---

### Post by mastablasta on 2012-07-25
what about if you run wine config as root (use gksudo to run it)

---

### Post by icegood on 2012-07-25
> **mastablasta said:**
> what about if you run wine config as root (use gksudo to run it)

```

wine: /home/ice/.wine is not owned by you

```

---

### Post by mastablasta on 2012-07-25
gksu nautilus
 
then go to wine folder, right click it and change the ownership.

---

### Post by Karlchen on 2012-07-25
Hello, icegood.
> In wine config  all options to change drive c properties are unavailable.Correct. Drive **c:** is just a fixed symbolic link. You can find it here - provided you have performed a default Wine installation: /home/ice/.wine/dosdevices. And **c:** points to **../drive_c**.
In case it point somewhere else on your machine, you may have changed to symlink yourself perhaps?
In case **c:** does not point to **../drive_c** fix it by executing these commands: ```
cd /home/ice/.wine/dosdevices
rm c:
ln -s ../drive_c c:
```> Why those *<censored>* change path from version to vesion?No, they do not do so. Has been like this for ages now.

And just in order to avoid any confusion: The Wine folder /home/ice/.wine should definitely be owned by ice:ice, not by root:root.

Kind regards,
Karl

---

### Post by HiImTye on 2012-07-25
you can always change your wine prefix to specify a new location. so your command would look like```
env WINEPREFIX=home/ice/Docunents/.wine/ winecfg
```and you can move your files to that new location

---

