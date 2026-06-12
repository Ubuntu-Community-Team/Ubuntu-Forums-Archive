---
title: "Brightnes issue on new install."
date: 2012-07-29
forum: New to Ubuntu
---

### Post by panzersword on 2012-07-29
I am a new user of Ubuntu and have installed 12.04 on my Toshiba Satellite laptop. My problem is that my screen is almost to dim for me to use anything. I have already tried going into settins and brightness and un-checked all the options for dimming screen. I have never used anything like this and need some guidance for putting in command prompts to fix this issue.  Any help would be great...:confused:

---

### Post by NikTh on 2012-07-29
Hi and welcome to Ubuntu Forums. 

Please open a terminal (ctrl+alt+t) and paste this command 
```

gsettings set org.gnome.desktop.screensaver idle-activation-enabled false 
```
worked ? 

Thanks

---

