---
title: "installing cube desktop"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by uper104 on 2008-05-07
ohkay... im following this tutorial and its rather easy to comprehend ... 

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

but when i get to this part

Now we need to find and install 4 key packages xserver-xgl, emerald-themes, beryl and xorg-driver-fglrx, the easiest way to do this is by searching and selecting as show on the pictures.

i can find all of them fine ... but not all of them download and i get an error message when its all done... 

what do i do?

---

### Post by tjwoosta on 2008-05-07
first off, your following a tutorial for setting up the cube in ubutu edgy (way outdated)


with ubuntu hardy or gutsy for that matter they come with compiz preinstalled

(compiz is the up to date version or beryl)


Depending on what you have already screwed up while trying to install beryl, the only package you would need to install would be the 

Compiz Config Settings Manager

go to Applications-Add/Remove..   then look up compiz (it should be the first in the list)

after installing the CCSM just go to System-Preferences-Advanced Desktop Effects Settings and turn on whatever extras you want including the cube

---

### Post by dondad on 2008-05-07
> **uper104 said:**
> ohkay... im following this tutorial and its rather easy to comprehend ... 

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

but when i get to this part

Now we need to find and install 4 key packages xserver-xgl, emerald-themes, beryl and xorg-driver-fglrx, the easiest way to do this is by searching and selecting as show on the pictures.

i can find all of them fine ... but not all of them download and i get an error message when its all done... 

what do i do?

What version of ubuntu are you running? That tutorial is quite old. If you have Hardy, compiz  (which replaced Beryl) should be installed by default. Emerald themes is in the repository also. 

If on hardy, make sure that you have the restricted drivers installed and you should then be able to turn on the effects if your video card supports them. 

In synaptic, do a search for compiz and make sure it is intalled. Also, in that same area will be the compiz configuration manager. Install that also. Most of this should run out of the box.

---

### Post by bumanie on 2008-05-07
The mention of beryl makes me think that you are following something that is out of date, as beryl is no longer a supported nor ongoing project in its own right. It was fused with compiz to form compiz-fusion. I suggest following [this]("http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074")

---

### Post by Sealbhach on 2008-05-07
What worked for me was to type in the terminal:
> 
sudo apt-get install compiz compizconfig-settings-manager

Then, when that's installed, go to the menu:

**System/Preferences/Advanced Desktop Effects Settings**

You can check the boxes to get the effects you want there.

Hope this helps.


.

---

### Post by uper104 on 2008-05-07
hey thanks:D

it works now YAY

but one question... i did that but now i have no exit,maximize,minmise buttons how do i get those back?

---

### Post by Tom--d on 2008-05-07
Use this..

[http://lhansen.blogspot.com/2008/04/3d-desktop-compz-fusion-on-ubuntu-804.html]("http://lhansen.blogspot.com/2008/04/3d-desktop-compz-fusion-on-ubuntu-804.html")

The graphics card bit may not be the same as yours so dont worry about that ;)

---

### Post by Tom--d on 2008-05-07
> **uper104 said:**
> hey thanks:D

it works now YAY

but one question... i did that but now i have no exit,maximize,minmise buttons how do i get those back?


Thats to do with emerald (thats if you are using it)

On the theme you are using in emerald, click edit.. and then you shall see a tab called buttons.. go on that ;)

---

### Post by uper104 on 2008-05-08
alright ... i messed around with it for a wile... but i still havent found it...

any clues or tips...??

btw how do you get a desktop on the top and bottom of the cube 

and what is a splash screen??

---

### Post by uper104 on 2008-05-08
ohkay ... i figured it out... i had windows decorator unchecked... but the the top and bottom of the cube still stump me

---

### Post by tjwoosta on 2008-05-08
its one of the options that you have to check, i think its called "cube caps" 
(but this doesnt make a useable desktop on the top and bottom, it just puts a picture there so your cube will look like a cube)

---

