---
title: "synaptic gone completely bananas!"
date: 2011-08-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-08-25
I did an update earlier this :am and synaptic proceeded to remove a perfectly good working Unity 2D and completely disable Unity 3D and Gnome Shell.

 Then, when I tried to re-install Unity 2d I got this:

Dell Optiplex GX270- 2.8GHz

---

### Post by sgage on 2011-08-25
> **ventrical said:**
> I did an update earlier this :am and synaptic proceeded to remove a perfectly good working Unity 2D and completely disable Unity 3D and Gnome Shell.

 Then, when I tried to re-install Unity 2d I got this:

Dell Optiplex GX270- 2.8GHz

It wouldn't have if you didn't let it. Synaptic always tells you what it's going to do, and gave a "to be removed" notice on the unity-2d stuff.

In any case, it's not Synaptics fault - things are out of sync right now, and will be put right. Remember, these are the alpha days! If you can't get into any shell, just boot into recovery mode and do apt-get update/upgrade. I suspect it will all be good within a few hours.

---

### Post by arpanaut on 2011-08-25
I didn't let synaptic to remove anything, kept reloading package list and everything cleared up moments ago.
Everything <well sorta> working as usual, 
Good Luck to those who were not cautious enough.

---

### Post by ventrical on 2011-08-25
> **sgage said:**
> It wouldn't have if you didn't let it. Synaptic always tells you what it's going to do, and gave a "to be removed" notice on the unity-2d stuff.

In any case, it's not Synaptics fault - things are out of sync right now, and will be put right. Remember, these are the alpha days! If you can't get into any shell, just boot into recovery mode and do apt-get update/upgrade. I suspect it will all be good within a few hours.


Luckily for me I have three other installs  of Oneiric on one of my laptops, all in very good working condition. I thought I would try an install on a desktop lastnight .. and that is when the 'stuff' more or less hit the fan.

---

### Post by ventrical on 2011-08-25
> **arpanaut said:**
> I didn't let synaptic to remove anything, kept reloading package list and everything cleared up moments ago.
Everything <well sorta> working as usual, 
Good Luck to those who were not cautious enough.


On my Dell desktop I sort of got caught off guard. I didn't realize what it was doing at first. I think it may have to do with a program called a 'nvidia checker' and I do not even have a nvidia card.

  However I got the Dell on ice right now :) waiting for the probs to get fixed because you can't really send  bug reports  when the OS is in that condition, with the exception of Gnome Classic (if it's working).

---

### Post by sgage on 2011-08-25
> **ventrical said:**
> Luckily for me I have three other installs  of Oneiric on one of my laptops, all in very good working condition. I thought I would try an install on a desktop lastnight .. and that is when the 'stuff' more or less hit the fan.

When things start breaking for me, I get more and more adventurous in trying to fix it - I figure it's the universe's way of telling me it's time for a fresh install anyway. Though sometimes I'm actually able to fix it, with the help of the good folks here  :KS

---

### Post by ventrical on 2011-08-25
> **sgage said:**
> When things start breaking for me, I get more and more adventurous in trying to fix it - I figure it's the universe's way of telling me it's time for a fresh install anyway. Though sometimes I'm actually able to fix it, with the help of the good folks here  :KS

I agree.. it is always good to fix a broken system. I have been fixing broken systems of all sorts for decades now. Linux (Ubuntu) is still rather new to me byt my firmal training was in UNIX several years ago.

 I think we learn more when we find a work-a-round. It's all for the better of the sum of the whole.

---

### Post by ranch hand on 2011-08-25
It might be a good time to try doing this through aptitude.  It will try to fix the dependency problem.  You will get a suggested fix.  Refuse it.  It will give you another,  Refuse it.

This will continue until it runs out of options.  If you like one of them, start over and it will come up again.

This was handy in getting Gnome Shell going on my Debian install.   It may fix your problem easily.  If not, so what, your system is screwed anyway.

---

