---
title: "Somebody give me a cookie."
date: 2004-12-16
forum: Programming Talk
---

### Post by mattisking on 2004-12-16
Well, I'm still pretty much a Linux newbie though I've come a decent ways in the past couple of months. Since switching from Fedora Core 2 (and testing 3) to Ubuntu I've been very happy and even more so since moving to Hoary. 

Recently the Hoary Mono distribution switched from 1.0.2 to 1.0.4 but only some of the packages. Certain packages like mono-assemblies-base haven't been updated so  movingto 1.0.4 isn't possible yet through Synaptic though if you're not paying attention (and using apt-get) you may accidentally remove mono in the process of thinking you are upgrading.

Anyway, having tired of waiting for this to be fixed I set about trying to build not only Mono, but also all the additional 'sharp' packages that are requirements to getting applications like MonoDevelop and Blam running. After quite a few evenings of trying (with a slight delay while the gnome-menus broke) I finally got everything including Monodevelop built and running. 

I highly recommend you others that don't want to wait for the packages and aren't using mission critical machines try out 1.1.3 instead of the latest 1.0.5 as the build/install process is far simpler. Still, you have to get quite a bit more than just mono going to get MonoDevelop running. I've been about to completely lose my temper over it a couple times now.

Anyway, yay. Now give me my cookie!

---

### Post by kamstrup on 2004-12-16
There you go *tosses a cookie to mattisking*

There's nothing like compiling stuff for your self. You learn quite a lot from it.

Cheers!

---

### Post by jdong on 2004-12-17
Guys, I have mono 1.0.5 packaged for Warty:[http://sourceforge.net/forum/forum.php?forum_id=430354](http://sourceforge.net/forum/forum.php?forum_id=430354)


I'll have it bumped to the backports stable tree over the weekend.

---

### Post by Enygma on 2004-12-20
Just wondering, jdong, does that contain the latest version of gecko-sharp?
If not, you know where I can get it?

Been playing around with Mono for a few weeks now and I'm really quite impressed.

---

### Post by jdong on 2004-12-20
Not currently. I'm backporting that as we speak.

---

### Post by jdong on 2004-12-20
uploaded into warty-backports-staging.

---

### Post by Enygma on 2004-12-20
Cool, excellent stuff! :D

---

