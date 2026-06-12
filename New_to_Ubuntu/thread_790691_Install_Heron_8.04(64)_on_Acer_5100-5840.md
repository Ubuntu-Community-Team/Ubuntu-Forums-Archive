---
title: "Install Heron 8.04(64) on Acer 5100-5840"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by ndo on 2008-05-11
Hello-

I'll get to the point, and not waste your time. I'm completely new to linux, so much so that a lot of the "fixes" on forums make no sense to me. I'm hoping to get some ground-level help on some issues I'm having, learning some useful ubuntu/xwindows knowledge along the way.

I've installed Hardy Heron 64 for my AMD Turion 64x2. It turns on. Yay. But there are some problems.

1. Wi-fi: I've google'd the hell out of this, and know its not an easy thing. So far, I've used ndiswrapper to install the ar5007eg-64-0.2 driver. After a reboot, it shows my wireless active, and even shows the available networks. But it won't associate with the access point or give me an ip!! Any ideas?

2. The built in webcam won't work, and all the google searches yield "webcam: worked out of the box." Mine doesn't. Is there a driver I need to ndiswrapper? Is there an application to utilize the webcam? I tried "camera monitor" - it doesn't do anything, as in, doesn't even open.

3. Torrents: yeah, I know this is a Ubuntu forum, and I get it - but let me explain. When I go to open a torrent file, Firefox asks if I'd like to use "Transmission" to open the torrent with. No, hell no I would not. I'd like to use Azureus, which I installed. But in the "select program" pulldown, there aren't any programs. Just files (i.e. photos, mp3s, system files) - no apps to select. WTF? Are they hidden or something?

A big thank you to ANYONE who can help with any of these items - a hotlink, a FAQ, anything, I'm desperate. Till then I'll keep scouring the web...

BTW, info (just so no one gets snippy):

Acer Aspire 5100-5840
AMD Turion 64 x2 1.6 Ghz
Atheros AR5007eg wireless LAN
Bison Orbicam
Hardy Heron ver. 8.04 AMD64

---

### Post by Tom--d on 2008-05-11
You can uninstall Transmission from add/remove :)

You can then save the torrent file and open it from your desktop or where ever in Azureus. (right click the torrent file and go to open. if Azureus is not there.. click Add.. it should be there. then select it :)


With wireless, I had the same problem but different wireless card. First of all, do this command in the terminal

'iwconfig' and find out your wireless interface, for example mine is:

```
tom@Laptop:~$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point:....
          and soo on
```
See where the wlan1 is, for yours it will be different. You will need that for the next bit. 
connect to your wireless as normal. **when the first light on the system tray lights up..do this command in the terminal**
```
sudo iwconfig <Your network interface (mines wlan1)> key open

so it would look like this:
sudo iwconfig wlan1 key open
```

Did it connect?
What encryption is your wireless?

---

### Post by ndo on 2008-05-11
> **Tom--d said:**
> You can uninstall Transmission from add/remove :)

You can then save the torrent file and open it from your desktop or where ever in Azureus. (right click the torrent file and go to open. if Azureus is not there.. click Add.. it should be there. then select it :)

Yeah, that's what I've been doing so far - is this just SOP for ubuntu, or is there a way to have Azureus (or anything else) set as the "default" application for handling torrents as in Windows? 

This is really a minor thing, its just annoying having to save, manually open, then delete afterwards. 

BTW, thanks for the advice! Good people make the difference!

The wireless:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Qnet-ARF"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

For the key open, i got an error:
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

---

### Post by Tom--d on 2008-05-11
ok..
Whats your encryption of your wireless?

---

### Post by L0cKd0wN on 2008-05-11
1) Right click on the .torrent file.
2) "Properties".
3) "Open With" tab.
4) Click "Add".
5) Search for Azureus. If it's not in the list, click "Use a custom command" and type in "azureus" (no-quotation marks). That should do the trick.

6) Be strong.  There can be a huge learning curve with Linux at first, but it pays off large dividends to those who stick with it! Cheers!

L0cK

---

### Post by shifty_powers on 2008-05-11
as for number three, just click on save as for the torrent, save on desktop, open azureus, and then drag and drop...

---

### Post by ndo on 2008-05-11
> **Tom--d said:**
> ok..
Whats your encryption of your wireless?

Uhm, sorry, I'm not sure I follow you. The answer I'm inclined to give is none - its an open network (so no WEP, WPA, etc). I'm showing the network, but I'm unable to associate with the access point.

