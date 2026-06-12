---
title: "the updates broke my desktop / monitor and compiz issues"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Novus on 2008-06-19
once again the updates broke my desktop.. NVIDIA drivers was gone sound didn't work and so on however I managed to fix that, the problems I now hawe:

1) the monitor info is gone from xorg.conf so the highest res I can get is 1024x768 which looks like crap on my BENQ T24IWA (24" wide screen) and the backup I had of xorg.conf is overwritten by exactley the same thing as is in current xorg.conf (thanx alot for that) so how do I get back my BENQ monitor in 1440x900? I tried ckicking "detect displays" in the screen resolution dialog, without any luck.

2) Compiz got broken after the updates too, the top bar of every window is gone, not a problem I'v had since I upgraded my graphics card. the NVIDIA driver for "latest" cards is installed and in use according to the system > administration > hardware drivers.

3) how can I manage what to notify when upgrades are available. I'v simply had it with upgrades breaking things so I only want to upgrade applications and the dependencies if it's needed by an upgraded application. sure I could uncheck everything I don't want when i install updates, but the list would be huge after a while, so no a good option. alternatively a good stable rollback system which backup EVERYTHING thats gonna be changed when I run updates and it's easy to go back.

---

### Post by philinux on 2008-06-19
You could boot the previous kernel. I think the ...19 broke things for some people whereas ...18 was fine.

Xorg in Hardy should not show any monitor info. It can but in it's intended state the devs chose to exclude monitor stuff.

Recovery mode has a menu structure and one is xfix.

---

### Post by Novus on 2008-06-19
ok, I managed to fix 1) with nvidia-settings.. and it also fixed 2) for some reason :D so just 3) left

---

### Post by LeoSolaris on 2008-06-19
If everything is stable, you can go to Software Sources (Computer->Admin->Software Sources) and click the updates tab. Unclick them all except Security (obvious reasoning there). I have found that usually the proposed updates are the ones that tend to break the system the most often. Backports are usually alright because you have few of them, and recommended updates are usually throughly tested.

Leo

---

