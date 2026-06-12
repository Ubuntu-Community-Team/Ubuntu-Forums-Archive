---
title: "wireless problems"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by marcusesses on 2008-07-25
Hi, 

This is my first post (presumably of many), and I apologize if this has already been answered, but I couldn't find much information...ok, I found A LOT, and couldn't make sense of it...

I'm on an Acer Aspire 2920, which is running Ubuntu 8.04.

I'm trying to connect from a wireless router...I have a Toshiba computer running Windows as well, and the connection is fine...I haven't tried connecting through ethernet.

My network controller is an Intel PRO/wireless 3945ABG Network conection. 

When I type lsusb in the terminal, I get something like this...

Bus 006 Device 003: ID 5986:0102 Bison
Bus 006 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.

Bus 006 Device 001: ID 0000:0000
....
And all the other "Bus" numbers (007, 005 to 001) all read the same...

when I type lshw -C network, I get the wireless info I've just given, plus..

physical id: 0
bus info: pci@0000:04:00.0
serial: 00:1c:bf:00:97:e4
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

(Sorry if I forgot something useful)..

I'm certain Ubuntu recognizes my wireless card, because it detects my wireless connection(with good connectivity), and ask me for my passphrtase (I'm using WPA), but it fails to connect. 

It may be a problem with the connection, but I'm using it right now to post this message, so I don't think that's it. 

Any help is appreciated Thanks.

---

### Post by marcusesses on 2008-07-25
and when I say "I'm using the connection to type this message" , I mean on my TOshiba(w/ Windows), not the Ubuntu machinge...

I checked the list of available wireless cards for Ubuntu, and mine is supported "right out of the box" as it says, but I'm still having trouble. 

Just wanted to clarify.

---

### Post by phidia on 2008-07-25
That card is said to be supported OOTB do you have a password protected network and if so is the package wpasupplicant installed? 
You can open synaptic and search for that package name if it is installed the check box will be green.
What's the output of "iwconfig"?

---

### Post by marcusesses on 2008-07-25
> **phidia said:**
> That card is said to be supported OOTB do you have a password protected network and if so is the package wpasupplicant installed? 
You can open synaptic and search for that package name if it is installed the check box will be green.
What's the output of "iwconfig"?

Yes it's a password protected network.

wpasupplicant IS installed (version 0.6.0 +0.5.8.0) (the check box is green).

The output after typing config shos thatlo, etho and wmastre0 all have "no wireless extensions"

wlan0:  IEEE 802.11g ESSID:"" Nickname:""..
        ...and a bunch of other stuff...I don't really want to type it out verbatim, so if you need anything specific from there, let me know...but it DOES have a bunch of stuff written.

---

### Post by sdowney717 on 2008-07-25
you can highlight and copy the information from terminal and post it here
It will make it easier to see what is going on.

---

### Post by marcusesses on 2008-07-26
when i type udo lshw -C network, i get this...

*-network
     description: Ethernet interface
     product: Netlink BCM5787M Gigabit Ethernet PCI Express
     vendor: Broadcom Corporation
     physical id:0
     bus info: pci@0000:02:00.0
     logical name:eth0
     version: 02
     serial: 00:1d:72:10:7a:34
     capacity: 1Gb/s
     width: 64 bits
     clock: 33MHz
     capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000br 1000bt-fd autonegotiation
     configuration: autonegotiation=on broadcast =yes drover=tg3 driverversion=3.86 firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
     description: Wireless interface
     product: PRO/Wireless 3945ABG Network Connection
     vendor: Intel Corporationilities 
     physical id: 0
    bus info: pci@0000:04:00.0
     logical name: wmaster0
     version: 02
serial: 00:1c:bf:00:97:e4
     width: 32 bits
     clock 33 MHz
     capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
     configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

---

### Post by marcusesses on 2008-07-26
laptop:~$ iwconfig

lo     no wireles extensions
eth0   no wireless extensions

wmaster0 no wireless extensions

wlan0    IEEE 802.11g ESSID:"" Nichname:""
         Mode:Managed Frequency:2.462GHz Accesss Point: 00:1E:C7:F8:A7:81
        Bit Rate=1MB/s Tx-Power=27dBm
         Retry min limit:7 RTS thr: off Fragment THr 2346  B
        Power Management: off
        Link Quality=36/100 Signal Level=-87dBm Noise level=-127 dBm
       Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
        Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by marcusesses on 2008-07-26