---

### Post by L0cKd0wN on 2008-05-11
> **shifty_powers said:**
> as for number three, just click on save as for the torrent, save on desktop, open azureus, and then drag and drop...

While I'm certain that would work, he wants default behavior enabled for every torrent.  I think my fix is more appropriate. ;)

L0cK

---

### Post by ndo on 2008-05-11
> **L0cKd0wN said:**
> 1) Right click on the .torrent file.
2) "Properties".
3) "Open With" tab.
4) Click "Add".
5) Search for Azureus. If it's not in the list, click "Use a custom command" and type in "azureus" (no-quotation marks). That should do the trick.

6) Be strong.  There can be a huge learning curve with Linux at first, but it pays off large dividends to those who stick with it! Cheers!

L0cK

Thanks, man -

I feel like a bonehead for not trying that myself...I'm just so institutionalized with Windows, that thinking of changing the "open with" properties outside of firefox didn't even occur to me - DUR! 

I appreciate the help, and the encouragement.

---

### Post by Tom--d on 2008-05-11
Encryption = WEP/WPA etc.. 

When you see your wireless, it doesnt have a lock next to it?

do this in terminal:```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo dhclient -r wlan0
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 essid "YOUR ESSID NAME"
sudo dhclient wlan0
```

Does it connect then? by checking, do 
```

ping -c 3 www.google.co.uk
``` 
(Its just easier that way)

---

### Post by ndo on 2008-05-11
> **Tom--d said:**
> Encryption = WEP/WPA etc.. 

When you see your wireless, it doesnt have a lock next to it?

do this in terminal:```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo dhclient -r wlan0
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 essid "YOUR ESSID NAME"
sudo dhclient wlan0
```

Does it connect then? by checking, do 
```

ping -c 3 www.google.co.uk
``` 
(Its just easier that way)

What I got:

ndo@NDO:~$ sudo ifconfig wlan0 down
[sudo] password for ndo: 
ndo@NDO:~$ sudo ifconfig wlan0 up
ndo@NDO:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:19:7d:f8:56:d4
Sending on   LPF/wlan0/00:19:7d:f8:56:d4
Sending on   Socket/fallback
ndo@NDO:~$ sudo iwconfig wlan0 mode Managed
ndo@NDO:~$ sudo iwconfig wlan0 essid "Qnet-ARF"
ndo@NDO:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:19:7d:f8:56:d4
Sending on   LPF/wlan0/00:19:7d:f8:56:d4
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ndo@NDO:~$ ping -c 3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (216.239.59.99) 56(84) bytes of data.

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2007ms

I have no idea what any of this means, but I know I'm still SOL...

Also, I went into the Hardware Drivers section, and both Atheros Hardware Access Layer and Support for Atheros 802.11 Wireless LAN Cards have checks in the "enabled" box, but under "status" they are showing "Not in Use" - is this normal, or indicative of the problem?

---

### Post by Tom--d on 2008-05-11
Are you positive you have no encryption on your wireless? anything at all? Looking at that tells me your wireless router is not accepting. this is due to encryption on the wireless. You need your wireless key to access the wireless.

```

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
```
this means the wireless is not accepting. 

A normal connection will look like this:
```
user@computer:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:12:17:35:17:10
Sending on   LPF/wlan0/00:12:17:35:17:10
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 299133 seconds.
```

Its all made up ;)

---

### Post by ndo on 2008-05-11
Not positive on the encryption, but I'm pretty sure there is none: I'm in a barracks in Kuwait, connecting to the Q-Net wireless access point, or trying to. Once connected, there is a login page where you, y'know, log in with username/pass and then get access to the net. In windows, I've always been able to connect, and it always shows (or showed, back when Windows was working) it as an open network.

So, the HAL and Atheros Card support not being in use is not an issue?

---

### Post by Tom--d on 2008-05-11
> **ndo said:**
> Not positive on the encryption, but I'm pretty sure there is none: I'm in a barracks in Kuwait, connecting to the Q-Net wireless access point, or trying to. **Once connected, there is a login page where you, y'know, log in with username/pass and then get access to the net.** In windows, I've always been able to connect, and it always shows (or showed, back when Windows was working) it as an open network.

So, the HAL and Atheros Card support not being in use is not an issue?

Thats encryption for the wireless.
Until you know it, i cannot do anything :\

When you click on the network icon in the system tray, and locate your wireless. Click on it. tell me what happens next? infact, just print screen it.

---

