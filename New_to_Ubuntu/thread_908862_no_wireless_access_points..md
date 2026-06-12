---
title: "no wireless access points."
date: 2008-09-02
forum: New to Ubuntu
---

### Post by dsmcginn on 2008-09-02
i'm new to ubuntu. i just installed the drivers for my wifi card, but now none of the WAPs show up in my network manager.

what do i need to do to fix this?

thanks in advance.

=)

---

### Post by falcon61102 on 2008-09-02
Need a bit more info.  Could you go into the terminal, run and post the results of:
```
sudo lshw -C network
```

That will tell us some details about your card.

---

### Post by dsmcginn on 2008-09-02
doug@doug:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:16:be:ac
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.10 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:3f:6d:d3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

### Post by falcon61102 on 2008-09-02
Are you using any type of encryption on your access points?

Also, I know it sounds trival but if you right click on the Network Manager, is Enable Wireless checked?

---

### Post by dsmcginn on 2008-09-02
no, my access point is unsecured, and yes, it's enabled. =)

---

### Post by falcon61102 on 2008-09-02
That's odd.  Did you follow a HowTO to get your drivers installed?  And which drivers did you use?

---

### Post by dsmcginn on 2008-09-02
i used ndiswrapper to install them

and i used this to help me out too:
[http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x)

and i got the driver from here:
[http://members.driverguide.com/driver/detail.php?driverid=1080937](http://members.driverguide.com/driver/detail.php?driverid=1080937)

---

### Post by falcon61102 on 2008-09-02
Ok try this and see if it works.  If it does, let me know and I'll show you how to make it permanent.
```
sudo rmmod ndiswrapper
sudo rmmod ath_pci
sudo modprobe ndiswrapper
```

Once you complete that, check for your access points.

---

### Post by dsmcginn on 2008-09-03
doug@doug:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
doug@doug:~$ sudo rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules
doug@doug:~$ sudo modprobe ndiswrapper
doug@doug:~$ 


that's what i got...i'm assuming that it didn't work. lol.

---

### Post by falcon61102 on 2008-09-03
Actually, it may have.  The two errors you received just mean that those modules weren't loaded earlier.  Try running:
```
sudo ndiswrapper -l
```
-l is a lower case L

That will list what driver ndiswrapper has loaded if any.

---

### Post by dsmcginn on 2008-09-03
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)
doug@doug:~$

---

### Post by falcon61102 on 2008-09-03
I think its the driver that you installed.  I don't think that it works for that card.  

The other day I set up a laptop with your card and in about ten minutes I was using the net.  I used the driver that is posted in Post #15 of the following thread:
[http://ubuntuforums.org/showthread.php?t=575785&highlight=TOPDOG+PCI+802.11n&page=2](http://ubuntuforums.org/showthread.php?t=575785&highlight=TOPDOG+PCI+802.11n&page=2)

What you'll need to do is uninstall the driver that is currently installed with ndiswrapper and install using this one.  Then you should be good to go.
To do that:
```
sudo rmmod ndiswrapper
sudo ndiswrapper -r net5211.inf
```

I think thats the name of the driver file, but I'm not positive.

EDIT: You may also want to look into ndisgtk in the Synaptic Package Manager.  Start Synaptic and search for ndiswrapper and you should see it there.  Install that and it is a graphical app that will install and uninstall network drivers for you without the command line interface.  Once it installs you can find it under System>Administration

---

