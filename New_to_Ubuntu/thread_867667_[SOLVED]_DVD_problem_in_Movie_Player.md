---
title: "[SOLVED] DVD problem in Movie Player"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by OMR on 2008-07-23
Movie Player wont play DVD's Ubuntu Documentation site said to download 
libdvdnav4 andlibdvdread3 which I've done, now when I try to Play A DVD it says I may not have permission, as the Administrator and only user of this machine how do I get "permission!

---

### Post by iaculallad on 2008-07-23
> **OMR said:**
> Movie Player wont play DVD's Ubuntu Documentation site said to download 
libdvdnav4 andlibdvdread3 which I've done, now when I try to Play A DVD it says I may not have permission, as the Administrator and only user of this machine how do I get "permission!

Add the Medibuntu Repository:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```

Install the Keyring:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

```
sudo apt-get install build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by collinp on 2008-07-23
You need libdvdcss, look here: [http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html). If that does not work, keep it installed, but run in terminal
```
sudo totem
```
then run your dvd from there.

---

### Post by OMR on 2008-07-23
> **Hellow said:**
> You need libdvdcss, look here: [http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html). If that does not work, keep it installed, but run in terminal
```
sudo totem
```
then run your dvd from there.

Thank you very much problem is solvedhttp://ubuntuforums.org/images/smilies/icon_smile.gif

---

### Post by collinp on 2008-07-23
No problem :).

---

