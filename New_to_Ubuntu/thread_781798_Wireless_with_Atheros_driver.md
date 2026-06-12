---
title: "Wireless with Atheros driver"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by hydrodo on 2008-05-04
Hi all,

I can't seem to get the wireless running on my Lenovo Thinkpad T61. I'm a newb when it comes to Linux, so please be patient with my ignorance...

I can connect fine under Windows (I have a dual-boot set up with XP), so I think it is a driver issue. I have an Atheros card, and from reading assorted threads on the forum, those tend to spell trouble.  Specifically, lspci has the line
```
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01) 
```

System -> Administration -> Restricted Drivers Manager lists the Atheros Hardware Access Layer (HAL) driver as enabled and in use. 

iwconfig returns the following:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"MIT"  Nickname:""
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:20:A6:51:CC:29  
          Bit Rate:1 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1 
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-39 dBm  Noise level=-93 dBm
          Rx invalid nwid:113776  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```

When I run iwconfig ath0 ESSID any, I get
```
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; Operation not permitted.
```

Somewhat strangely (but perhaps that's unrelated?) when I re-run the same command with sudo in front of it, there is no result.

Does anyone know what the problem actually is or what I should do to fix it? The connection listed under ath1 makes me wonder how 'deep' the problem ultimately is, because it looks like Ubuntu is recognizing the card. Thanks for helping me out! Troubleshooting by myself hasn't gotten me very far, and I'm getting rather discouraged by how quickly time passes without results while I'm doing that.

---

### Post by jimbob on 2008-05-04
I'll give you a bump to keep things going here with a couple of questions although I probably won't be much help.  Why are you working at the terminal level and not using the Network Manager GUI?  My Toshiba laptop with Atheros chip worked "out of the box" with Ubuntu a couple of releases ago although I had to switch to Wicd at that time to use WPA2 security.
What does ifconfig -a show? Is this SSID secured or unsecured?

---

### Post by forrestcupp on 2008-05-04
It should be working.  Actually, Atheros chipsets are some of the easiest to get working.

Do you have an icon in your notification area for wireless?  It looks like wireless signal strength bars.  If not, right click on the panel and choose 'Add to panel'.  Then choose to add the 'Network Monitor'.  It should show your connection.  You may have to go through that to choose the correct connection and set up your WEP password.

---

### Post by hydrodo on 2008-05-04
Jimbob and forrestcup,

The SSID (my college's) is unsecured. 

I started working with the terminal because the various network management GUI screens didn't bring me much luck in getting a connection. The network manager shows two LCD screens. Upon right-clicking, I get the options Wired Network (greyed out, FWIW) and Manual Configuration. The latter brings me to the Network Settings screen, where wireless connection is checked, and the ESSID is already listed as MIT (Address: dhcp). So it seems at a first glance with my newb eyes that I should be connected...but I'm not. I seem to recall having managed to get the network manager to show a  list of available networks before, but even when one (with high signal strength) was selected, I could not actually connect to the internet. 

Lastly, iwconfig gives me the following:
ath0      Link encap:Ethernet  HWaddr 00:1F:3A:0F:CC:71 
          inet6 addr: fe80::21f:3aff:fe0f:cc71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:1F:3A:0F:CC:71 
          inet addr:169.254.6.38  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:1C:25:74:83:A0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x1840 Memory:fe000000-fe020000

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3312 (3.2 KB)  TX bytes:3312 (3.2 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-3A-0F-CC-71-00-00-00-00-00-00-00-00-00-00 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16530 errors:0 dropped:0 overruns:0 frame:18038
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:1368681 (1.3 MB)  TX bytes:2087 (2.0 KB)
          Interrupt:21 

Hopefully that is helpful...thanks again!

---

### Post by jimbob on 2008-05-05
From a terminal type ***[COLOR="RoyalBlue"]sudo dhclient ath0[/COLOR]*** and post the output.

---

### Post by hydrodo on 2008-05-05
sudo dhclient ath0 gives the following:

Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1f:3a:0f:cc:71
Sending on   LPF/ath0/00:1f:3a:0f:cc:71
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Nucleus on 2008-05-05
Hello
I have exactly same problem with my MSI VR601 and lookinf forward the solution.
lspci output is :
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I have applied this tutorial:
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

Now, it recognized wifi card but does not allow ethernet traffic on it.

My dhclient is exactly same with hydrodo's

Thanks

---

### Post by jimbob on 2008-05-05
It appears to me that everything should work at this point, at least for hydrodo.  I am not familiar with the card that nucleus is using.

Do you have any other access points that you could try such as dorm areas, public libraries, Starbucks, etc?  Does your Network Manager GUI show any other access points?  Make sure you have roaming mode disabled in network manager also.

The only other thing I would try is to delete Network Manager (***[COLOR="RoyalBlue"]sudo apt-get remove --purge network-manager[/COLOR]***) and install Wicd which works great for me.  Get it here:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by jimbob on 2008-05-07
Just finished installing Hardy from the alternate CD on my Toshiba laptop with Atheros AR5212 wireless chip and it worked "out of the box" for me and this is with Ubuntu's Network Manager.  I didn't have to do anything special.

The only things in my /etc/network/interfaces file are:

auto  lo
iface lo inet loopback

auto eth0

---

### Post by hydrodo on 2008-05-07
Sorry for taking my time to get back to you; it's been a crazy week so far. Thanks for all your help, Jimbob!

I tried to install wicd, but doing so through the Synaptic Package Manager is rather difficult without an internet connection. Is there a way to get the files outside of the OS and install from the command line?

I am not sure if wicd will be necessary anymore. I had turned off roaming mode as I was trying to fix the issue by myself before. Enabling it again immediately resulted in Network Manager showing me as being connected to the wireless network here, with great signal. Yet, when I try to actually do anything that requires a connection (surf the web, download wicd), I still can't connect...

---

### Post by phidia on 2008-05-07
Perhaps the 5212 chipset is an easy one to get recognized and working.
However it is incorrect to say that Atheros is the easiest to set up-some atheros cards are a real pain. I have the AR5007EG and while it can be made to work (there are several guides in the forums here) it is by no mean easy nor does it "work out of the box".

---

### Post by jimbob on 2008-05-07
If you are truly connected, ***[COLOR="Blue"]ifconfig ath0[/COLOR]*** from the terminal should show an IP address. Does it?

---

