---
title: "laptop not being identified as laptop"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by JazzPotato on 2011-12-02
I heard that you get a slider for screen backlight if your pc is identified as a laptop. I cannot change backlight any other way and my battery life is 30 minutes! Could somebody please tell me how to identify my laptop as a laptop?

---

### Post by wolfen69 on 2011-12-02
The Fn key doesn't work?

---

### Post by JazzPotato on 2011-12-02
the fn key works for everything but backlight control. Grrr!!

---

### Post by wolfen69 on 2011-12-02
What kind of laptop is it?

---

### Post by NipitMaster on 2011-12-02
Click the power logo in the top right corner of the screen, click "System Settings..." and select "Screen". It should have a slider for brightness.

---

### Post by JazzPotato on 2011-12-02
It dosnt have the slider for some reason, i heard that it is beacause my machine is not identified as laptop.

---

### Post by JazzPotato on 2011-12-02
My laptop is one from pcspecialist.co.uk, they lets you configure your own pretty much.

---

### Post by NipitMaster on 2011-12-02
If you have an ati video card, you may need to install radeontool.

If that doesn't work run:
sudo laptop-detect -v

This will tell you if the computer thinks it's a laptop or not.

---

