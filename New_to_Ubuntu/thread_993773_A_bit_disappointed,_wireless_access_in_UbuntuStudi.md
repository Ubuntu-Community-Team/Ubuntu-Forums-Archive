---
title: "A bit disappointed, wireless access in UbuntuStudio"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by thealtruismsociety on 2008-11-26
I've tried normal Ubuntu and Kubuntu and they both read my wireless device fine (Intel) and I was connected in second, Ubuntu Studio Distro had alot of aps I wanted preinstalled so I went with it but not only is there no option to find my wireless connection, I can't find anywhere to access a GUI to set it up. The place all forums want me to go Start > System > Admin > Network is not in the Menu. Help!!!

---

### Post by thealtruismsociety on 2008-11-26
Uppin, this can't just be the Distro, 8.10 worked for normal Ubuntu and Kubuntu for me, why not this distro???

---

### Post by bobnutfield on 2008-11-26
> **thealtruismsociety said:**
> Uppin, this can't just be the Distro, 8.10 worked for normal Ubuntu and Kubuntu for me, why not this distro???

If you have nothing in the menus about your network config, then I wonder if you have the network manager installed.  First, make sure your wireless is recognized.  Open a terminal and type:

> lshw -C Network

See if your wireless shows up in the listing.  If it does, then try:

> sudo apt-get install network-manager-gnome

---

### Post by thealtruismsociety on 2008-11-26
Everything shows up as:

*-network DISABLED

---

### Post by bobnutfield on 2008-11-26
What wireless card to you have, and is this Ubuntu Studio 8.10?

---

### Post by thealtruismsociety on 2008-11-26
I looking up the Gnome network manager on my mac, DL.ed the .tar on a thumbdrive but couldn't install it, i did ./configure and it ran through a bunch of stuff, but when typing make, nothing.

---

### Post by thealtruismsociety on 2008-11-26
Yes this is 8.10 and I have a Intel Pro 3945ABG

---

### Post by bobnutfield on 2008-11-26
The network-manager should be on your install cd  and you should be able to install it from there.  If you have access to a wired connection (ethernet) you can download and install from the repos.

But type lscpi in a terminal and look for which wireless chipset you have and we can help configure it.

---

### Post by bobnutfield on 2008-11-26
> **thealtruismsociety said:**
> Yes this is 8.10 and I have a Intel Pro 3945ABG

In 8.10 that chipset is supported natively.  It should work right out of the  box.  Type in a terminal 

> sudo ifconfig wlan0 up

> sudo ifconfig


This is to see if the wireless is recognized after bringing it up.

---

### Post by thealtruismsociety on 2008-11-26
Hmmm well that brought up three things lo, wlan0 and wmaster0, they all have information there.

---

### Post by Paqman on 2008-11-26
> **thealtruismsociety said:**
> Uppin, this can't just be the Distro, 8.10 worked for normal Ubuntu and Kubuntu for me, why not this distro???

UbuntuStudio 8.10 actually uses a different kernel from regular Ubuntu. There's also bug in the Studio kernel which disables SMP support, meaning multi-core CPUs wouldn't work properly.

Can you post the output of this terminal command:
```
uname -r
```

Just to see what kernel you're actually running.

---

### Post by thealtruismsociety on 2008-11-26
2.6.27-7 generic

---

### Post by bobnutfield on 2008-11-26
> **thealtruismsociety said:**
> Hmmm well that brought up three things lo, wlan0 and wmaster0, they all have information there.

OK, wlan0 is up and can probably be configured.  Are you using encryption on your network?  If so, try these command and see if you can get on line.

> sudo iwconfig wlan0 essid <the name of your network>

> sudo iwconfig wlan0 mode managed

> sudo iwconfig wlan0 key <you encryption key

> sudo dhclient wlan0

If you are not using encryption, leave out the third command.

Since it is showing up with ifconfig, these commands may bring it up.

---

### Post by thealtruismsociety on 2008-11-26
> **bobnutfield said:**
> OK, wlan0 is up and can probably be configured.  Are you using encryption on your network?  If so, try these command and see if you can get on line.









If you are not using encryption, leave out the third command.

Since it is showing up with ifconfig, these commands may bring it up.


At work now I'll try when I get home, by encripted network are you talking about security on the router? On my wireless internet connection? There is a password on that.

---

### Post by thealtruismsociety on 2008-11-27
One thing my Wireless network has a space in the name, when I do taht I get in error, I tried a _ beneath them and it seemed to take. After all that I get this.

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by thealtruismsociety on 2008-11-27
Ok I reinstalled Ubuntu and the Wireless is working fine, I'll just have to install alot of those apps Ubuntu Studio had, oh well.

---

### Post by bobnutfield on 2008-11-27
> **thealtruismsociety said:**
> Ok I reinstalled Ubuntu and the Wireless is working fine, I'll just have to install alot of those apps Ubuntu Studio had, oh well.

Well, it probably would have been possible to get your wireless working in Studio, but I believe you have made the best decision.  As someone else has already mentioned, Studio does not use the same kernel as Intrepid.

Glad it has worked out for you.

---

