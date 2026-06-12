---
title: "[SOLVED] wireless network not recognized"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by paker on 2008-10-19
I have 2 computers. Both have the same wireless network card (US Robotics 5417). I used one wireless and the other wired. This morning I moved the used-to-be-wired and went wireless. But it didn't recognize the wireless network, any wireless network at all. Moved it next to the router. Still didn't recognize the wireless network.

I see 3 wireless networks, including my neighbors, on the other computer. I am clueless. 

Both computers run Hardy.

---

### Post by roger_1960 on 2008-10-19
Hi

Have you got NAT (Network Address Translation) enabled on your wifi router?

Do you see any wireless networks on your newly wireless PC.  If not, perhaps you need to enable wireless roaming.  Open network settings(system-admin-network), select 'wireless' select 'properties' and check the 'roaming mode enabled' box

---

### Post by iwc5893 on 2008-10-19
You may also want to check the settings in your router.  Do you have things like MAC address restrictions enabled, and are you broadcasting your SSID?

---

### Post by melojo on 2008-10-19
Do you have dhcp enable if yes then 
open a terminal and post the output of
lshw -C network
ifconfig
iwconfig

---

### Post by paker on 2008-10-19
> **roger_1960 said:**
> Hi

Have you got NAT (Network Address Translation) enabled on your wifi router?

**[COLOR="Navy"]I don't know what NAT is. All I did after installing a wireless router was to set the network name and pass phrase.[/COLOR]**

Do you see any wireless networks on your newly wireless PC.  If not, perhaps you need to enable wireless roaming.  Open network settings(system-admin-network), select 'wireless' select 'properties' and check the 'roaming mode enabled' box

[LEFT][COLOR="Navy"]No, I don't see any wireless network. But the Roaming Mode Enabled box is already checked.[/COLOR][/LEFT]




Thanks.
I don't know if this is important or not. The wireless network card was sitting in the computer while wired network was used. What I did this morning was to disconnect the wire and fired it up as wireless. I was expecting the 3 or 4 neighborhood wireless network names recognized right away. But not even one was recognized.

---

### Post by iwc5893 on 2008-10-19
> **paker said:**
> Thanks.

Then you might want to take a look at [WICD]("http://wicd.sourceforge.net/").  If not, then you will need to disable wireless roaming and configure the wifi yourself.  Basically, you need to enter the SSID of your network, and choose your DHCP configuration.

---

### Post by melojo on 2008-10-19
> **paker said:**
> Thanks.
I don't know if this is important or not. The wireless network card was sitting in the computer while wired network was used. What I did this morning was to disconnect the wire and fired it up as wireless.

I have done that before and it does make a difference.  You can leave it plugged in but you have to shut down eth0 or whatever you wired network is called.  Ex.  sudo ifconfig eth0 down

---

### Post by paker on 2008-10-19
> **iwc5893 said:**
> You may also want to check the settings in your router.  Do you have things like MAC address restrictions enabled, and are you broadcasting your SSID?
I am too ignorant to understand your question. All I did after installing a wireless router was to enter the general US Robotics router address on internet (192.168.....) and set network name and pass phrase as described in the manual. Since then I have used one computer  wired and the other wireless. But the wired computer had the same wireless network card plugged in all the time.

---

### Post by roger_1960 on 2008-10-19
Hi again

If you have been using the two PCs at the same time before, this is probably not a router problem.  Confirmed by the fact that you cant see the other local networks.

I'm assuming you have right clicked the signal strength icon (usually top right) and checked the 'enable wireless' box.  (Sorry if I'm stating the obvious but you never know!)  Your card is based, I believe on a broadcom 4318 chipset which is not good news

Before you go into all that may follow from searching on that chipset, have you compared all the settings with your other PC which does work?

Also have a look at [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) which may solve the problem.

---

### Post by paker on 2008-10-19
> **roger_1960 said:**
> .....

I'm assuming you have right clicked the signal strength icon (usually top right) and checked the 'enable wireless' box..........

THANKS! I checked SYSTEM > ADMINISTRATION > HARDWARE DRIVER. "Broadcom B43 Wireless Driver" is not checked and not enabled. I clicked on Enable box, but the computer does nothing. 

I installed 8.04 using DVD. Is this a problem? I put the DVD in before enabling, but still no response from the computer.

PS: Signal strength is okay on the wireless computer. This PC is conneccted back to wire and sits right next to the wireless router.

---

### Post by paker on 2008-10-19
Finally, it dawned on me that this PC with network problem has 64 bit whereas the troubleless PC has 32 bit. I fresh installed 32 bit version on this one, and it's working fine now. Thanks.

---

