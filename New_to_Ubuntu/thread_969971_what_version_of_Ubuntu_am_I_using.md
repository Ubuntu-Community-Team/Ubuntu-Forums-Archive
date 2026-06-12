---
title: "what version of Ubuntu am I using?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by mitar on 2008-11-03
few questions about ubuntu version.

1. How can I see what version is installed?

2. What's the current one?

3. If I decide to upgrade would the files that are on there be saved or I would need to backup?

---

### Post by OutOfReach on 2008-11-03
You can check by going to System>Administration>System Monitor and go to the first tab, it should say the version number.

The current version is 8.10 Intrepid Ibex

If you decide to upgrade without reinstalling, then yes all your files will stay.

---

### Post by tuxxy on 2008-11-03
1. ```
lsb_release -a
```

2. Ibex 8.10 , current LTS release is Hardy.

3. Upgrade you .home will be fine but they would be deleted with a clean install, you could move your /home to a seperate partition first to save your personal files/settings

---

### Post by mitar on 2008-11-03
ok. so the upgrading would be just like installing in? First I need a cd and then install that or is there some specific way to do it?

---

### Post by kansasnoob on 2008-11-03
Upgrades can be more troublesome than fresh installs!

Maybe I should add, "In my opinion"!

---

### Post by zvacet on 2008-11-03
If you want to upgrade it is good idea to have separate home.Thar way your settings will be saved.Read [here]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") how to do it.Easyer way is to back up your data ansd files (burn on CD/DVD) and make clean install but this time on the install prosec make home partition.[Here]("http://www.ubuntu.com/getubuntu/upgrading") you can find more about upgrading.

---

### Post by Iowan on 2008-11-03
> **mitar said:**
> few questions about ubuntu version.

1. How can I see what version is installed?Most of the versions I use have a default "homepage" for Firefox that tells you which version is running.

---

### Post by niccholaspage on 2008-11-03
An upgrade doesn't need a CD. It updates your system to 8.10. I recommend doing a fresh install.

---

### Post by zvacet on 2008-11-04
> An upgrade doesn't need a CD.

Truth,but there is allways a chance that something goes wrong with net upgrade.If you do upgrade with alternate CD even if something goes wrong you have CD for fresh install. ;)

---

