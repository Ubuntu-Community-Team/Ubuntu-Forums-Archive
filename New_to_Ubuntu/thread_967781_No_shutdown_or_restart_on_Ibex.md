---
title: "No shutdown or restart on Ibex"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by jerrynewt on 2008-11-02
When I shutdown or restart on Ibex, the procedure stops at "Shutting down ALSA" and I have to hold the power button down to turn it off. Startup if just fine and everything else seems to be aces. Any ideas on the problem would be appreciated. 


Intel dual core processor, 2 gig ram, 160 gig hd, dual boot 8.04 and 8.10.

---

### Post by phidia on 2008-11-02
Is this the release candidate or final of Ibex? In any case try > sudo apt-get update && sudo apt-get upgrade reboot and see is that helps.

If the problem continues see if "halt" from a teminal shuts down properly.

---