:~$laptop lsusb

Bus 006 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 5986:0102 Bison
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 003 Device 001: ID 0000:0000

If there is any more information you need, please let me know.

---

### Post by sdowney717 on 2008-07-26
I have a wireless system using wep, 128 bit key.
I could not get wpa working.
I tried and tried, but it never could negotiate the connection.
Is it possible for you to switch your router to use wep?

Usually the way to do this is to disable wireless security first to see if you can connect at all.

So try turning off wpa and turn off wep to the router and see if it connects. Then try turning on wep and see if it works.

---

### Post by sdowney717 on 2008-07-26
what does iwlist scanning give you?
I show two available networks, Gateway and TnfQ2


 iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:10:21:32:01
                    ESSID:"Gateway"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:18:01:EF:0D:57
                    ESSID:"TNFQ2"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by sdowney717 on 2008-07-26
what does iwlist auth show you?
I am using wep

kristin@kristin-desktop:~$ iwlist auth
lo        no authentication information.

eth0      no authentication information.

wlan0     Authentication capabilities :
		WPA
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		disabled
          Current Key management :
          Current Pairwise cipher :
		WEP-104
          Current Pairwise cipher :
		WEP-104
          Current Authentication algorithm :
		open


kristin@kristin-desktop:~$

---

### Post by marcusesses on 2008-07-27
I'm currently on a wired connection (away from my wireless connection), but the wired connection doesn't seem to be working either! (I'm on a desktop)

:~$ iwlist scanning

lo         Interface doesn't support scanning

eth0       Interface doesn't support scanning

wmaster0   Interface doesn't support scanning

wlan0      No scan results


However, my Ubuntu sytem detects the wired system that I'm connected to, and 5 wireless networks at the moment.

UPDATE: I just successfully connected to an unsecure wireless connection...but no luck with the wired connection OR the secure wireless connection

---

### Post by marcusesses on 2008-07-27
:~$ iwlist auth

lo         no authentication information.

eth0       no authentication information.

wmaster0   no authentication information.

wlan0      Authentication capabilities :
                  WPA
                  WPA2
                  CIPHER-TKIP
                  CIPHER-CCMP
            Current Authenitcation algorithm: 
                   open

---

### Post by sdowney717 on 2008-07-27
> 
UPDATE: I just successfully connected to an unsecure wireless connection...but no luck with the wired connection OR the secure wireless connection


Thats good news! So you can connect wirelessly without secure encryption.
Then you should be able to at least get wep working.

Got to match up the key. It was easier for me to do wep on ubuntu than on windows xp

---

### Post by marcusesses on 2008-07-27
But while it says I'm connected, I don't think it is connected (or at least not very well), as I can't access the internet, download anything,etc...

Could I just switch the connection from WEP to WPA on the computer I'm connecting from? How would I then connect using WEP?

---

### Post by sdowney717 on 2008-07-27
what is your DNS setting?
so you cant do anything try to ping this
If you can ping the octet numbers and not the name it is a DNS issue

scott@scott-desktop:~$ ping 68.180.206.184
PING 68.180.206.184 (68.180.206.184) 56(84) bytes of data.
64 bytes from 68.180.206.184: icmp_seq=1 ttl=55 time=94.6 ms
64 bytes from 68.180.206.184: icmp_seq=2 ttl=55 time=94.1 ms
64 bytes from 68.180.206.184: icmp_seq=3 ttl=55 time=91.6 ms
64 bytes from 68.180.206.184: icmp_seq=4 ttl=55 time=94.1 ms

--- 68.180.206.184 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 91.631/93.636/94.665/1.198 ms
scott@scott-desktop:~$ 

scott@scott-desktop:~$ ping yahoo.com
PING yahoo.com (68.180.206.184) 56(84) bytes of data.
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=1 ttl=55 time=89.8 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=2 ttl=55 time=88.7 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=3 ttl=55 time=91.4 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=4 ttl=55 time=92.4 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=5 ttl=55 time=91.4 ms

--- yahoo.com ping statistics ---
6 packets transmitted, 5 received, 16% packet loss, time 5001ms
rtt min/avg/max/mdev = 88.703/90.786/92.458/1.343 ms
scott@scott-desktop:~$

---

### Post by sdowney717 on 2008-07-27
> 
Could I just switch the connection from WEP to WPA on the computer I'm connecting from? How would I then connect using WEP?


your router determines you connection. This would be setup in the router settings. Log into the router using a browser and setup security WPA WEP or none.

The router also sets up you IP address and it should be setup dynamically. So the PC connects to router and requests an IP and the router hands it out. You can set starting IP and range for the network in the router. You should be able to get the wired connection going fairly easily compared to the wireless.

These settings then have to match with your PC connecting to the router.
I think wep uses the passphrase and method like TKIP that you setup in the router. When you are having trouble connecting, get it working without any security layer first, then add in security.

---

### Post by marcusesses on 2008-07-27
The router was set up for WPA...When I try to ping the IP address for the router, it says " connection: network is unreachable" ..so NOT a DNS issue

I tried a wired connection earlier, and that didn't work, I'll try a wired connection again...So it works with the wired conection, when I ping from my computer (with teh same IP address), it reads a whole bunch of data, similar to what you posted. It also pings a website successfully.

I also disabled the WPA key, with no success. The only options my router has is WPA, WPA-PSK (which I've been using) , and IEEE802.1x

---

### Post by anewguy on 2008-07-27
So, just so I know I am starting at the right place, if you click on your network manager icon it shows at least 1 wireless network available by name?

I also have never been able to get WPA of any flavor working,  However, if you search this forum hard enough, you will find some entries which show things you must put in at the command line, put in a file, etc., before they ever get it to work.  

In particular, check out "man iwconfig" from the command line.  Sometimes you have to set your session id, key, etc., via this prior to trying to connect.

---

### Post by sdowney717 on 2008-07-27
[https://launchpad.net/ndisgtk](https://launchpad.net/ndisgtk)

Is this installed as a helper gui for setting up ndiswrapper?
You said you had an inf file and did get ndiswrapper working already?

This is in synaptic package manager

I never could get WPA working for me. What is your router model?

wpa supplicant has to be configured thru a config file
[http://ubuntuforums.org/showthread.php?t=356672](http://ubuntuforums.org/showthread.php?t=356672)
[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

perhaps you need to do something like this
this talks about how to configure WPA in Ubuntu
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=(wpa](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=(wpa))

---

### Post by mikewhatever on 2008-07-27
> **sdowney717 said:**
> [https://launchpad.net/ndisgtk](https://launchpad.net/ndisgtk)

Is this installed as a helper gui for setting up ndiswrapper?
You said you had an inf file and did get ndiswrapper working already?

This is in synaptic package manager

I never could get WPA working for me. What is your router model?

PRO/Wireless 3945ABG card works well WPA and WPA2 included. No ndisrapper is needed.

marcusesses, what's your router model and also, are you using DHCP or static IP?

---

### Post by marcusesses on 2008-07-27
> **sdowney717 said:**
> [https://launchpad.net/ndisgtk](https://launchpad.net/ndisgtk)

Is this installed as a helper gui for setting up ndiswrapper?
You said you had an inf file and did get ndiswrapper working already?


I never could get WPA working for me. What is your router model?

I don't have that wrapper installed. My router model is a D-Link DI-514 2.54 GHz wireless router

> **anewguy said:**
> So, just so I know I am starting at the right place, if you click on your network manager icon it shows at least 1 wireless network available by name

I DID have several wireless networks available. (and wired, when I was connected), but I followed the instructions given [here]("http://ubuntuforums.org/showthread.php?t=318539"), and now my computer doesn't detect any networks at all..when I left click on the network manager. "Enable Networking" is the only option, and it is checked off...I think I may have gotten myself into a bit of a mess...

> **mikewhatever said:**
> PRO/Wireless 3945ABG card works well WPA and WPA2 included. No ndisrapper is needed.

marcusesses, what's your router model and also, are you using DHCP or static IP?
 I believe I'm using DHCP

---

### Post by mikewhatever on 2008-07-27
> I DID have several wireless networks available. (and wired, when I was connected), but I followed the instructions given here, and now my computer doesn't detect any networks at all..when I left click on the network manager. "Enable Networking" is the only option, and it is checked off...I think I may have gotten myself into a bit of a mess...

That's because you are using manual config. Go to System>Prefs>Network and enable roaming mode for wireless, then the network manager will work again.

---

### Post by marcusesses on 2008-07-27
Roaming mode is enabled...and still no wireless networks to be seen..I rebooted the computer just to be sure...(one thing I like about Linux/Ubuntu...it takes about 60 seconds to reboot)

---

### Post by mikewhatever on 2008-07-27
It may be helpful to look at the related log messages. Post the output of 
**dmesg | grep wlan0**

Which section of the guide have you followed? You may need to manually re-edit interfaces back to what it was, namely
> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp 

There is no need to reboot after doing this, just run
> sudo /etc/init.d/networking restart

---

### Post by marcusesses on 2008-07-27
When I type that, it says  

"bash: syntax error near inexpected token 'newline'"

I tried it a number of ways (with spaces, without, etc...), but when I remove the brackets, I get a whole bunch of stuff...

Also , I followed this part

*****************************Sample configuration WPA2 & DHCP, ESSID broadcast enabled***************
Quote:
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key> [IMPORTANT: See "WPA-PSK key generation"]
*****************************

---

### Post by mikewhatever on 2008-07-27
> **marcusesses said:**
> When I type that, it says  

"bash: syntax error near inexpected token 'newline'"

I tried it a number of ways (with spaces, without, etc...), but when I remove the brackets, I get a whole bunch of stuff...

Don't type, just copy/paste, it's a little hard to get them right in the beginning, but the commands are ok.

Have you noticed that you've followed WPA2 guide?

---

### Post by marcusesses on 2008-07-27
I hadn't noticed that...I switched it to the WPA1 guide, rebooted with no luck...though I probably messed up. 

Here's the output...gross

:~$  dmesg | grep wlan0 

[   30.835385] wlan0: Initial auth_alg=0
[   30.835390] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   31.011367] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   31.013154] wlan0: RX authentication from 00:11:95:1f:d4:43 (alg=0 transaction=2 status=0)
[   31.013157] wlan0: authenticated
[   31.013160] wlan0: associate with AP 00:11:95:1f:d4:43
[   31.014996] wlan0: invalid aid value 1; bits 15:14 not set
[   31.015000] wlan0: RX AssocResp from 00:11:95:1f:d4:43 (capab=0x11 status=0 aid=1)
[   31.015002] wlan0: associated
[   35.965538] wlan0: disassociate(reason=3)
[   36.862243] wlan0: Initial auth_alg=0
[   36.862252] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   36.862887] wlan0: Initial auth_alg=0
[   36.862895] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   36.864343] wlan0: RX authentication from 00:11:95:1f:d4:43 (alg=0 transaction=2 status=0)
[   36.864350] wlan0: authenticated
[   36.864353] wlan0: associate with AP 00:11:95:1f:d4:43
[   36.866363] wlan0: invalid aid value 1; bits 15:14 not set
[   36.866370] wlan0: RX ReassocResp from 00:11:95:1f:d4:43 (capab=0x11 status=0 aid=1)
[   36.866374] wlan0: associated
[   38.236238] wlan0: disassociate(reason=3)
[   38.260108] wlan0: Initial auth_alg=0
[   38.260116] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   38.260784] wlan0: Initial auth_alg=0
[   38.260791] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   38.261500] wlan0: RX authentication from 00:11:95:1f:d4:43 (alg=0 transaction=2 status=0)
[   38.261507] wlan0: authenticated
[   38.261511] wlan0: associate with AP 00:11:95:1f:d4:43
[   38.263033] wlan0: invalid aid value 1; bits 15:14 not set
[   38.263042] wlan0: RX ReassocResp from 00:11:95:1f:d4:43 (capab=0x11 status=0 aid=1)
[   38.263047] wlan0: associated
[   39.870844] wlan0: disassociate(reason=3)
[   40.581845] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.015289] wlan0: Initial auth_alg=0
[   41.015298] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   41.015949] wlan0: Initial auth_alg=0
[   41.015955] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   41.018779] wlan0: RX authentication from 00:11:95:1f:d4:43 (alg=0 transaction=2 status=0)
[   41.018787] wlan0: authenticated
[   41.018791] wlan0: associate with AP 00:11:95:1f:d4:43
[   41.020697] wlan0: authentication frame received from 00:11:95:1f:d4:43, but not in authenticate state - ignored
[   41.023243] wlan0: invalid aid value 1; bits 15:14 not set
[   41.023251] wlan0: RX ReassocResp from 00:11:95:1f:d4:43 (capab=0x11 status=0 aid=1)
[   41.023254] wlan0: associated
[   41.026821] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   47.375164] wlan0: disassociate(reason=3)
[   47.674177] wlan0: no IPv6 routers present
[   48.991641] wlan0: Initial auth_alg=0
[   48.991650] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   48.993855] wlan0: Initial auth_alg=0
[   48.993864] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   48.995445] wlan0: RX authentication from 00:11:95:1f:d4:43 (alg=0 transaction=2 status=0)
[   48.995452] wlan0: authenticated
[   48.995456] wlan0: associate with AP 00:11:95:1f:d4:43
[   48.997321] wlan0: authentication frame received from 00:11:95:1f:d4:43, but not in authenticate state - ignored
[   49.001267] wlan0: invalid aid value 1; bits 15:14 not set
[   49.001275] wlan0: RX ReassocResp from 00:11:95:1f:d4:43 (capab=0x11 status=0 aid=1)
[   49.001279] wlan0: associated
[   50.646872] wlan0: disassociate(reason=3)
[   50.699336] wlan0: Initial auth_alg=0
[   50.699344] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   50.700484] wlan0: Initial auth_alg=0
[   50.700491] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   50.701670] wlan0: RX authentication from 00:11:95:1f:d4:43 (alg=0 transaction=2 status=0)
[   50.701678] wlan0: authenticated
[   50.701681] wlan0: associate with AP 00:11:95:1f:d4:43
[   50.702960] wlan0: authentication frame received from 00:11:95:1f:d4:43, but not in authenticate state - ignored
[   50.704481] wlan0: invalid aid value 1; bits 15:14 not set
[   50.704492] wlan0: RX ReassocResp from 00:11:95:1f:d4:43 (capab=0x11 status=0 aid=1)
[   50.704496] wlan0: associated
[   52.239564] wlan0: disassociate(reason=3)
[   53.186196] wlan0: Initial auth_alg=0
[   53.186205] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   53.186951] wlan0: Initial auth_alg=0
[   53.186957] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   53.191748] wlan0: RX authentication from 00:11:95:1f:d4:43 (alg=0 transaction=2 status=0)
[   53.191756] wlan0: authenticated
[   53.191761] wlan0: associate with AP 00:11:95:1f:d4:43
[   53.193391] wlan0: authentication frame received from 00:11:95:1f:d4:43, but not in authenticate state - ignored
[   53.194766] wlan0: invalid aid value 1; bits 15:14 not set
[   53.194773] wlan0: RX ReassocResp from 00:11:95:1f:d4:43 (capab=0x11 status=0 aid=1)
[   53.194777] wlan0: associated
[   56.427334] wlan0: disassociate(reason=3)
[   57.176332] wlan0: Initial auth_alg=0
[   57.176339] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   57.177855] wlan0: Initial auth_alg=0
[   57.177862] wlan0: authenticate with AP 00:11:95:1f:d4:43
[   57.184292] wlan0: RX authentication from 00:11:95:1f:d4:43 (alg=0 transaction=2 status=0)
[   57.184302] wlan0: authenticated
[   57.184305] wlan0: associate with AP 00:11:95:1f:d4:43
[   57.186340] wlan0: invalid aid value 1; bits 15:14 not set
[   57.186348] wlan0: RX ReassocResp from 00:11:95:1f:d4:43 (capab=0x11 status=0 aid=1)
[   57.186352] wlan0: associated
[   60.223011] wlan0: disassociate(reason=3)
[   60.698182] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   96.604183] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  106.959581] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by mikewhatever on 2008-07-28
I've tried googling <wlan0: disassociate(reason=3)>, and while there was no clear solution, one suggested checking WPA passhare to have only alphanumeric characters, no spaces etc.

