---
title: "HOW TO: Network Manager and New Edgy Install (supports WPA)"
date: 2007-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by featherking on 2007-01-18
This guide was written to help those who cant quite get Network Manager up and running for one reason or another.

[COLOR="RoyalBlue"](NOTE: This is only tested in gnome but in theory it should work the same in KDE but substitute the package 'network-manager-gnome' for 'knetworkmanger')

(NOTE2: Network Manager doesnt support Static IP's at this time, you will have to either use DHCP or not use NM until static ip's are supported. This includes your ethernet configuration as well..)[/COLOR]

My first advice is to check if your wireless card is actually supported by Network Manager by looking [[COLOR="DarkOrange"][COLOR="Red"]here[/COLOR][/COLOR]]("http://live.gnome.org/NetworkManagerHardware").

Once you have figured out if your card is supported, next we need to install the packages required:

```
sudo apt-get install network-manager-gnome network-manager wpasupplicant
```

(wpasupplicant is only required if you are planning on using WPA encryption)

The easiest way to get NM to start controlling your network interfaces (plural because it will also control your wired connection) is to open up (in gnome, not sure on kde) System > Admin > Networking (the default networking tool) open the properties for all the devices there, whether wired or wireless and in the properties dialog box clear the box that says 'enable this connection'

This should change the output of your /etc/network/interfaces file to read:
```

auto lo
iface lo inet loopback
```

(In theory KDE users could just comment out all the lines in /etc/network/interfaces except for those listed above)

You may need to exit NetworkManager and restart your networking for these changes to take effect by running

```
sudo killall NetworkManager
```

then
```

sudo /etc/init.d/networking restart
```

To bring Network manger back type
```

sudo NetworkManager
```

Now make sure (by right clicking the NM icon) that wireless is enabled, if so, simply left-click the icon to select a nearby network or specify by selecting 'connect to other wireless network' and fill out the information required (encryption type, SSID, TKIP key, etc)

*EDIT* According to snowboard975 and this [[COLOR="Red"]post[/COLOR]]("http://www.ubuntuforums.org/showthread.php?p=2043859#post2043859") an error can occur with the icons preventing NetworkManager from loading display the error:
```
The NetworkManager applet could not find some required resources. It cannot continue.
```

this is fixed by running:
```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

Everything should work now.. once you get it going it is pretty reliable, at least for me. Good luck!

---

### Post by m.musashi on 2007-01-20
Nice how to. Thanks for doing this. I'm sure it will be useful to a lot of people wanting to use this.

I'm still trying to figure out how to add the icon back if it's deleted. Not much luck yet.

EDIT I found it. It seems I managed to delete the notification area. For anyone else that has this problem, right click the panel and choose add to panel. near the bottom of the window that opens is an option for "notification area". Add it and you will be set for not only NM but other notifications.

---

### Post by snowboard975 on 2007-01-21
According to another thread ( [http://www.ubuntuforums.org/showthread.php?p=2043859#post2043859](http://www.ubuntuforums.org/showthread.php?p=2043859#post2043859) ) 
The following code could solve a problem where Network Manager won't start.

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/ 
```

I think the addition of this material to the HOW TO will be beneficial for many users who are suffering from the problem as I was.

---

### Post by featherking on 2007-02-20
@snowboard975
I have updated the how to with your post just in case someone has that error

I posted this how to a while ago and never saw it actually get posted! Lo and behold, here it is! i apologize to anyone for not being around to answer questions!

*SUBSCRIBED*

---

### Post by Falkon MX-5 on 2007-02-22
Thanks!  This is EXACTLY what I needed.  Before I was using my own setup with wpa_supplicant, and it didn't like to play well with hidden SSIDs.  Network-Manager works just fine.  Your how-to worked with XFCE btw.

---

### Post by featherking on 2007-02-22
@Falkon
Glad you got it working! I always thought there were a ton of NetworkManager how to's, perhaps i was wrong.. At any rate congratulations!

---

