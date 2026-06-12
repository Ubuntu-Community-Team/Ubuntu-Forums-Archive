---
title: "Hardware driver popup question"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by spacemanps on 2008-05-17
can someone tell me what this means? i keep on getting this notification when i start up... i started getting them when i updated the nvidia drives... i think...


and if someone could help me i was looking around the net and i found this video of a desktop that is sort of like a cube i think it was called Beryl? can someone explain how to go about getting that?

---

### Post by cardinals_fan on 2008-05-17
> **spacemanps said:**
> can someone tell me what this means? i keep on getting this notification when i start up... i started getting them when i updated the nvidia drives... i think...


and if someone could help me i was looking around the net and i found this video of a desktop that is sort of like a cube i think it was called Beryl? can someone explain how to go about getting that?
1. It means that Ubuntu is using a few proprietary (closed-source) drivers to make things function properly.  This is probably a good thing for you.

2. You want Compiz Fusion (it used to be Beryl).  Go under System &#8594; Preferences &#8594; Appearance &#8594; Desktop Effects and test the various options.  If it works, you can fine-tune the effects with CCSM.  To get it, open a terminal  (Accessories -> Terminal) and type the following command:
```
sudo apt-get install compizconfig-settings-manager
```
It will ask for your password and work for a minute.  Then type ```
ccsm &
```Enjoy!

---

### Post by spacemanps on 2008-05-17
how do i get it to the view of the cube where i can choose of the 4 sides.. right now when i scroll it flips to the other side as if it is only a 2 sided surface

---

### Post by spacemanps on 2008-05-18
any one...........

---

### Post by philinux on 2008-05-18
right click on the workspace switcher then preferences and select columns 4 rows 1.

Then ctrl alt left mouse, hold down the mouse key to rotate the cube.

---

### Post by shifty_powers on 2008-05-18
that's assuming that you have 3d cube enabled in compiz. it isn't by default you know ;)

---

### Post by spacemanps on 2008-05-18
yup got it thanks guys

---

### Post by spacemanps on 2008-05-18
Okay just a question, maybe its dumb but i dont know.. okay well when i usually redo windows i have to install all my chipset and laptop crap from dell... do i have to do any of that in this ubuntu system?

---

### Post by spacemanps on 2008-05-18
bumppp

---

### Post by philinux on 2008-05-19
> **spacemanps said:**
> Okay just a question, maybe its dumb but i dont know.. okay well when i usually redo windows i have to install all my chipset and laptop crap from dell... do i have to do any of that in this ubuntu system?

Don't think you have to. If everything works you're good to go.

---

### Post by spacemanps on 2008-05-19
well thats the thing, its not, i want the laptop screen off and it wont go off.. it actually generates more heat so i want it off..

---

