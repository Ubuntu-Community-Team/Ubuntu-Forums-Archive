---
title: "Skype icon in tray missing"
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by maxxer on 2011-10-10
Hi. I installed 11.10 yesterday and today I installed skype, but I cannot seem to find the skype icon in tray when I launch it, so once closed I cannot use it anymore! 
It's the first time I use unity, where is the icon supposed to be?
thanks

---

### Post by awam66 on 2011-10-10
I've had this problem even in Natty. There is a way to add it to the indicator applet viz: ```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Skype', 'Dropbox']"
```
I still find it doesn't always show, but should work. Add anything else you want to show to the white list.

---

### Post by mtron on 2011-10-10
it should be in the panel and whitelisted in unity.

try this and logout afterwards:
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
sudo apt-get install sni-qt
```

This will allow all applications to show notifications in the unity panel and adds ubuntu indicator support to qt apps.

---

### Post by wgarcia on 2011-10-10
If you install the package "sni-qt" in 11.10 you get now a Skype app-indicator, that is an actual Unity indicator and not a systray indicator. Same thing for other QT applications who have lost their indicators if not whitelisted.

---

### Post by maxxer on 2011-10-10
> **mtron said:**
> it should be in the panel and whitelisted in unity.

try this and logout afterwards:
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
sudo apt-get install sni-qt
```

This will allow all applications to show notifications in the unity panel and adds ubuntu indicator support to qt apps.

I tried this but didn't work. sni-qt package was installed already, I just issued the gsettings command, relogged in, but still I cannot see skype icon! :(

---

### Post by maxxer on 2011-10-10
I just installed dropbox and it's visible, if matters

---

### Post by mtron on 2011-10-10
ok, seems you're affected by bug #[860322]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/860322")

Login, and click on the "Does this bug affect you?" Link to let the devs know.

---

### Post by maxxer on 2011-10-10
> **mtron said:**
> ok, seems you're affected by bug #[860322]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/860322")

thanks!

---

