---
title: "How do I install a driver?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Moonhead on 2008-07-17
I recently installed Ubuntu 8.04 on my HP 6710b laptop and everything seems to work fine except my wireless connection. Roaming mode does not detect any wireless networks. The laptop has a wireless kill switch that will that I cannot activate, and I suspect this is the problem. The wireless card is an Intel Pro/Wireless 3945 ABG, PCI ID 8086:4222. When I look in Device Manager the kill switch is listed under the main heading of the wireless card but it has a question mark for an icon. I found and downloaded a linux driver from the intel site but I have no idea how to make use of it. I extracted the file and read the included installation instructions which looked horribly complicated. I even attempted to enter some of the commands at a terminal (after entering sudo) but all I got was "no such job". I can't even figure out how to find out what my current driver is. All attempts to find a straightforward explanation of how to load a driver in Linux or Ubuntu on the web were utterly fruitless.

---

### Post by MobiusNZ on 2008-07-18
Does your wireless card show up in the Restricted Drivers Manager? I use Kubuntu so it's a little different for me, but have a look for it in your System menu.

---

### Post by framinglory on 2008-07-18
the intel 3945ABG drivers are built-in to the linux kernel after 2.6.24 or something like that, and the fact that you have a roaming mode suggests the card is working. Try typing in a console "sudo iwconfig" and see if it returns the name of an interface (probably eth1 or something similar) that has wireless extensions

edit: also, to see what modules are loaded into the kernel, type lsmod into a terminal. it will give a (probably) decently long list, so you can use 
lsmod | grep "iwl3945" to find if the driver is loaded. if it returns something like iwl3945 and some numbers, then the module is loaded. if it returns nothing, than it is not loaded

---

### Post by Moonhead on 2008-07-18
I am currently using a wired connection on the laptop. When I click on the network icon in the notification area, the option for enable wireless is greyed out. The ESSID "Nickname" is not the name of my router's SSID. There are no restricted drivers loaded. 

david@david-laptop:~$ sudo iwconfig
[sudo] password for david: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod yeilded the following:
iwl3945                89844  0 
snd_seq_oss            35584  0 
iwlwifi_mac80211      219108  1 iwl3945

Thank you for your replies.

---

### Post by framinglory on 2008-07-18
okay, so the driver is loaded, and the interface is detected (your interface for wireless is wlan0)
go to System>Administration>Network. Click the unlock button on the bottom right, enter your password, and then make sure the box next to wireless connection is checked, and double click on the entry to make sure it is in roaming mode.

---

### Post by Moonhead on 2008-07-18
Roaming mode is checked but everything else is grayed out. Sorry I didn't reply sooner but I didn't expect such a quick reply.

---

### Post by Moonhead on 2008-07-18
Roaming mode is checked but everything else is grayed out. Sorry I didn't reply sooner but I didn't expect such a quick reply. Should I use the quick reply button for any particular reason? What is the difference?

---

### Post by firdausazizan on 2008-07-18
i'm a new user. i'just install the ubuntu os. but i have a problem with my grapihc card driver.. i'm using acer 4520 notebook. I hope you all can help me on how to install these driver. i can't wait to show my new os to my friends. Ubuntu is the best!!

---

### Post by philinux on 2008-07-18
> **firdausazizan said:**
> i'm a new user. i'just install the ubuntu os. but i have a problem with my grapihc card driver.. i'm using acer 4520 notebook. I hope you all can help me on how to install these driver. i can't wait to show my new os to my friends. Ubuntu is the best!!

This is called hijacking a thread. Please start your own with a specific title regarding graphics card.

---

### Post by framinglory on 2008-07-18
everything else is grayed out because you are in roaming mode. Before you double clicked on the "wireless connections" there was a box to the left of the name, was that checked? I attached a picture of the network screen with the box highlighted.

---

### Post by Moonhead on 2008-07-18
All of the boxes have a "-" in them and do not respond to any clicking.

---

### Post by framinglory on 2008-07-18
Alright, does your network have a password? i'm not sure about the commands for using a password, but you can use
iwconfig wlan0 essid your_essid
then use
dhclient wlan0
to see if that works. if you have a password on your wireless, please tell me if it's wpa or wep and i'll try to get back to you with those commands

---

### Post by Moonhead on 2008-07-18
david@david-laptop:~$ iwconfig wlan0 essid ummagumma
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
No password, only a router password and a WEP encryption key.

---

