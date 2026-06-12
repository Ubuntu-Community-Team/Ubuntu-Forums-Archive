---
title: "Monitor frequency out of range when booting or shutting down"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by hito1 on 2008-07-16
I've just did a clean install of Hardy Heron, and I'm having a problem:

Right after the grub screen I get an error from the monitor saying its frequency is out of range, this lasts until the login screen. I also get the same problem when shutting down the computer.

Does anyone has a clue on it?

Thanks in advance.

---

### Post by mingle on 2008-07-17
Hi,

Sorry, I can't actually help, but this is a problem I've had too.

It's obviously some issue with teh GFX driver, as it appears that it is switching to a frequency/resolution that the screen (an HP L1530 LCD in my case) can't handle.

I also had this problem when I tried playing the SuperTux platform game: by default the game appears to go into full-screen mode. Whatever mode it was using was also beyond the scope of my screen. By sheer fluke I managed to hit the correct key combination to get to windowed mode and I got my desktop back.

My PC has an Intel 82845G GFX chipset and it's using the Intel i810 driver that comes with Ubuntu 8.04

Does anyone know if better/new/more specific GFX drivers are available and if so, where do I look?

Cheers,

Mike.

---

