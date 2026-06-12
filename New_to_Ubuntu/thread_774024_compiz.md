---
title: "compiz"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-04-29
hi i just got my graphics card to work and my wifi card also to work..but now i cant seem to get compoz to install...well actually i really dont no what im doing so if any one could please help me install it step by step i would be very thankful!

---

### Post by hackle577 on 2008-04-29
Compiz Fusion is installed in Hardy by default.

---

### Post by mkarnicki on 2008-04-29
[ you could possibly skip first step ]
System -> Administration -> Synaptic -> search for: compiz

Make sure it's installed (i think it is by default so you could skip this step acutally).

You need nvidia drivers (I assume you have geforce or something) which you can find in System->Administration->Hardware drivers
[ --- cut here --- ]

System -> Preferences -> Appearance -> tab: Visual effects -> click Extra

If you're using nvidia drivers and you have adequate hardware configuration, it should enable successfully. If you want to tweak compiz for your needs:

Applications -> Add/remove programs -> search for: compiz

Tic "Advanced Desktop Effects Settings" and have fun. You can find it l8r in System -> Preferences I guess.

I've just go a problem installing this under amd64. Hope you succeed.

---

### Post by hermes0710 on 2008-04-29
What do you mean by saying you cant see compiz getting installed? In order to activate the desktop effects go "System">"Preferences">"Appearance" and in the last tab select "Extra"

---

### Post by Alldan on 2008-04-29
what graphic card do you have? 
look in system - administration -  Hardware drivers and you can enable restricted drivers if available for your graphic card from there, then restart computer. Then  you can enable additional effect from system - preference - desktop effect

---

### Post by Alldan on 2008-04-29
enable your restricted drivers from system - administration - hardware drivers, restart computer then enable additional graphic effecta from system - preferences - desktop efects

---

### Post by billgoldberg on 2008-04-29
> **betterthanjordan79 said:**
> hi i just got my graphics card to work and my wifi card also to work..but now i cant seem to get compoz to install...well actually i really dont no what im doing so if any one could please help me install it step by step i would be very thankful!

First go to synaptic and install this package:

compizconfig-settings-manager

The go to system - preferences - appearance.

In the last tab select "extra".

Then you can change/add effects in "system -> preferences -> advanced desktop effects settings".

ps: Some of you guys really need to read the OP better. The guy clearly stated his graphics card is already installed and working.

---

### Post by betterthanjordan79 on 2008-04-29
thanks mkarnicki-just wat i needed

---

### Post by mkarnicki on 2008-04-29
**@betterthanjordan79** My pleasure to help out :) By the way, if everything works fine now you can mark this thread SOLVED (above your first post click Thread Tools -> Mark as solved.

(my problem also solved. i had to remove "web" word from sources.list)

Have a nice day.

---

### Post by Absorbed on 2008-04-29
> **mkarnicki said:**
> By the way, if everything works fine now you can mark this thread SOLVED (above your first post click Thread Tools -> Mark as solved.

I don't think you can mark a thread as solved at the moment; it disappeared when they upgraded the forums. Thanks also initially disappeared, but that's reappeared, so I expected Solved with make a reappearance as well.

---

### Post by mkarnicki on 2008-04-29
Oh, sorry. I haven't noticed that marking option disappeared.

---

