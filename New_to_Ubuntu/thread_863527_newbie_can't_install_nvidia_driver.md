---
title: "newbie can't install nvidia driver"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by carpk on 2008-07-18
I have tried multiple approaches from hitting ctl-alt-f1 and stopping the gdm(?) in the tty1 screen and it tells me "cannot open" samething happens it reg. terminal. also the only way I can get it to even initialize is just double clicking it "run in terminal" it starts but then says needs to be run as root. I have downloaded multiple drivers, eliminating that varible. and well... I'm lost. it's a geforce 9600 gt, replacement for my 8600gts that got fried from lightning(i just love fl)

---

### Post by LittleLORDevil on 2008-07-18
Go to System>Administration>Hardware Drivers then enable it from there and it should work after a reboot.

---

### Post by carpk on 2008-07-18
tried it, there is nothing in the hardware drivers menu

---

### Post by LittleLORDevil on 2008-07-18
In Add/Remove install the envy application then run that and it should automatically configure everything.

---

### Post by carpk on 2008-07-18
I don't know if its me.. my res. is 400x600 on my 19' monitor but the only thing I can find on envy is for sound cards in add/remove programs, but another thing is they have a driver in there and well, I tried all this yesterday....

---

### Post by BGFG on 2008-07-18
hey, can you still open a terminal ? if so, paste in this command 

```
 sudo apt-get install nvidia-glx 
```

And run it. Running something as root basically means putting 'sudo' in front of it. that's not ALL there is to root commands but for now that's all you should need.

Also, because of your res, i'm not sure how you can navigate, but if you can get in to synaptic, you can search for the relevant nvidia utilities and install them from there.

System>>Administration>>Synaptic Package manager

Just search for nvidia.

---

### Post by carpk on 2008-07-18
well.. I did a system repair and my screen never looked better

---

### Post by BGFG on 2008-07-18
Cool ! :)

---

