---
title: "Wireless network not selected on startup"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by thomsany on 2008-10-04
Hey guys!
I recently installed Ubuntu 8.04.
When I log into Ubuntu, it recognizes my wireless networks etc, but for some reason it doesn't connect to any of them until I click on the network icon and select my wireless network.
Is there something I am doing wrong?
I know that on other installations that I did on this same computer it would load up just fine automatically without me having to select anything.
Any suggestions?
Thanks much in advance,

Teo

---

### Post by PocketDog on 2008-10-04
Let click the network icon >
Manual configuration >
(unlock, enter password) >
Wireless connection - properties >
Untick roaming mode - Enter the ESSID of your router and enter encryption type if you use any, leave it blank if not. If you haven't set up a static IP then leave the connection setting's configuration as DHCP. CLick ok.

Now in the network settings window enter a name for the network, and click the save icon. Click close.

Hopefully it'll choose this network on boot next time

---

### Post by hyper_ch on 2008-10-04
well, I have not been happy with any of the network managers. The other day I discovered WICD and I like it very much. You might want to check it out also: [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

