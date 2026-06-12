---
title: "[SOLVED] no custom compiz enabler"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-11
in appearence preferences, in gutsy, there was an option past none, normal, and extra for the desktop effects, custom, which allowed you to use your custom compiz settings. i upgraded to hardy, and temporarily switched it to 'none' to see if my computer went noticably faster. i went to switch it back, but the custom option was gone! why is this???

---

### Post by nynoah on 2008-05-11
do you have compiz settings manager downloaded from synaptic?

---

### Post by Zopiac on 2008-05-11
> **nynoah said:**
> do you have compiz settings manager downloaded from synaptic?

what do you mean? i can edit settings, but i cannot change the fact that is shows my custom settings.

---

### Post by nynoah on 2008-05-11
open synaptic.........search compiz

see if you have compiz settings manager downloaded to your computer.  If you do not, you will not be able to choose custom settings.  It may have been wiped off when you did your upgrade.  So check to see if you still have it.  If not, then you need that.

---

### Post by Zopiac on 2008-05-11
> **nynoah said:**
> open synaptic.........search compiz

see if you have compiz settings manager downloaded to your computer.  If you do not, you will not be able to choose custom settings.  It may have been wiped off when you did your upgrade.  So check to see if you still have it.  If not, then you need that.

yes, i do, but its version (installed and latest) is 7.4, does that correspond with ubuntu's version?

perhaps i could un/reinstall compiz fusion, but how would i do that?

---

### Post by svbh07 on 2008-05-11
Is there a System>Preferences>Advanced Desktop Effects Settings option? Just recently, I began messing with Compiz. That's where I found the cube desktop switcher, the mirroring effect for windows, etc.

---

### Post by Zopiac on 2008-05-11
> **svbh07 said:**
> Is there a System>Preferences>Advanced Desktop Effects Settings option? Just recently, I began messing with Compiz. That's where I found the cube desktop switcher, the mirroring effect for windows, etc.

yes. like i said, i can edit the settings, but cant enable actually using MY settings.

---

### Post by Zopiac on 2008-05-11
bump

can someone tell me how to reinstall compiz???

---

### Post by nynoah on 2008-05-11
do you have your hardware drivers enabled. If you do not, you will not be able to use the custom settings.  go to **system - administrator - hardware drivers** and enable your video card drivers.

---

### Post by Zopiac on 2008-05-11
> **nynoah said:**
> do you have your hardware drivers enabled. If you do not, you will not be able to use the custom settings.  go to **system - administrator - hardware drivers** and enable your video card drivers.

1: When i switched to hardy, everything worked perfectly, just when i turned the settings off i realized i couldnt turn them back on

2: my drivers are enabled

---

### Post by forestpixie on 2008-05-11
I had to install simple-ccsm before I got the custom option for some reason, maybe that will help

```
sudo apt-get install simple-ccsm
```

---

### Post by Zopiac on 2008-05-11
> **forestpixie said:**
> I had to install simple-ccsm before I got the custom option for some reason, maybe that will help

```
sudo apt-get install simple-ccsm
```

i thought of that, but the computer was going slow, so i restarted it before installing it. theni  forgot :P ill try now



edit:  tyvm! forever in debt ;)

---

### Post by nynoah on 2008-05-11
go to system - preferences - advanced desktop settings manager.  Then change some stuff with that.  See if that then does anything.  Really what you have to do to change anything in a custom way is to use the manager.

---

### Post by Zopiac on 2008-05-11
> **nynoah said:**
> go to system - preferences - advanced desktop settings manager.  Then change some stuff with that.  See if that then does anything.  Really what you have to do to change anything in a custom way is to use the manager.

yeah, it does. the thing is, there is a bug for me with the simple: scroll down menus are permanent ;) im restarting my comp. now to get rid of two of them, but its not like ill be fusing the simple settings manager....now that i can use the full one again! thx again!

---

