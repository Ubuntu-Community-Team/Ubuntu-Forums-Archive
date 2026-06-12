---
title: "Slow Wifi with 12.10"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by mattc1977 on 2013-01-13
Hi all
I have decided to give ubuntu another try on my new machine. I tried on an old computer and failed to get it online, so gave up.

This time im running 12.10 but the wifi is dodgy ok to begin with but then goes slow. 
I know other people have had a similar problem but there seems to be various fixes and imk not sure what im doing. 
Some people say I need to up date network manager? Im not sure how to do this?
And others give fixes I just dont understand (yet) how to do.
Im determined to get this working as I dont want to go back to the dark side (windows)

Many thanks 

Matt

---

### Post by Pjotr123 on 2013-01-13
Try disabling power management for the wireless card only:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card)
(item 2.1, right column)

---

### Post by mattc1977 on 2013-01-13
Hi thanks for replying

Ive done that and the power management for wireless has been turned off but it sadly hasnt made a difference. :(

---

### Post by mattc1977 on 2013-01-13
Any other idea guys?

---

### Post by bkratz on 2013-01-13
> **mattc1977 said:**
> Any other idea guys?



It would be nice to know what wireless card you have. Please post the output of 

```
lspci -vnn | grep -i net
```

---

### Post by mattc1977 on 2013-01-13
Thanks for the reply

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
matt@matt-GA-970A-DS3:~$ 

That seems to be for the ethernet controller perhaps I should of said im using a usb D-link DWA-140

---

### Post by bkratz on 2013-01-13
> **mattc1977 said:**
> Thanks for the reply

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
matt@matt-GA-970A-DS3:~$ 

That seems to be for the ethernet controller perhaps I should of said im using a usb D-link DWA-140



look under 

lsusb

---

### Post by mattc1977 on 2013-01-13
Thanks

Bus 003 Device 002: ID 07d1:3c09 D-Link System DWA-140 RangeBooster N Adapter(rev.B1) [Ralink RT2870]
Bus 004 Device 002: ID 04d9:2517 Holtek Semiconductor, Inc. 
Bus 007 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

---

### Post by bkratz on 2013-01-13
Not an expert on that device---but
Here is a link about the same thing, but on 12.04, I bet the solution is similar.

[http://askubuntu.com/questions/131768/dlink-wireless-dwa-140-speeds-are-crippled-on-12-04](http://askubuntu.com/questions/131768/dlink-wireless-dwa-140-speeds-are-crippled-on-12-04)

---

### Post by mattc1977 on 2013-01-13
Sadly the down load it suggests dosnt seem to be there.

---

### Post by bkratz on 2013-01-13
> **mattc1977 said:**
> Sadly the down load it suggests dosnt seem to be there.



Ralink has apparently been merged with another company and the website doesn't seem to have all the links working yet. 

Anyway I PM'ed an expert and hopefully he can join us in the thread, if not I will keep looking for information.

---

### Post by mattc1977 on 2013-01-13
Thats really kind of you! 

Thank you :p

---

### Post by chili555 on 2013-01-13
I'm not sure my first option would be to install Ralink's 2010 version driver.

They are now known as Mediatek: [http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

I'd probably try a driver parameter first:```
sudo modprobe -r rt2800usb
sudo modprobe rt2800usb nohwcrypt=Y
```If that helps, we can write a conf file and make it persistent.

If not, you might try Ubuntu's custom version of compat-wireless:```
sudo apt-get install linux-backports-modules-[COLOR="Red"]cw[/COLOR]-3.6-quantal-generic
```Reboot and let us have your report.

---

### Post by mattc1977 on 2013-01-13
Thank you for your time and help guys the last fix you mentioned seems to work just fine. I cant thank you enough I owe you all some beers ;)

Best Wishes

Matt

---

### Post by bkratz on 2013-01-13
Glad you got it going, sure is good to be able to depend on a very sharp friend!  Please mark the thread as solved ( in the tools ) in case it helps someone else.

---

### Post by chili555 on 2013-01-13
Awesome! Glad it's working. We're happy to have helped.

---

