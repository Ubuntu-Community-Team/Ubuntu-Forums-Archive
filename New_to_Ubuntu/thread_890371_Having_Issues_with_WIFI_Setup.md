---
title: "Having Issues with WIFI Setup"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by drboard on 2008-08-15
I installed Ubuntu 3 days ago and am currently having a heck of a time getting my WIFI to work properly.  Hopefully someone can help.  I have a 2Wire USB WIFI adapter with a provider installed (AT&T Uverse) gateway.  Every time i try to connect to my network with my WEP key i cannot gain access to the network... It just seems to timeout and continue to ask for the Passphrase.  I CAN currently connect to the internet via an unsecured wireless connection (no I have double and triple checked the passphrase, which is correct.  My WEP connected internet works good currently when I dual boot into XP and also on my phone so I'm pretty sure I just don't have something set up right.  Any ideas or suggestions would be greatly appreciated. I am new to Ubuntu.  Below is some attached information about my system: (currently not connected via WEP Key in place on gateway)

-----iwconfig:

dustin@dustin-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Link Quality=98/100  Signal level=45/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


-----sudo lshw -C network:

dustin@dustin-desktop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1e:37:93:be:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g

-----cat /etc/network/interfaces:

dustin@dustin-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback



iface eth1 inet dhcp
wpa-psk 42bdf98e9aa9ab132aa2e1e39de4631bd83421e1963fb2947075601821d53974
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid wormwood


sorry for the long post but wanted to be as complete as possible.... Thanks in advance!!

---

### Post by InfinityCircuit on 2008-08-15
You said WEP in the post but your setup in /etc/network/interface is for WPA.  Which one is it?

---

### Post by drboard on 2008-08-15
Good observation... Thank you for the help... I ended up setting the gateway to WPA instead of WEP and everything is working well.. I appriciate your help with something that should have been obvious to me.  I guess I have been looking it for what seems to be forever that I overlooked it.  Thanks again!

---

