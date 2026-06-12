---
title: "restart x"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-10-20
in 12.04 is was alt + printscreen + k. this doesnt seem to work in 12.10 even tried the old  control + alt + backspace that was used with ubuntu prior to 10.04 and that didnt work. any ideas? tks

---

### Post by zombifier25 on 2012-10-20
There's an option in keyboard layouts to enable the key combination to kill X. Go to System Settings > Keyboard > Keyboard Layout > Options (or words with similar meanings, not using English locale right now)

---

### Post by kc1di on 2012-10-20
The terminal command to restart x is
```
sudo restart lightdm
```
or you can enable it by going to dash >keyboard layout> Options> Key squence to kill X server > check the box control-Alt-Backspace. that's it

---

### Post by dj_deef on 2012-10-20
that actually restarts even the desktop login manager

---

### Post by lachild on 2012-10-20
Anyone know how this is setup in XUbuntu?  I can't find the setting your describing under the keyboard settings.

---

### Post by rburkartjo on 2012-10-20
la neither can i that is why i started this thread

---

### Post by rburkartjo on 2012-10-20
here is what i did i wrote this script 
#!/bin/bash
echo xxx | sudo -S restart lightdm



where xxx is my password made it exe

put in in my home folder
works great

---

### Post by kc1di on 2012-10-21
> **rburkartjo said:**
> here is what i did i wrote this script 
#!/bin/bash
echo xxx | sudo -S restart lightdm



where xxx is my password made it exe

put in in my home folder
works great

Glad you were able to sort it out hope it will help others also.
Cheers!

---

