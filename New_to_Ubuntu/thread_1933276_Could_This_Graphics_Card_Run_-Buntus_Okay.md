---
title: "Could This Graphics Card Run -Buntus Okay?"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by unknowngal on 2012-02-29
I'm wondering if this graphics card would run any type of -buntu okay. I know NVIDIA is pretty well supported, but any information on this particular one?
 
**ATI Radeon 3100 Graphics**

I'm thinking of buying a refurbished computer with that card in it, but if it's not well supported, or lacks good drivers, then I'll just drop it. Thank you!

---

### Post by unknowngal on 2012-02-29
Bump!

---

### Post by Matt__ on 2012-02-29
Its listed as supported here on the [URL="http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html#contenttoc3"]Radeon man page
[/URL]
(assuming its the HD3100 as I don't think there's any other)
[ ]("http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html#contenttoc3")

---

### Post by unknowngal on 2012-02-29
Thank you very much!

---

### Post by Krytarik on 2012-02-29
> **Matt__ said:**
> Its listed as supported here on the [Radeon man page]("http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html#contenttoc3")
> **unknowngal said:**
> Thank you very much!
That doesn't mean that the ATI Radeon HD 3100 is sufficient to run Unity, Gnome Shell, or Compiz (without Unity), hardware-wise! So I'd definitely do some more research, wait for some people here confirming that it works, or, if possible, test an Ubuntu 11.10 or 12.04 pre-release Live CD/DVD/USB-drive on that laptop!

Regards.

Addition: Oh, and if testing it yourself, don't let Unity 2D trick you! ;-) :
```
ps ax | grep unity-2d
```

---

### Post by dFlyer on 2012-02-29
I'd do a search of this forum concerning this video card, to see what problems with unity if any people are facing.

---

### Post by unknowngal on 2012-03-01
> **Krytarik said:**
> That doesn't mean that the ATI Radeon HD 3100 is sufficient to run Unity, Gnome Shell, or Compiz (without Unity), hardware-wise! So I'd definitely do some more research, wait for some people here confirming that it works, or, if possible, test an Ubuntu 11.10 or 12.04 pre-release Live CD/DVD/USB-drive on that laptop!

Regards.

Addition: Oh, and if testing it yourself, don't let Unity 2D trick you! ;-) :
```
ps ax | grep unity-2d
```

Thanks for your reply! I do have a couple of questions/thoughts though...

1. I thought that any -buntu distro would be able to run on older computers without too many problems. Particularly Lubuntu, seeing that it's really a slim version of other -buntus. 

2. About Lubuntu, does it have Gnome Shell or Compiz? I would probably run Lubuntu on the computer I'm considering most likely.

It's actually a small computer by the way, not a laptop. I -would- like more info if at all possible. I haven't found any related threads yet, but it's my first search so I'll try again with another search query. :)

Wait, how would Unity 2D trick me? :P *confused, sorry!*

---

### Post by unknowngal on 2012-03-01
> **dFlyer said:**
> I'd do a search of this forum concerning this video card, to see what problems with unity if any people are facing.

Doing that now! Thanks! :)

---

### Post by HeroOfCanton on 2012-03-01
Good to see you might have found a card for that old computer unknowngal. Even better to see you are making sure this one will work! I love it when people actually pay attention. lol. Best of luck!!!

Compiz does not come with lubuntu by default, but you can install it. More info [here]("http://ubuntuforums.org/showthread.php?t=1576889").
Gnome shell would kind of defeat the purpose of lubuntu (as would Compiz IMO).

You're probably going to have to give up some of the eye candy on that one, but you can always try and see what happens... Different setups tend to produce different results.

You may want to try Xubuntu as a compromise between the two, but remember I'm proudly biased towards my new favorite DE. :)

---

### Post by Krytarik on 2012-03-01
> **unknowngal said:**
> 1. I thought that any -buntu distro would be able to run on older computers without too many problems. Particularly Lubuntu, seeing that it's really a slim version of other -buntus. 

2. About Lubuntu, does it have Gnome Shell or Compiz? I would probably run Lubuntu on the computer I'm considering most likely.
Lubuntu, or other lightweight DEs, should run fine - as long as you don't try forcing Compiz upon them. :D For a detailed overview of these, have a look here:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

> **unknowngal said:**
> It's actually a small computer by the way, not a laptop.Oops, somehow foisted a laptop on you; guess because everyone seems to buy/own laptops nowadays. :P

> **unknowngal said:**
> Wait, how would Unity 2D trick me? :P *confused, sorry!*
Unity 2D looks almost the same as the regular Unity, but, unlike that, doesn't require state-of-the-art graphics; that leads to confusions like [here]("http://ubuntuforums.org/showthread.php?t=1933585"). :P

---

### Post by mastablasta on 2012-03-01
This card
RS780                       RadeonHD 3100/3200/3300

 
has 3D acceleration even with opensource drivers only. and as i know AMD provides their own drivers for it as well.
 
> **unknowngal said:**
> Thanks for your reply! I do have a couple of questions/thoughts though...
 
1. I thought that any -buntu distro would be able to run on older computers without too many problems. Particularly Lubuntu, seeing that it's really a slim version of other -buntus. 

I don't know your CPU and RAM but indeed they will run even on old computers. the one you plan to buy is older but not really that old. 
 
Minimum 256 MB ram is recomended though.
 
> 
2. About Lubuntu, does it have Gnome Shell or Compiz? I would probably run Lubuntu on the computer I'm considering most likely.
*
 
 
Lubuntu uses LXDE not Gnome. Xubuntu uses XFCE (again not Gnome) and Kubuntu uses KDE (and not Gnome). KDE has Compiz like effects using Kwin. The only one that uses Gnome is Ubuntu. If it feels sluggish you can use unity 2D (instead of default 3D).
If you want to give Kubuntu a try it can also run well on a bit older systems but to get it run faster low fat package needs to be installed (i think that one removes effects a bit).
 
Lubuntu is the lightest, but you would probably do just fine with Xubuntu which is a bit more mature DE than LXDE.
 
 
but the onyl way you woll knwo is to try it live and see how it runs. if computer has enough ram you can run Ubuntu anyway...

---

### Post by pootan on 2012-03-01
That card will run Xubuntu or Lubuntu no problems. . 

 Lubuntu is a very good way to start off your ubuntu experience as it starts off using very low resources and you can add any programs you like from the repository.

---

