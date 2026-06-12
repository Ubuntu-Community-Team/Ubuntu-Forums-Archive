---
title: "I don't have the lock screen button at the bottom of the menu."
date: 2019-07-29
forum: New to Ubuntu
---

### Post by mariojavierperdomo on 2019-07-29
I don't have the lock screen button at the bottom of the menu. I am using 19.04 on Dell Inspiron 14z 5423.


Also, I can not access the settings of Lock Screen in the Privacy menu because it's completely "grey" (inaccessible). I need help with this.

---

### Post by deadflowr on 2019-07-29
Check out the [dconf/gsettings]("https://askubuntu.com/a/191013") settings.
Either through the dconf editor program (needs to be installed)
or using the gsettings commands like this one
```
gsettings get org.gnome.desktop.lockdown disable-lock-screen
```
if set to true, change it to false
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen false
```

If you go by way of dconf editor, just follow the above path : org > gnome > desktop > lockdown
and check the setting for disable-lock-screen.

---

