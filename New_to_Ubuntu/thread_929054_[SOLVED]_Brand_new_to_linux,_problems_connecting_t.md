---
title: "[SOLVED] Brand new to linux, problems connecting to internet"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by xravex on 2008-09-24
I have just installed Kubuntu KDE-4 8.04.1 on my desktop computer. This is my first attempt at using linux, and am a little slow at getting started. I'm trying to get my computer connected to the internet, the problem is I cannot detect the information automatically( My ISP provides me with a set IP address, subnet mask, default gateway and DNS servers.)I have been unsuccessful on finding any information on how to do this manually. Anything to send me in the right direction is appreciated.

---

### Post by knix on 2008-09-24
If you still have windows, you can probably find out in windows. Or just call you ISP.

---

### Post by xravex on 2008-09-24
I have all that information.. I'm just having a hard time inputting it into linux. I can't seem to find a place to do that

---

### Post by The Cog on 2008-09-24
How do you want to connect? Ethernet, USB modem (make/model), wireless etc?

---

### Post by xravex on 2008-09-24
Sorry I failed to mention its an Ethernet connection

---

### Post by lwvmobile on 2008-09-24
You know I tried out Kubuntu with KDE 4 recently as a test and coming from Ubuntu with GNOME the KDE 4 version seems to be missing tons of configuration menu's, so you have  to do a lot of stuff via the terminal. I think your best bet  for ease of use to put in a manual network configuration would be to download a synaptic package to handle it, but you'll need an Internet connection, so try using the commands:

```
sudo ifconfig eth0 192.168.99.14 netmask 255.255.255.0 up

```

and for DNS open /etc/resolv.conf and add

nameserver 208.67.222.222
nameserver 208.67.220.220

into the list. You can open it with  kwrite I think in KDE  so that would paste this into the terminal 

```
sudo kwrite /etc/resolv.conf
```

and paste your DNS or just what's up above since its OpenDNS numbers.

Good Luck.:KS

---

### Post by xravex on 2008-09-24
Okay I will give that a try. Is there anything I need to do to set the default gateway or will that not matter?

---

### Post by xravex on 2008-09-24
When I type
```
sudo kwrite /etc/resolv.conf
```
I get the error "sudo: kwrite: command not found

---

### Post by perlluver on 2008-09-24
> **xravex said:**
> When I type
```
sudo kwrite /etc/resolv.conf
```
I get the error "sudo: kwrite: command not found

Try sudo : kate.  That should be installed.

---

### Post by xravex on 2008-09-24
i know kate is installed. but I get the same error when I type
```
sudo kate /etc/resolv.conf
```

---

### Post by lwvmobile on 2008-09-24
Sorry about that, but let me do you one better.

For manual configuration of ip, mask, and gateway, use the command

```
sudo kate /etc/network/interfaces
```

and paste your info like so

```
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.254.77
netmask 255.255.255.0
gateway 192.168.254.254

auto eth0

```

and the same above for DNS, open /etc/resolv.conf

```
sudo kate /etc/resolv.conf
```

and paste in your naemservers

```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5019
#
### END INFO

search domain.invalid




nameserver 208.67.222.222
nameserver 208.67.220.220

```

save and that should stick.
:KS:KS

Edit: Restart the interface after applying these settings, use 

sudo ifconfig eth0 down
sudo ifconfig eth up

and if that doesn't work, reboot once.

---

### Post by lwvmobile on 2008-09-24
> **xravex said:**
> i know kate is installed. but I get the same error when I type
```
sudo kate /etc/resolv.conf
```

you can always use 

```
sudo nano /etc/resolv.conf
```

but its a terminal text editor, but ou can still paste into it, then use ctrl+x to exit and hit y to save.

---

### Post by xravex on 2008-09-24
I got interfaces open. When I try to save the file I get this error

The document could not be saved, as it was not possible to write to /etc/network/interfaces

Check that you have write access to this file or that enough disk space is available.

I know I have the disk space available.

---

### Post by lwvmobile on 2008-09-24
> **xravex said:**
> I got interfaces open. When I try to save the file I get this error

The document could not be saved, as it was not possible to write to /etc/network/interfaces

Check that you have write access to this file or that enough disk space is available.

I know I have the disk space available.

make sure to sudo on the command to open it; else you cannot save it.

---

### Post by Ptero-4 on 2008-09-24
use kdesu instead of sudo since you´re using a KDE app.

---

### Post by xravex on 2008-09-24
I have made those changes, checked and rechecked them. Now knetworkmanager does not even see an active device.

---

### Post by lwvmobile on 2008-09-24
Not sure how reliable the KNetworkManager is, but what is the output of 

```
ifconfig
```

you may need to bring the interface up using

```
kdesu ifconfig eth0 up
```

We'll get you going:popcorn:

---

### Post by xravex on 2008-09-24
I double checked everything and restarted the system and now it is working. thanks for all the help everyone

---