### Post by Rhesuso on 2007-03-05
Thanks so much for this! It just worked - I've been wrestling with my wireless connection on and off for months and going about it in completely the wrong way. And it turns out the solution was really simple.

Thank you, Thank you, Thank you!

---

### Post by featherking on 2007-03-05
@Rhesuso
Yeah its really not too bad to setup, im not sure why they cant make it more automated. like having it edit the required files on install. But hey, i dont write programs i just use them! again, congrats!

---

### Post by Viper Daimao on 2007-03-05
I had this working perfectly, but am now having some problems. I'm not sure what caused it, the last changes I made were uninstalling beryl. I upgraded to edgy, but I think it was working after that. I am on a dell inspiron 6000 with intel wireless. I have a linksys wireless router using WPA2, AES+TKIP.

I unplugged my cable modem and put the computer on standby and went to work. I come home start up the computer, and it doesn't connect of course. So I plug the modem back in, but can't get it to connect. The little balls never turn green, stuck on waiting for the shared key. I restart the computer, Restart the router and modem. Still wasn't connecting. I could connect to other networks alright, so I turned off the encryption on my wireless signal, and could connect fine. Then did WEP and it worked, then WPA, then WPA2 and both worked. 

So now it works, but it doesn't work automatically. When I start up and sometimes when I come out of standby, it doesn't connect to my network. To get it to connect I click on "connect to other wireless networks" and enter in my networks information again. 

Also, dunno if this is related or not, but after upgrading from dapper to edgy, I started having to enter my passkey twice. I think it expired at some point too, and I entered in the same password.

Any help would be appreciated.

---

### Post by featherking on 2007-03-06
@Viper
Ive never been able to get anything on my computer to work after coming out of standby. Having said that, i have heard about the 'entering your password twice' problem. It seems there is a package that sticks out in my mind called like pam-keyring or something. It is something someone created so you dont have to enter your password at all.

Perhaps if you could install this package your NetworkManager would auto-connect, because you wouldnt have to enter your password at all? [Here]("http://www.ubuntuforums.org/showthread.php?t=192281&highlight=pam-keyring") is a How To that I found searching the forums. Check it out and see if that solves your problem

---

### Post by sch-chris on 2007-03-07
I am new to this and followed the below link to get WPA-PSK going on my Dell 600m with IPW2200 series
[http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)

However, at work we use WEP.  Is network manager like it's counterpart in XP/OSX where I can specify separate locations and have a different protocol for each?  I would like to be able to continue to run WPA at home while still being able to connect to the WLAN at work w/ WEP.  Thanks a lot.

-Chris

---

### Post by featherking on 2007-03-07
@sch-chris
I dont think you should have any problems. NetworkManager should store your WEP password in the gnome-keyring and your WPA password is stored there too each with its own entry. This makes your other howto redundant because with networkmanager you dont have to edit anything with wpa_supplicant. Having said that, I dont know exactly what it will do because I only use WPA or no encryption. I seriously doubt you will have problems, NetworkManager is built to easily switch between networks WPA, WEP, Wired and more

*NOTE* you cant  have a static IP at all with NetworkManager. In the howto you linked to, it looks like he had a static IP setup. Everything has to be dynamically assigned with NetworkManger

---

### Post by sch-chris on 2007-03-07
featherking,

thanks for the quick reply.  will I need to "undo" anything that I already did with the previous "how-to" that I posted a link to in my original post?

the IPs for all networks that I connect to are assigned dynamically, so that is why I am looking to NM.  Thanks again.

---

### Post by featherking on 2007-03-08
@sch-chris
no you shouldnt have to change anything. In fact i even sometimes use my old wpa_supplicant setup as a backup if something goes wrong. NetworkManager stores you passwords and SSID's totally seperate from your wpa_supplicant.conf file. But yeah, if everything you use is dynamic NetworkManager is probably exactly what you need

---

### Post by trd79 on 2007-03-08
Hi, I have just installed edgy on a brand new Toshiba A120 and am trying to get the Intel 3945 wireless to work.

