---
title: "Which ATI driver to use?"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by splicerr on 2011-09-24
So I have been using the open radeon drivers that come with Oneiric for a while now. They are fine for normal desktop usage, but not very good for gaming. So I want to try the proprietary drivers see if they are any better.

But which one to use?  Additional drivers in Oneiric lists two proprietary drivers:


[LIST]
[*]Video driver for the AMD graphics accelerators
[*]ATI/AMD proprietary FGLRX graphics driver
[/LIST]

anyone knows what is the difference between them? And are these the latest drivers or are those listed on the ATI site ( Catalyst 11.8 ) newer?

---

### Post by Martin Marshalek on 2011-09-24
I'm not sure what those two link to myself actually, I would think one is the fglrx driver and one is the proprietary libgl that is optional with the fglrx driver. My suggestion however, would be to install manually by doing:

```
sudo apt-get install fglrx fglrx-amdcccle
```

Then running:

```
sudo aticonfig --initial
```

And then rebooting.

---

### Post by ratcheer on 2011-09-24
I use fglrx and it is working very well. Just my 2-cents worth.

Tim

---

### Post by rbrick49 on 2011-09-25
> **ratcheer said:**
> I use fglrx and it is working very well. Just my 2-cents worth.

Tim
but is it working ok with gnome-shell Tim
regards ron

---

### Post by ratcheer on 2011-09-25
> **rbrick49 said:**
> but is it working ok with gnome-shell Tim
regards ron

Not completely, there is some garbling of some of the fonts. It is usable, but not always pretty.

I do not see that the OP mentioned gnome-shell. fglrx is perfectly fine with normal Ubuntu.

Tim

---

### Post by splicerr on 2011-09-25
Yes I do not care about gnome-shell. I was hoping that the proprietary ATI  drivers would be good enough to play the game Deus Ex: Human Revolution.  I just installed them with apt-get as mentioned in this topic. 

Unfortunately  the  proprietary ATI drivers are still garbage and almost as slow as the open source ones, making the game completely unplayable :(.

---

### Post by ratcheer on 2011-09-25
I'm sorry to hear that, splicerr. Maybe there is some alternative in the Xorg Edgers PPA at Launchpad. Or maybe you can get some tips at Phoronix.

Tim

---

### Post by screaminj3sus on 2011-09-25
> **ratcheer said:**
> I use fglrx and it is working very well. Just my 2-cents worth.

Tim
fglrx and gnome-shell is currently broken, but will be fixed in october's catalyst release.

---

