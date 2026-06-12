---
title: "CAN'T connect to my Wifi, but CAN connect to a friend's"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by pcvchriskmg on 2012-12-10
I have my Broadcomm wifi adapter working under 10.10 (Maverick) but I can't seem to connect to the wifi at my own home.

I brought my machine to a friend's house, connected to the internet via RJ-45, ran:

sudo apt-get remove bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
sudo reboot

and then was able to connect to her Wifi no problem. I did not lose the connection and was able to surf the internet until I shut down my computer and went home.

When I came home, I could not connect to the Wifi at my house, however. It won't connect, and after a minute of trying, it asks me to re-enter the pass phrase to the Wifi.

I turned off the modem this morning, and restarted it after 5 minutes and that didn't solve the problem.

What could be preventing me from connecting to my Wifi, specifically?

Thanks in advance,
Chris

---

### Post by grahammechanical on 2012-12-10
So, you have established that the wireless adapter in your machine is working and that you have installed a driver for it and that is also working. What could be wrong?

The wireless access point (router/hub) is set to a different encryption mode to that being used by Network Manager. You need to edit the connection and make sure that the router and network Manager are talking to each other using the same encryption method.

It might be simpler to delete that connection and the use Network Manager to select your wireless network, then NM may correctly work out for itself the correct encryption method.

I have not used 10.10 for a long time so I cannot give you specific directions.

Regards.

---

### Post by pcvchriskmg on 2012-12-10
Hi thank you for the reply.

I wanted to delete the connection and then just reset the router and reboot my machine.

How do I delete the existing connection, though?

Thank you,
Chris

---

