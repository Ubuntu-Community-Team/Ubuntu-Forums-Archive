---
title: "Pls Help!! Problem with wireless after upgrading to 8.04"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by CalvinChile on 2008-05-11
Hi, 
I had Kubuntu 7.10 running fine but after upgrading to Kubuntu 8.04 my wireless card is not detected (0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)), and (of course) also KNetManager doesn't show any wireless network
My PC is a Dell Inspiron 6400


Any hint?

---

### Post by hermes0710 on 2008-05-12
Had you manually installed the driver? If yes then you might need to recompile and reinstall the driver. If not, check "System>Administration>Hardware Driver" to see if the driver is listed, checked as enabled and in use. If it's listed but not enabled, you should establish an internet connection and tick the checkbox in order to let the old Restricted hardware drivers manager download and install it.

---

### Post by shifty_powers on 2008-05-12
tbh, doing an upgrade is always risky. most people will recommend you either back up your data and do a clean install or that you have a separate /home partition. (my advice personally).

a tip. download and burn the livecd and run it. This will soon tell you if a clean install will work with your wireless or if hardy just doesn't like your wireless card anymore....

---

### Post by subzero316 on 2008-05-12
> **CalvinChile said:**
> Hi, 
I had Kubuntu 7.10 running fine but after upgrading to Kubuntu 8.04 my wireless card is not detected (0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)), and (of course) also KNetManager doesn't show any wireless network
My PC is a Dell Inspiron 6400


Any hint?




try

```
sudo modprobe iwl3945
```

---

