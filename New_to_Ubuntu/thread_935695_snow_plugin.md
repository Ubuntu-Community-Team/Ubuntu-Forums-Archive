---
title: "snow plugin"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by thomas_1990 on 2008-10-01
quick question..does anyone know where I can find the snow plugin for compiz..and also how to install?.. :D

thomas

thankyou

---

### Post by tjwoosta on 2008-10-02
here is the page for Ubuntu Hardy

[http://forum.compiz-fusion.org/showthread.php?p=56851]("http://forum.compiz-fusion.org/showthread.php?p=56851")

here is the page for Ubuntu Gutsy

[http://forum.compiz-fusion.org/showthread.php?t=5303]("http://forum.compiz-fusion.org/showthread.php?t=5303")


just read carefully, everything you need to know is there




also on the Hardy install page when you see the part that looks like this

```
cd ~/compiz
git clone git://anongit.compiz-fusion.org/users/wodor/anaglyph
git clone git://anongit.compiz-fusion.org/fusion/plugins/atlantis
git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
git clone git://anongit.compiz-fusion.org/users/rcxdude/dialog
git clone git://anongit.compiz-fusion.org/users/rcxdude/ghost
git clone git://anongit.compiz-fusion.org/users/metastability/snowglobe
git clone git://anongit.compiz-fusion.org/fusion/plugins/tile

**skip over it and use the part below it that looks like this**

[CODE]
wget -O /tmp/cubemodel.tar 'http://oreaus.googlepages.com/cubemodel.tar' && tar -xf '/tmp/cubemodel.tar' -C ~/compiz/
wget -O /tmp/elements.tar 'http://oreaus.googlepages.com/elements.tar' && tar -xf '/tmp/elements.tar' -C ~/compiz/
wget -O /tmp/extra-animations.tar 'http://oreaus.googlepages.com/extra-animations.tar' && tar -xf '/tmp/extra-animations.tar' -C ~/compiz/
wget -O /tmp/fireflies.tar 'http://oreaus.googlepages.com/fireflies.tar' && tar -xf '/tmp/fireflies.tar' -C ~/compiz/
wget -O /tmp/freewins.tar 'http://oreaus.googlepages.com/freewins.tar' && tar -xf '/tmp/freewins.tar' -C ~/compiz/
wget -O /tmp/photowheel.tar 'http://oreaus.googlepages.com/photowheel.tar' && tar -xf '/tmp/photowheel.tar' -C ~/compiz/
wget -O /tmp/screensaver.tar 'http://oreaus.googlepages.com/screensaver.tar' && tar -xf '/tmp/screensaver.tar' -C ~/compiz/
wget -O /tmp/snow.tar 'http://oreaus.googlepages.com/snow.tar' && tar -xf '/tmp/snow.tar' -C ~/compiz/
wget -O /tmp/stars.tar 'http://oreaus.googlepages.com/stars.tar' && tar -xf '/tmp/stars.tar' -C ~/compiz/
wget -O /tmp/wallpaper.tar 'http://oreaus.googlepages.com/wallpaper.tar' && tar -xf '/tmp/wallpaper.tar' -C ~/compiz/
wget -O /tmp/wizard.tar 'http://oreaus.googlepages.com/wizard.tar' && tar -xf '/tmp/wizard.tar' -C ~/compiz/


```

---

### Post by bigdee973 on 2008-10-02
> **tjwoosta said:**
> here is the page for Ubuntu Hardy

[http://forum.compiz-fusion.org/showthread.php?p=56851]("http://forum.compiz-fusion.org/showthread.php?p=56851")

here is the page for Ubuntu Gutsy

[http://forum.compiz-fusion.org/showthread.php?t=5303]("http://forum.compiz-fusion.org/showthread.php?t=5303")


just read carefully, everything you need to know is there




also on the Hardy install page when you see the part that looks like this

```
cd ~/compiz
git clone git://anongit.compiz-fusion.org/users/wodor/anaglyph
git clone git://anongit.compiz-fusion.org/fusion/plugins/atlantis
git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
git clone git://anongit.compiz-fusion.org/users/rcxdude/dialog
git clone git://anongit.compiz-fusion.org/users/rcxdude/ghost
git clone git://anongit.compiz-fusion.org/users/metastability/snowglobe
git clone git://anongit.compiz-fusion.org/fusion/plugins/tile

**skip over it and use the part below it that looks like this**

[CODE]
wget -O /tmp/cubemodel.tar 'http://oreaus.googlepages.com/cubemodel.tar' && tar -xf '/tmp/cubemodel.tar' -C ~/compiz/
wget -O /tmp/elements.tar 'http://oreaus.googlepages.com/elements.tar' && tar -xf '/tmp/elements.tar' -C ~/compiz/
wget -O /tmp/extra-animations.tar 'http://oreaus.googlepages.com/extra-animations.tar' && tar -xf '/tmp/extra-animations.tar' -C ~/compiz/
wget -O /tmp/fireflies.tar 'http://oreaus.googlepages.com/fireflies.tar' && tar -xf '/tmp/fireflies.tar' -C ~/compiz/
wget -O /tmp/freewins.tar 'http://oreaus.googlepages.com/freewins.tar' && tar -xf '/tmp/freewins.tar' -C ~/compiz/
wget -O /tmp/photowheel.tar 'http://oreaus.googlepages.com/photowheel.tar' && tar -xf '/tmp/photowheel.tar' -C ~/compiz/
wget -O /tmp/screensaver.tar 'http://oreaus.googlepages.com/screensaver.tar' && tar -xf '/tmp/screensaver.tar' -C ~/compiz/
wget -O /tmp/snow.tar 'http://oreaus.googlepages.com/snow.tar' && tar -xf '/tmp/snow.tar' -C ~/compiz/
wget -O /tmp/stars.tar 'http://oreaus.googlepages.com/stars.tar' && tar -xf '/tmp/stars.tar' -C ~/compiz/
wget -O /tmp/wallpaper.tar 'http://oreaus.googlepages.com/wallpaper.tar' && tar -xf '/tmp/wallpaper.tar' -C ~/compiz/
wget -O /tmp/wizard.tar 'http://oreaus.googlepages.com/wizard.tar' && tar -xf '/tmp/wizard.tar' -C ~/compiz/


```

now it says to go to cd /compiz/atlantis2 by skipping what you mentioned i dont have an atlantis2 could u explain for me please.

---

### Post by nkri on 2008-10-02
Do you know if this will work using Compiz 0.7.6 (not 0.7.4) on Hardy?

Thanks!
-nkri

---

### Post by tjwoosta on 2008-10-04
i have .0.7.6 and snow plugin works fine, but i couldn't get the elements one working

i havn't tried any others

---

### Post by Kurosawa22 on 2008-11-19
I'm confused, I want the cool snow effect but I'm very new to Ubuntu and some things are just passing me by. 
I managed to get Compiz running and it has most things on there but not the snow tab.
I'm running ubuntu 8.10
I don't know what herdy or gusty is. I use windows normally and things tend to be dumbed down to the point where you just click it and it goes. 
Ubuntu is interesting though so I'll keep at it. 
cheers

---

### Post by Aiello on 2008-11-19
I am using the Compiz Fusion Elements plug in (gives leaves, fireflies, bubbles, snow, and stars all in one plug in) in 0.7.6 and it seems to work fine for me. I installed via the script made by the creator of the plug in, which can be downloaded here: [http://www.elementsplugin.com/downloads/]("http://www.elementsplugin.com/downloads/"). Even though it says the script is meant for .0.7.4, it seems to work fine in .0.7.6 for me. I don't know how it will work in 8.10 version of Compiz Fusion though.

---

### Post by tjwoosta on 2008-11-19
> I'm confused, I want the cool snow effect but I'm very new to Ubuntu and some things are just passing me by.
I managed to get Compiz running and it has most things on there but not the snow tab.
I'm running ubuntu 8.10

with ubuntu 8.10 the snow plugin should be easy to install


open synaptic package manager and search for compiz

look through the list that shows up and install "compiz-fusion-plugins-extra" and "compiz-fusion-pugins-unsupported"

after it finishes installing reboot your computer and the plugins should all be installed

if you dont already have it you should also install CCSM (compiz config settings manager)

(you can find CCSM in the add/remove list under the applications menu, just make sure to set it to search for "all available applications")

---

