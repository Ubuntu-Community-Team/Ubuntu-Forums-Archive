---
title: "display goes off after login screen"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by gaegi on 2008-08-20
installed nvidia drivers after which i could only pass through login screen .after entering password display goes off showing error out of range, but the range shown there is within the bounds of monitor. I'm not able go to terminal to enter commands as there is no display  after login screen plese suggest some way to go to terminal so as to enter commands to uninstall the drivers or suggest some other way

---

### Post by skymera on 2008-08-20
How did you install the Nvidia drivers?

I highly suggest using Envy. 

```
 sudo apt-get install envyng-gtk 
```

Run that, it should fix everything after.

---

### Post by tarps87 on 2008-08-20
Try ctrl+alt+f1 you will need to login and then reset the diplay settings using:```

sudo dpkg-reconfigure xserver-xorg
```
This will allow you to reset the graphics, it will also go through keyboard and mouse settings, you should be able to hit escape to keep the current settings for these devices.
It sounds like a driver problem, rather that the resolution

---

### Post by gaegi on 2008-08-20
sorry i don't remember the code i've used to install drivers just pasted it .also i'm not able get past login screen to go to terminal as display goes off as soon as i enter the password .the display keeps on if i don't enter anything on login screen also the screen resolution there is 1440*900 the highest monitor can display .after login it shows out of range message

---

### Post by tarps87 on 2008-08-20
> **tarps87 said:**
> Try ctrl+alt+f1 you will need to login and then reset the diplay settings using:```

sudo dpkg-reconfigure xserver-xorg
```
This will allow you to reset the graphics, it will also go through keyboard and mouse settings, you should be able to hit escape to keep the current settings for these devices.
It sounds like a driver problem, rather that the resolution

pressing ctrl+alt+f1 will take you to a unix/posix interface (black screen with white writing) this will not use a great deal of graphics so it should load. At this screen you will be asked for your username and password then you can type:```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by gaegi on 2008-08-20
first thanx a lot tarps87 it worked and now i can get past th login screen. but i've been used to work on higher resolution it's very difficult to cope with 800*600 could u please suggest how to configure the resolution .I've been searching for this n ended up with the now solved problem

---

### Post by tarps87 on 2008-08-21
Is you driver listed in system -> administration(if not its under preferences) -> hardware. If its here you can activate it and it should work, if not you can try using envyng to install the nivia drivers. I have not used it so don't know a lot about it, it can be installed using:
```

 sudo apt-get install envyng-gtk

```
If none of that works one of the last parts of:
```

sudo dpkg-reconfigure xserver-xorg

```
will give you an option of simple, medium, advanced. With medium and advanced you should be able to select a list of resolutions if you select the ones you want, you can then set them in the 'screen resolution' menu.

---

### Post by gaegi on 2008-08-22
that doesn't work again after installing thru envyg i can't get past login screen

---

### Post by tarps87 on 2008-08-31
You can do the ctrl+alt+f1 thing again with this code to reset it, I don't know how to fix the graphics though
```

sudo dpkg-reconfigure xserver-xorg
```

---

