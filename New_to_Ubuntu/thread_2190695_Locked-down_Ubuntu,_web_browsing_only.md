---
title: "Locked-down Ubuntu, web browsing only"
date: 2013-11-28
forum: New to Ubuntu
---

### Post by Cleveland Rock on 2013-11-28
My dad uses his computer for web browsing (including web-based email) and nothing else, so I want to install an OS that's just the bare basics he needs, so he doesn't get into any trouble. It has to be something that rarely or never asks him to install, download, or update anything. Maybe even something that ***prevents*** him from installing, downloading, or updating anything. 

[Eldy]("http://www.eldy.eu/") looks very interesting, but it would be nice if he could use Firefox, so I could import his old bookmarks for him and set up Adblock Plus. I was wondering if there was a way to customize Ubuntu to suit his needs. Is there a desktop environment or distro or something that would be good for him?

---

### Post by ian-weisser on 2013-11-28
> **Cleveland Rock said:**
> I want to install an OS that's just the bare basics he needs
Uninstall everything he doesn't use. Easy to do in Software Center. Simply scroll down the list of installed applications...and uninstall them. Even uninstall Software Center itself.
 

> **Cleveland Rock said:**
> It has to be something that rarely or never asks him to install, download, or update anything.
There is a setting for that in Software Center --> Software Sources

---

### Post by sandyd on 2013-11-28
> **Cleveland Rock said:**
> My dad uses his computer for web browsing (including web-based email) and nothing else, so I want to install an OS that's just the bare basics he needs, so he doesn't get into any trouble. It has to be something that rarely or never asks him to install, download, or update anything. Maybe even something that ***prevents*** him from installing, downloading, or updating anything. 

[Eldy]("http://www.eldy.eu/") looks very interesting, but it would be nice if he could use Firefox, so I could import his old bookmarks for him and set up Adblock Plus. I was wondering if there was a way to customize Ubuntu to suit his needs. Is there a desktop environment or distro or something that would be good for him?
If your really bored, and want to make it foolproof, try the below. Might need some tweaking

1. Install Ubuntu Server, during the installation, make sure that when it asks you what programs to install, all are unchecked.
2. Login
3. Run the below, uncomment the lines that deal with the Canonical Partner repository, press control+x to save
```

sudo nano /etc/apt/sources.list
```
3. Run the following
```

sudo apt-get install xorg openbox firefox flashplugin-installer gdm
```
4. Assuming this is his account your logged into, run the following
```
mkdir -p ~/.config/openbox/
echo "/usr/bin/firefox" > ~/.config/openbox/autostart
echo "openbox --exit" > ~/.config/openbox/autostart
```
5. Restart
6. you should be faced with a GDM screen on login, try logging in, and FF should auto-start. When FF is closed, openbox (should) exit.

---

### Post by shakkurbaby2004 on 2013-11-28
Using the browser needs dynamic system which needs your constant attention related to the browser such as sound, flash player for web videos. Once the browser is up and running, you can exit the updates on Ubuntu everytime it pops up on Ubuntu startup.
Or you can change the settings of update from SOFTWARE UPDATER.

---

### Post by Cleveland Rock on 2013-11-28
I guess that works… But there's no way I can prevent Firefox from saving files, is there?

---

### Post by ian-weisser on 2013-11-28
Caching pages? Sure, you can stop it...but firefox will run slow.
Or Downloading? Sure, you can change the permission of the directory so Firefox can't write to it...but then he will get an error every time, and pester you about it. Pick your poison.

---

### Post by vasa1 on 2013-11-28
> **ian-weisser said:**
> Caching pages? Sure, you can stop it...but firefox will run slow.
Or Downloading? Sure, you can change the permission of the directory so Firefox can't write to it...but then he will get an error every time, and pester you about it. Pick your poison.
Maybe what OP wants is to prevent the user from saving files to disk which is different from caching. I think caching can easily be turned off in Edit, Preferences, Advanced, Network, Cached Web Content.

About preventing Firefox from saving files ... I don't know if Apparmor is part of the setup, but it maybe possible to modify the Firefox profile to block saving. But as you've said, it may not be silent :)

---

### Post by drac-noc on 2013-12-07
Perhaps having the system automatically sign in as Guest only, so that any downloads that are kept will be wiped at the end of the session...

Here's a thread to customise it

[http://ubuntuforums.org/showthread.php?t=2152804](http://ubuntuforums.org/showthread.php?t=2152804)

You might need something to sync bookmarks... oh wait, FF has that anyway. Might need to change a few extra permissions on Guest to get what you want, but this seems a clean way of doing what you want.

---

