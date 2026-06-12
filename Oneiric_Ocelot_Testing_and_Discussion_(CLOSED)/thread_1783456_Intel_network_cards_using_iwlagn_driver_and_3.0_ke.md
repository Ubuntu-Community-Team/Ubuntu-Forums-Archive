---
title: "Intel network cards using iwlagn driver and 3.0 kernel"
date: 2011-06-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2011-06-15
#File has been added to 3.0 for iwlagn driver: Seems to fix the unstable 
use of "N" in the intel network cards using iwlagn driver as in previous kernels. 
Was stable in "G" so had to set router in 2.4 ghz to use mixed "G" and "N" instead of just N. Also had to use
a iwagn.conf in /etc/modprobe.d to make card stable, actually taking away the "N"
use in intel card by adding line to /etc/modprobe.d/iwlagn.conf                                   
options iwlagn 11n_disable50=1 11n_disable=1
# Now is stable in "N' of the intel card using iwlagn driver with 3.0 kernel.
#rick@rick-HP:~$ locate iwlagn
/etc/modprobe.d/iwlagn.conf
/etc/modprobe.d/iwlagn.conf~
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.39-3-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/3.0-0-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/usr/src/linux-headers-3.0-0-generic/include/config/iwlagn.h
rick@rick-HP:~$

---

### Post by pferraro on 2011-06-16
> **garvinrick4 said:**
> #File has been added to 3.0 for iwlagn driver: Seems to fix the unstable 
use of "N" in the intel network cards using iwlagn driver as in previous kernels. 
Was stable in "G" so had to set router in 2.4 ghz to use mixed "G" and "N" instead of just N. Also had to use
a iwagn.conf in /etc/modprobe.d to make card stable, actually taking away the "N"
use in intel card by adding line to /etc/modprobe.d/iwlagn.conf                                   
options iwlagn 11n_disable50=1 11n_disable=1
# Now is stable in "N' of the intel card using iwlagn driver with 3.0 kernel.
#rick@rick-HP:~$ locate iwlagn
/etc/modprobe.d/iwlagn.conf
/etc/modprobe.d/iwlagn.conf~
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.39-3-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/3.0-0-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/usr/src/linux-headers-3.0-0-generic/include/config/iwlagn.h
rick@rick-HP:~$

Really?  I had been dealing with sucky wireless until I figured out the trick of disabling support for N.  It sounds like I can remove that hack?  Cool!  I'll test it out.

---

