---
title: "HOWTO: IPW2200 WLAN under Edgy with WPA encryption"
date: 2006-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by ronzo on 2006-11-01
After upgrading from Dapper to Edgy my wpa-encrypted WLAN-connection did not work anymore. So I was looking for HowTos on the Internet but none of them worked properly on my Acer TM800. So I figured the settings out on my own.

Here's what I did:

1)
Installation of Edgy (from the alternate CD)

2)
Modification of /etc/network/interfaces - eth1 is my IPW2200:
auto eth1
iface eth1 inet dhcp
(note that I'm using DHCP)

3)
Creation of a file named /etc/wpa_supplicant.conf with this content:
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2
network={
   ssid="myessid"
   scan_ssid=1
   proto=WPA
   key_mgmt=WPA-PSK
   pairwise=TKIP
   psk="mypsk"
}

4)
Reboot.

5)
Try if everything works with:
sudo wpa_supplicant -D wext -i eth1 -c /etc/wpa_supplicant.conf -w -dd

6)
If you're using dhcp, try "sudo dhclient eth1" and watch if you'll get an IP-Address.

7)
Create a start-script as described in other HowTo's.
(like here: [http://www.ubuntuforums.org/showthread.php?t=26623;](http://www.ubuntuforums.org/showthread.php?t=26623;) be sure to locate wpa_supplicant ... in my case it's in /sbin and not in /usr/sbin)

---

