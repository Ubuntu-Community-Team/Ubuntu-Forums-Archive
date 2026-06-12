---
title: "Cool window effects and what not"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by MikesGuitar on 2008-09-23
I just got Ubuntu and just got it to recognize my nvidia card and I want to get some of those cool effects like wobbly windows and stuff rocking. How does one do this?

---

### Post by sam_delta on 2008-09-23
go to system>preferences>appearance, then click on the effects tab, and activate the effects by clicking on normal or extra.

then, you can tweek the effects(activate them and deactivate them) by installing compizconfig-settings-manager ```
sudo apt-get install compizconfig-settings-manager
```
then go to system>preferences>advanced desktop effects to tweek/configure them


sam

---

### Post by jamesrfla on 2008-09-23
What you are looking for is called compiz. I do belive the command to get the gui utility is ```
sudo apt-get install libgnome-compiz-manager0
``` compiz is installed by default when you install Ubuntu. Let me know how it works out. :)

---

### Post by Bölvaður on 2008-09-23
> **MikesGuitar said:**
> I just got Ubuntu and just got it to recognize my nvidia card and I want to get some of those cool effects like wobbly windows and stuff rocking. How does one do this?

Under Applications find Add/Remove and type "compiz" It is the top one called Advanced Desktop Effect Settings. When that is installed go to:
- System -> Preference -> Appearance -> Visual Effects
set it to custom or advanced... not sure what it is called.
You can change all the effects from that application you installed. Which you probably saw just before.

Btw you might want to install Emerald, and even perhaps concky. Perhaps even Awn or some other dock.

---

### Post by Shazaam on 2008-09-23
Here is a good link for you...
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by Tatty on 2008-09-23
Go to System->Preferences->Appearance, and select "Normal" or "Extras".

For slightly more control install:
```
sudo apt-get install simple-ccsm
```
This will add a "custom" button to the appearances dialog with some extra options.

If you want the full compiz settings manager then install:
```
sudo apt-get install compizconfig-settings-manager
```
Which should appear in your preferences menu.

If you want to use different window decoraters then you want to install emerald:```
sudo apt-get install emerald
```

---

### Post by steveneddy on 2008-09-23
WOW! Looks you got all of the right answers!

---