---

### Post by anewguy on 2008-07-28
There is a bug thread sort of along these lines:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217809]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217809")

It has a lot of other messages besides the did not associate reason 3 message.  The particular filer ended up noting (as mentioned in the above post by mikewhatever) that they had quotes and a space in the passphrase.  Removing the quotes and any spaces made it work for them.

Also, you are not using ndiswrapper and the Windows XP drivers at this time (you said you didn't have the wrapper installed), correct? There have been a few bug reports filed with sort of similar problems, mostly since a recent update (early July).  Perhaps you should try ndiswrapper using the Windows XP drivers and blacklisting iwl3945 (this module has been mentioned in some of the bug reports).  These all seem to be associated with realtek drivers - I don't know if this is what is being used or not.  Please post back the output of the following:

lsmod | grep rt

Thanks, and we'll keep looking. :)

---

### Post by marcusesses on 2008-07-28
That's correct, I don't have ndiswrapper installed. The output of lsmod |grep rt gives:

parport_pc            3620   0
parport               37832  3 ppdev,parport_pc,lp
agpgart               34760  3 drm,intel_agp
iTCO_vendor_support   4868   1 iTCO_wdt

UPDATE: So I re-copied the hex passkey to /etc/network/interfaces (along with the other WPA1 criteria), and I enabled roaming mode in system->administration->network...and it detected wireless networks. and now it says that I'm connected to my wireless network (with 90% connectivity, apparently), but when I type in the passphrase, it thinks for about 20 seconds, and then asks me again, as if I entered the wrong passphrase, or it just can't connect. I AM entering the correct passphrase though.

So basically, it's back to where it started, only now it claims to be working...

---

### Post by anewguy on 2008-07-28
Could you copy and paste the output of "lspci" back here?

I was checking the Acer support site for the driver for the wireless you mentioned, and it is a Vista driver.  Unless something has changed - which someone out there please correct if I'm wrong now - ndiswrapper doesn't like Windows Vista drivers.  

Did you install the 32-bit or 64-bit version of Ubuntu?  

I'm not sure on ndiswrapper support in the 64-bit version - I assume it still works.

Additionally, as mentioned by mikewhatever, the best information I can find indeed says that the driver is included in Ubuntu now.  This would also explain why you at one time had wireless.

If at all possible, this is about the best I can think of at this time:

- disable all encryption, etc, at the router
- back out all of the changes you made - especially those having to do with wpa.  Any files that were edited may have the original version available if you check the filename.extension~ (that's a tilde "~" on the end).
- see if your wireless is back and if you can connect

If that doesn't work, your best bet at this point may be to reinstall so you are at a clean restart point, then post back for help on the wpa stuff.  I'm sure you've probably seen that wpa seems to be a bit of a hit or miss for most people.

Sorry I can not be of more help to you!

---

### Post by marcusesses on 2008-07-28
> **anewguy said:**
> Could you copy and paste the output of "lspci" back here?

I was checking the Acer support site for the driver for the wireless you mentioned, and it is a Vista driver.  Unless something has changed - which someone out there please correct if I'm wrong now - ndiswrapper doesn't like Windows Vista drivers.  

Did you install the 32-bit or 64-bit version of Ubuntu?  

I'm not sure on ndiswrapper support in the 64-bit version - I assume it still works.

Additionally, as mentioned by mikewhatever, the best information I can find indeed says that the driver is included in Ubuntu now.  This would also explain why you at one time had wireless.

If at all possible, this is about the best I can think of at this time:

- disable all encryption, etc, at the router
- back out all of the changes you made - especially those having to do with wpa.  Any files that were edited may have the original version available if you check the filename.extension~ (that's a tilde "~" on the end).
- see if your wireless is back and if you can connect

If that doesn't work, your best bet at this point may be to reinstall so you are at a clean restart point, then post back for help on the wpa stuff.  I'm sure you've probably seen that wpa seems to be a bit of a hit or miss for most people.

Sorry I can not be of more help to you!


:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


Also, I installed the 32 bit version of Ubuntu...oh, and see the update I put in the above post...the wireless tells me it's working now (though it's not)

---

### Post by anewguy on 2008-07-28
I found some more posts on your wireless:

[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/")

This gets the backport version which apparently works.

Also:

Did you install WICD to use in place of network manager?  There are posts that indicate that network manager has a goofy patch of some sort to try to work around a problem with this device but it doesn't work right.  People say to remove network manager and install WICD.

IF you already have WICD installed, do the following:

ls /opt/wicd/data/wired-settings.conf

if it shows the file, delete it:

sudo rm /opt/wicd/data/wired-settings.conf

then RESTART your computer.

This supposedly works when you can't use wired or wireless anymore.





Also, could you post back the results of:

dmesg | grep 3945

so we can see if there are other errors in the log for the device driver?


EDIT:  also found this for windows xp drivers for your adaptor if you reload and want to try ndiswrapper:

[http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=2259&DwnldID=13000&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=2259&DwnldID=13000&lang=eng")


A lot of the problems people seem to be noting have to do with switching from the iwl driver which used ndiswrapper to the new ipw driver not requiring ndiswrapper.  I would still need to do a lot more digging through the net to get through this.



Thanks,
Dave :)

---

### Post by marcusesses on 2008-07-29
I installed the backport version, but that didn't help things...

I haven't installed WICD at all, still using network manager

:~$ dmesg | grep 3945

[   27.373426] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   27.373430] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   27.373609] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   28.725907] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   28.727141] wmaster0: Selected rate control algorithm 'iwl-3945-rs'


