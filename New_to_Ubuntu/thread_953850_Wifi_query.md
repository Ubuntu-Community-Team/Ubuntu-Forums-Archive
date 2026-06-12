---
title: "Wifi query"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by nnjond on 2008-10-20
Hi,

Does anyone know if the next version of Ubuntu will have a driver to solve the "dreaded Atheros" wifi prob with some laptops?

thanks .

---

### Post by shifty_powers on 2008-10-20
the wireless support is much better yes. specifically don't know. and anyways, whats wrong with madwifi?

---

### Post by t0p on 2008-10-20
> **nnjond said:**
> 
Does anyone know if the next version of Ubuntu will have a driver to solve the "dreaded Atheros" wifi prob with some laptops?

What is this "dreaded Atheros" wifi problem?  I run ubuntu hardy on my Eeepc, and it has an Atheros wifi card that uses madwifi.  The wireless doesn't work "out of the box" but it was easily [tweaked]("http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly").

---

### Post by nnjond on 2008-10-20
Well, I tried installing madwifi once; If i did it correctly it didn't work.

thanks for your replies.

---

### Post by sethvath on 2008-10-20
There is madwifi, wicd, wifi-radar

---

### Post by igknighted on 2008-10-20
What version of Ubuntu did you use, and what method did you use to try to install it?

I wouldn't call anything "dreaded" about Atheros, they are one of the best supported wireless chips in linux, and Ubuntu 8.04 and 8.10 should automatically install the drivers for you through the "restricted driver manager", or whatever it is called these days (looks like "hardware drivers" in my Intrepid install).  If you have had trouble with earlier versions, try the Intrepid beta.  There is a newer driver out for Atheros that may solve your problem, I don't know if it is in 8.04 or not.

EDIT: @SethVath: madwifi is a driver, while wicd and wifiradar are applications to manage connections.  If he/she has driver issues, wicd and wifiradar are of no value yet anyways.  I don't think there is really any reason for someone to replace the default (network manager) except in fringe cases, so lets keep it simple and not confuse the OP.

---

