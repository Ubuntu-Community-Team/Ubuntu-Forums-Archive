---
title: "Uninstalled policykit-1 by mistake"
date: 2014-08-21
forum: New to Ubuntu
---

### Post by madatadam on 2014-08-21
Hi,

I am pretty new to Ubuntu. I installed 14.04 on my new HP Zbook 15 and after fiddling around with various things for a couple of weeks, I decided to look for a fingerprint recognition software for the Validity sensor. 

I found fingerprint-gui but it did not work. So I decided to remove it and checked for the packages it had installed, one of which was policykit-1-fingerprint-gui. I ran sudo apt-get remove but by mistake I typed in sudo apt-get remove policykit-1. 

Since then all internet options are off and I am not able to mount USB drives or do anything much. For instance when I try to open a USB drive it says "Not authorized to perform operation (polkit authority not available and caller is not uid 0). I figured all this has to do with removing policykit-1 but I cannot reinstall that either because when I say sudo apt-get install policykit-1 it says it cannot find the repositories, which in turn must be because of no working internet, I figure.

I typed in the command grep -iw remove /var/log/dpkg.log based on an answer to someone else's question and I see that I have removed, among other things, policykit-1:amd64*, update-manager, ubuntu-system-service, network-manager, software-center and a bunch of other things.

Can someone please help me figure out how to get my computer back? I need a working internet connection for my work.

Thanks!

---

### Post by sisco311 on 2014-08-21
How do you connect to the Internet? Can you use a wired connection?

---

### Post by steeldriver on 2014-08-21
Is your user account part of the sudo group? if so, there are a couple of ways you can try to bring up an interface without inheriting the required permissions via policykit-1

As a first shot (have to admit I've never tried this irl) see if you can do it via the regular desktop NetworkManager service using the nmcli utility
```

sudo nmcli nm enable true

```

If you are using wireless you will likely also need to do
```

sudo nmcli nm wifi on

```

If the interface doesn't connect automatically, you may need to list the available interface connections
```

nmcli con list

```

and then connect manually using something like
```

sudo nmcli con up id NETGEAR68-5G

```

(replacing NETGEAR68-5G with the name of the correct connection as identified from the previous step). If that all seems to work, confirm that the interface really is up for example using ping
```

ping -c4 www.google.com

```

If none of that works you can do it the old-fashioned way via the networking interface and/or /etc/network/interfaces file. Either way, once the interface is up you should be able to reinstall the policykit-1 package from the online repo

---

### Post by grahammechanical on 2014-08-21
Re-install 14.04.

---

### Post by madatadam on 2014-08-21
I normally use the wifi connection but no the wired connection doesnt work now either.

---

### Post by madatadam on 2014-08-21
Unfortunately the network manager has also been uninstalled (along with a bunch of other things). So none of these things work.

---

### Post by madatadam on 2014-08-21
[COLOR=#000000][INDENT]Re-install 14.04.[/INDENT]
[/COLOR]
[INDENT]
[/INDENT]I guess I could do that but I am saving the best for the last :)

---

### Post by steeldriver on 2014-08-21
OK how about connecting the wired interface then

```

sudo ifconfig eth0 up

sudo dhclient -v eth0

```

(you may need to replace eth0 depending on your local interface naming)

---

### Post by sisco311 on 2014-08-21
> **madatadam said:**
> I normally use the wifi connection but no the wired connection doesnt work now either.

 Setting up a wired connection from the CLI (terminal) is probably easier than setting up a wireless connection.
 
Just plug in the Ethernet cable and run:
```
sudo dhclient **eth0**
```

replace **eth0 **with your NIC's device name. 


```
ls /sys/class/net
```
should list the device names for all NICs on your computer. I'm not sure about the naming convention used in Ubuntu, but the name of the hardwired NIC should be something like *ethX *or *enpXsY*.

EDIT: ninja'd by steeldriver :)

---

### Post by madatadam on 2014-08-21
> **sisco311 said:**
> Setting up a wired connection from the CLI (terminal) is probably easier that setting up a wireless connection.
 
Just plug in the Ethernet cable and run:
```
sudo dhclient **eth0**
```

replace **eth0 **with your NIC's device name. 


```
ls /sys/class/net
```
should list the device names for all NICs on your computer. I'm not sure about the naming convention used in Ubuntu, but the name of the hardwired NIC should be something like *ethX *or *enpXsY*.

EDIT: ninja'd by steeldriver :)

Thanks steeldriver and sisco. I actually managed to get back the network manager and WiFi connectivity with it by manually downloading and copying .deb packages from the internet repositories using another computer and installing them. But when I tried to pull the same stunt on the Software Center and the Update Manager, it kind of backfired due to some dependency issues. What I have now is a working system WITH internet but the Software Center and the Update Manager are gone.

sudo apt-get install software-center just runs into a lot of unresolved dependencies and similar problems for the installation of update-manager etc.

---

### Post by sisco311 on 2014-08-21
> **madatadam said:**
> 
sudo apt-get install software-center just runs into a lot of unresolved dependencies and similar problems for the installation of update-manager etc.

Try to fix the broken dependencies:
```
sudo apt-get update
sudo apt-get -f install
```

If that doesn't help, then please post the error messages.

---

### Post by madatadam on 2014-08-21
Ok. I think I pretty much solved most things. I managed to hunt down the different packages that I uninstalled in one go with a lazy apt-get remove. Then manually I pieced together the Network Manager, Software Center and other parts of the system. Now only the Synaptic Update Manager GUI does not work. Everything else seems to have come back to shape. Thanks all for your help. Learnt a bit about Linux along the way!

EDIT: Thanks Sisco I guess you posted just a sec before me!

---

