---
title: "need terminal code script to open launcher on 12.4"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by vegas89 on 2012-10-27
I need the terminal code script to open the launcher or the keyboard sequence keys so I can get the launcher to turn on . I was useing compiz manager and turned off the ubuntu unity plugin then the launcher went away. I closed out the compiz manager before to enabled the ubuntu unity plugin. Now I can't get the launcher to open up. Please help me get it back on!

---

### Post by CTate on 2012-10-27
Open up a terminal (Control alt t) and type:

```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

(Easier to highlight the code, open the terminal and middle-click. That should paste whatever's highlighted)

Put Launcher as the name and this for the command:

```
/usr/bin/gnome-desktop-item-edit /home/YOURUSERNAME/Desktop --create-new
```

Change YOURUSERNAME to your username.

Click OK and you should have a new desktop item called Launcher.

Note Launcher needs full path to the command, so stuff like '~/bin/myscript' or 'google-chrome' won't work. You'd need '/usr/bin/google-chrome'

---

### Post by CTate on 2012-10-28
I may have completely misunderstood the question. I switched to gnome-classic right away as I didn't like Unity. That list of apps on the left?

Try opening a terminal and typing:

```
unity --reset
```

---

### Post by NikTh on 2012-10-28
Hi , 

the code to open compizconfig-settings-manager from terminal is 

```
ccsm
```Open it and re-enable the Unity plugin. 
Logout - login or reboot. 

You can open the terminal with CTRL+ALT+T keys combo.

Thanks

---

### Post by vegas89 on 2012-10-28
Thanks for the help!! Everything is back as it should be   ):P

---

