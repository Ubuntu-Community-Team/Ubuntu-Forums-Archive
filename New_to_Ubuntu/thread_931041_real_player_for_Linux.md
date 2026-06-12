---
title: "real player for Linux"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by jeff Odom on 2008-09-26
I downloaded real player for Linux and Helix player, but it says neither one is supported. How can I get get these two to run on my laptop?

---

### Post by Tatty on 2008-09-26
If you go to Applications->Add/Remove, you can install the helix player from there.

EDIT: Or i think the realplayer might be in the medibuntu repo's.  But I have always had more success with helix.

---

### Post by cardinals_fan on 2008-09-26
Click [here]("http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.bin") and save the file on your Desktop.  Open a terminal and enter the following:
```
cd Desktop/
chmod +x RealPlayer11GOLD.bin
sudo ./RealPlayer11GOLD.bin


```Follow the instructions, hitting enter when you're not sure.  Let me know if that doesn't work.

---

### Post by Foster Grant on 2008-09-26
> **jeff Odom said:**
> I downloaded real player for Linux and Helix player, but it says neither one is supported. How can I get get these two to run on my laptop?

mplayer (preinstalled) plays Realmedia format without having to install either RealPlayer or Helix.

---

### Post by Crafty Kisses on 2008-09-26
The codecs support RealPlayer, but follow Cardinal if you want to run the official player.

---

### Post by cardinals_fan on 2008-09-26
> **Foster Grant said:**
> mplayer (preinstalled) plays Realmedia format without having to install either RealPlayer or Helix.
MPlayer isn't preinstalled, is it?

---

