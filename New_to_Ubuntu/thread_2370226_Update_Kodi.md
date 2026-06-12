---
title: "Update Kodi"
date: 2017-08-31
forum: New to Ubuntu
---

### Post by rudybaby on 2017-08-31
I got a message on opening Kodi that there is a new stable release. How is the easiest, safest way to update Kodi?

---

### Post by again? on 2017-08-31
Add the kodi ppa. (uses old name of xbmc)
```
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt update
sudo apt upgrade
```

---

### Post by Frogs Hair on 2017-08-31
Hello and Welcome 

Did you install Kodi from Ubuntu Software ?

---

### Post by rudybaby on 2017-09-01
I installed from ubuntu software. when u type sudo apt-get upgrade, does it only upgrade kodi in the example above?

---

### Post by Frogs Hair on 2017-09-01
I would use the PPA as suggested by guber2. Be sure your system is up to date before using the commands.

---

### Post by again? on 2017-09-01
> **rudybaby said:**
> I installed from ubuntu software. when u type sudo apt-get upgrade, does it only upgrade kodi in the example above?
When you add a ppa it is included in your package sources and your system will prompt you to upgrade (including kodi) through automatic updates.
or
after adding a ppa you can manually update and upgrade your packages immediately (including kodi), using the terminal commands shown in my last post.
[**What is a ppa?**]("https://help.ubuntu.com/community/PPA")

---

