---
title: "How to: Wifi-Radar with WPA (Inspiron 6400/E1505 w/ Broadcom 1390)"
date: 2007-06-19
forum: Outdated Tutorials &amp; Tips
---

### Post by walkerk on 2007-06-19
I set up wifi-radar today to work with WPA because Network Manager has been acting flakey. I did this on Feisty Fawn but it should work with Edgy Eft as well. This will work with other wireless NICs as well. See the list below for a list of drivers.

Firstly, if you do not have connection you should check out **paperdiesel's** thread to see how > [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

Once you have a working connection complete the following..
```
sudo apt-get wifi-radar wpasupplicant
```

Create the wpa_supplicant.conf file that wifi-radar will be looking for..
```
sudo gedit /etc/wpa_supplicant/wpa_supplicant.conf
```

Enter the following and save/exit:
```
# path to UNIX socket control interface
ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="your_ssid"
	psk="your_secret_paraphrase"
	priority=1
} 
```

Once you've done this open wifi-radar..
```
sudo wifi-radar
```

> Select your wireless network from the list. (If you don't see any networks see below..)
> Press Connect at which time it will ask you to set up a profile. Click Yes.

Enter the following:
```
> Network Name: Your SSID (will be there by default)
```

Click the Arrow next to_ WiFi Options_..
```
> Mode: auto
> Channel: auto
> Key: 
> Security: open (as I understand it WPA/WPA2 require Open authentication.. could be wrong)
```

Next, click the Arrow next to _No WPA_ then enter:
```
wext
```

Once this is done you should be able to connect to your WPA using TKIP. For additional encryption standards you can read the wpa_supplicant README file which should be here: /usr/share/doc/wpasupplicant/examples/README.wpa_supplicant.conf.gz

Also, to run wifi-radar at boot up just add it to System > Preferences > Sessions.
```
sudo wifi-radar -d
```

Hope this helps. Good luck!


*Alternate Drivers to use WPA.
```
**hostap**
(default) Host AP driver (Intersil Prism2/2.5/3). (this can also be used with Linuxant DriverLoader). 
**hermes**
Agere Systems Inc. driver (Hermes-I/Hermes-II). 
**madwifi**
MADWIFI 802.11 support (Atheros, etc.). 
**atmel**
ATMEL AT76C5XXx (USB, PCMCIA). 
**wext**
Linux wireless extensions (generic). 
**ndiswrapper**
Linux ndiswrapper. 
**broadcom**
Broadcom wl.o driver. 
**ipw**
Intel ipw2100/2200 driver. 
**wired**
wpa_supplicant wired Ethernet driver 
**bsd**
BSD 802.11 support (Atheros, etc.). 
**ndis**
Windows NDIS driver.
```

Ralink and Zydas NICs need to be brought up after each boot so you need to need to alter the Wifi-Radar config file  
```
sudo gedit /etc/wifi-radar.conf
```
as such:
```
ifup_required = True
```
By default this would be set to False..


[COLOR="Gray"]* If you didn't see any SSIDs listed you might need to change the interface that wifi-radar is scanning.

First close wifi-radar.

Next check what your wireless interface is named. If nothing is listed ensure you followed paperdiesel's thread...
```
iwlist scanning
```

Next ensure wifi-radar is scanning on the right interface...
```
sudo gedit /etc/wifi-radar.conf
```

Ensure that under [DEFAULT] the interface is set correctly to what you saw with iwlist scanning.

In my case it is set to:
interface = eth1

Once you've set it correctly save & exit. If your interface was in fact set incorrectly you should see SSIDs listed once you've re-opened wifi-radar...[/COLOR]


If this didn't work for you or you don't care to use it you can remove wifi-radar. I would leave wpasupplicant installed for use with another wireless tool such as Network Manager.
```
sudo apt-get remove wifi-radar
```

---

