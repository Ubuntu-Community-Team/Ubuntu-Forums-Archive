---
title: "Audio Jack not working!"
date: 2016-07-26
forum: New to Ubuntu
---

### Post by coolguy692 on 2016-07-26
My headphone jack isn't working after installing Lubuntu 16.04! I am fairly certain that this problem isn't a hardware defect for it worked perfectly on Windows. I'm completely new to Lubuntu or any Linux OS for that matter so any help or proposed solutions are greatly appreciated! :KS

**_Plausibly Useful Information_**
1. Speakers Work just fine 
2. Audio comes through speakers even though headphones are plugged in
3. Laptop model Dell Latitude E5500

---

### Post by &amp;KyT$0P# on 2016-07-26
Lubuntu uses ALSA for sound, and I found that the ALSA volume levels were set absurdly low by default on 16.04.  You can open a Terminal and run [FONT=Courier New]alsamixer[/FONT] to check if that's your case as well and adjust volume levels as needed.

* never mind, I didn't see your edit.  I don't think this is likely to help much.

---

### Post by coolguy692 on 2016-07-26
Unfortunately no sound out of the headphones even at max volume :(

---