First of all I followed gotgenes instructions [here](http://ubuntuforums.org/showthread.php?t=286188&page=2).

I now have Network Manager installed and it is showing my access point. When I click on the access point it asks for my passcode (WPA) which I enter.
The icon then just spins round for ages before reverting to wired connection.

I have tried with WEP and no encryption with the same result.

Is there any error output that I can look for? Could there be anything that I need to install? So far I have only installed network-manager-gnome.

All help much appreciated!

---

### Post by featherking on 2007-03-08
I dont know if you are dual-booting at all but if you are could you test your wireless connection in windows? just to rule out your network setup.

I cant remember where NetworkManager stores its log. You could try connecting with NM and then type in terminal

```
dmesg
```
and look for errors with your wifi connection

if not try
```
tail /var/log/messages
```

see if there is any errors there that mention NetworkManager, if there arent there either try:
```
tail /var/log/syslog
```

I would think it would be in one of those areas if there is an error. But If you are able to see your networks then NetworkManger is working with your card properly because there arent any settings you can really adjust. This is why i think it is more likely a network problem.

---

### Post by trd79 on 2007-03-08
Hi featherking

Output from dmesg (after trying to connect to wireless) is
```
[17179759.452000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179769.920000] eth1: no IPv6 routers present

```

tail /var/log/messages
```
Mar  9 00:33:07 tosh2 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Mar  9 00:33:30 tosh2 kernel: [17180107.580000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Mar  9 00:35:24 tosh2 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Mar  9 00:35:24 tosh2 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Mar  9 00:35:24 tosh2 dhcdbd: message_handler: message handler not found under /com/redhMar  9 00:33:07 tosh2 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Mar  9 00:33:30 tosh2 kernel: [17180107.580000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Mar  9 00:35:24 tosh2 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Mar  9 00:35:24 tosh2 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Mar  9 00:35:24 tosh2 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Mar  9 00:35:25 tosh2 kernel: [17180222.860000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

/var/log/syslog
There is a lot in here. The section I have copied below is repeated several times before it gives up and connects back to eth0.
```
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Wireless event: cmd=0x8b15 len=20 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Wireless event: new AP: 00:00:00:00:00:00 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Setting scan request: 0 sec 100000 usec 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Added BSSID 00:12:17:07:d1:c3 into blacklist 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): State: ASSOCIATED -> DISCONNECTED 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WEXT: Operstate: linkmode=-1, operstate=5 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: External notification - portEnabled=0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: SUPP_PAE entering state DISCONNECTED 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: SUPP_BE entering state INITIALIZE 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: External notification - portValid=0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: External notification - EAP success=0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): connect event - remove keys 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 31 39 36 2d 35 00 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): State: DISCONNECTED -> SCANNING 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Starting AP scan (broadcast SSID) 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Scan timeout - try to get results 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Received 480 bytes of scan results (2 BSSes) 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Scan results: 2 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Selecting BSS from priority group 0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): 0: 00:12:17:07:d1:c3 ssid='WalkleyLAN' wpa_ie_len=24 rsn_ie_len=0 caps=0x11 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172):    selected based on WPA IE 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Trying to associate with 00:12:17:07:d1:c3 (SSID='WalkleyLAN' freq=0 MHz) 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 31 39 36 2d 35 00 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Cancelling scan request 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WPA: clearing own WPA/RSN IE 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Automatic auth_alg selection: 0x1 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WPA: using IEEE 802.11i/D3.0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WPA: clearing AP RSN IE 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WPA: using GTK TKIP 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WPA: using PTK TKIP 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WPA: using KEY_MGMT WPA-PSK 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): No keys have been configured - skip key clearing 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): wpa_driver_wext_set_drop_unencrypted 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): State: SCANNING -> ASSOCIATING 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WEXT: Operstate: linkmode=-1, operstate=5 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): wpa_driver_wext_associate 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Setting authentication timeout: 10 sec 0 usec 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: External notification - EAP success=0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: External notification - EAP fail=0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: External notification - portControl=Auto 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Wireless event: cmd=0x8b06 len=8 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): b1a len=19 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Wireless event: cmd=0x8b15 len=20 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Wireless event: new AP: 00:12:17:07:d1:c3 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): State: ASSOCIATING -> ASSOCIATED 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WEXT: Operstate: linkmode=-1, operstate=5 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Associated to a new BSS: BSSID=00:12:17:07:d1:c3 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): No keys have been configured - skip key clearing 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Associated with 00:12:17:07:d1:c3 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 31 39 36 2d 35 00 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WPA: Association event - clear replay counter 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: External notification - portEnabled=0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: External notification - portValid=0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: External notification - EAP success=0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: External notification - portEnabled=1 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: SUPP_PAE entering state CONNECTING 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: SUPP_BE entering state IDLE 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): Setting authentication timeout: 10 sec 0 usec 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: startWhen --> 0 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: SUPP_PAE entering state CONNECTING 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): EAPOL: txStart 
Mar  9 00:48:38 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0) 
Mar  9 00:48:44 tosh2 NetworkManager: <information>^Iwpa_supplicant(6172): 0 
Mar  9 00:48:44 tosh2 NetworkManager: <information>^IActivation (eth1/wireless): association took too long (>120s), failing activation. 
Mar  9 00:48:44 tosh2 NetworkManager: <information>^IActivation (eth1) failure scheduled... 
Mar  9 00:48:44 tosh2 NetworkManager: <information>^IActivation (eth1) failed for access point (WalkleyLAN) 
Mar  9 00:48:44 tosh2 NetworkManager: <information>^IActivation (eth1) failed. 
Mar  9 00:48:44 tosh2 NetworkManager: <information>^IDeactivating device eth1. 
Mar  9 00:48:46 tosh2 NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Mar  9 00:48:46 tosh2 NetworkManager: <information>^IWill activate connection 'eth0'. 
Mar  9 00:48:46 tosh2 NetworkManager: <information>^IDevice eth0 activation scheduled... 


