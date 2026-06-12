---
title: "how to disable to automatic wireless interface up in ubuntu?"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by surjya on 2012-10-15
On my laptop I have a built in wireless card and I got one external connected via usb. By ifconfig command I saw both the cards connects to internet and gets IP.

eth1 - the interface my laptop has in-built wlan1 - I have connected externally via usb.

Now I applied "sudo ifconfig eth1 down" so that i can use only wlan1. But this eth1 goes down for sometime and then come up again automatically. So I am not able to test my externally usb connected wifi adapter.

Can anyone suggest me way to disable eth1 interface?

---

### Post by squakie on 2012-10-15
Well, if I had a built in wireless and it worked, the only reason I could see to try a USB wireless adapter would be if it provided more functionality - things like better security, 802.11n, etc..  That being said, is there an option in your BIOS to turn off the on board wireless adapter?

---

### Post by surjya on 2012-10-15
> **squakie said:**
> Well, if I had a built in wireless and it worked, the only reason I could see to try a USB wireless adapter would be if it provided more functionality - things like better security, 802.11n, etc..  That being said, is there an option in your BIOS to turn off the on board wireless adapter?

Actually I need to work on both interfaces as I am developing something and testing. So I need a flexible way to switch between the two interfaces frequently. So I need an easiest way to do rather than disabling it in BIOS or blacklisting.

---

### Post by NikTh on 2012-10-15
If you want to disable the wireless , find the driver that uses and remove it. 

Give this command ```
lspci -nnk | grep -iA2 net
``` see in "Kernel driver in use:" and then give this command 
```
lsmod
``` 

Probably you will see the module (driver) listed there. 

You can remove it with ```
sudo modprobe -rvf <module-name>
``` 

Alternatevly you can use this command 
```
sudo lshw -C network
``` take a look at "description: Wireless interface" and see driver= 

Thanks

---

### Post by grahammechanical on 2012-10-15
I do not understand this statement:

> eth1 - the interface my laptop has in-built wlan1

My motherboard has 2 x built in ethernet adapters and 1 x wireless adapter. They work independantly of each other. I can disconnect the wireless adapter and still use either ethernet adapter and I can disconnect the ethernet adapters and still use the wireless adapter.

Have you tried Network manager to edit these connections. If you have eth(0) or eth(1) (now called wired connection 1 and wired connection 2 in 12.10) set to Connect automatically in Network Manager then that is what will happen.

The situation will be the same with any wireless connection if it is set to connect automatically.

Regards.

---

