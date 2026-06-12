---
title: "Which Wine should i choose?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by fmpfmpf on 2008-05-28
i am using Ubuntu 7.10
i want to use a Windows program in Linux
When i search for Wine in Synaptic Manager, i get 2 search results:-
1. wine
2. wine-dev

Which one should i choose?

tq

---

### Post by sayakb on 2008-05-28
```
sudo apt-get install wine
```
Should install the needed files. You do not normally need Wine-dev (development files for wine)

---

### Post by kesman on 2008-05-28
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

You should follow these instructions of adding Wine-repository to your apt-sources, so you ALWAYS get the latest and best-performancing build of wine.

---

### Post by mini_g on 2008-05-28
> **fmpfmpf said:**
> i am using Ubuntu 7.10
i want to use a Windows program in Linux
When i search for Wine in Synaptic Manager, i get 2 search results:-
1. wine
2. wine-dev

Which one should i choose?

tq

1. WINE, as the WINE-dev package consists of the development files needed to compile programs using wine's free version of the Microsoft Windows API.

---

### Post by housam on 2008-05-28
Read this : [[COLOR="Red"]_wine_[/COLOR]]("https://help.ubuntu.com/community/Wine#head-3acca7686806077923c05fa38c442e856ffacc54")

---

