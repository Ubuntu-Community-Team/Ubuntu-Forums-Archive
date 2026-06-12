---
title: "Wireless Internet Not Working"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by daewalka on 2008-11-10
Hey I'm new to Ubuntu.  I just installed it for the first time and I'm trying to get my wireless working on my Dell Vostro 1500.  I can only connect to my network through wired connections.  Can anyone help me out with this?

---

### Post by saj0577 on 2008-11-10
Can you post the output of 

```
ifconfig
```

please

Saj

---

### Post by Ryadt on 2008-11-10
Can you post the specs of your laptop. Also the output of ```
lshw -C network
```

---

### Post by daewalka on 2008-11-10
ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:1d:09:c6:14:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17088 (17.0 KB)  TX bytes:17088 (17.0 KB)

```


lshw -C network:
```

  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:c6:14:48
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:5d:fb:38:e1:db
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by Ryadt on 2008-11-10
Go in System > Administration > Hardware Drivers and enable your wireless card in there.

---

### Post by daewalka on 2008-11-10
Thanks for the help thus far...

I don't see any options for enabling a wireless card.  Actually, all I see are options to enable two NVIDIA drivers and a driver named "w|".  The NVIDIA drivers are disabled the "w|" driver is enabled.

Do I need to be connected to the internet?

---

### Post by Ryadt on 2008-11-10
What version of ubuntu are you using?

---

### Post by daewalka on 2008-11-10
Just clean installed 8.10.

---

### Post by Ryadt on 2008-11-10
You have the same card that I have and here is how I've got mine working:


```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx
wget http://myspamb8.googlepages.com/R151517-pruned.zip
unzip R151517-pruned.zip

``````

sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

``````

sudo aptitude remove b43-fwcutter
``````
gksu gedit /etc/init.d/wirelessfix.sh
```Paste this
> 
#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
Save and close the text editor.
```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
``````
sudo update-rc.d wirelessfix.sh defaults
```Reboot and you should get your wireless working.

---

### Post by Jackp90 on 2008-11-10
Another option that might be simpler is this:

From my understanding Ubuntu does not recognize your wireless card . . . this is a quick walk through to use windows wireless drivers in Ubuntu.

1.  Basically what you have to do is install ndiswrapper:

> sudo apt-get install ndisgtk

2.  Download the windows driver from the in the .inf file extension. 

If all that you have is a .exe file for the driver install it in wine so that the inf file shows up when you look at the "c:\\".  

This is the course of action that you are going to have to take because I was only able to find the following driver download directly from dell:

[http://support.us.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R151517&formatcnt=1&libid=0&fileid=202136](http://support.us.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R151517&formatcnt=1&libid=0&fileid=202136)

3.  Install it by going **system** --> **preferences** --> **windows wireless drivers** and choosing the location of the inf file.

---

