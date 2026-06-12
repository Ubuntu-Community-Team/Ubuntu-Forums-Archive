---
title: "Is there a way to &quot;repair&quot; network connection as in windows?"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by sergiobd on 2008-09-27
Hi there,

I'm using ubuntu 8.04.1. I have found the network manager is sometimes buggy, specially when i come back from hibernation. Is any way for "repairing" the internet connection as in windows?

---

### Post by RequinB4 on 2008-09-27
The windows "repair" network connection would not help you here - all it does is:

>     *  Attempts to renew the DHCP lease, if the connection obtains its IP address through DHCP, using a broadcast message.
    * Flushes the Address Resolution Protocol (ARP) cache using the command

      arp -d * 

    * Flushes the NetBIOS cache using the command

      nbtstat -R

    * Flushes the DNS cache using the command

      ipconfig /flushdns

    * Reregisters the NetBIOS name and IP address with WINS using the command

      nbtstat -RR 

    * Reregisters the computer name and IP address with DNS using the command

      ipconfig /registerdns



I don't really have a specific answer other than try to use suspend over hibernate - but wanted to note the difference - this windows tool only does specific things that aren't really an issue in ubuntu, you're probably having issues with the program nm itself.

Well, there is always the alternative program (wicd) that is questionably better than nm, but someone else can probably help you if you need to install it correctly. :)

---

### Post by sergiobd on 2008-09-30
OK! thanks!

---

### Post by wilsong on 2008-09-30
Suspending your computer still keeps the system using battery power, if you kept it in suspend and put in into a carrying case, (lets say you went to fly on a plane) your system might get really hot, and not be good for the system. Hibernation, turns the system completely off storing the systems running programs from ram, to the hard drive.  So the system is completely off, not just using very minimal battery power to keep the ram from loosing its memory. If you want to try ifconfig here is some info about it.

I used  "  ifconfig " a lot, 

Its like the IPCONFIG of windows, 

sometimes if i have a ethernet or wireless (mostly wireless) card that is messing up ill do something such as

ifconfig wlan0 0.0.0.0 

that will set the IP address to all 0's 

and then I will set it back to the ip adress that i wanted 

ifconfig wlan0 192.168.1.2 

man ifconfig if you want to see all the settings avaible 

you might have to do '   sudo ifconfig wlan 192.168.1.*  ' 

i do everything from root console, so i dont typically have to do sudo, but i think that is a Super User task, so if ifconfig doesnt work alone, put sudo in front of it.

---

### Post by techstop on 2008-09-30
You could try restarting networking by;

```
sudo /etc/init.d/networking restart
```

---

