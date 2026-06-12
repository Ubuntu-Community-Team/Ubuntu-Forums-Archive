---
title: "Wireless is plug and play in 11.04 but not 10.04"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by mccuisinart on 2011-09-10
Relevant components:

CenturyLink Q1000 modem connected upstairs (includes wireless station)
Cheap TP-Link TL-WN722N wireless USB adapter connected downstairs

This setup is plug and play in 11.04 (using it right now with trial/uninstalled ubuntu 11.04) but I'm having trouble getting it to work with 10.04, which I need for its real-time kernel. I've fiddled around with Network Connections app in 10.04 for a while and nothing doing. I can connect the modem from upstairs to this rig to be able to access the internet for a while to do whatever is needed to get this setup working in 10.04, I just need to know where to go from there, if it's possible at all to get this working in 10.04.

Thanks in advance for any help!

---

### Post by marin123 on 2011-09-10
Do you have wireless networks to choose in 10.04? I mean, does your usb adapter work?
My guess is that 11.04 has newer kernel with drivers for your usb wireless, or the realtime kernel doesn't have that drivers.
Doesn't 11.04 have rt kernel?

---

### Post by gandaran on 2011-09-10
>  TP-Link TL-WN722N wireless USB adapter
what is the wireless chipset model and brand?
to find out type in terminal
```
lsusb
```
depending on the chipset you may have to install drivers or maybe just a minor fix to get it working.

---

### Post by mccuisinart on 2011-09-10
> **marin123 said:**
> Do you have wireless networks to choose in 10.04? I mean, does your usb adapter work?
My guess is that 11.04 has newer kernel with drivers for your usb wireless, or the realtime kernel doesn't have that drivers.
Doesn't 11.04 have rt kernel?

No wireless networks to choose from. Only dialoge that comes up under the connections tab are
[
Wireless Network
disconnected
-----------
VPN Connections ->
]

[QUOTE=gandaran]what is the wireless chipset model and brand?[/QUOTE]

```
ubuntu@ubuntu:~$ lsusb
Bus 002 Device 003: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
```

---

### Post by mccuisinart on 2011-09-10
If this is a driver issue is there any way I can download them from my temp 11.04 connection, put them on another USB stick and just plug the driver files into somewhere on the file system?

---

### Post by gandaran on 2011-09-11
> **mccuisinart said:**
> If this is a driver issue is there any way I can download them from my temp 11.04 connection, put them on another USB stick and just plug the driver files into somewhere on the file system?
I think you don't have to install the driver as the Ubuntu kernel already includes the ath9k driver, maybe you just need to install some firmware for the AR9271 chip.
wait till someone with more knowledge on atheros wireless chips can help you or try posting in the network and wireless section and to get quicker help put "atheros AR9271" on the thread title
[http://linuxwireless.org/en/users/Drivers/ath9k_htc](http://linuxwireless.org/en/users/Drivers/ath9k_htc)
[http://linuxwireless.org/en/users/Drivers/ath9k_htc/devices](http://linuxwireless.org/en/users/Drivers/ath9k_htc/devices)
[http://dwiel.net/blog/tp-link-tl-wn722n-on-ubuntu-10-04/](http://dwiel.net/blog/tp-link-tl-wn722n-on-ubuntu-10-04/)

---

### Post by mccuisinart on 2011-09-11
> **gandaran said:**
> I think you don't have to install the driver as the Ubuntu kernel already includes the ath9k driver, maybe you just need to install some firmware for the AR9271 chip.
wait till someone with more knowledge on atheros wireless chips can help you or try posting in the network and wireless section and to get quicker help put "atheros AR9271" on the thread title
[http://linuxwireless.org/en/users/Drivers/ath9k_htc](http://linuxwireless.org/en/users/Drivers/ath9k_htc)
[http://linuxwireless.org/en/users/Drivers/ath9k_htc/devices](http://linuxwireless.org/en/users/Drivers/ath9k_htc/devices)
[http://dwiel.net/blog/tp-link-tl-wn722n-on-ubuntu-10-04/](http://dwiel.net/blog/tp-link-tl-wn722n-on-ubuntu-10-04/)
Thanks for the links. I did some googling like I should have done in the first place and learned that 10.04 indeed, does not come with the right firmware for the drivers that are already installed. But my timing on this was poor and the place to download the firmware from, kernel.org, is down for maintenance. Hope that hasn't been going on too long...

Anyone have this in their filesystem that they can share? I can't find this thing anywhere on the web, and I think it's all I need because I've got all of the drivers. (?) 

/lib/firmware/ar9721.fw

---

