---
title: "connect printer using ethernet"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by JonahBird on 2013-06-28
hi, im using Ubuntu 12.04 LTS  on this HP G60 laptop. I want to connect a high capacity anciet tank of a printer (HP laserjet 8000DN) using a direct ethernet connection.
I connect to the intenet via a nighbors wireless router (we share) so I cant connect to the router, I need a direct connection via ethernet. the printer has an preset ip address 128.96.88.18 but that can be reconfigured. 
I tried just adding the printer but no luck. also there is a regular warning saying wired network disconnected, i think it tries to acceess a network via ethernet and doesnt get a response so it keeps restting the connection. I am using an ethernet crossover cable so there should be two-way communication, but i cant seem to get it to work 
I really appriciate any assistance.
cheers

---

### Post by cwsnyder on 2013-06-29
I believe that you have your Ethernet port set up incorrectly.  Either your computer's Ethernet port or your printer's Ethernet port must be set as the 'router' or 'host' for the network, answering pings, DHCP, and other housekeeping and controlling traffic on the network.  Or get a cheap wired router and connect your computer and printer to that router.

You do know you can connect to multiple networks, not just one?

---

