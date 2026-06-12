---
title: "Problems to play a DVD"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by Jonatan Formentera on 2013-02-15
Hi, I have got Ubuntu 12.4. I've tried to play a commercial DVD with it, for instance a movie, but I can't. It says to me it's encrypted. I've installed a couple of DVD-players softwares but it doesn't work.
What can I do?
Thanks

---

### Post by grahammechanical on 2013-02-15
The first thing that you can try is to open the Ubuntu Software Centre and search for Ubuntu Restricted Extras. Are they installed? It may be that you are missing a codec.

I have never tried to play a commercial DVD of that type. When you get the error message, do you get an invitation to enter some kind of code?

[http://en.wikipedia.org/wiki/Digital_Rights_Management]("http://en.wikipedia.org/wiki/Digital_Rights_Management")

Regards.

---

### Post by 3rdalbum on 2013-02-15
Unlicensed (cost-free) DVD decryption software is of dubious legality in some parts of the world, so it is not shipped as part of Ubuntu. It is actually not shipped with Windows either, actually.

It is really easy to add DVD playback support to Ubuntu. Follow the instructions at [www.medibuntu.org](www.medibuntu.org) to install the libdvdcss2 package which will add decryption facilities to your Linux video players.

The best player is VLC - I would recommend installing VLC along with libdvdcss2.

---

### Post by speartip on 2013-02-15
As well as installing Ubuntu restricted extras, you also need to install libdvdcss
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Jonatan Formentera on 2013-02-15
I've installed Ubuntu extras but it continuous to appear "a DVD decryption library is not installed". No problem anyway. I can used Windows 7 or a simple DVD player

---

### Post by speartip on 2013-02-15
Did you install the package in the link?
```
sudo apt-get install libdvdread4
```
then
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
Then reboot.

---

### Post by Jonatan Formentera on 2013-02-16
Fine, I've just tried Speartip's method and it works perfectly. I only needed to introduce the DVD and it started authomaticaly.
Thanks

---

