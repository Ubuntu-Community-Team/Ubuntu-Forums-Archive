---
title: "Is it really impossible to get an Atheros 5007eg wireless modem to work?"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Carnivorum on 2008-11-15
Bs'd

Is there nobody who can tell me how to get my atheros 5007eg modem to work??

---

### Post by bobnutfield on 2008-11-15
Are you using Hardy or Intrepid?  The ath5k module in Intrepid's 2.6.27 kernel should support it natively.  In Hardy you will need the madwifi drivers.  But, either way it will work, assuming by modem you are talking about the wireless chipset to connect to a wireless router.

---

### Post by drs305 on 2008-11-15
> Is there nobody who can tell me how to get my atheros 5007eg modem to work??
Perhaps not, given the information. Please tell us which version of ubuntu you are using and perhaps what you have tried. 

There is a note about the atheros 5000 series wireless cards in the Intrepid Release notes if you are running the 2.6.27 kernel. If this applies to you, check out the note about 2/3 of the way down regarding your card:
[http://www.ubuntu.com/getubuntu/releasenotes/810]("http://www.ubuntu.com/getubuntu/releasenotes/810")

---

### Post by Patrick793 on 2008-11-15
Open a terminal and enter this:
```
sudo apt-get install linux-backports-modules-intrepid-generic
```
Reboot, go to System > Administration > Hardware Drivers, disable "Support for Atheros 802.11 wireless LAN cards.", but keep "Support for 5xxx series of Atheros 802.11 wireless LAN cards." enabled.

Reboot again. Now in your network program, you can connect to wireless.

If network manager isn't working, try [Wicd](http://wicd.sourceforge.net/).

---

### Post by Carnivorum on 2008-11-16
> **Patrick793 said:**
> Open a terminal and enter this:
```
sudo apt-get install linux-backports-modules-intrepid-generic
```
Reboot, go to System > Administration > Hardware Drivers, disable "Support for Atheros 802.11 wireless LAN cards.", but keep "Support for 5xxx series of Atheros 802.11 wireless LAN cards." enabled.

Reboot again. Now in your network program, you can connect to wireless.

If network manager isn't working, try [Wicd](http://wicd.sourceforge.net/).

Bs'd

I followed the instructions, installed Wicd, because with the network manager I couldn't get it to work, but now I don't get Wicd to work. 

When I type "wicd" in the terminal, he tells me:  "Root priviledges are required for the daemon to run properly.  Exiting."

How do I get around that one?

---

### Post by seshomaru samma on 2008-11-16
> **Carnivorum said:**
>  

When I type "wicd" in the terminal, he tells me:  "Root priviledges are required for the daemon to run properly.  Exiting."

How do I get around that one?
like this:
```
sudo wicd
```

---

### Post by bumanie on 2008-11-16
I ended up resorting to using ndis wrapper on my laptop - has worked well since.

---

### Post by dgillie on 2008-11-24
ok got wicd to work, but now i can not scan for networks. it says no wireless networks available

---

