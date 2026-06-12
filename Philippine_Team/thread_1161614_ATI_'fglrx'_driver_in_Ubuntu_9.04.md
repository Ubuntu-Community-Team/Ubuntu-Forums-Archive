---
title: "ATI 'fglrx' driver in Ubuntu 9.04"
date: 2009-05-16
forum: Philippine Team
---

### Post by mghambunan on 2009-05-16
Meron ba dito ngkaproblema sa ATI 'fglrx' driver after installing or upgrading to Ubuntu 9.04? How did you solve this problem?

I'm planning on upgrading my system to Ubuntu 9.04 but nagdadalawang isip ako dahil hindi na supported sa Ubuntu 9.04 ang ATI 'fglrx' driver. 

Your help is highly appreciated. Thanks...

---

### Post by loell on 2009-05-17
I'm an nvidia, 

I think the ATI open source driver kinda replaced the 'fglrx'.

---

### Post by frustphil on 2009-05-17
There's no fglrx that's compatible with the Xorg 9.04 is shipping with AFAIK. So you either have to have an open source driver or downgrade to 8.10 so you could use fglrx. You could also downgrade your Xorg and use fglrx.

---

### Post by kingair_six on 2009-05-17
same issue here. sucks badly that a regression in terms of graphics performance is taken place in this case. although i wonder, every now and then i read people got some fglrx version to run propperly under 9.04.

however, all that happens when i compile the packages from the ati-provided version (8.6002) is a wildly coloured screen. no luck there.

the support by OSS drivers (-ati; -radeon; -radeonhd) is, mildly put, poor. no offence to the hard-working developers, but the performance just does not compete just as the stability doesn't. 3D does not work at all (compiz, google earth or the like are just not doing a thing), which is a major loss for my enjoyment of linux. 

so, should we all consider buying an nvidia card quickly or can we poor ATI users hope for resurrection from the unsupported? 

any constructive ideas or clues? sorry for the slightly polemic tone, it is just a little bit frustrating, this issue.

---

### Post by oenone on 2009-06-15
do i need to install the ati drivcers from their site or should i sue the ones found in system - ardware drivers ???

---

### Post by ismoke101 on 2009-06-22
ganun din sakin, ang malas lang kasi, kakabili ko lang last month nang video card, para sana dun sa jaunty, kaso, not supported, e panu yun pag na iwanan na tayo ng upgrade sa 8.10? di na tyu updated wawwwwwwwaaaaaa](*,)	](*,)	](*,)



-----------------------------
p4 2.something
512 ram
512 ati agp x1650 pro video card 
------------------------------

---

### Post by frustphil on 2009-06-22
> **ismoke101 said:**
> ganun din sakin, ang malas lang kasi, kakabili ko lang last month nang video card, para sana dun sa jaunty, kaso, not supported, e panu yun pag na iwanan na tayo ng upgrade sa 8.10? di na tyu updated wawwwwwwwaaaaaa](*,)    ](*,)    ](*,)



-----------------------------
p4 2.something
512 ram
512 ati agp x1650 pro video card 
------------------------------

There's hope with Karmic. Just be patient. For the mean time, just use the open source driver.

---

### Post by oldrocker99 on 2009-06-22
> **frustphil said:**
> There's hope with Karmic. Just be patient. For the mean time, just use the open source driver.

THAT is devoutly to be hoped; I'm getting by with the radeon driver (the radeonhd driver is much slower in glxgears). IF the next Xorg allows the so-called "legacy" fglrx drivers, my faith in Canonical will be restored.

:guitar:

---

