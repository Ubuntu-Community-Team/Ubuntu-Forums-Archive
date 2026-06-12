---
title: "Problems with hibernate/suspend"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by gustasonfrever on 2008-08-04
Whenever I need to leave my computer (Lenovo thinkpad t61) for a long period of time I close the lid so that it will hibernate. Hibernate seems to work if I leave my computer for only a few minutes. I open the lid and then it comes out of sleep and prompts me for a password. If I leave it for longer then when I open it, it does nothing and I have to power up again. However, when I power up it goes to the page with Ubuntu written at the top and the loading bar bellow, the bar goes about halfway and then stops, and the screen goes black. After a second or two the Ubuntu text comes back but at the top of the screen in a 1 inch bar are green lines. Then after 30 seconds or so the screen vanishes and turns black. After this I can restart again fine, but this is a major functionality issue for me.
Suspend also doesn't work very well for me and if I leave the computer suspended overnight, I'll wake up and the computer will have shut down. 
Hibernate is very important for me, when I have to go from class to class. I don't want to have to shut down and then power up again 5 times a day. If I can't find a reasonable solution I fear that I will have to go back to XP.

---

### Post by nicedude on 2008-08-11
I have had same problem with my Acer 5520 and gave up and just don't use suspend or hibernate and instead wrote a power management script ( still a work in progress actually ) which now gives me at least 2 hours on battery but in future I think I can get even more out of it. So in short I would recomend setting all suspend & hibernate off and set it to black screen when lid closed and just shutdown system if you need to close screen for a long time. My system boots in 32 seconds while hibernate takes like 10 seconds so all I lose is 22 seconds and I can live with that. Sorry I don't have an answer but I am not even sure there is one as many people suffer from this under Ubuntu Hardy. 

PS to watch what is taking up the most power you cna install powertop and to troubleshoot your boot time use bootchart both are in the repositories and can help you get a good grasp of what is going on.

nicedude

---

