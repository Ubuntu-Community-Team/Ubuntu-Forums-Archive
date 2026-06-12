---
title: "Acer Aspire 7250 Laptop only works with Ethernet cable!"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by janmartin on 2012-04-26
Hi all,

I have a new Acer Aspire 7250 laptop with 
Acer Nplify 802.11/b/g/n for WIFI.

So I connect to the wireless, then unplug the Ethernet cable, get an "Wired Network Disconnected" message, and then the laptop freezes.

I have to press the Power button to switch it off and then back on. That only works as long as the Ethernet cable is plugged in.

I can do it repeatedly.
I need to carry it away from my desk. 
What to do?

Thanks.

---

### Post by calavier62 on 2012-04-27
This is a relatively well known bug with ubuntu - of any release really. when you boot your computer, try forcing the kernel option "acpi=on" at boot, and see if that helps. 

Also try typing this into the terminal
```
sudo modprobe -r acer_wmi
``````
sudo rfkill unblock wifi
``````
sudo rfkill unblock all
```*note each line is a separate command.

Cheers!

---

### Post by janmartin on 2012-04-28
Didn't help at all.

I think it has to do with the 
Atheros AR9485 Wireless Network Adapter 

not being supported.

---

### Post by wildmanne39 on 2012-04-28
Hi, try this please it helps most people with your problem.

Possible fix is to make network boot as a first option in BIOS (hold F2 after reboot). 
Thanks

---

### Post by janmartin on 2012-04-28
Already tried that. 
I can switch Network boot on or off, (without change) but not move the entry.

---

### Post by ReneMages on 2012-04-29
Try to remove atl1c module just before to use wifi :

modprobe -r atl1c

best regards
Rene Mages ( GnuPG_key 1024D/2CC455D9 )
[http://renemages.wordpress.com](http://renemages.wordpress.com)

---

### Post by centaurusa on 2012-04-29
> **janmartin said:**
> 
I think it has to do with the 
Atheros AR9485 Wireless Network Adapter 
not being supported.

If you can get by using just the wireless connection, you may be able to disable the Ethernet controller and avoid the machine hanging when trying to connect to the Internet.  This has been an issue with the Acer Aspire One netbook which also uses an Atheros wireless adapter.  Full details are posted at:

[http://linuxnorth.wordpress.com/2011/10/23/wireless-less/](http://linuxnorth.wordpress.com/2011/10/23/wireless-less/)

---

### Post by janmartin on 2012-04-30
centaurusa,

that worked.

Thanks.

---

