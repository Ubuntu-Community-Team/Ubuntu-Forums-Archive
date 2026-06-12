---
title: "installing itunes to ubuntu"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by edwin2105z on 2008-07-18
is it possible to install itunes into ubuntu. i really like there player

---

### Post by schauerlich on 2008-07-18
It's possible to install through a program called Wine. It can help windows programs run in Ubuntu, but it's sort of hit-and-miss as to what programs will work, and even if it does work, there may be functionality issues. That being said, try this:

First, install wine:
```

sudo apt-get update
sudo apt-get install wine
sudo apt-get install winesetuptk 

Then to configure stuff do:

winesetuptk 

```
Click ok to everything, the defaults are fine. 

Then follow this:
[http://www.wine-reviews.net/applications/itunes-73-on-linux-with-wine.html](http://www.wine-reviews.net/applications/itunes-73-on-linux-with-wine.html)

---

### Post by hyper_ch on 2008-07-18
have you tried to do it yourself already?

---

### Post by edwin2105z on 2008-07-18
> **hyper_ch said:**
> have you tried to do it yourself already?

havent tried it yet

---

### Post by nothingspecial on 2008-07-18
Have you tried all the players available here. gtkpod, banshee, amarok, rhytmbox. There`s one called songbird that I believe has a plugin that makes it look like iTunes. Not tried it myself though.

---

### Post by XCan on 2008-07-18
Maybe I can make a follow up question. Is there any software available to transfer music to ipods native for linux?

---

### Post by Canis familiaris on 2008-07-18
If you like iTunes then you'll like Songbird as well.
How to install Songbird:

Cut, copy and paste the following commands in the terminal.

```
wget -c ftp://ftp-mirror.internap.com/pub/www.getdeb.net/ubuntu/hardy/so/songbird_0.5-1~getdeb1_i386.deb
```

In case you have 64bit Ubuntu, replace the i386 by amd64 in each of the entries(that's what I did)

```
sudo dpkg -i songbird_0.5-1~getdeb1_i386.deb
```

Songbird would be installed.

Get the icons and set it:
```
wget -c -q http://www.psychocats.net/ubuntu/songbirdicon.png
sudo mv songbirdicon.png /usr/share/pixmaps/songbird.png
```

Run Songbird by Applications->Sound and Video->Songbird

Source: [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

Personally my favourite music player is Amarok by far. I think you should give Amarok a try. It honestly rocks.

---

### Post by Canis familiaris on 2008-07-18
> **XCan said:**
> Maybe I can make a follow up question. Is there any software available to transfer music to ipods native for linux?

Amarok does that too. It simply rocks. I am not sure whether Songbird syncs with iPod, but you can try.

---

### Post by nothingspecial on 2008-07-18
> **XCan said:**
> Maybe I can make a follow up question. Is there any software available to transfer music to ipods native for linux?

Banshee will sync your mp3`s with your iPod, but I only use that for podcasts. I use gtkpod because of it`s video support - You just drag and drop new songs or videos. 
 I have 3 boxes all with gtkpod installed and I can mess with my iPod to my hearts content.
Alternatively you could Rockbox your iPod then it`s just a matter of copying files just like you would with any usb drive.

[http://download.rockbox.org/manual/rockbox-ipodvideo/rockbox-build.html#rockbox-buildch10.html](http://download.rockbox.org/manual/rockbox-ipodvideo/rockbox-build.html#rockbox-buildch10.html)

---

### Post by pi.boy.travis on 2008-07-18
> **nothingspecial said:**
> Alternatively you could Rockbox your iPod then it`s just a matter of copying files just like you would with any usb drive.

[http://download.rockbox.org/manual/rockbox-ipodvideo/rockbox-build.html#rockbox-buildch10.html](http://download.rockbox.org/manual/rockbox-ipodvideo/rockbox-build.html#rockbox-buildch10.html)


I use Rockbox on my Toshiba Gigabeat.  Highly recommended, but it hasn't been ported to the latest generation ipods yet. . .

---

### Post by rubikscube on 2008-07-23
Hi, 

I have a really newbie question - I have no idea what you are talking about when you say 64 bit or i386. Can someone clarify what this means? Sorry for my ignorance and thanks in advance.

---

### Post by enlightenment now on 2008-07-23
> **rubikscube said:**
> Hi, 

I have a really newbie question - I have no idea what you are talking about when you say 64 bit or i386. Can someone clarify what this means? Sorry for my ignorance and thanks in advance.

1. [64bit]("http://en.wikipedia.org/wiki/64-bit")

2. [i386]("http://en.wikipedia.org/wiki/Intel_80386")

> **XCan said:**
> Maybe I can make a follow up question. Is there any software available to transfer music to ipods native for linux?

As for player that the OP posted a follow up post for I recommend [Amarok]("http://amarok.kde.org/") also.

This Amarok forum post may help:
[http://amarok.kde.org/forum/index.php/topic,15414.0.html](http://amarok.kde.org/forum/index.php/topic,15414.0.html)

---

