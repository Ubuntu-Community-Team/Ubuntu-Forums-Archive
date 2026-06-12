---
title: "Server/firewall"
date: 2017-09-11
forum: New to Ubuntu
---

### Post by pengyou2 on 2017-09-11
I have been using Mint for a while but for nothing other than the standard computer stuff - internet, word processing, etc.  I have a new need.

I will be moving to Beijing for a few years to teach.  I am concerned about safety when surfing the web.  I have an old HP Pavilion - has a huge screen that has some issues but the mobo on it is very fast - faster than the desktop I had of the same cpu and specs.  I have mint on it now.  I also have recently purchased a Qnos NAS that has a celeron and mobo inside running a modified version of Ubuntu.  I am thinking of installing a firewall on the notebook (it has the added benefit of being able to run for a long time on a UPS if the power goes off) and using the NAS as a server for my tv, other notebook, desktop, cell phone and tablet, connecting a wifi modem to the server and then connecting all devices either via wifi or cable to the modem.  Does this sound reasonable?  I want the notebook to run the firewall because my hotspot and that notebook will still run if the power goes out - so can still use my battery powered devices.  Does this make sense?  Any suggestions for a good firewall for a newbie to install?  I know that there are some routers that have built in firewall capability but I will most likely be using a VPN and, based on what I have read, the two capabilities in one router may conflict.

---

### Post by deadflowr on 2017-09-11
The best firewall is already installed:
[https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")
and for ease of use
[https://help.ubuntu.com/community/UFW]("https://help.ubuntu.com/community/UFW")

---

### Post by SeijiSensei on 2017-09-12
I'd be more concerned about having my outbound traffic be monitored.  Are you planning to use a VPN to tunnel through the Chinese firewall?  

An ordinary Ubuntu desktop or laptop shouldn't be very vulnerable as long as you stick to software from the actual Ubuntu repositories.

---

