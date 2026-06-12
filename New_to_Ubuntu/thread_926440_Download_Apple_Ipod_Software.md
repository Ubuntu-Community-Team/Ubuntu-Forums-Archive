---
title: "Download Apple Ipod Software"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-09-21
We have an Apple Ipod and have been using on another computer with Microsoft Windows XP on it. I would like to install Ubuntu on that computer also. Will I be able to still use the Ipod with Ubuntu ?

---

### Post by aysiu on 2008-09-21
Read this:
[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

---

### Post by linux5uper on 2008-09-21
Yes, you sure can. You'll have to do it through another application than iTunes though (I use Amarok).

A very nice article and instructions on the excellent psychocats website:

[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

---

### Post by CoCoKnots on 2008-09-21
Will we be able to keep & use the music previously recorded using the computer with Microsoft XP if I download Amarok ?

---

### Post by linux5uper on 2008-09-21
Yes, you will just need to install the necessary codecs first.

First, check that you have all repositories enabled in System > Administration > Software sources. 

Then run:

```
sudo apt-get install ubuntu-restricted-extras
```

and you should be fine.

edit: to 'keep' the music, you will just have to make sure you do not overwrite the partition where it is stored during the Ubuntu installation. You should be able to access the partition easily from your Ubuntu system (should be listed in the 'Places' menu).

---

### Post by trestamanos on 2008-09-22
or one can run windows on virtual box??
but why would you want to do that?  there are so many players available through open source.

---

