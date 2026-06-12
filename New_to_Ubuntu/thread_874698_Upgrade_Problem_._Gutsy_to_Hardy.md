---
title: "Upgrade Problem . Gutsy to Hardy"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by sharks on 2008-07-30
I decided to upgrade to hardy today.so i went to use this command:
sudo apt-get dist-upgrade

it all went fine and at a certain point it showed me:
> Setting up locales (2.7.9-4)...
Generating locales
en_AU.UTF-8..

and the screen doesnt chsnge for more than two hours.

I dont want to make a fresh install because i installed a lot of apps in gutsy. How can i complete the upgrade process?

---

### Post by abn91c on 2008-07-30
try using different repositories servers, like the us servers

---

### Post by sharks on 2008-07-30
i cancelled that operation and now i cant go into the GUI.

---

### Post by Seisen on 2008-07-30
Open up a terminal and put this in it

```
sudo dpkg-reconfigure -a
sudo apt-get -f install
```

---

### Post by t0p on 2008-07-30
> **sharks said:**
> 
I dont want to make a fresh install because i installed a lot of apps in gutsy. How can i complete the upgrade process?

You could create a separate home partition by following the instructions [here]("http://www.psychocats.net/ubuntu/separatehome") and [here]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/"), and then do an install.  I realize you'd have to then install all the apps you've currently got, but at least your configuration files would be saved.

I've tried upgrading instead of installing a couple of times, and it's never worked for me. Of course, YMMV.

---