So I would reckon that I currently have the iwl driver then...I'm going to keep exploring, see if I can't put an end to this madness...

Oh, and a lot of the problems people seem to be having are to do with the lack of any networks..but my computer sees all the networks just fine, it just can't connect to any of them.But with the Vista OS that came with the comp, wireless worked fine...

---

### Post by imdano on 2008-07-29
> **anewguy said:**
> IF you already have WICD installed, do the following:

ls /opt/wicd/data/wired-settings.conf

if it shows the file, delete it:

sudo rm /opt/wicd/data/wired-settings.conf

then RESTART your computer.

This supposedly works when you can't use wired or wireless anymoreJust fyi, deleting that is only sometimes useful if the wicd tray/gui fails to start after working previously.  Because of a bug in 1.4.2 its possible for the file to get in a state that keeps it from being parsed correctly, which makes the daemon crash (its fixed in the newest version).  Also, after you delete the file, all you have to do is run ```
sudo /etc/init.d/wicd start
```Then the tray/gui should run normally.  No need to reboot.

---

### Post by anewguy on 2008-07-30
From what you said in your last post, I assume the wireless itself is working.  If you click on the network manager icon and see wireless networks then it is working.  Now on to why you can't connect.  Are any of the networks you see completely open at the router - no mac filtering, no wep, no wpa, etc?  If so, can you connect to it?  For your own network router, try temporarily disabling mac filtering and turn off encryption (wep and wpa) so the wireless network is temporarily wide open.  Can you connect to it?

If you are connecting to networks with wep, be aware that the default in the pull-down box when you connect is 128-bits - I needed 64 bits on my old router and it took forever for me to find that little thing.  The same goes for WPA, and it can be a challenge to get working.

So, as I mentioned in a previous post - I would back out all of the changes you made.  Check the how-to you followed to be sure you reversed everything from there.  When you are back to a clean point, disable mac filtering and any encryption on your local router, then try connecting again.

If all else fails, reinstall Ubuntu but don't do any of the wpa things - just leave it as it installed (plus the wireless driver if needed).  You want to be able to see wireless networks in network manager.  Then do the no mac filtering no encryption thing at your local router so it is a completely open network and try connecting.   Add 1 thing at a time back in, and if you add WPA then post back here so we can try to walk you through it.


imdano:  Thanks for the info!  All I ever knew was to delete the file and reboot the computer.  Your way will save time!

---

### Post by apienk01 on 2008-07-30
Hi Marcusesses,

be sure to give [COLOR="Magenta"]wicd[/COLOR] a try. I've had many problems with Network Manager, and since I use wicd - no problems at all (thanks [COLOR="SeaGreen"]imdano[/COLOR]). :rolleyes:

Before you install wicd, you have to add a repository for it in Synaptic. The instructions are [here]("http://wicd.sourceforge.net/download.php").

Then click update, and you should be able to find wicd listed in Synaptic. Note that wicd is an alternative to Network Manager, so it uninstalls network-manager and network-manager-gnome packages.

Good luck

---

### Post by marcusesses on 2008-07-30
So I installed WICD, with no luck at all...at first, it couldn't see my wireless network, and after hitting "refresh" about 30 times I realized that I had the connection at my router set to "disable" (D'oh!)...so it sees all the networks, but, as before, it fails to connect to any of them (even the open, albeit weak ones). 

On that note, I'm just going to purge the current Ubuntu, re-install and try again...

Any recommendations as to how I should start...again? anewguy, you mentioned that I should make my wireless open, then give it a go..I'm not entirely sure how to do that (Delete the mac address?). After I do that, any suggestions? If it makes anything easier, I can just change my security to WEP, since WPA seems to cause headaches (I tried connecting with WEP, to no avail).

I'd just like to thank everyone who's helping me here...I'm sure this problem has been dealt with before ( and I don't understand for the life of me why I'm having so much difficulty), but like I said, thanks a ton for all the advice...now here's hoping it works (*knock on wood*)

---

### Post by anewguy on 2008-07-30
You will need to log in to your router's management screens, then disable MAC filtering, be sure neither WEP or WPA is selected (I think it will either be "none" or "open" but it's been a while).  Also be sure the ssid is being broadcast - some routers allow you to hide it but I have found that in my case at least it made it darn near impossible for me to connect.  Once you've done that, save the changes and let your router reset.  At that point anyone should be able to connect to your wireless router without any passwords, passphrases, etc..

Having done that, you really don't need to do anything other than make sure the driver is loaded (do the dmesg | grep 3945 to be sure it lists the driver as before).  Then just try to connect to your wireless router.  You should not be prompted for any type of password or anything - it should just connect.  If you can connect, the problem lies with either MAC filtering (which would seem not possible considering you can connect with Windows), WEP or WPA handling.  Since you've done a lot of different things already to try to get WPA working, this is when I would just wipe out Ubuntu and reinstall it (there's a possibility that given the correct package names you could actually remove networking and reinstall networking, but I think it would be easier just to start from scratch with Ubuntu IF you either backup what you need or don't have anything you need to save).

Once you have done that, and have left your wireless router "open", you should be able to just connect (given that the driver still shows). From there, if you want to add any protections, I would start with MAC filtering on the router (you'll need the MAC address from each device that you want to connect to the wireless network).  Once you get that working you could try WEP and see if it will work for you.  Remember what I mentioned in an earlier post to be sure to match the number of bits, the type (ascii or hex) and the case (remember everything in Linux is case sensitive - so Password doesn't match password) on the network connection screen.  If you want to try WPA, I would post back again with perhaps a new thread, and mention everything you tried before, the resulting failures, etc., so that people won't try to direct you to things that didn't work.  You may also want to research via a Yahoo! or Google search for ubuntu wpa.

If you set the router wide open and it still doesn't work, post back letting us know so we will know you'll be taking some time to reload Ubuntu.  Then post back with the results after the reinstall.

Thanks!
Dave :)

---

### Post by marcusesses on 2008-07-31
So last night(before I tried the open network), I just said the hell with it and re-installed Ubuntu. I just tried to connect with an my wireless network(open), and says I'm connected (As before), but I can't install updates, access the internet, etc...

So it doesn't connect automatically, but claims to connect when I do some fixing (WPA protocols, etc.), but I don't receive any data....I'm flummoxed.

---

### Post by mikewhatever on 2008-08-01
I find it extremely odd that the same hardware should malfunction on one machine, and not on another. I also have the Intel PRO/Wireless 3945ABG card which has been working with WPA/WPA2 since I started using Ubuntu Edgy in 2006. The only glitch that appeared with Hardy is that I have to restart the network to get connected with a static IP (wasn't the case with Gutsy).

As the last resort, you might try Gutsy instead of Hardy. There is no need to reinstall right away. You can test it trying to connect while running from CD.

---

### Post by velsd on 2010-11-02
indeed, I had the same problem after updating to SUSE 11.3, the symptom being a 

wlan0: invalid aid value 1; bits 15:14 not set

message in /var/log/messages

changing the password in the wireless router to one without dots (.) made it work!

---

