---
title: "Sound intermittent through HDMI, audio fine off laptop speakers"
date: 2022-05-06
forum: New to Ubuntu
---

### Post by UltimatePredator on 2022-05-06
HI there, I'm pretty new to linux (posted in the past but not used linux much recently), wasn't sure where to post this thread as I'm not sure if its a hardware or software issue. 
I currently have installed Xubuntu 22.04, as the title says the sound intermittently cuts out over hdmi, but off my laptop speakers its fine. I've tried other ubuntu based distros but they have the same problem, and yet I know its this laptop as other laptops don't have a problem with the same hdmi cable and tv.

If it helps I'm using nvidia driver 510.

Appreciate any help. Thank you.

---

### Post by ActionParsnip on 2022-05-06
Have you tried a different HDMI cable?
Have you tried a different HDMI port on the TV (if it has more than one)?

---

### Post by UltimatePredator on 2022-05-06
> **ActionParsnip said:**
> Have you tried a different HDMI cable?
Have you tried a different HDMI port on the TV (if it has more than one)?

Yep to both, same problem I'm afraid.

---

### Post by UltimatePredator on 2022-05-06
I fixed the issue! The refresh rate for the tv was automatically set at 30 each time I replugged in the hdmi, once I upped it to 59.9 the problem resolved itself!

---

### Post by pfjan on 2022-05-20
Thanks for the post, I'm apparently facing the same problem here, when connected a TV (as a monitor) to a desktop via HDMI. My system is also a Ubuntu 22.04 and the issue seems to happen in various applications (video watching in chrome, steam games, listening to music, etc.).

In windows (dual boot) it works fine, ruling out hardware.
.
My monitor was configured at 60Hz. I changed it to 59.9 following your suggestion and it also fixed the issue -- I have no clue why though ...

---

