---
title: "wireless card monitor mode"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by cooldude786 on 2012-08-28
Hi,

I would like to know that when i put my wireless card in monitor mode using the command: 
sudo iwconfig wlan0 mode monitor

why do i loose wireless connectivity??? Also how could i connect to the internet after i put my wlan0 card in monitor mode???? I have the intel link wifi   1000 bgn wireless card in my laptop. Please reply as i am using kismet.


Thank you

---

### Post by fractalman on 2012-08-29
You should stop the wifi before putting it in monitor mode, the correct way would be

```


sudo ifconfig wlan0 down 

sudo iwconfig wlan0 mode monitor 

sudo ifconfig wlan0 up
```[B]

Monitor mode[/B], or RFMON (Radio Frequency MONitor) mode, allows a computer with a wireless network interface controller  (NIC) to monitor all traffic received from the wireless network, monitor mode allows packets to be captured without having to associate with an access point or ad hoc network first. Monitor mode only applies to wireless networks, while promiscuous mode  can be used on both wired and wireless networks. Monitor mode is one of  the six modes that 802.11 wireless cards can operate in: Master (acting as an access point), Managed (client, also known as station),  Ad hoc, Mesh, Repeater, and Monitor mode.

Usually the wireless adapter is unable to transmit in monitor mode and is restricted to a single wireless channel, though this is dependant on the wireless adapter's driver, it's firmware,  and it's chip set's features.  Also in monitor mode the adapter does not check to see if the cyclic redundancy check (CRC) are correct so some packets captured may be corrupted


If you are using kismet to crack wifi networks then you won't get any advice on this forum as they don't discuss hacking/cracking here so please bear that in mind before asking more questions

---

