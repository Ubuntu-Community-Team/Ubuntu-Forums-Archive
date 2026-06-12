---
title: "Opera/Firefox Prob - Flash"
date: 2008-07-20
forum: Philippine Team
---

### Post by initial_m on 2008-07-20
mga bro, help naman, di ako makapag browse ng maayus sa mga site na gumagamit ng flash, magulo ung screen and sometimes ayaw maopen nung my mga flash objects.. such as [www.nick.com/www.nba.com](www.nick.com/www.nba.com)

try nyo lang ung mga site na post ko, sa NBA site nag loloko ung sa mga tabs nya di mo makikita, ung sa nick nag hahang ung page nya, wala ka makita blank na white pero ung heading makikita mo..

[[IMG]http://img172.imageshack.us/img172/1295/screenshot1pj5.th.png[/IMG]](http://img172.imageshack.us/my.php?image=screenshot1pj5.png)

---

### Post by loell on 2008-07-20
na try mo  nang ni-reinstall ang flash?

---

### Post by initial_m on 2008-07-20
i dont know how bro. saka tatakot ako baka mag loko Ubuntu.
-tinatamad nako mag reinstall ng Ubuntu..

---

### Post by linuxisfree on 2008-07-20
Punta ka lang Synaptic Package Manager (System --> Administration --> Synaptic Package Manager) and look for flashplugin-nonfree (i think that's the one you're using). Then right click then mark for reinstallation.

---

### Post by loell on 2008-07-20
plugin lang naman yun, wala namang mangyayari pag ne-reinstall mo sya

anyway kung gusto mong itry, just do a .

```
sudo apt-get remove --purge flashplugin-nonfree
```

install mo lang ulit

```
sudo apt-get install flashplugin-nonfree
```

tingnan mo kung may pinagkaiba.

edit--

ayun.. nauna si linuxisfree :D

---

### Post by initial_m on 2008-07-20
I already reinstall mga bros but still having the same prob..:(

---

### Post by loell on 2008-07-20
not sure if this will make any difference how about deleting flash settings

first backup your settings

```
cp -rf .macromedia/ macromediabackup
```

then delete the settings

```
rm -rf .macromedia
```

try restarting firefox.

---

### Post by initial_m on 2008-07-20
Im using Opera, would it be ok.. an then what will happen if I do that, mababalik ba ung settings na sinasabi mo sir loell?

---

### Post by linuxisfree on 2008-07-20
Even if you use opera, i THINK it should be the same... did you uninstall it also, before deleting the folder?
EDIT: Wait... my bad, sir loell's code uninstalled flash pala... sorry.

---

### Post by loell on 2008-07-20
gagawa lang ang flash nang bagong settings

pag-mag loko, for some strange reason, ibalik natin yung lumang settings na binackup mo.

---

### Post by initial_m on 2008-07-20
Wala paring nangyari sir loell, try ko na gamitin ung code mo sa terminal.. any idea?

---

### Post by loell on 2008-07-20
tiningnan ko ulit yung screenshot mo, may compositing ka, Compiz/desktop effects?

1. what's your graphics card?

2.ano yung side toolbar sa browser mo? plugin yun?

---

### Post by linuxisfree on 2008-07-20
Use these code to uninstall and reinstall flash.

```
sudo apt-get remove --purge flashplugin-nonfree
``````
sudo apt-get install flashplugin-nonfree
```

---

### Post by initial_m on 2008-07-20
Meron akong Compiz.. 
Graphics Card = ATi Radeon Xpress 1550 512MB
side bar wala un sir loell options lang un sa opera...

---

### Post by initial_m on 2008-07-20
> **linuxisfree said:**
> Use these code to uninstall and reinstall flash.

ok na ba ung sa reinstall sa Synaptic Mngr, dun ko kasi ni reinstall..

---

### Post by linuxisfree on 2008-07-20
> **initial_m said:**
> ok na ba ung sa reinstall sa Synaptic Mngr, dun ko kasi ni reinstall..

Pwede rin naman... you can also uninstall and reinstall flash in Synaptic...

---

### Post by loell on 2008-07-20
di kaya sa opera lang talaga ito?

found an iteresting thread [http://help.lockergnome.com/linux/10-Flash-problems-ftopict414452.html]("http://help.lockergnome.com/linux/10-Flash-problems-ftopict414452.html")

basically try to execute this command,

```
export OPERAPLUGINWRAPPER_PRIORITY=0
```

then

```
opera & 
```

---

### Post by initial_m on 2008-07-20
sabi din kasi ng bayaw ko Sir Loell, kahit sa Firefox ganun din, they used to visit that site kasi sa haus nung naka IE sila, pero napansin nya nung try nya sa Firefox using Ubuntu.. and even Opera daw..

anyways sir loell, try ko ung code......

---

### Post by initial_m on 2008-07-20
wala paring nangyari sir loell, nawawala pa rin ung mga objects..:(

---

### Post by loell on 2008-07-20
heheh, i'm out of ideas :D

probably a graphics driver problem?

one last thing, can you disable desktop effects , see if it makes any difference?

---

### Post by linuxisfree on 2008-07-20
> **loell said:**
> heheh, i'm out of ideas :D

probably a graphics driver problem?

one last thing, can you disable desktop effects , see if it makes any difference?

@loell: I probably have to agree with you there... i visited those sites, ok naman sakin.

@initial_m: ano ba hardware mo?

---

### Post by initial_m on 2008-07-20
I tried using Firefox: 
[[IMG]http://img133.imageshack.us/img133/7259/screenshot1yq0.th.png[/IMG]](http://img133.imageshack.us/my.php?image=screenshot1yq0.png)

it used to work on Firefox, but look sir loell on the side menus, napapatungan ng objects ng Middle page..:(

---

### Post by initial_m on 2008-07-20
@ linuxfree

- Processor: AMD Athlon 64 X2 2.5 GHz
  Video: ATi Radeon Xpress x1550 512MB
  Memory: 2 Gb PC 667

---

### Post by loell on 2008-07-20
wala namang problema dun  kung nakapatong yung isang object sa submenus

yung center pane nang page ay parehas lang ang links nang nandoon sa submenus.

dito sa aking yun din ang display nang page.

---

### Post by initial_m on 2008-07-20
It does bro. kasi sa NBA.com yan ang nagiging same prob, kasi di ko makita ung mga selection sa sub menus nung mga tabs, yan ang prob bat kung normal talga ung page dapat makikita bro...sa IE sa windows ok naman, meron bang ways para makagamit ng IE 7 sa Ubuntu?:(

---

### Post by loell on 2008-07-20
maybe you can use [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Installation")

---

### Post by linuxisfree on 2008-07-20
You can also try using Epiphany browser like i do... just a suggestion:D

---

