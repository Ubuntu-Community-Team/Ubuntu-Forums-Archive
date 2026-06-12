---
title: "Problems upgrading to Hardy"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by danielrs on 2008-04-26
I'm currently using Gutsy and I'm trying to upgrade to Hardy. When I use the "normal" way (in the update-manager), after downloading something (don't know what it is), it freezes. I've downloaded the ISO image and burnt it to a CD, but there's no option for upgrade (tried booting from it and insert it after login).

Any suggestions? 

PS: I'm using a x86 with dual boot XP-Ubuntu.

---

### Post by meborc on 2008-04-26
> **danielrs said:**
> I'm currently using Gutsy and I'm trying to upgrade to Hardy. When I use the "normal" way (in the update-manager), after downloading something (don't know what it is), it freezes. I've downloaded the ISO image and burnt it to a CD, but there's no option for upgrade (tried booting from it and insert it after login).

Any suggestions? 

PS: I'm using a x86 with dual boot XP-Ubuntu.

i suggest you backup everything to xp partition (better yet to external hdd) and do a clean hardy install from cd to ubuntu partition...

---

### Post by Alehbye on 2008-04-26
danielrs,

I'm pretty new as well and had a similar issue. I just used patience. :) I left it to do it's thing and walked away. The issue is, EVERYONE is trying to upgrade and the servers are getting hammered which is in turn causing studdering, download freezes, etc.

If you are actually getting an error, post what it says exactly and I am sure some one on these forums can help.

-Alehbye

---

### Post by danielrs on 2008-04-26
I get no error, the screen just freeze.

it'll take a lot of time to install everything I had.

I'll try to do the clean install. Is there any folder that I have to backup other than /home and /opt?

---

### Post by ghost_ryder35 on 2008-04-26
> **danielrs said:**
> I get no error, the screen just freeze.
 
it'll take a lot of time to install everything I had.
 
I'll try to do the clean install. Is there any folder that I have to backup other than /home and /opt?
did you download the alternate install cd?  that is the one with the option to upgrade

---

### Post by elmer_42 on 2008-04-26
> **danielrs said:**
> I've downloaded the ISO image and burnt it to a CD, but there's no option for upgrade (tried booting from it and insert it after login).
You need to download the alternate disk if you want to upgrade. Just burn it and insert it while your computer is still on. It will see it as a disk of packages and will give you an option to upgrade. Use it. As much as a certain member has spammed this [link]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html") around the forum, it lists what you need to do.

---

### Post by danielrs on 2008-04-26
> **ghost_ryder35 said:**
> did you download the alternate install cd?  that is the one with the option to upgrade

Ooops, I missed that part:), that'll probably solve the problem

---

### Post by danielrs on 2008-04-26
This is the image I got before the window turn blank:[http://bp1.blogger.com/_jNOhZn984Uw/SBEGgCCq59I/AAAAAAAAEtA/YcejQtVKVf0/s1600-h/50-Screenshot-Distribution+Upgrade.png](http://bp1.blogger.com/_jNOhZn984Uw/SBEGgCCq59I/AAAAAAAAEtA/YcejQtVKVf0/s1600-h/50-Screenshot-Distribution+Upgrade.png) . The difference is that is only on: "preparing to upgrade", instead of "Getting new packages", so it will probably happen the same thing with the alternate CD :(

---

### Post by ghost_ryder35 on 2008-04-26
not necessarly. the downloads could be corrupt
could try
```

sudo apt-get clean       #####should delete downloaded packages
sudo apt-get update     ##### make sure the system is update before upgrading
sudo apt-get upgrade   ##### upgrade to get ready for the dist-upgrade
sudo apt-get dist-upgrade  ##### yeah!

```
 
Also running the dist-upgrade from the command line might reveal some error messages that are not being displayed in the gui for apt

---

### Post by danielrs on 2008-04-26
There are 3 updates that I can't do:dpkg-dev, g++ and libc6-dev

---

### Post by meborc on 2008-04-26
> **danielrs said:**
> There are 3 updates that I can't do:dpkg-dev, g++ and libc6-dev

try to force them... **sudo apt-get -f install** it might help to force overwriting some files

---

### Post by danielrs on 2008-04-26
> **meborc said:**
> try to force them... **sudo apt-get -f install** it might help to force overwriting some files

I'm doing: sudo apt-get build-dep. If it does not work after this, I'll try as you suggested

---

### Post by danielrs on 2008-04-26
I'm still not able to do the updates :(

---

### Post by danielrs on 2008-05-06
I've downloaded the Alternate CD, but I get the same problem :(

---

### Post by danielrs on 2008-05-30
When I open update manager I see: [IMG]http://on-logica.net/Screenshot-Update Manager.png[/IMG]

---

