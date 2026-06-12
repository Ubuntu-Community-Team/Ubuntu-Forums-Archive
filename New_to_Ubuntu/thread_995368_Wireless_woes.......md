---
title: "Wireless woes......"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Beller88 on 2008-11-27
Can somebody help me?
I have a HP Pavillion Laptop dv9700 and have recently tried to run ubuntu 8.10, however i cannot detect the wirless networks. 
Is there anybody out there that knows what i need to do or would have failed to have done?
p.s. i have made sure my wireless is turned on.....

---

### Post by laurielegit on 2008-11-27
Do you have your wireless drivers activated in the restricted drivers menu. If not, you will need to connect to the Internet to install them. I find this very annoying, and always forget to do it.

Good luck,

Laurie

---

### Post by Olivier2371 on 2008-11-27
hello there, and Welcome,

To determine what wireless card/chipset you have, open up a terminal and type the following.

lspci -v | less



To check the status on your wireless connection, use:

iwconfig

Post both result here.

---

### Post by Omega88 on 2008-11-27
Im sitting beside beller88 here because he obv cant post online from his ubuntu account.

lspci brings up

03.00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI express adapter (rev 01)

and iwconfig brings up "no wireless extensions" for "lo" "eth0" "eth1" and "pan0"

---

### Post by Olivier2371 on 2008-11-27
Have you checked in

System->Administration->Hardware Drivers

to see if the driver is install properly.


I found this link:
[http://ubuntuforums.org/showthread.php?t=967654&highlight=Atheros+AR242x+802.11abg+Wireless+PCI+express+adapter+(rev+01)]("http://ubuntuforums.org/showthread.php?t=967654&highlight=Atheros+AR242x+802.11abg+Wireless+PCI+express+adapter+(rev+01)")
Hopefully it will help.

---

