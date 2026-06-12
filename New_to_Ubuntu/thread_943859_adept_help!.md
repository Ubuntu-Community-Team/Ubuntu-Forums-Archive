---
title: "adept help!"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by benji.ijneb on 2008-10-10
I'm planning to switch to Kubuntu 8.10 (from ubuntu) when it's released. I've been looking at some live cd images of intrepid beta, and i'm very impressed! however, I have noticed that by comparrison to synaptic (which i don't want to install in kubuntu), adept 3 is missing some essential functionality. Most notably, it doesn't display local or obsolete packages (very handy) or residual config (equally so)

are there any alternative ways of getting this information that don't include the installation of synaptic? (i'm open to terminal-based solutions if I must)

thanks for all your help in advance!

---

### Post by benji.ijneb on 2008-10-11
sorry, but...

bump!

---

### Post by SunnyRabbiera on 2008-10-11
Well I think the new adept in Kubuntu 8.10 will probably be QT4 based, so a lot of functions are probably going to be missing for some time (it seems that every every KDE4 app is taking forever, Amarok, Dragon Player and things like that are seriously behind the functions you see in Amarok kde3 and Kaffeine)
Maybe you wont have a choice in it and have to install synaptic, but me i prefer synaptic over adept so such a choice would not be hard for me if I didnt opt to stay with Hardy.

---

### Post by benji.ijneb on 2008-10-11
that's just annoying...
is there any way to remove all residual config packages from the terminal? and any way to display packages that are not from repositories? oh! and any way to force the version of a package in adept / terminal?

hmm...

thanks so far, anyway!

---

### Post by SunnyRabbiera on 2008-10-11
Well apt does have a few commands for you to try:
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean

But for a graphical approach yeh I am afraid it will be a while before the new adept becomes as usable as the adept in hardy.

---

### Post by awakatanka on 2008-10-11
> **SunnyRabbiera said:**
> Well I think the new adept in Kubuntu 8.10 will probably be QT4 based, so a lot of functions are probably going to be missing for some time (it seems that every every KDE4 app is taking forever, Amarok, Dragon Player and things like that are seriously behind the functions you see in Amarok kde3 and Kaffeine)
Maybe you wont have a choice in it and have to install synaptic, but me i prefer synaptic over adept so such a choice would not be hard for me if I didnt opt to stay with Hardy.
Dragon player and Kaffaine are not the same, kaffaine is getting a kde4 version. Dragon player is working as it should don't have any problem with it. And it is just a simple player nothing more.

[http://kaffeine.kde.org/](http://kaffeine.kde.org/)
[http://www.dragonplayer.org/](http://www.dragonplayer.org/)

And here some info over the function that are in/comeing back our are dropped : [http://amarok.kde.org/blog/archives/809-Missing-features-in-Amarok-2.html](http://amarok.kde.org/blog/archives/809-Missing-features-in-Amarok-2.html)

Adept isn't working for me to it just is in development like kubuntu 8.10 is. using synaptic till its ready

---

### Post by SunnyRabbiera on 2008-10-11
> **awakatanka said:**
> Dragon player and Kaffaine are not the same, kaffaine is getting a kde4 version. Dragon player is working as it should don't have any problem with it. And it is just a simple player nothing more.

[http://kaffeine.kde.org/](http://kaffeine.kde.org/)
[http://www.dragonplayer.org/](http://www.dragonplayer.org/)

And here some info over the function that are in/comeing back our are dropped : [http://amarok.kde.org/blog/archives/809-Missing-features-in-Amarok-2.html](http://amarok.kde.org/blog/archives/809-Missing-features-in-Amarok-2.html)

I know dragonplayer and kaffeine are not the same app, but it does suck as a standard until kaffeine is fully ported to KDE4.
Amarok for KDE4 is still very buggy and unstable and those who push out the known to be stable amarok for KDE3 in favor for the one in KDE4 is insane.
Actually i think all KDE4 distros are insane, KDE4 is still too new and unstable to make it a standard.

---

### Post by benji.ijneb on 2008-10-11
let's not get too sidetracked here...

surely if synaptic is just a front-end for apt, there must be an apt command to show locally installed aps, and remove residual config... musn't there?

---

### Post by awakatanka on 2008-10-11
try kpackage, don't know if it is capable what you want didn't tryed it for a long time

---

### Post by venik212 on 2008-11-03
If I were to install Synaptic in Kubuntu, will I have to uninstall or upgrade packages that were installed using Synaptic with it?  Once Adept grows up and regains its lawful functions, will I be able to use it on those packages that were installed with Synaptic?

---

