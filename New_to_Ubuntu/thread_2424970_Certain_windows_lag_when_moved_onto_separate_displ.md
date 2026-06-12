---
title: "Certain windows lag when moved onto separate display (Multi-GPU)"
date: 2019-08-18
forum: New to Ubuntu
---

### Post by digbipper188 on 2019-08-18
So I have an issue that so far is kicking my rear when it comes to 3D applications and anything that uses GPU composition. and I'm on the belief that it could be due to my admittedly weird as heck system config.

The issue is as follows;

Any 3D application (including programs run via Steam Proton / WINE) will lag on my main display unless I have a couple pixels of the application sitting on my secondary or tertiary display.

Steam also gives me trouble when it's loaded on my main display as well. When it's on my other screens it's not a problem but when it's on my main display it's DOG SLOW. The only thing I can think of that quantifies how slow it is would be... Imagine succeeding in running CRYSIS... in 4K, ultra details... on a S3 Mirage GPU... yup, it's that slow.


Regular windows, such as the file manager, terminal, Firefox and Chrome are pretty much trouble free provided I have at least one of the secondary displays enabled, but disabling them causes the entire desktop to slow to the point it takes anywhere between 40 seconds and 2 minutes to even open the context menu on the desktop. My only guess that this is because the system is rendering the desktop and all my applications on the RX 580 and it's not compiling on the RX 5700 even if I disable the other displays, although this doesn't explain why everything that isn't a 3D applicaition (or Steam) doesn't lag on any of the displays.


Hardware as it stands:

AMD RyZen 5 2600 CPU @ 4.00GHz
ASRock B350M Pro4 mainboard
16GB RAM
AMD Radeon RX 5700 (Main display is connected to this)
AMD Radeon RX 580 (secondary and tertiary displays connected to this)
Running Ubuntu 19.04

I have the latest version of AMD's driver stack installed which is 19.3 at the time of posting this thread.

---

### Post by Claritux on 2019-09-12
It's possible your RX 5700 isn't being properly recognized by the system as AMD's driver stack only really supports Ubuntu 18.04, and out of the box support for Navi GPUs doesn't land until 19.10. Try removing the AMD driver and use open drivers via newer kernel and mesa-versions: See my guide here: [https://ubuntuforums.org/showthread.php?t=2425799&highlight=5700](https://ubuntuforums.org/showthread.php?t=2425799&highlight=5700)

---

