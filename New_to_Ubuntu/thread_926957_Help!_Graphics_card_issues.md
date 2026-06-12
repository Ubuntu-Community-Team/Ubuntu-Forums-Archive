---
title: "Help! Graphics card issues"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by BuyOurEverything on 2008-09-22
I don't know a whole lot about Linux so I'd appreciate some help with this issue here. I recently reinstalled Ubuntu 8.4 on my computer, I'm now running a dual Ubuntu/XP boot on a Dell Inspiron 5150 laptop. I was trying to get compiz running, so I wanted to make sure my graphics card driver was up to date and running.

I downloaded and installed the driver from nVidia and activated the accelerated graphics driver. I think I messed something up somewhere though, because when I rebooted, Ubuntu didn't recognize my graphics card driver and ran in low-res mode, which I'm stuck in now.

I tried selecting my graphics card from the menu that came up or start up, but it didn't do anything. I have a nVidia GeForce FX Go5200. I tried running Envy both automatically and manually selecting my card, which seemed to work but every time when I restart, it doesn't recognize my graphics card, and boots in low-res mode.

I would really appreciate some ideas about this. What else can I do?

---

### Post by Tatty on 2008-09-22
can you post the output of

```
lsmod | grep nvidia
```

So we can see if the correct driver is running.

---

### Post by BuyOurEverything on 2008-09-23
OK, so I actually tried using Envy to uninstall the graphics card driver, and when I rebooted it seemed to recognize my card, and everything worked fine. When I went to enable the accelerated graphics driver and rebooted again, it stopped recognizing my card again.

Now I'm in low-res mode again, and this is what that command gives:

nvidia               4718832  0 
i2c_core               24832  1 nvidia
agpgart                34760  2 nvidia,intel_agp

---

### Post by BuyOurEverything on 2008-09-23
So I tried using Envy to remove my driver again and restarted but this time, it still didn't recognize my card. I'm still stuck in low-res mode. This time, when I run the command, I get:

nvidia               7106084  26 
i2c_core               24832  1 nvidia
agpgart                34760  2 nvidia,intel_agp

---

