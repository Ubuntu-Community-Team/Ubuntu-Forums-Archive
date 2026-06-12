---
title: "Accidentally Removed All of my Network Devices?"
date: 2015-01-15
forum: New to Ubuntu
---

### Post by tim85 on 2015-01-15
Just installed 14.04 on new Lenovo Yoga 2. Getting the message "no network devices available" when trying to connect to the internet.

Previously wasn't able to connect because the ideapad device was hard-blocked. A few seemingly appropriate forum posts took me further down the rabbit-hole - apparently now in need of some serious hand-holding.

Happy to post the output of any commands / further hardware details which make diagnosing the problem easier. Thank you.

EDIT: Here is the output of "lscpci | grep Wireless"

01:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)

---

### Post by grahammechanical on 2015-01-16
Do you know what "hard blocked" means? It means that the network adapters/devices are switched off by the hardware. Can you now switch the network devices on? You may also need a driver for the Broadcom. Can you make a wired/ethernet connection to the router? Do so.

Then try going to System Settings>Software and Updates>Additional Drivers tab. It may offer a wireless driver for that Broadcom device. Allow the utility time to do its work.

Regards.

---

