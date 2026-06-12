---
title: "Connects only occasionally - PPPOE"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by ineuw on 2008-06-16
I installed Ubuntu a few days ago as a dual boot system (XP + Ubuntu) and I would enjoy it more if I could connect to the internet on a regular basis.  The connection sometimes works, and sometimes it doesn't (60% - 40%).  Also, when it connects, it does so after 10 to 15 minutes of logging on.  I know it's not a hardware or a login problem since I am posting this from XP where I always connect without a problem.  I have the latest version of Ubuntu and it was updated 2 days ago through the web (when the connection worked).  The installation recognized the modem instantly.  I also tried shutting down and resetting the modem prior to starting up Ubuntu, but to no avail.  My suspicion is that the problem may lie with my ISP as I switch between the two OS.  Could this be possible?

Any help would be greatly appreciated.

The modem is a GNet ADSL modem using the Ethernet port (not USB).  There are no error messages.

---

### Post by kalesh7 on 2008-06-16
what have you used to configure your connection?
sudo pppoeconf 
and use everything default just enter your user and pass for connection.
to check connection use 
plog
if that give nothing then restart connection with
pon dsl-provider
and then use plog (after some time) to there are any errors.

---

