---
title: "ASUS USB N10 Wirelss Adaptor"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by Confused2570 on 2012-10-03
Hello!

I'm new to Ubuntu, installed it alongside XP the other day and it's all working fine apart from one thing, my wireless adaptor. The first time I tried to get it working, I messed up Linux so I had to reinstall from CD (oops). This time, I have all the drivers I need for my Adaptor (RTL8192SU) loded up in Ndiswrapper. However, when I try to connect to my BT-HOMEHUB 2.0 with WPA security (802.11n) it won't connect even though it has connected before. It will however connect to unprotected wireless networks. Does anyone know how I can get the adaptor working properly again? Thanks!

Ubuntu 12.04 LTS
Fujitsu Siemens Amilo Li 1705
1.7GB RAM
1.60GHz Intel Processor
VA250 Motherboard

---

### Post by westie457 on 2012-10-03
Welcome to the Forum

Realtek drivers are not my favourite things to work with. Having said that I am willing to help or at least start you in the right direction. Follow the instructions in this post please.

[http://ubuntuforums.org/showpost.php?p=12177056&postcount=2](http://ubuntuforums.org/showpost.php?p=12177056&postcount=2)

The information generated will be very helpful.

Thank you

---

### Post by Confused2570 on 2012-10-05
Hello again! Here is the NetInfo.txt file [http://db.tt/KCYYrpnL](http://db.tt/KCYYrpnL), it was made while connected to an open network though. Many thanks!

---

### Post by NikTh on 2012-10-05
Hi , 
you must clear up some things here. 

I can see two network adapters. One Usb and one Pci (internal). 

So what is your point now ? I mean what exactly you want to do ? 
Do you want to use the Usb network adapter and not use the internal ? (pci) 

You cannot use both at the same time ! 

What I suggest is .. 
0) Remove (unplug) your Usb wireless adapter.

1) Remove completely the ndiswrapper 

```
sudo modprobe -rf ndiswrapper 
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk 
sudo rm /etc/modprobe.d/ndiswrapper.conf 
sudo rm -r /etc/ndiswrapper/*  
sudo depmod -a
```2) Disable hardware encryption for ath5k driver 
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
```Reboot your PC (without usb wireless adapter) and see if Internal wireless Pci adapter works and if you can connect. 

IF NOT , then run again the script and upload again the results. (Without Usb wireless) It will be much clear if you could connect via Ethernet cable. 

Thanks

---

### Post by Confused2570 on 2012-10-05
The internal adaptor does not work, it can't connect to 802.11n networks. I keep it off all the time and no drivers are installed for it. As for Ethernet, no Ethernet cables will work with my pc for some reason so I can't connect to that. I'm only trying to get the USB adaptor to work.

---

### Post by westie457 on 2012-10-06
Is this a laptop you are using?

With laptops unless things have changed the internal wireless chip must be turned on for a USB wireless adaptor to work.

Just checked and it is still right, the internal chip must be turned on.

The advice posted by 'NikTH' is good. So try his as well along with my suggestion.

Hope this helps

Thank you

---

### Post by kurt18947 on 2012-10-06
I think perhaps you're making things more complicated than they need to be.  I have 2 adapters using the Realtek 8192SU chip.  Both have been plug 'n' play since 11.04.  Yes, the internal Wifi switch will probably have to be on.  You may need to blacklist the other device's drivers.

---

### Post by Confused2570 on 2012-10-07
Okay, that explains it better. I am using a laptop so ill turn on the internal card and see if that works!

---

### Post by kurt18947 on 2012-10-07
If you haven't done so, you may have to remove NDISwrapper is you haven't done so.  There is kernel support for the 8192SU chip set.

---

### Post by Confused2570 on 2012-10-08
Thanks nikTh! It works again! (The USB that is! :) Thanks everyone else for their suggestions too! :popcorn:

---

