---
title: "(Lucid) Wireless connects; disconnects; connects, etc"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by LearningPerson on 2011-11-23
Hello, My neighbor wants to share his bandwidth with me; he tested whether it would be received at the site of my terminal and it could.  

I see his wireless network; have Lucid Lynx; a TL-WN722N adapter; an Atheros Communications Inc. AR5001 Wireless Network Adapter; and when I input: 
$ sudo iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Encryption key:off 
          Power Management:off 
          
It does connect and after about 15 secs, disconnects but tries a again.  I'm connected with a wired provider (Qwest) at this moment. 

I've been through every post possible and have come this far but now need more expert help.

Thanks, Sharon

---

### Post by Sealbhach on 2011-11-23
Try connecting this way, with the command line:

```
sudo dhclient wlan0
```

Watch the terminal and see if it gives you any useful information. Also look in the System Log to see if your neighbours router is giving any reasons for disconnecting.

.

---

### Post by LearningPerson on 2011-11-23
Hi Sealbhach,

Here it is:
 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:24:23:00:33:05
Sending on   LPF/wlan0/00:24:23:00:33:05
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Sealbhach on 2011-11-23
That suggests you didn't get a connection. It looks like you haven't configured you network manager to connect automatically to that router. 

If you have your network manager configured correctly, it should look something like this when you run iwconfig:

```
wlan0     IEEE 802.11abgn  [COLOR=Green]ESSID:"BTHomeHub2-FHDX[/COLOR]"  
          Mode:Managed  Frequency:2.462 GHz  [COLOR=Green]Access Point: 00:8B:5D:94:EB:2A[/COLOR]   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:224  Invalid misc:66   Missed beacon:0

```

If you look at your iwconfig, you don't have an ESSID (the name of your neighbour's router device) and you don't have an Access Point. 

So if I were you I would make sure that you have your network manager set to connect automatically to that router, make sure you have all necessary passwords etc all entered.

.

---

### Post by LearningPerson on 2011-11-24
> **Sealbhach said:**
> That suggests you didn't get a connection. It looks like you haven't configured you network manager to connect automatically to that router. 

If you have your network manager configured correctly, it should look something like this when you run iwconfig:

```
wlan0     IEEE 802.11abgn  [COLOR=Green]ESSID:"BTHomeHub2-FHDX[/COLOR]"  
          Mode:Managed  Frequency:2.462 GHz  [COLOR=Green]Access Point: 00:8B:5D:94:EB:2A[/COLOR]   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:224  Invalid misc:66   Missed beacon:0

```

If you look at your iwconfig, you don't have an ESSID (the name of your neighbour's router device) and you don't have an Access Point. 

So if I were you I would make sure that you have your network manager set to connect automatically to that router, make sure you have all necessary passwords etc all entered.

.


Sealbhach,  

Will try this when my neighbor responds, and get back to you as to whether it worked or not.  Thanks so much,  Sharon

---

### Post by LearningPerson on 2011-11-25
Hi Sealbhach,

I input the ESSID but the Access Point still reads: "Not-Associated".  I have what I believe to be the 10 digit alpha-numeric string and tried inputting it through "Edit Connections" in the box for MAC but it still doesn't show up in the "iwconfig".  Is there a way to input it through the terminal?  Or...any other ideas?  Thanks, Sharon

---

### Post by Sealbhach on 2011-11-25
Hi, you don't need to manually input the ESSID or the Access Point, these are assigned automatically. You just need to select your neighbour's router from the list of available networks and make sure you have the right password or passphrase.

Make sure you have selected the right type of encryption, whether it is WEP or WPA or whatever. All these things you can do in the gui of the network manager.

.

---

### Post by LearningPerson on 2011-11-25
Don't like to be dim but where do I find the "gui of the network manager"?   

Earlier today when I typed "iwconfig", my neighbor's 6 digit router name came up.  Now I'm just getting a really long string of numbers opposite ESSID.  Think I'm going backward here.

Sharon

---

### Post by LearningPerson on 2011-11-25
Ok, Sealbhach,  I got ESSID back (who knows how).  Figured out what you meant by "gui of network manager"....but there are no choices under VPN  - if that is where I'm to look?  If not VPN, which tab should it be?

---

### Post by LearningPerson on 2011-11-26
Hello,

Output of "iwconfig" in the Terminal WHILE there is a connection being tried:

wlan0     IEEE 802.11bg  ESSID:"JT1969"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:XXXXXXX   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


When I am disconnected or it can't access, this is the output:
wlan0     IEEE 802.11bg  ESSID:"p\xE9>\xA1A\xETC\xEC\x18\xDB\"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Also, the try to connect always asks for the password again although Connect Automatically is checked.

Please help.  Thanks, Sharon

---

### Post by Sealbhach on 2011-11-26
Looks like you got connected there. Maybe you could try a different tool than network-manager for connecting to the network. I use something called wicd, which I find works very well and is stable.

You could install it and give it a try, it works much the same way as network-manager and has a nice simple gui:

```
sudo apt-get install wicd-gtk
```Give it a go and see if it works any better.

.

---

### Post by LearningPerson on 2011-11-26
I uninstalled Network Manager and installed WICD.  Seemed to work - again - for a few minutes.  Then it said the password was bad?   Network Manager never said that!

I assume I can't have both Network Manager and WICD installed together?  

I have tried disconnecting my wired connection and trying the wireless - no joy.

---

