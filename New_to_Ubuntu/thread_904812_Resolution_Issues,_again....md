---
title: "Resolution Issues, again..."
date: 2008-08-29
forum: New to Ubuntu
---

### Post by SuperPetRalf on 2008-08-29
So I've got around to installing Ubuntu, after using off and on for a while, and I've got a few basic issues. Since I've posted here a few times I know you community will help.

1. I'm having problems with the resolution, I've seen allot of posts on changing the this however all of them resulted to a trip to reinstall avenue. I finally managed to change it, not a clue how, a tool came up I have never seen before (And no it wasn't the "monitor resolution settings" tool). How do I change it even higher like past the 800x600 (I've got a 22" monitor and its possible to accurately see size 12 font from the other end of the room (cant fit more than 10 words on the screen though). Can anyone tell me how to change the resolution. 

2. When this tool appeared I managed to amp the resolution, and its also changed the resolution of the login screen, so now I cant see the menu at the bottom such as the session options.

3. Setup fusion and emerald, used "emerald --replace" works fine but goes away when I close terminal. How do I make it auto start and continue though the session.

Cheers I know it's a bit much to ask. SuperP

3.

---

### Post by Crafty Kisses on 2008-08-29
For the Emerald problem try this:

Press **Cntrl+Alt+F2** then run > emerald --replace

---

### Post by _Atreides_ on 2008-08-29
Do you have an nvidia or ati graphics card? When you install ubuntu and you do not have an intel graphics card, you have limited graphics performance and are going to need to install restricted drivers for your cards.

---

### Post by sidewinder46 on 2008-08-29
Atreides is correct if you have a nvidia or ati you have to install and enable the restrited drivers:

System> Administration> Hardware Drivers

...and to actually change resolution:

System> Preferences> Screen Resolution

---

### Post by t0p on 2008-08-29
> **_Atreides_ said:**
> Do you have an nvidia or ati graphics card? When you install ubuntu and you do not have an intel graphics card, you have limited graphics performance and are going to need to install restricted drivers for your cards.

To get drivers for NVIDIA and ATI graphics cards, you can go to **System > Administration > Hardware Drivers**.  If that doesn't help, you can try installing and running an app called **Envyng**.  Envy installs NVIDIA and ATI drivers for you.

---

