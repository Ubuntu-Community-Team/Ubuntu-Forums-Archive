---
title: "problems whit ubuntu eee on my 901"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by sensimanic on 2008-10-22
I just bought a pceee 901 and put in 2bgs of ram och ubuntu eee. Every thing works fine, all buttons, networks everyting... everything but "visuel effects", everytime i chous normal or extra effects, a message pops up that says i dont have compiz? why?
It is the first time i use linux, so keep in pretty simpel please hehe

---

### Post by No-Neck on 2008-10-22
The logical answer would be that you don't have compiz.

I forget all the packages, but try this in the terminal:

```
sudo apt-get install compiz compizconfig-settings-manager
```

Compiz has some incredible effects, like multiple desktops on a 3D cube. Very impressive, I have Debian on an EEE PC 1000 and can confirm they do have enough power for such effects. :)

---

### Post by LowSky on 2008-10-22
there is a comuple resons you might not have compiz, 

1. you cant run it as your graphics are horrible on that machine
2. or you need a grapihcis driver: go to system>admin>restricted drivers, and turn the graphics driver on

---

### Post by Meskarune on 2008-10-22
I looked up your computer. Is it similar to this?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220354R]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834220354R")

Do you have an integrated graphics card? If your graphics card does not support 3D rendering compiz will not work on your computer. If your graphics card does support 3D then the drivers may not be installed or there may not be any linux drivers for your card.

---

### Post by No-Neck on 2008-10-22
I have the same PC as the OP, mine just has a larger screen and a different SSD. I can confirm that Compiz works just fine, a testament to Compiz itself. However, mine runs Debian.

---

### Post by sensimanic on 2008-10-22
> **Meskarune said:**
> I looked up your computer. Is it similar to this?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220354R]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834220354R")

Do you have an integrated graphics card? If your graphics card does not support 3D rendering compiz will not work on your computer. If your graphics card does support 3D then the drivers may not be installed or there may not be any linux drivers for your card.

I tried to update the graphics drivers and the system told me i had the latest version.
I installed compiz, and it dosent work right, i gess my hardware is not god enoug

---

### Post by cjv8888 on 2008-10-22
Have a look at the Eee Ubuntu forum [here]("http://forum.eeeuser.com/viewforum.php?id=43").

---

### Post by Bölvaður on 2008-10-22
Here is a list of the packages I found installed on my system.

But first, go into System &#8594; Administration &#8594; Synaptic Package Manager
and search for "compiz" (the search button is in the upper right corner or middle).

Here is the list of my packages (make sure you got them also)
If you dont have any of them (indicated with blank box next to it) then you need to click the box and pick "mark for installation". And when you have marked all the packages you need, click Apply from the toolbar (next to the green tic).
you can also use apt-get from the terminal like the guy above me suggested.. but I like to get newcommers warm welcome with Synaptic package manager and Add/Remove, to let them see it is just as good as the commandline, just without some extra advance stuff you dont have to think about yet :)

compiz
compizconfig-backend-gconf
compizconfig-settings-manager
compiz-core
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
libcompizconfig0
libdecoration0
python-compizconfig

I do not use emerald but you might want to check it out, it is a window decorator.
Also you might want to install "simple-ccsm" as it is a program that has premade compiz settings.

---

