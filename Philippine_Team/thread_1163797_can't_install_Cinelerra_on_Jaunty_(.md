---
title: "can't install Cinelerra on Jaunty :("
date: 2009-05-19
forum: Philippine Team
---

### Post by killer_d76 on 2009-05-19
i have tried using this process from Cinelerra site  [http://cinelerra.org/getting_cinelerra.php#ubuntu]("http://cinelerra.org/getting_cinelerra.php#ubuntu") unfortunately still no good.. i am looking for a nice OpenSource Video editting software for my personal video editing only.. have anybody installed it with success on Jaunty?.. patulong naman oh! :(

---

### Post by Script Warlock on 2009-05-19
ako meron file nyan 8.10 pero nagswitch ako sa kdenlive bak2bak wid kino..galing ng kdenlive

---

### Post by killer_d76 on 2009-05-19
try ko nga kdenlive.. thanks bro.

---

### Post by killer_d76 on 2009-05-19
i got error after i install kdenlive using this command from their site..

```
sudo apt-get install kdenlive dvgrab frei0r-plugins swh-plugins libfaad0
```

---

### Post by Script Warlock on 2009-05-19
sdl llibraries ata ang kulang sayo bro -dev..nagcompile ka ba?

---

### Post by killer_d76 on 2009-05-19
pano yun boss?... hehehe sorry di ko ma-gets eh.

---

### Post by Script Warlock on 2009-05-19
try to read this [https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/363430](https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/363430)
and this one [http://www.kdenlive.org/forum/kdenlive-073-ubuntu-jaunty](http://www.kdenlive.org/forum/kdenlive-073-ubuntu-jaunty)

sa akin no problem ang installation sa 9.04 uninstalled and reinstall lately...no glitches

---

### Post by Script Warlock on 2009-05-19
or install the deb package at your own risk sabi nga....

[https://launchpad.net/ubuntu/jaunty/i386/+search?text=kdenlive](https://launchpad.net/ubuntu/jaunty/i386/+search?text=kdenlive)

---

### Post by loell on 2009-05-20
yeah, it'sa bug with kdenlive

from [https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/363430/comments/1]("https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/363430/comments/1")


> 

I confirm the bug.

Workaround:
1 uninstall frei0r-plugins
2 start kdenlive
3 make configuration wizard
4 close kdenlive
5 reinstall frei0r-plugins


---

### Post by Script Warlock on 2009-05-20
everything is fine sa laptop ko ang kdenlive running sa 9.04 no glitches...wala akong ginawa install lang sa terminal running fine at kita naman ang mlt module during configuration.. pero kung may sayad nga sayo then sundin na lang ang workaround.

---

### Post by killer_d76 on 2009-05-21
i was not able to install any of the video editting software that i prefer.. though i haven't tried KINO yet.. i'll try and do a fresh install of Jaunty and install Cinelerra afterwards ;).. thanks for all the help though!.. ):P

---

### Post by Samhain13 on 2009-05-21
> **killer_d76 said:**
> ...i am looking for a nice OpenSource Video editting software for my personal video editing only...

Blender (in Video Sequence Editor mode). Been using it for basic video editing for around a year now. It's not easy to use at first but you'll get the hang of it. And I can help you with what I can. :D

Currently using the non-install ( version 2.48 ) package from the Blender site, not the one in the repos. Basically, you download and unpack it, CD to the unpacked directory and do a "$ ./blender" to start.

---

