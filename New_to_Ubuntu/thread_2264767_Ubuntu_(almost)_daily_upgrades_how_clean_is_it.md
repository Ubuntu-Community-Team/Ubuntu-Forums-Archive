---
title: "Ubuntu (almost) daily upgrades how clean is it?"
date: 2015-02-10
forum: New to Ubuntu
---

### Post by tomerbd on 2015-02-10
Almost daily ubuntu asks me to upgrade a few libs / apps / ubuntu base.  It downloads a few MB or even tens of MB on these occasions.  Are these upgrades by any chance eating my hard drive? or is it very clean so after it upgrades a library or an app it deletes the older one so my hard disk wont be eaten by these daily upgrades?

---

### Post by sandyd on 2015-02-10
> **tomerbd said:**
> Almost daily ubuntu asks me to upgrade a few libs / apps / ubuntu base.  It downloads a few MB or even tens of MB on these occasions.  Are these upgrades by any chance eating my hard drive? or is it very clean so after it upgrades a library or an app it deletes the older one so my hard disk wont be eaten by these daily upgrades?

By default, Ubuntu overwrites the old files on a upgrade.

Do note that apt caches the packages. These can be removed by```

sudo apt-get clean
```

---

### Post by mastablasta on 2015-02-10
it is not "eaten".

also you dont' have to do daily updates. I mean update as soon as they are available. you could also setup to for example only get security updates. they are usually not so frequent.

---

### Post by Impavidus on 2015-02-10
There is one exception though: In case of kernel upgrades the old version is kept. This is because on rare occasions the new kernel may not boot properly, so you can keep the old one as a fallback. You have to remove it later. Most of the time autoremoving works:```
sudo apt-get autoremove --purge
```But kernel upgrades are rare and, unless you have a small /boot partition, won't eat all your hard drive space.

---

