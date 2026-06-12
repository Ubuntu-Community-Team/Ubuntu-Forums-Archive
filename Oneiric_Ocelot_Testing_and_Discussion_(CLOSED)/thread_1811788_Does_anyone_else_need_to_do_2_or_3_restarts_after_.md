---
title: "Does anyone else need to do 2 or 3 restarts after a new kernel?"
date: 2011-07-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-07-25
Nowadays it seems necessary to re-install nvidia-current after each kernel (and at other times too). No problem, that's life :-)
Now it seems that whenever a new kernel arrives and I do a restart then re-install the nvidia driver and restart again I get just an empty desktop background (and my trusty conky display) :-) No panel.
A REISUB later and the desktop loads normally but gdm is using 100% of one cpu. (This only happens occasionally, not every time).
Another REISBUB later and everything is fine.
Is this the norm now or is my system dodgy? 
Thanks :-)

---

### Post by Muskegman on 2011-07-25
Same thing here , already did the re-install nvidia-current and it got me back to a working desktop, but it seems every second boot or so im left with an empty desktop with no launcher. This is alpha2 so i do realize that it is expected to be buggy ;)

---

### Post by dino99 on 2011-07-25
works fine here :)

you might clean the room or make a fresh install again in case of too many borked tweaks

---

### Post by coffeecat on 2011-07-25
How well is the nouveau driver working with your card in Oneiric now that they've incorporated what was libgl1-mesa-dri-experimental so that it's no longer experimental?

---

### Post by Quackers on 2011-07-25
Thanks.
Once mine is up and running again it's fine. It just takes 2 or 3 restarts to get there at first.
I used to get a gdm problem every 7 or 8 restarts but that hasn't happened for quite some time now.
By the way I'm on a fully updated upgrade from Natty (64 bit), as alpha2 was a disaster for me.

---

### Post by Quackers on 2011-07-25
> **coffeecat said:**
> How well is the nouveau driver working with your card in Oneiric now that they've incorporated what was libgl1-mesa-dri-experimental so that it's no longer experimental?

Dunno boss, I'm a permanent gnome-shell user :-)
I'll have to experiment one day :wink:

---

### Post by Quackers on 2011-07-25
> **dino99 said:**
> works fine here :)

you might clean the room or make a fresh install again in case of too many borked tweaks

Err, tried that with alpha2, but let's not go there :-)

---

### Post by coffeecat on 2011-07-25
> **Quackers said:**
> Dunno boss, I'm a permanent gnome-shell user :-)
I'll have to experiment one day :wink:

I thought that gnome shell was less demanding of 3d acceleration than Unity. Someone please correct me if I'm wrong! Which means that you might be fine with the nouveau driver. Worth checking out. :)

---

### Post by Quackers on 2011-07-25
I did try Nouveau for a while but I had cairo-dock running at the time and it made it a little laggy and the animations were a bit slow. It's much better than previous versions I've tried though.
Not sure about demands though between Unity and gnome-shell.

---

### Post by 23dornot23d on 2011-07-25
> 
Nowadays it seems necessary to re-install nvidia-current after each kernel (and at other times too). No problem, that's life :smile:
Is it the way the packages are sequenced now .....

Nvidia-current ......

then

kernel  header .... then kernel image  .....
or
kernel image .... then kernel header .....

I always look now for the [COLOR=Red]**RED FAIL**[/COLOR]  against the graphics drivers as the headers are added ..... when upgrading ....... 

usually re-installing the kernel headers again solves it too for me ..... as it seems to re-build the kernel again ...
and hopefully with the graphics card and not a [COLOR=Red]red FAIL[/COLOR] mark against it ......

I never restart my system untill  OK  comes up against everything ...........

Just watch the terminal carefully when installing .... I use Synaptic ......

Not sure what you see on the Ubuntu upgrade ...

**or is there a better way to make sure that this will always be successful **?

---

### Post by Harry33 on 2011-07-25
The latest 3.0.0 kernel versions 6 and7 do not start dkms properly.
This leads to the directory /lib/modules/3.0.0-x-generic/updates/dkms not contain the file nvidia-current.ko.
This in turn means you do not have nvidia drivers installed correctly.

Also the latest mesa branch (7.11) changes the locations of some files so that nvidia-current does not function any more (missing 3D).

So, you can overcome this only by reinstalling nvidia-current after kernel and/or mesa installation.

---

### Post by 23dornot23d on 2011-07-25
Will always check the [COLOR=Red]Red FAIL[/COLOR] is a good indication .... and it was related to DKMS .... 
after putting the headers back in again is the only way I get to see it ... 

and it definately said OK next to it when I re-installed it ....... otherwise I would have not re-booted ....
 

> 
So, you can overcome this only by reinstalling nvidia-current after kernel and/or mesa installation.
That's good to know .... I must have re-installed the nvidia-driver again too then ....... 

[COLOR=Red][B]Afterwards will the Nvidia Drivers all be installed automatic and install properly ?
[/B] [/COLOR]
So Nvidia driver needs to be installed last then ....... where is the output .....  to let you know its succeeded ?
in one of the logs I guess.

If so does anyone know which one ?

or is re-installing the headers a simple way of seeing that they are ok ?

---

### Post by cariboo on 2011-07-26
It's not only the nvidia driver that needs to be re-installed after a kernel upgrade, I also have to re-install the bcmwl drivers on my netbook after a kernel upgrade.

---

### Post by Quackers on 2011-07-26
Thanks for all the input people :-)

---

