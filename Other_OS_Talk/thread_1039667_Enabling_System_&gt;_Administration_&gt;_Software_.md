---
title: "Enabling System &gt; Administration &gt; Software Sources"
date: 2009-01-14
forum: Other OS Talk
---

### Post by Twitch6000 on 2009-01-14
Okay I was wondering how to enable System > Administration > Software Sources on Linux Mint 6.

I want to know mainly because this is the only thing that they do not have(well took out) that makes me upset and I cannot seem to put back in...

So is there anyway to put it back in :o?

---

### Post by smartboyathome on 2009-01-14
Is Synaptic installed on Linux Mint? It is included in that (don't ask me where, I can't remember :P).

---

### Post by Twitch6000 on 2009-01-14
> **smartboyathome said:**
> Is Synaptic installed on Linux Mint? It is included in that (don't ask me where, I can't remember :P).

Yes that is what Mint Install uses to do the initial download and install while making searching for programs easy and good looking.

Sad you can't remember where :(... I like my sources thing lol...(it saves me a few clicks darn it)

---

### Post by blackened on 2009-01-14
Try running 
```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```

from the terminal to see if it's installed and just not included in the menus. If it's installed, then use alacarte to add it to the main menu.

---

### Post by Twitch6000 on 2009-01-14
> **blackened said:**
> Try running 
```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```

from the terminal to see if it's installed and just not included in the menus. If it's installed, then use alacarte to add it to the main menu.

It seems it is not installed.

---

