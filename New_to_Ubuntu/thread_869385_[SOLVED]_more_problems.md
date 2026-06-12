---
title: "[SOLVED] more problems"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Joshfan on 2008-07-24
am a big online media user, like my favorite of all time is youtube, second is [http://www.surfthechannel.com]("http://www.surfthechannel.com")
but they will not play right. On windows they play great, on Ubuntu they are slow and the scene change's like still slide shows how do i get streaming media to play normal?



[IMG]http://img292.imageshack.us/img292/1647/475869vz3.png[/IMG][http://counter.li.org/]("http://counter.li.org/")

my computer is:

Dell intel P3 1ghz cpu 384mb of ram integrated graphics card

---

### Post by iaculallad on 2008-07-24
> **Joshfan said:**
> am a big online media user, like my favorite of all time is youtube, second is [http://www.surfthechannel.com]("http://www.surfthechannel.com")
but they will not play right. On windows they play great, on Ubuntu they are slow and the scene change's like still slide shows how do i get streaming media to play normal?



[IMG]http://img292.imageshack.us/img292/1647/475869vz3.png[/IMG][http://counter.li.org/]("http://counter.li.org/")

my computer is:

Dell intel P3 1ghz cpu 384mb of ram integrated graphics card

Try replacing your current Adobe Flash with [GNASH]("http://www.gnu.org/software/gnash/"), it's available in the repository.

```
sudo apt-get install gnash
```

---

### Post by cozmicharlie on 2008-07-24
Not knowing what you have and have not done as far as installing video apps, I would recommend this tutorial - the best IMHO how to on multimedia - especially check out the sections on installing Flash plugins.  My guess is you need to reinstall flash.  Try this command in a terminal and see if that helps (note you do need the medibuntu repository enabled) as per the link).

```
sudo apt-get purge flashplugin-nonfree gnash gnash-common libflash-mozplugin libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

---

### Post by Joshfan on 2008-07-24
Will i need to remove the flash i installed from the synaptic package program or will gnash replace it on its own

---

### Post by Joshfan on 2008-07-24
> **cozmicharlie said:**
> Not knowing what you have and have not done as far as installing video apps, I would recommend this tutorial - the best IMHO how to on multimedia - especially check out the sections on installing Flash plugins.  My guess is you need to reinstall flash.  Try this command in a terminal and see if that helps (note you do need the medibuntu repository enabled) as per the link).

```
sudo apt-get purge flashplugin-nonfree gnash gnash-common libflash-mozplugin libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```


how do i get this medibuntu enabled

---

### Post by Sef on 2008-07-24
> how do i get this medibuntu enabled 

Read Ubuntu-Geek's [HowTo]("http://www.ubuntugeek.com/enable-dvd-playback-in-your-ubuntu-system.html").

---

### Post by cozmicharlie on 2008-07-24
Open the terminal (Applications > Accessories > Terminal and paste these wget commands into it:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

