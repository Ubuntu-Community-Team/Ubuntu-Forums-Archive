---
title: "VirtualBox small issues"
date: 2011-09-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-09-07
I am having a few problems with VirtualBox on Oneiric. I am using a W7 Enterprise 64Bits Guest OS.

- In seamless mode, it becomes impossible to switch to another desktop. Touching the left part of the screen won't make the switcher appear. The keyboard shortcut (Super+s) only works sometimes, don't know why. Making it visible all the time is not functional (it will be over the Windows Start Menu button).

- In seamless mode and fullscreen: You click the W7 Start Menu button and Oneiric trash window comes up. (so although you are not seeing it, the switcher is active behind the W7 desktop and receiving focus). 

- In seamless, fullscreen or windowed mode: Screen corruption. You minimize a guest OS window but it stays there, sort of "painted" on the background, although its not really there at all.

- In seamless, fullscreen or windowed mode: Focus problems. You will click a guest OS window, but it won't gain focus sometimes. You have to switch to another desktop and back again in order to be able to click on the guest OS window and make it active.

I have tried using regex on ccsm to exclude virtualbox window class from some behaviors, add to others. I believe the answer is there, but haven't come up with a definitive working setup. 

Maybe anyone is already trying to fix this things and can share some knowledge?

Thanks,
Effenberg

PS: Yes, I have tried rdesktop, but it seems to be rendering very slow and create some artifacts on screen. I have obviously disabled W7 composite and effects, energy saving, etc. All the common advices.

---

