---
title: "Unable to connect to Netvigator ISP"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by andrewkeenan on 2012-02-07
Hi, I recently installed Ubuntu (latest version) on my old Inspiron 500m and it all looks and sounds great. However, I can't connect to the internet. I'd happily give you screenshots but I can't work out how to do that even, I'm afraid to say. 

I do remember that it returns a line saying the password is bad, but the password is fine. I checked with PCCW Netvigator. And I can connect fine via my EeePC. So, clearly I have done something wrong somewhere. 

Although not urgent, I would appreciate any help or advice (to say nothing of then trying to set up a network and get wireless working, but let's leave that for another day). 

For what it's worth I followed the Makeuseof.com guide, which is a little out of date, as well as the instructions on the site. 

Let me know what you need me to find out for you and how to get a screengrab if that's possible. Hoping someone can help (was a little disappointed to see no one else in the HK group seems to have had any problems hooking up to Netvigator). 

Thanks lots, Andrew

---

### Post by cariboo on 2012-02-09
The first thing you need to determine is if networking is working at all. Because you aren't able to connect to the internet, the easiest way to troubleshoot your problem, is to use the terminal. You didn't specify what version you are using, so it's hard to tell you how to access the terminal. If you are using 11.04 or newer press Ctrl-Alt-t to open a terminal, if you are using something older, click Applications->Accessories->terminal. Once you have a terminal open type the following command:

```
sudo lshw -C network
```

The output of the above command should look something like this:

> description: Ethernet interface
       product: MCP61 Ethernet
       vendor: NVIDIA Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       **logical name: eth0**
       version: a2
       serial: 00:24:21:b7:69:49
       size: 100000000
       capacity: 100000000
       width: 32 bits
       clock: 66MHz
       capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=forcedeth** driverversion=0.64 duplex=full ip=192.168.1.225 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 memory:dee7d000-dee7dfff ioport:de00(size=8)

In the above output, I have bolded the two most important parts of the output.

If you have a usb thumb drive, you can create a text file of the output of the above command, and transfer it to a system with a working internet connection, the command would look like this:

```
sudo lshw -C network > network.txt
```

this will create a text file called network.txt that you can copy to your thumb drive. Paste the text file in your next post.

---

### Post by andrewkeenan on 2012-02-11
Hi Cariboo,
Many thanks for your advice. Apologies for not having the relevant info at hand first time around. Here's what I got with: 
sudo lshw -C network  

(as you can see, i didn't have any luck with "> network.txt"


andrew@andrew-Inspiron-500m:~$ sudo lshw -C network > network.txt
    [sudo] password for andrew: 
    andrew@andrew-Inspiron-500m:~$ sudo lshw -C network
      *-network:0             
           description: Wireless interface
           product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
           vendor: Intel Corporation
           physical id: 3
           bus info: pci@0000:01:03.0
          logical name: eth1
           version: 04
           serial: 00:04:23:95:9b:93
           width: 32 bits
           clock: 33MHz
           capabilities: pm bus_master cap_list ethernet physical wireless
           configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
           resources: irq:5 memory:fcfff000-fcffffff
      *-network:1
           description: Ethernet interface
           product: 82801DB PRO/100 VE (MOB) Ethernet Controller
           vendor: Intel Corporation
           physical id: 8
           bus info: pci@0000:01:08.0
           **logical name: eth0**
           version: 81
           serial: 00:0d:56:7a:37:0c
           size: 10Mbit/s
           capacity: 100Mbit/s
           width: 32 bits
           clock: 33MHz
           capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes **driver=e100 **driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
           resources: irq:11 memory:fcffe000-fcffefff ioport:ecc0(size=64)
    andrew@andrew-Inspiron-500m:~$ sudo lshw -C network > network.txt
    andrew@andrew-Inspiron-500m:~$ sudo lshw -C network > network.txt
    andrew@andrew-Inspiron-500m:~$


from the little i've read elsewhere and vaguely understood the driver=e100
could be a problem






here's another command i tried that may give some useful info:
  


andrew@andrew-Inspiron-500m:~$ cat /etc/network/interfaces
    auto lo
    iface lo inet loopback
     
   
   
   
  auto dsl-provider
    iface dsl-provider inet ppp
    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
    provider dsl-provider
     
   
  auto eth0
    iface eth0 inet manual
    andrew@andrew-Inspiron-500m:~$

Thanks again for your help, Cariboo. Much appreciated.

---

