---
title: "hp dv6000 , no sound!"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by donkeykong81585 on 2008-05-25
Hi All, 

Just d.led ubuntu for the first time. Love it, but my sound doesnt work now. I have  a HP dv6000 laptop. The mute button wont turn off above the keyboard. Everything in the system says that I should be hearing something, but nothing is coming out?

How to fix?

Thanks!

---

### Post by marty1011 on 2008-05-25
Are you using Gutsy or Hardy? I have dv6000 too and I have realtek sound card. If you are using Gutsy and realtek then follow this link: [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

### Post by sayakb on 2008-05-25
At a terminal:
```
sudo apt-get install linux-backports-modules
```

---

### Post by Inxsible on 2008-05-25
Before you try anything else, try this. Type in ```
alsamixer
``` in a terminal and max all the volume levels and then see if you get sound.

---

