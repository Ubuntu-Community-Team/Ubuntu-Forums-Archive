---
title: "Vista sees more wireless networks than Ubuntu"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by TimX on 2008-06-10
There are 4 wireless networks around here. Vista see all 4, one of which is unsecured. Ubuntu only sees the unsecured network and most of the time it doesn't see that. Most of the time i have to create a new wireless connection and manually enter the name of it. Once i do that it works but it won't remember it. Next time I boot i have to manually do it again. How can i get ubuntu to see more networks and to remember a default network?

---

### Post by TimX on 2008-06-10
and yes roaming mode is enabled.

---

### Post by cariboo on 2008-06-10
Are you the owner of this unsecured router?

---

### Post by stchman on 2008-06-10
> **TimX said:**
> There are 4 wireless networks around here. Vista see all 4, one of which is unsecured. Ubuntu only sees the unsecured network and most of the time it doesn't see that. Most of the time i have to create a new wireless connection and manually enter the name of it. Once i do that it works but it won't remember it. Next time I boot i have to manually do it again. How can i get ubuntu to see more networks and to remember a default network?

What kind of Wireless card do you have?  I would use Wicd over network manager for wireless.

---

### Post by twright on 2008-06-10
you could try using the windows driver with ndiswrapper

---

### Post by wannadumpwindows on 2008-06-10
> **stchman said:**
> What kind of Wireless card do you have?  I would use Wicd over network manager for wireless.

+1 for WICD

It's excellent! Except for stchman's problem. LoL.

P.S. Certain drivers will get much better performance out of your card than others. For me it's exactly the opposite. I get almost twice the signal with Ubuntu over Vista.

---

### Post by sam_delta on 2008-06-10
> **wannadumpwindows said:**
> +1 for WICD

It's excellent! Except for stchman's problem. LoL.

P.S. Certain drivers will get much better performance out of your card than others. For me it's exactly the opposite. I get almost twice the signal with Ubuntu over Vista.
+1 for "sudo apt-get install wicd"

wannadumpwindows you got me wondering... whats your wireless card and driver??? :p

---

### Post by wannadumpwindows on 2008-06-10
> **sam_delta said:**
> +1 for "sudo apt-get install wicd"

wannadumpwindows you got me wondering... whats your wireless card and driver??? :p

Atheros chipset with the Madwifi drivers and a few patches. :)

P.S. I happen to have the exact same wirelees card in my Toshiba laptop and my EeePC. After I applied the patch for the EeePC to the drivers on the Toshiba, it worked soooo much better.

---

