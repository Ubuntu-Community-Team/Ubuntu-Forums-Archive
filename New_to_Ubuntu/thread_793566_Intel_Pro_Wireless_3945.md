---
title: "Intel Pro Wireless 3945"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by DeezNuts on 2008-05-13
I have a Compaq nx7400 Laptop with an inbuilt Intel Pro Wireless 3945 card. I am using Hardy Heron.

The LED on my laptop is not displaying, I cannot connect to or see any networks.

I have tried so many ways to get the card fully working, but still no luck.

I have got the backports from the previous kernel, I have tried creating a new file in /etc/modprobe.d for the iwl3945 driver.

Still no luck. Any suggestions

---

### Post by Inxsible on 2008-05-13
I don't have any problems with intel 3945. Does your laptop have a switch that needs to be in the on position for wireless? If yes, Make sure its in the on position.

---

### Post by DeezNuts on 2008-05-13
Yeah, there is just a single button that is normally used to Active/Deactivate the WLAN.

I just did a fresh install and the Wireless worked fine after I follow this guide that got to me to fix up the IWL3945 driver.

Only thing that I need to fix now is the fact that the LED light does not come on. The net itself works, just doesn't show the LED.

---

