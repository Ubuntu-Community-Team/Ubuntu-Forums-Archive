---
title: "Problems installing flash"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by zamadatix on 2008-08-27
i clicked the install missing plugins and converted the rpm to a deb then installed flash player 9, well i stil have no flash in my ff... whered i mess up this time ;)

---

### Post by billgoldberg on 2008-08-27
> **zamadatix said:**
> i clicked the install missing plugins and converted the rpm to a deb then installed flash player 9, well i stil have no flash in my ff... whered i mess up this time ;)

**"Converted the rpm to a deb" **

No no no, where have you read that guide?

--

In a terminal issue this code:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

Besides flash, that will install some other codecs, like divx and dvd support.

--

You might want to try flash player 10 RC, it performs MUCH better on Ubuntu, but is not 100% bug free yet.

[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

---

### Post by zamadatix on 2008-08-27
actually it was quite a few guides on google... assumeing i jsut installed all of that without reading ahead... how do i knowremove flash 9 and put in flash ten, thanks for that btw

---

### Post by billgoldberg on 2008-08-27
> **zamadatix said:**
> actually it was quite a few guides on google... assumeing i jsut installed all of that without reading ahead... how do i knowremove flash 9 and put in flash ten, thanks for that btw

Did you used the first code (you should)?

Then if you just follow the guide for flash 10, it will tell you how to remove flash player 9..

---

### Post by zamadatix on 2008-08-27
well thats what i thought with flash 9 so making sure thanks again

---