### Post by Sealbhach on 2011-11-26
OK, so you manage to get connected for a while but then the signal drops. Maybe it's just too weak a signal to remain connected all the time?

It's probably best to remove network-manager while you're using wicd.

If you make changes to wicd and want to bring down and restart the network you can do it this way:

```
sudo service wicd restart
```I don't know why the connection is dropping but I suspect it's because you're too far way from your neighbour's router to maintain a good connection. 

You could look in the sytem log to see if you get any messages or try connecting using only the command line  - you could play around with some of the troubleshooting tips in [this guide]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html").

Hope you get it working 100% soon, sounds like you're making progress.

.

---

### Post by LearningPerson on 2011-11-26
I think you may be right.  The signal strength which only showed up in WICD shows between 37% and then doesn't even show my neighbor's WiFi.  Although he got a strong signal when he tried it in my house in the same place?

However, my USB hookup may not be of good quality?

Will try another one later this evening.

Thanks for sticking with me!

Sharon

---

### Post by fdrake on 2011-11-26
let's see what your neighbor's router looks like
```

sudo iwlist wlan0 scan 
dmesg | grep wlan0 | less 

```
tell us what the name of the essid your are trying ot connect to:
have you tried to connect to an open wifi before with the same computer? have you encountered the same problem? it may be the encryption the issue sometimes or the router itself. Are you able to use a smart phone (with an usb cabble connect to your pc) as a wifi adapter for your computer?

---

### Post by LearningPerson on 2011-11-26
Hi Sealbhach,

There are several wireless in the vicinity but here is his:

sharon@sharon-desktop:~$ sudo iwlist wlan0 scan

[sudo] password for sharon: 

wlan0     Scan completed :


          Cell 05 - Address: 00:14:BF:30:63:CB

                    Channel:6

                    Frequency:2.437 GHz (Channel 6)

                    Quality=28/70  Signal level=-82 dBm  

                    Encryption key:on

                    ESSID:"JT1969"

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

                              24 Mb/s; 36 Mb/s; 54 Mb/s

                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s

                    Mode:Master

                    Extra:tsf=000004cfe7ba9da2

                    Extra: Last beacon: 928ms ago

                    IE: Unknown: 00064A5431393639

                    IE: Unknown: 010882848B962430486C

                    IE: Unknown: 030106

                    IE: Unknown: 2A0100

                    IE: Unknown: 2F0100

                    IE: IEEE 802.11i/WPA2 Version 1

                        Group Cipher : TKIP

                        Pairwise Ciphers (2) : CCMP TKIP

                        Authentication Suites (1) : PSK

                    IE: Unknown: 32040C121860

                    IE: Unknown: DD06001018020204

                    IE: WPA Version 1

                        Group Cipher : TKIP

                        Pairwise Ciphers (2) : CCMP TKIP

                        Authentication Suites (1) : PSK

          
Can't see the top of this but     dmesg | grep wlan0 | less     returns:  


[   23.757586] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   82.160101] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   82.632204] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   86.518461] wlan0: direct probe to AP 00:14:bf:30:63:cb (try 1)

[   86.716041] wlan0: direct probe to AP 00:14:bf:30:63:cb (try 2)

[   86.718070] wlan0: direct probe responded

[   86.718078] wlan0: authenticate with AP 00:14:bf:30:63:cb (try 1)

[   86.719731] wlan0: authenticated

[   86.719771] wlan0: associate with AP 00:14:bf:30:63:cb (try 1)

[   86.721970] wlan0: RX AssocResp from 00:14:bf:30:63:cb (capab=0x411 status=0 aid=2)

[   86.721974] wlan0: associated

[   86.722768] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[   86.744535] wlan0: deauthenticating from 00:14:bf:30:63:cb by local choice (reason=3)

[   86.977612] wlan0: deauthenticating from 00:14:bf:30:63:cb by local choice (reason=3)

[   87.209396] wlan0: direct probe to AP 00:14:bf:30:63:cb (try 1)

[   87.211403] wlan0: direct probe responded

[   87.211407] wlan0: authenticate with AP 00:14:bf:30:63:cb (try 1)

[   87.213213] wlan0: authenticated

[   87.213234] wlan0: associate with AP 00:14:bf:30:63:cb (try 1)

[   87.215434] wlan0: RX AssocResp from 00:14:bf:30:63:cb (capab=0x411 status=0 :



What do you think?

Sharon

---

### Post by fdrake on 2011-11-26
I can suggest you 2 things:

1- ask you neighbour to change the configuration of the router to use for encryption either wpa or wpa2 not both in mix mode (like it does from you output!)

2- to use b/g mode of transmizzion . Do not use "n" mode or mix mode with "n" (b/g/n). "n" tends to create problems for many hardware especially the one pre 2009/10 (for both windows/linux).

another suggestion for you is to try maybe a live cd (either Ubuntu 10.04 or fedora core-16) . Strangly i had your same issue but after trying the live cd (fedora 16) with the wifi, i rebooted to ubuntu  and the wifi was working perfectly with no drops... don't ask me why.

---

### Post by LearningPerson on 2011-11-26
Ooops.  Forgot to answer the rest.  His ESSID is JT1969.  I've never tried to connect to any wifi before.  I'm using a TL-WN722N USB Adapter and have just tried plugging it directly into my computer: Averatec All in One D1133 with the guts under the monitor (very small).

Sorry I don't have a smart phone.
Sharon

---

