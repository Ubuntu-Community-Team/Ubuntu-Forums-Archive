---
title: "64 bit migration"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by pzs on 2008-07-29
I've just installed 64 bit Ubuntu alongside my existing installation. The process went very smoothly and I'm now bringing the configuration up to scratch. 

I was wondering if there are any tools to help me do this. I want an "import user" wizard that will grab my Firefox, Thunderbird and Gnome settings. I was quite tempted to just symbolic link the home directory on the old partition from the new /home, but had a feeling this might make the Linux gods angry. 

Any thoughts?

---

### Post by pzs on 2008-07-29
(Sorry, self reply)

Another very useful feature would be to be able to duplicate, as far as possible, the package setup from the previous installation. Otherwise, I'm going to have to play the old package whack-a-mole for a while as I put in packages that I used before.

---

### Post by forger on 2008-07-29
your home directory contains "hidden" configuration folders with a dot in front.
Head to your old home and press CTRL+H in nautilus to show up all the configuration folders.

Example:
mozilla firefox is in .mozilla/firefox/
thunderbird is in .thunderbird/ (or .mozilla-thunderbird/ ? I forgot)

If you copy-paste those folders in your new /home directory, it might just do the trick :) Also, close the program in question before copying the old data

---

### Post by pzs on 2008-07-29
Will this work for Gnome? I thought it would probably try to write new config files for the current setup over the ones I've just copied across...

---

### Post by philinux on 2008-07-29
> **pzs said:**
> Will this work for Gnome? I thought it would probably try to write new config files for the current setup over the ones I've just copied across...

I had a new pc 2 months ago. Put 64 bit on then copied my config files off my old 32 bit machine no probs.

When you install the apps it picks up the settings no bother since they are just text files.

---

### Post by forger on 2008-07-29
> **pzs said:**
> Will this work for Gnome? I thought it would probably try to write new config files for the current setup over the ones I've just copied across...

sure! I kept my 32-bit home and used it for 64-bit ubuntu with no problems :)

gnome configuration is in .gnome .config and .gnome2 I think

---

### Post by pzs on 2008-07-29
Copied those three directories. Did a restart. Got "Nautilus cannot start. Unknown error" and my config not present. Decided it was quicker to generate my config by hand.

(sigh) In the old days, I would have just copied my .fvwm2rc file across and it would have been fine...

Copying the Thunderbird directory worked fine though :)

---

