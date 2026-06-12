---
title: "Wireless networks dissapeared from Network Settings"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Djalmahal on 2008-04-29
Hi,


so, i'm running 8.04 and suddenly (meaning I don't know what happened) the wireless option dissapeared from the Network Settings. 
Also the enable wireless option from right clicking the connection icon in the panel is gone.


Any suggestions?


Thanks,
Andreas

---

### Post by Dark Aspect on 2008-04-29
> **Djalmahal said:**
> Hi,


so, i'm running 8.04 and suddenly (meaning I don't know what happened) the wireless option dissapeared from the Network Settings. 
Also the enable wireless option from right clicking the connection icon in the panel is gone.


Any suggestions?


Thanks,
Andreas

Yeah I have had this problem before try in the terminal:

> nm-applet

Its a little buggy since you have to leave the terminal open to use it but it should at least come back without reseting you system.

---

### Post by Djalmahal on 2008-04-29
No, nm-applet, just shows the wired connection and the modem, the problem is deeper, when I look up my connections "eth1" is gone, there is just something called "lo". I didn't do anything to disable it.

Andreas

---

### Post by smile-its-smiley on 2008-04-29
i've just had the same problem after trying hard to connect wirelessly and it worked for like 1min for me then disconected itself. so i restarted in windows and i completly lost the wireless signal in that aswell, ive just had to re register every thing not sure if i'll be able to reconnect in ubuntu or not

---