```

It does look like something to do with WPA but I tried earlier with no encryption and still didn't connect. Will try no encryption again and post the logs if I still don't get any joy.

This machine has never had windows installed, so could be a hardware problem. If all else fails I will have to install XP and see if it works. Can connect to the network using another laptop (XP) without problem, so assuming that my wireless is set up correctly.

Got a day off tomorrow so hoping to get it sorted then. Fed up of tripping over all these wires :-?

Cheers,

Tom

---

### Post by featherking on 2007-03-08
Very wierd,

i cant see any reason for it not to associate, and if you have another computer that does connect wirelessly then chances are your network is setup properly. I dont see any reason for it not to work if you are using WPA-PSK on both your router and your wifi card.. Something is wrong somewhere though if you cant even connect with no encryption.. Sorry im not being of more help, you are doing everything right   :(

EDIT: See if you can connect manually using wpa_supplicant (sorry its a little long). Do the following in terminal

```
sudo gedit /etc/wpa_supplicant.conf
```

change the following bold sections and then paste into the open gedit window
```
network={
ssid="**YOUR SSID**"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
psk="**YOUR WIFI PASSWORD**"
}

```
close and save that.

back in terminal type:
```
gedit ~/Desktop/wificonnect.sh
```

paste the following
```
gksudo "killall wpa_supplicant"
sudo wpa_supplicant -Dwext -B -w -ieth1 -c /etc/wpa_supplicant.conf
sudo /etc/init.d/networking restart
sudo dhclient eth1

```
save and exit

now type
```
chmod +x ~/Desktop/wificonnect.sh
```

now kill NetworkManager
```
sudo killall NetworkManager
```

Now after all those steps you have a script that sets up a manual connection using WPA on your wifi access point. The script should be on your desktop called wificonnect.sh and when you double click and run it, you should connect and be assigned an IP by your dhcp server. I use this as a backup sometimes on my laptop. See if you are able to connect via WPA to your access point..

---

### Post by trd79 on 2007-03-09
Thanks featherking.

Did as you suggested. Here is the output from running wificonnect.sh from a terminal:

```

