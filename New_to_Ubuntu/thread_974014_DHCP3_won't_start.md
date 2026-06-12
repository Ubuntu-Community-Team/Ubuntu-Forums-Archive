---
title: "DHCP3 won't start"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by BUNAC on 2008-11-07
Hi guys,
Can someone advise me as to why DHCP won't start on my Ubuntu Server? 

I've installed the desktop enviroment and I'm running these commands throught the terminal window: 

sudo /etc/init.d/dhcp3-server status
Returns: dhcpd3 is not running.

sudo /etc/init.d/dhcp3-server start
Returns: [fail]

Can anyone help as I'm not sure where to go from here?
Thank you. :)

Tom

---

### Post by B34ST1Y on 2008-11-07
typically, if the dhcp server wont start, it could be due to a bad .conf setup script. Double check to make sure you have your script set up correctly. You could try loading a dhcp configuration (wizard) program from synaptics

---

