---
title: "[SOLVED] Can't find INF file for HP M7670"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by segalm on 2008-08-25
I have looked everywhere through Google to see if I can find the Linux WiFi LAN drivers for my HP media PC M7670-UK. The only files on the HP web site are executables, which of course won't run on Ubuntu. Can anybody point me in the right direction of where I can find the INF file I need to install WiFi drivers under Ubuntu? Thanks in advance.

---

### Post by tangibleorange on 2008-08-25
> **segalm said:**
> I have looked everywhere through Google to see if I can find the Linux WiFi LAN drivers for my HP media PC M7670-UK. The only files on the HP web site are executables, which of course won't run on Ubuntu. Can anybody point me in the right direction of where I can find the INF file I need to install WiFi drivers under Ubuntu? Thanks in advance.

download the .exe file. then, navigate to the folder in which you downloaded it (using 'cd' from the terminal) and run:

```
sudo apt-get install cabextract
cabextract *driverfile.exe*
```

replacing driverfile with the file name. this should then produce all the files, including a folder with the .inf and .sys files (both required for ndiswrapper, which i assume you are using)

hope that helps :)

EDIT:
if there is an option, make sure to select the Windows XP driver, not the Vista one. vista don't seem to play nice with ndiswrapper (or anything for that matter)

---

### Post by segalm on 2008-08-25
Thanks for your prompt reply. The instructions you give work OK but I'm obviously not using the correct executable from HP's web site because everything works but it does not enter a wireless entry in my Network Setting dialog. I have tried both the following files from the HP web site., neither create the entry. Could I trouble you to further assist me?
	
»   	Fall 2006 Original Intel LAN Drivers
				04-2007 				9.4.14.0 				- 				1.07M 			
	  				  				  				  				 
	
»   	Fall 2006 Original HP Wireless LAN Drivers
				09-2006 				4.1.2.112 				- 				1.13M

---

### Post by tangibleorange on 2008-08-25
> **segalm said:**
> Thanks for your prompt reply. The instructions you give work OK but I'm obviously not using the correct executable from HP's web site because everything works but it does not enter a wireless entry in my Network Setting dialog. I have tried both the following files from the HP web site., neither create the entry. Could I trouble you to further assist me?
	
»   	Fall 2006 Original Intel LAN Drivers
				04-2007 				9.4.14.0 				- 				1.07M 			
	  				  				  				  				 
	
»   	Fall 2006 Original HP Wireless LAN Drivers
				09-2006 				4.1.2.112 				- 				1.13M

yeah no problem! well I think you need the wireless LAN drivers. how far have you got into installing ndiswrapper? have you installed the inf file by using:
```
sudo ndiswrapper -i *inffile.inf*
```
also, could you also post the output of:
```
cat ~/.bash_history | grep ndiswrapper
```

---

### Post by phidia on 2008-08-25
What wireless card do you have "lshw -C network" entered in a terminal should show it.
There are several guides with links to the drivers for many wireless cards at the forums here but of course you need to know the card type first.

Plus if you have an atheros card (popular with HP's) there is madwifi which works without windows drivers.

---

### Post by segalm on 2008-08-25
I ran the install through the Network Settings application as opposed to Terminal. But I have tried the terminal command as you say and it says it's already installed. I have also run the cat command but sorry, don't know where the output has been written to. I have the correct exe from the HP web site. And yes, it's and Atheros card! - as below
maxwell@Maxwell-Linux:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562V 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:18:f3:94:be:18
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-2 ip=192.168.0.4 latency=0 module=e1000 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10

---

### Post by tangibleorange on 2008-08-25
ah ok my mistake. in that case, could you post the output of:

```
ndiswrapper -l
```

---

### Post by segalm on 2008-08-25
Yes, it's 
maxwell@Maxwell-Linux:~$ ndiswrapper -l
wn5301a : driver installed
        device (168C:001B) present (alternate driver: ath_pci)
maxwell@Maxwell-Linux:~$

---

### Post by tangibleorange on 2008-08-25
> **segalm said:**
> Yes, it's 
maxwell@Maxwell-Linux:~$ ndiswrapper -l
wn5301a : driver installed
        device (168C:001B) present (alternate driver: ath_pci)
maxwell@Maxwell-Linux:~$

ok. so the driver has installed properly, but is not registering. could you do the following and then reboot:

```
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'blacklist ath_pci' | sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by segalm on 2008-08-25
Well tangibleorange that certainly worked well! It just needed another reboot after I had been able to configure the wireless connection entry. I thank you very much. One of my areas of knowledge is in Windows and mobile communications, if you need any help please let me know.

BTW, is there anything I need to know for future if it suddenly stops working?

Regards,
Maxwell

---

### Post by tangibleorange on 2008-08-25
> **segalm said:**
> Well tangibleorange that certainly worked well! It just needed another reboot after I had been able to configure the wireless connection entry. I thank you very much. One of my areas of knowledge is in Windows and mobile communications, if you need any help please let me know.

BTW, is there anything I need to know for future if it suddenly stops working?

Regards,
Maxwell

ok no problem! glad it's working for you. i can't think of anything if it stops working, but I doubt it will - I've been using ndiswrapper for about 10 months and it hasn't let me down once!

please marked this thread solved (Thread Tools -> Solved).

---

