---
title: "I am new   I am having program installing problems"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by stormchas2000 on 2008-06-22
Ok I  have ubuntu 8.04 and I have installed limewire, opera web browser, as well as other software. from other sites,  and i have used Gdeb to install them. everything checks out and it says installing, then it is done and i can't find the program.       did it install it or did it loose it.  i dont know  cant find the program, i can find the package,   but not a working program.    please help,

oh and so far i cant get libdvdread3 to work so i can watch my dvd's   but right now that is not the big problem

---

### Post by macaholic on 2008-06-22
Are the programs listed in synaptic? (System Administration > Synaptic Package Manager)

---

### Post by sharks on 2008-06-22
For the noobs better install it via synaptic(package manager) from system---administration.

---

### Post by macaholic on 2008-06-22
> **sharks said:**
> For the noobs better install it via synaptic(package manager) from system---administration.
That won't work for his case since he is installing non-repository software like limewire and opera.

---

### Post by aysiu on 2008-06-22
I've never installed Limewire, but Opera should have a menu item under applications. You can always launch it by pressing Alt-F2 and typing ```
opera
```

---

### Post by stormchas2000 on 2008-06-22
Ok i tried the alt-f2  and typed it in      it could not find it

---

### Post by macaholic on 2008-06-22
Are the packages you isntalled listed in synaptic as installed?

---

### Post by aysiu on 2008-06-22
If *opera* didn't launch Opera, then it's not installed.

It's not enough to open the .deb file with gDebi. You also have to click *Install Package* to have it installed.

---

### Post by RiceMonster on 2008-06-22
Check this out if you want to watch DVDs. You'll need to install livdvdcss2 to watch DVDs.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Also, If you're using Totem for DVDs I'd reccomend typing this in a terminal:

```
sudo apt-get install totem-xine && sudo apt-get remove totem-gstreamer
```

That will change totem to use the xine backend, which I find works better for DVDs.

---

