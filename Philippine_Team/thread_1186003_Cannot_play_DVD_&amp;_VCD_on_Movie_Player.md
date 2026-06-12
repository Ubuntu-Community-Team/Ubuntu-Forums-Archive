---
title: "Cannot play DVD &amp; VCD on Movie Player?"
date: 2009-06-12
forum: Philippine Team
---

### Post by zilu54 on 2009-06-12
Balak ku sanang manuod ng Final Fantasy: Advent Children (VCD original copy) at hindi ku siya mapanuod dahil may missing plugin ba yun or file kaya hindi ma play, nag search na aku kasu wala silang nakitang file na para ma read.

Can you guys help me?

---

### Post by guitar_man on 2009-06-13
anong format ng video??
pakitignan nga sa mga folders nya...
may files kasi na pahirapan magplay,kagaya ng .DAT

---

### Post by badrra on 2009-06-13
Gamit ko VLC click ko lang media tapos open disc then choose ko VCD yun na.

---

### Post by zilu54 on 2009-06-13
@guitar_man: nakikita ku ditu ay .DAT and .VCD mga formats nila

---

### Post by Script Warlock on 2009-06-13
sudo apt-get install w32codecs
use vlc or mplayer nasa repo lahat....

or manually  
[B]mplayer   [COLOR=#990000]vcd://[/COLOR]1
kung ayaw pa rin 
[/B][B]mplayer   -cdrom-device   /dev/cdrom   [COLOR=#990000]vcd://[/COLOR]1

or install gxine....
[/B]

---

### Post by dannybuntu on 2009-06-14
1. update sources.list to include medibuntu repos

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

2. install w32codecs *if using 32-bit 

```
$ sudo aptitude install w32codecs
```

3. install dvd support

```
$ sudo aptitude install libdvdcss2
```

4. install vlc player - the **_best video player evar!_**

```
$ sudo aptitude install vlc
```

---

### Post by diegoman on 2009-07-29
try installing "ubuntu-restricted-extras" via add/remove

---

### Post by reneorense on 2009-07-29
> **dannybuntu said:**
> 1. update sources.list to include medibuntu repos

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```2. install w32codecs *if using 32-bit 

```
$ sudo aptitude install w32codecs
```3. install dvd support

```
$ sudo aptitude install libdvdcss2
```4. install vlc player - the **_best video player evar!_**

```
$ sudo aptitude install vlc
```

Amen po ako dito...

VLC or simply updating totem's codecs would do the trick... :D

---

### Post by rannable on 2009-07-29
VLC will play anything...

---