tom@tosh2:~$ ~/Desktop/wificonnect.sh 
wpa_supplicant: no process killed
 * Reconfiguring network interfaces...                                   [ ok ] 
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:19:d2:53:7c:b9
Sending on   LPF/eth1/00:19:d2:53:7c:b9
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Does this mean that I am successfully connecting, but having a problem with DHCP?
What is the easiest way of testing with a static IP?

Think I might revert to XP just to make sure that it actually works :)
Assuming that is successful, would you suggest trying the latest version of feisty?

---

### Post by trd79 on 2007-03-09
Result!

Have been able to lay my hands on an identical laptop with factory settings (WinXP Pro)
Still had problems connecting to access point using this (even though my other laptop was working fine using a netgear PCMCIA adaptor)

Started changing settings on my router. Changing the Wireless channel from 2 to 7 did the trick!
For some reason the Intel Pro/Wireless 3945 was having problems with my access point (Linksys WRTG) running on channel 2 (both in linux and WinXP). Not sure if this has been found by anyone else but if I can find anywhere to report it I will.

Just one question now... how do I set the default route when using Network Manager? It automatically sets the Default Route and Primary DNS to the ip address of my access point, however my local dns and gateway is via another server. I have set this manually using the below and everything is fine.```
sudo route add gw 192.168.1.1 eth1
```

Is there any way to set this via Network manager?

Anyway, am typing this wire free so am happy :-)
Featherking, thanks very much for all your help. Were it not for your feedback I would still be blaming ubuntu for my lack of wireless!

All the best,


Tom

---

### Post by linuxbuddhist on 2007-03-14
Hmm.. I've followed all the instructions but to no avail.
Running Edgy on a Dell Inspiron 6000 with Intel 2200 wireless and have installed wpa supplicant and network manger with gnome icon "supposedly."
 
[I][INDENT]sudo apt-get install network-manager-gnome network-manager wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-gnome is already the newest version.
network-manager is already the newest version.
wpasupplicant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/INDENT][/I]

[INDENT]sudo apt-get install network-manager-gnome network-manager wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-gnome is already the newest version.
network-manager is already the newest version.
wpasupplicant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/INDENT]

Then reloaded the cache file

*[INDENT]gtk-update-icon-cache -f /usr/share/icons/hicolor/Cache file created successfully.[/INDENT]*

and STILL I see no other icon but the regular Wireless network icon.  My wireless works on my home system after editing the Network setup but there is no other icon to view available wireless networks or connect to a different network.  

I need to use this at my University which requires a certificate and WPA but can't see to figure out the problems.

[I][INDENT]This is what my /etc/network/interfaces gedit shows:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid Brie
wireless-key XXXX......
[/INDENT][/I]

Any ideas of what to do?  


I've also removed and reinstalled wpa supplicant and networking to no avail.

Thanks!

---

### Post by dillon533 on 2007-03-14
Thanks great guide. Having read about 100 others and getting no where. This really help      ed once again thankyou :)

---

### Post by featherking on 2007-03-14
@dillon533
glad you liked it  !!


@linuxbuddhist
you didnt follow the guide exactly, the screenshot you provided should have no boxes checked. refer to this step

> The easiest way to get NM to start controlling your network interfaces (plural because it will also control your wired connection) is to open up (in gnome, not sure on kde) System > Admin > Networking (the default networking tool) open the properties for all the devices there, whether wired or wireless and in the properties dialog box **clear the box that says 'enable this connection'**

This should change the output of your /etc/network/interfaces file to read:

```
auto lo
iface lo inet loopback

```


NetworkManager will control all of your network interfaces if you use it. So you need to un-configure everything in gnome. Follow that step and the rest of the guide and it should work

---

### Post by jfanaian on 2007-03-15
trd79, I had a similar problem with the default route. I was able to fix it by running the following command

