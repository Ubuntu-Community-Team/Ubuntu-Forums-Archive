---
title: "Screen resolution"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by gulmer on 2008-11-07
I cannot get the x to remember the screen resolution and refresh that I set up in the nvidia x server settings. What do I need to do to fix this, every time I log in my resolution is at 800X600 and I set it to 1024X768. I'm using a 19" 4X3 monitor, and my video card is GeForce 6200.

---

### Post by fooman on 2008-11-07
in a terminal try:

```
gksudo nvidia-settings
```

after you make the adjustments,  click on the "save to x configuration file" button.

see if that works.

---

### Post by earthpigg on 2008-11-08
> I cannot get the x to remember the screen resolution and refresh that I set up in the nvidia x server settings.

i had the same problem as soon as i switched to 8.10.

1. rename xorg.conf file to something else:

```
sudo mv /etc/X11/xorg.conf /etc/X11/backupofxorg.conf
```

2. start nvidia-settings as root and you should be able to save now:

```
sudo nvidia-settings
```

i have no idea why that worked, but it did for me.

---

### Post by philinux on 2008-11-08
I had the same problem but when I used system>prefs>screen res the resolution stuck.

---

### Post by drakeman007 on 2008-11-08
Why you dont just install the ubuntu restricted drivers for nvida an ati, i think this install fix the problem!

---

