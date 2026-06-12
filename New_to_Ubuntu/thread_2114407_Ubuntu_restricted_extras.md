---
title: "Ubuntu restricted extras"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by Soviet Hound99 on 2013-02-10
Hello, I have got ubuntu 12.04 lts on my chromeboook series 3, i have installed ubuntu restricted extras to get flash. But when i go to youtube it say i dont have it.
I typed the following command into terminal: 

sudo apt-get install ubuntu-restricted-extras

and i get

user@localhost:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

What can i do to get flash working?

Thanks

---

### Post by QIII on 2013-02-10
Try to install the flash plugin installer.

```
sudo apt-get install flashplugin-installer
```

I don't think restricted extras will do that for you automatically.

---

### Post by deadflowr on 2013-02-10
You say you are on a chromebook, by any chance are you running chrome?
If so, then you might be suffering from the chrome flash bug that hit last week.
In which case the flash installed through the ubuntu restricted extra package isn't getting called into use, as the built-in pepperflash plugin takes priorty in chrome.
If you are using chrome, try disabling the pepperflash plugin in the chrome plugin section.

This of course is only my complete guess work, and not subject to anything you're actually experiencing.

---

### Post by drawkcab on 2013-02-10
You might need to install a newer version of flash.

[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

---

