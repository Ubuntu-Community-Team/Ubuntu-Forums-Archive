---
title: "Wireless dropping out"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by Carlzam on 2011-11-14
[B]Eeepc 701 - 900 Mhz,  2Gb. Ram,  4Gb + 8Gb Ext.  Lubuntu 11.10...
[/B]
I just installed Lubuntu 11.10, everything works very good except for My wireless connection, it does connect ok, but it last for maybe 2 minutes then it drop out, then after a minute it will connect again, then it will hold for a minute or two and drop again and it keep doing this for good.
I should say I am new in Linux, but I have a general idea how works.

So, if somebody can help me to solve this problem it will be much appreciate 

Thanks in advance

Carl

---

### Post by SteveDee on 2011-11-15
> **Carlzam said:**
> [B]...So, if somebody can help me to solve this problem it will be much appreciate ...

I suggest you start by running a wireless monitor to watch what happens during the 2 mins that it runs.

Go to Synaptic Package Manager and search for: wavemon
Once you have installed wavemon, open a terminal and just type: wavemon

Note: wavemon may crash straight away if the terminal window is too small, so stretch the window to a reasonable size then run it again.

You don't say whether wifi is/was working on this netbook with other operating systems, or whether the whole setup (including wifi) is new.

---

### Post by gandaran on 2011-11-15
> **Carlzam said:**
> [B]Eeepc 701 - 900 Mhz,  2Gb. Ram,  4Gb + 8Gb Ext.  Lubuntu 11.10...
[/B]
I just installed Lubuntu 11.10, everything works very good except for My wireless connection, it does connect ok, but it last for maybe 2 minutes then it drop out, then after a minute it will connect again, then it will hold for a minute or two and drop again and it keep doing this for good.
I should say I am new in Linux, but I have a general idea how works.

So, if somebody can help me to solve this problem it will be much appreciate 

Thanks in advance

Carl
paste the output of this command
```
sudo lshw -C network
```

---

### Post by nothingspecial on 2011-11-15
> **gandaran said:**
> paste the output of this command
```
sudo lshw -C network
```

In your menu go Accessories > LXTerminal and put the above command in there.

Post the results in code tags please which can be done by clicking the # symbol at the top of the posting box and pasting the terminal results in between them.

---

### Post by MG&amp;TL on 2011-11-15
I get this occasionally too when I'm uploading AND downloading. What are you doing at the time?

---

### Post by Carlzam on 2011-11-15
I will install wavemon and will report what's happening.
I had Ubuntu for netbooks I don't remember what version installed here before but it was too slow, but the wireless internet connection worked very good, but everything was slow, so far with Lubuntu 11.10 everything work fine except for the wireless.

I opened Synaptic Package manager and search for wavemon but I got nothing back

> **SteveDee said:**
> I suggest you start by running a wireless monitor to watch what happens during the 2 mins that it runs.

Go to Synaptic Package Manager and search for: wavemon
Once you have installed wavemon, open a terminal and just type: wavemon

Note: wavemon may crash straight away if the terminal window is too small, so stretch the window to a reasonable size then run it again.

You don't say whether wifi is/was working on this netbook with other operating systems, or whether the whole setup (including wifi) is new.

---

### Post by Carlzam on 2011-11-15
```

 carlzam@carlzam-701:~$ sudo lshw -C network
[sudo] password for carlzam: 
  *-network               
       description: Ethernet interface
       product: L2 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:50:58:b6
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 duplex=full firmware=L2 ip=192.168.1.69 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fbfc0000-fbffffff memory:fbfa0000-fbfbffff
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:66:cd:81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fbef0000-fbefffff
carlzam@carlzam-701:~$ 

 
```> **gandaran said:**
> paste the output of this command
```
sudo lshw -C network
```

---

### Post by Carlzam on 2011-11-15
```

```Actually not much, just waiting, idling to see how long will it last connected.
sometimes I go online and it will drop out, wait for some time and will comeback.

> **MG&TL said:**
> I get this occasionally too when I'm uploading AND downloading. What are you doing at the time?

---

### Post by gandaran on 2011-11-15
>    description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
I tried searching the problem with this wireless chipset but haven't found any, the ath5k driver usually works very well so all I can do is ask what security mode is the router set to? or try changing the security mode (and maybe the channel too) to see if it can fix the problem.

---

### Post by Carlzam on 2011-11-15
```

```Thank for your response, the security mode is Wep and the settings here are with WPA, I tried to changed to WEP in the network manager and save but it won't make the changes and will create another network with the same name and WPA, so I don't know; now like I said I am not very knowledgeable with Linux, so if you want me to make some changes or try something I would appreciate if you tell me how and what, if not I will be running around like a chicken with out head....
Thanks again
Carl
> **gandaran said:**
> I tried searching the problem with this wireless chipset but haven't found any, the ath5k driver usually works very well so all I can do is ask what security mode is the router set to? or try changing the security mode (and maybe the channel too) to see if it can fix the problem.

---

### Post by gandaran on 2011-11-15
> **Carlzam said:**
> ```

```Thank for your response, the security mode is Wep and the settings here are with WPA, I tried to changed to WEP in the network manager and save but it won't make the changes and will create another network with the same name and WPA, so I don't know; now like I said I am not very knowledgeable with Linux, so if you want me to make some changes or try something I would appreciate if you tell me how and what, if not I will be running around like a chicken with out head....
Thanks again
Carl
changing the security mode is done on the router configuration not network manager and  also try changing the wireless channel if network manager detects more than one network as this could be the problem if other networks are using the same channel.

---

### Post by SteveDee on 2011-11-15
> **Carlzam said:**
> ...I opened Synaptic Package manager and search for wavemon but I got nothing back...

I'm surprised you could not find wavemon.

You could also install it by opening LXTerminal and typing:-
```

sudo apt-get install wavemon

```

You may also find "wifi-radar" useful as it shows all local wifi access points and the channels they are running on. It may help to avoid channels already in use, but other devices also operate in this band, and other factors may affect performance: [http://ubuntuforums.org/showthread.php?t=1768125](http://ubuntuforums.org/showthread.php?t=1768125)

---

### Post by Carlzam on 2011-11-16
```

```I got a little frustraded, so I formated and re installed the system and so far is working, I will keep my fingers crossed.......
Thanks you guys for your help.

Carl
> **gandaran said:**
> changing the security mode is done on the router configuration not network manager and  also try changing the wireless channel if network manager detects more than one network as this could be the problem if other networks are using the same channel.

---

### Post by Rex Bouwense on 2011-11-16
So the re-installation of the OS has apparently solved your problem.  Keep us informed and be sure to mark the thread as solved if you have it working.

By the way, welcome to the forums and thank you for choosing Lubuntu.

---

