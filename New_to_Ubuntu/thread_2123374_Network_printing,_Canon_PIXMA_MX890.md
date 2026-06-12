---
title: "Network printing, Canon PIXMA MX890"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by Cheapshades97 on 2013-03-07
I'm trying to get a printer working from an Ubuntu 12.04 LTS computer. The printer is a Canon PIXMA MX890 and is connected to the router via wi-fi. The computer is connected via ethernet to a coax to the router. I am able to print from my laptop on the same Ubuntu version, it is connected directly to Wi-Fi.

---

### Post by sully101 on 2013-03-11
You could have the firewall in the router blocking it? Have you turned on a firewall in ubuntu? Can you copy the device uri from the laptop and paste it into the add printer dialog box on the other computer

---

### Post by alphacrucis2 on 2013-03-11
I have MX870 which is probably similar. I recall having trouble until changing some setting on the printer itself. I can't check right now but you can connect to the printer configuration  using a web browser and there are various settings you can adjust. I vaguely recall something to do with lpr query but I will check when I get home this evening.

---

### Post by alphacrucis2 on 2013-03-12
Ok the printer settings were under "Advanced" --> "Other" on the printer web page. Make sure LPR and LPR service notification are enabled. That seemed to fix the problem for me.

---