### Post by framinglory on 2008-07-18
oh i'm sorry! i forgot the sudo part.
sudo iwconfig wlan0 essid your_essid
sudo dhclient wlan0
edit: and for wep, i belive you just do
sudo iwconfig wlan0 key your_key

---

### Post by Moonhead on 2008-07-18
This is what I got. Does it matter that I'm currently using a wired connection to the same router?

david@david-laptop:~$ sudo iwconfig wlan0 essid ummagumma
david@david-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 17994
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: Input/output error
SIOCSIFFLAGS: Input/output error
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:77:af:7e:b5
Sending on   LPF/wlan0/00:1b:77:af:7e:b5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
david@david-laptop:~$

---

### Post by framinglory on 2008-07-18
it's possible, i'm not entirely sure at this point. try
sudo ifconfig eth0 down to knock out the wired connection, then do sudo ifconfig wlan0 down and sudo ifconfig wlan0 up and then the sudo iwconfig essid and sudo dhclient commands again. Finally use sudo ifconfig eth0 up to bring it back up if wireless doesn't work.

---

### Post by Moonhead on 2008-07-18
No luck.
david@david-laptop:~$ sudo ifconfig eth0 down 
david@david-laptop:~$ sudo ifconfig wlan0 down
david@david-laptop:~$ sudo ifconfig wlan0 up
david@david-laptop:~$ sudo iwconfig essid ummagumma
iwconfig: unknown command "ummagumma"
david@david-laptop:~$ sudo iwconfig wlan0 essid ummagumma
david@david-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 18783
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:77:af:7e:b5
Sending on   LPF/wlan0/00:1b:77:af:7e:b5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
david@david-laptop:~$ sudo ifconfig eth0 up
david@david-laptop:~$ sudo iwconfig wlan0 key 0312893348866de847976db4e
david@david-laptop:~$ iwconfig wlan0 essid ummagumma
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.

In windows there is a wireless kill switch/button that is lit when wireless is active. In Ubuntu I can't get it to come on. I suspect that to be the problem. As I mentioned earlier, I have already acquired an Intel driver for my wireless card that is specifically for Linux, but I don't know how to install it. I am assuming that it is a different driver from the one I have now because no propriety drivers show up on my system. Do you think that it's worth a shot installing the new driver?

---

### Post by Moonhead on 2008-07-18
No luck.
david@david-laptop:~$ sudo ifconfig eth0 down 
david@david-laptop:~$ sudo ifconfig wlan0 down
david@david-laptop:~$ sudo ifconfig wlan0 up
david@david-laptop:~$ sudo iwconfig essid ummagumma
iwconfig: unknown command "ummagumma"
david@david-laptop:~$ sudo iwconfig wlan0 essid ummagumma
david@david-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 18783
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:77:af:7e:b5
Sending on   LPF/wlan0/00:1b:77:af:7e:b5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
david@david-laptop:~$ sudo ifconfig eth0 up
david@david-laptop:~$ sudo iwconfig wlan0 key 0312893348866de847976db4e
david@david-laptop:~$ iwconfig wlan0 essid ummagumma
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.

In windows there is a wireless kill switch/button that is lit when wireless is active. In Ubuntu I can't get it to come on. I suspect that to be the problem. As I mentioned earlier, I have already acquired an Intel driver for my wireless card that is specifically for Linux, but I don't know how to install it. I am assuming that it is a different driver from the one I have now because no propriety drivers show up on my system. Do you think that it's worth a shot installing the new driver?

---

### Post by framinglory on 2008-07-18
well, i use a similar laptop with a killswitch, and my light is currently off, if you don't have the light working in linux, then it'll just stay like it's off. The fact that you have a wlan0 says that a) the wireless card is on, and working, and b) the drivers are also working. I'm not sure why you're having the problems that you are though. Also, it looks like you entered the essid and then used dhclient, and then later tried to enter the key? I'm pretty sure you have to enter the key before using dhclient.

Edit: also, which driver did you download? ipw3945? or iwl3945? ipw is an old and abandoned driver, and iwl is the one you are currently using. You could try installing ipw, but it'll be a hassle and i don't think it will get you any further. You may want to try and install an alternative wireless manager such as netapplet (sudo apt-get install netapplet) and see if that one will let it work.

---

### Post by Moonhead on 2008-07-18
The driver is iwlwifi_1.0.0-1. I downloaded netapplet and a new icon appeared in the notification area. It said that wireless wlan0 was active but I could not browse. I have to hang it up for now. Thank you very much for your help.

---

### Post by framinglory on 2008-07-18
sorry i couldn't be of more help!

---

