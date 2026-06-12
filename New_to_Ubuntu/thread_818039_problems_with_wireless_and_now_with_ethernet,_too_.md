---
title: "problems with wireless and now with ethernet, too :("
date: 2008-06-04
forum: New to Ubuntu
---

### Post by hardingfele on 2008-06-04
hi,

i tried to establish internet access on my laptop to two wireless points, one at a library and one at home. the one at the library is unencrypted and i managed to get it working using this thread:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

and the following part out of it:
```
sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "DNBWLANF"
sudo iwconfig eth1 mode Managed
sudo dhclient eth1
```

and putting it into 
```
gksu gedit /etc/rc.local
```

so that it connects at boot worked fine as well.

at home i would like to use wpa1, dhcp, broadcast essid. i tried to get that working yesterday using this thread:

[http://ubuntuforums.org/showthread.php?t=225290](http://ubuntuforums.org/showthread.php?t=225290)

and since then i don't even have ethernet anymore. i tried to undo all the changes that i made which was essentially only one change in a script (at least i think so), but i also tried to delete network manager using synaptic. maybe that was a problem?
anyway, here is what i tried in more detail and i would be grateful if somebody could help :-)! thx....

iwconfig gives:

```
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-105 dBm
          Rx invalid nwid:30060  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:35490   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-95 dBm
          Rx invalid nwid:30060  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:35490   Missed beacon:0
```

iwlist scan gives:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      No scan results

wifi0     No scan results
```

unfortunatly i don't have record from before anymore...this is from the time after my cable connection had stopped working. but i definatly remember that both eth1 and wifi0 found my wireless signal at home when i did the scanning.

i put into ```
sudo gedit /etc/network/interfaces
``` the following code:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid <my_essid>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <ps-hex-key>
```
 
i also managed to get the key in hex by typing ```
wpa_passphrase <your_essid> <your_ascii_key>
``` (8x8 hex-numbers for an 8dig-psk).

after saving i tried ```
sudo /etc/init.d/networking restart
```
twice, also after rebooting, and it gave (again this is from the time after things stopped working):

```
 * Reconfiguring network interfaces...                                          
There is already a pid file /var/run/dhclient.eth1.pid with pid 5509
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:02:8a:f1:fd:a0
Sending on   LPF/eth1/00:02:8a:f1:fd:a0
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 1.1.1.1 port 67
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:02:8a:f1:fd:a0
Sending on   LPF/eth1/00:02:8a:f1:fd:a0
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Ignoring unknown interface wifi0=wifi0.
```

---

### Post by kubaknopp on 2008-06-04
There is one thing I don't understand. Why you just can't use network-manager?

---

### Post by Kinnza on 2008-06-04
cause command mode gives actuall data :D

---

### Post by hardingfele on 2008-06-04
establishing an internet connection with the networkmanager would sometimes work in the library and sometimes not. i couldn't figure out why. and when i tried it at home, it would never remember my psk, which i also couldn't figure out why :(.

i've just tried my connection in the library. that's gone as well :cry:

pls, can somebody help me? is it actually possible to run two different kinds of connections for different places (unencrypted and WPA1)?

am new to ubuntu and really have no idea how to set it all up other than what i've tried (and messed up ;))

tanks a lot in advance!!

---

