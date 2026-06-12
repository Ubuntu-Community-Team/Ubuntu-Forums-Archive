---
title: "No edit connection option in ubuntu 16.04"
date: 2020-08-14
forum: New to Ubuntu
---

### Post by nickshah23 on 2020-08-14
I have installed ubuntu OS 16.04 on my new system. I am not able to see network interfaces on terminal, only loopback 0 interfaces is what i see.

After few troubleshooting command from youtube/google now i dont see edit connection option. Typing “Sudo apt-get —-purge remove network-manager“ command i dont see edit connection option now. So from my another laptop i downloaded respective network-manager package and but couldn’t install it in my new system

Could someone please help me setting up network interface so that i can connect to internet. I have wifi at home and i have connected my system through LAN cable and wants it to assign ip address automatically.

Please please..any help would be greatly appreciated 
Thanks

---

### Post by CelticWarrior on 2020-08-14
Welcome.

> [COLOR=#000000]I have installed ubuntu OS 16.04 on my new system.[/COLOR]


WHY? Ubuntu 16.04 has less than a year of support left. 

> [COLOR=#000000]I have installed ubuntu OS 16.04 on my new system. I am not able to see network interfaces on terminal, only loopback 0 interfaces is what i see.[/COLOR]


Could have other cause but most probably support for your network devices came with newer releases. Then everything you did to troubleshoot is an absurd. Never do things willy nilly just because some random YT video says so. You would have done much better asking here before doing stuff you don't understand.


Conclusion: Install the current LTS release, **Ubuntu 20.04**. Should any problem persist then before anything else read [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) and proceed as instructed (run the script to obtain diagnostic information) and post the results here.

---

### Post by nickshah23 on 2020-08-14
@CelticWarrior.
I want to install eve-ng(a networking simulator) which only runs on ubuntu 16.x version, thats why i installed this version.
Is there anything else i can do to fix this now?
Or downloading new 16.x version in pendrive from another laptop and installing again in my new pc.
Pls guide

---

### Post by nickshah23 on 2020-08-15
I have downloaded network-manager_1.2.6-0ubuntu0.16.04.3_amd64.deb & network-manager-gnome_1.2.6-0ubuntu0.16.04.4_amd64.deb. When i opened that and clicked on install button i can see below details like 
Version: 1.2.6-0ubuntu0.16.04.3, 
license:Open Source. 
Source:Ubuntu 
Size: 9.8MB. 
When i click on OPEN SOURCE it takes me to below website and because i dont have internet access nothing opens. [https://www.ubuntu.com/about/about-ubuntu/licensing](https://www.ubuntu.com/about/about-ubuntu/licensing). 
Same with gnome network-manager.deb

---

### Post by nickshah23 on 2020-08-15
Now i have uninstalled previous version i.e 16.04.6 LTS and installed 16.04.7. Now someone please guide me how to connect it to internet. Ifconfig shows only loopback interface. I could troubleshoot but little scared of running into the problem again. It took lot of time for me to install this OS back.

---

### Post by nickshah23 on 2020-08-16
When i did cd /etc/NetworkManager i can see below files. 
1)Conf.d 2)dnsmasq.d 3)NetworkManager.comf 4)VPN 5) dispatcher.d 6)dnsmasq-shared.d 7)system-connections –


Sudo nano /etc/NetworkManager/NetworkManager.conf shows managed to false which i changed to true. Also i did sudo service network-manager restart and rebooted the system but nothing changed

Lspci | grep -i network shows 28.00.0 Network controller: Intel Corporation Device 2723 (rev 1a). And for ethernet it shows 26.00.0 Ethernet controller:Realtek Semiconductor Co., Ltd. Device 8125 (rev 04). When i issued sudo lshw -C network i didnt see any drivers keyword in output. In capabilities i have: pm msi pciexpress msix vpd bus_master cap_list. Does this mean i have drivers missing??? 

Please help

---

### Post by grahammechanical on 2020-08-17
When running lshw -C network we get an output something like this

>  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: enp6s4
       version: 14
       serial: 00:1a:92:82:d4:32
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.14 latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: irq:19 memory:feaf4000-feaf7fff ioport:b800(size=256) memory:feac0000-feadffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlx0015af0e9be0
       serial: 00:15:af:0e:9b:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=5.4.0-42-generic firmware=N/A ip=192.168.1.67 link=yes multicast=yes wireless=IEEE 802.11


From that output I know that there are drivers for both the Wired and the Wireless adapters. The key words to look for are: broadcast= driver= driverversion= 

If by some chance the ethernet and the WiFi adapters were switched off there would not be anything after the = sign with those three keywords. Is there a setting in the BIOS/UEFI settings that has disabled the WiFi?

When you installed Ubuntu did you install it with an active internet connection so that the installation could be updated as part of the installation process?

Please run this command

```
rfkill list
```

On my machine is see this

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


That tells me that the WiFi adapter is not switched off in hardware (for whatever reason) nor is it switched in software (that is by the operating system)

Regards

---

### Post by nickshah23 on 2020-08-23
root@eve-ng:~# lshw -C network
*-network UNCLAIMED
description: Ethernet controller
product:Realtek Semiconductor Co. ,Ltd.
Vendor: Realtek Semiconductor Co. ,Ltd.
Physical id: 0
bus info: pci@0000:26:00.0
Version:04
width: 64 bits
Clock: 33Mhz
Capabilities: pm msi pciexpress msix vpd bus_master cap_list
Configuration: latency=0
Resources: ioport:f000(size=256) memory: f7700000-f770ffff memory: f7710000-f7713ffff

*-network UNCLAIMED
description: Network controller
Product:Intel Corporation
Vendor:Intel Corporation
Physical id: 0
bus info: pci@0000:28:00.0
Version: 1a
Width: 64 bits
Clock: 33Mhz
Capabilities: pm msi pciexpress msix bus_master cap_list
Configuration: latency 0
Resources: memory:f7600000-f7603fff

And when tried running rfkill list
The program rfkill is currently not installed. You can install it by typing: apt install rfkill

When i issued lspci there is a long output in which i can see Ethernet controller: Realtek Semiconductor Co., Ltd Device 8125(rev 04). In bios i can see its Realtek PCIe 2.5GBE family controller.

Network controller: Intel Corporation Device 2723 (rev 1a)

I am installing ubuntu 16.04.7 server amd64.iso OS and also while OS installing LAN is connected to my system. I checked in bios setting
onboard lan controller is enabled.
Network stack: enabled
Ipv4 PXE support: enabled



I also installed “ &#8234;linux-image-4.20.17-eve-ng-ukms+_4.20.17-eve-ng-ukms-brctl_amd64.deb&#8236;” but still no luck.

I told this to my friend and he said the ethernet adapter is very new and doesn’t support ubuntu. He suggested to buy older version of ethernet adapter and this could solve your problem.


Now i am totally confused what to do to solve this.

---