```

sudo -S route add default gw <ip>

```

---

### Post by featherking on 2007-03-16
@trd79
Sorry i never responded! i sort of went out of town for a few days, i didnt even realize till right now that you got it fixed! To answer your question about routes i believe you have found the only way to add routes, because there isnt any option to add them in NetworkManager (AFAIK). Again, congrats

---

### Post by indica on 2007-03-17
Thank you Thank you Thank you!!!

---

### Post by trd79 on 2007-03-17
@jfanaian
Thanks, that is exactly what I am doing. The problem is, if I add this to a script that is always executed on connection, it will screw up my connection to other APs.
When I have a spare few moments I will try and write a script which will check the SSID of the AP and reset the route if it matches my home network. Alternatively, the 'cleanest' solution would be to get my router to do it's job and route traffic via my gateway!

@featherking
No problem. Really appreciate the time and patience you dedicate to helping us in these forums. Am looking forward to NetworkManager being fully integrated in Feisty. Hopefully it will be the latest version which does not rely on the gnome keyring manager.

---

### Post by linuxbuddhist on 2007-03-17
Ok, worked that time.  Should have read more closely I suppose.  Thanks!

Now the next hurdle is figuring out how to configure WPA to use a certificate for my University.  I have the cert itself which isn't a problem and know that it will ask for the location but need to figure out the rest.

Thanks again.

---

### Post by gigermunit on 2007-03-17
OMFG THANKS SO MUCH i combined all the tuts from this foruma and none worked till i used this one thanks so much all i need now is to get wine working and im fully switching

---

### Post by featherking on 2007-03-17
@linuxbuddhist
No problem, but i could see your problem instantly from your screenshot. glad you got it working.

@gigermunit
Nice job, good luck with wine it works great for some things and horrible for others..!

---

### Post by gigermunit on 2007-03-17
Thanks to you when im on windows i find my self clicking the top of my screen to try and run applications :P as soon as i can backup soem of my new files on windows and find out why 2 kernels of ubuntu are coming up after i updated ill be full linux since i found out how to get wow to work.

---

### Post by LeperUnclean on 2007-03-18
Does this tutorial work the same on Dapper Drake???

I want to make sure I have covered every possible extreme before setting up Linux and finding out that Wireless wouldn't work for me...

Heck, Wireless is the only reason I am still using Windows...

---

### Post by oderus on 2007-03-18
Thanks! This worked liked a charm.

Feisty Fawn x86_64 Heard 5
Dell D620 Core 2 Duo 1.83ghz 2GB ram
Broadcom Wireless
(lspci
0c:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

Cheers.

---

### Post by featherking on 2007-03-19
@LeperUnclean
yeah it should work for dapper. Ive used NetworkManager for a long time, even before dapper I think..

---

### Post by LeperUnclean on 2007-03-19
Thanks featherking, guess I am going Ubuntu after work....

---

### Post by featherking on 2007-03-19
@LeperUnclean
Heck if you are worried about installing ubuntu, you could do all these steps from just booting the liveCD of dapper. Then you dont risk harming the machine at all. But im pretty confident it will work as long as you have a supported card

---

### Post by LeperUnclean on 2007-03-19
@Featherking

Naw, I am not worried about installing it, I have it running on my desktop, I just have been to laz t put it on my laptop yet...

---

### Post by krayzee8 on 2007-03-21
This how to worked great for my Compaq V5209US running a Dell Broadcom 1390 PCI Express card.  Unfortunately, I am only able to connect to unencrypted networks.  I am pretty sure that it is the 1390 card though as NetworkManager sees all the area networks and tells me if they are encrypted or not.  I have found others that have the same problem with this card as well.

However, thanks for the great How To!

---

### Post by featherking on 2007-03-21
@krayzee8
Glad is sort of works for you. I agree that it is probably your broadcom. Everything i read about those  is bad as far as linux support goes..

---

### Post by postalservice14 on 2007-03-22
AWESOME!!! Worked great for me.

Thank you,

John

---

