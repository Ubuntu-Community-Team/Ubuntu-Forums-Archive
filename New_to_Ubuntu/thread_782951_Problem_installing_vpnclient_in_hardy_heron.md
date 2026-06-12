---
title: "Problem installing vpnclient in hardy heron"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by dashdash on 2008-05-05
Hi,

I am new to linux. I installed kubuntu 8.04 (hardy heron) and then downloaded the vpnclient from my school website and used the following commands

1)  tar -xzvf <filename>
2) apt-get install network-manager-gnome 
   apt-get install network-manager-pptp  
3)changed the following 2 lines of interfaces file of /etc/networks

from:
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


to: 
auto wlan0
iface wlan0 inet dhcp
address 127.0.0.1
netmask 255.0.0.0

4) then I killed the 'NetworkManager' and the 'NetworkManagerDispatcher' and tried to restart them using the following commands

/etc/init.d/networking restart

but instead of getting the available wireless networks with their signal strengths I got the following error:

 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:16:cf:55:b0:85
Sending on   LPF/wlan0/00:16:cf:55:b0:85
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:16:cf:55:b0:85
Sending on   LPF/wlan0/00:16:cf:55:b0:85
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping

This did not happen when I installed vpnclient with kubuntu 8.04 (beta).

I loose all wireless connection if I change the interfaces file. 

Can anyone give a clue why this is happening?

Thanks in advance

---

### Post by honeydew on 2008-05-05
I dont think you need to compile anything or change anything in your /etc/network/interfaces for this to be active. instead try setting everything back to default..  and using the vpn client in the gui.  the settings should be pretty straight forward 


do you know what kind of vpn it is? I see 3 different pluggins in the repositories:
network-manager-openvpn-network management framework(OpenVPN plugin)        
network-manager-pptp- network management framework(PPTP plugin)           
network-manager-vpnc- network management framework (VPNC plugin)  


confirm with your school which is the correct client(pptp, cisco-vpn, or openvpn).. then use the network icon at the top in order to configure.. 


example:
[http://freeborn.dreamhosters.com/example.ogg](http://freeborn.dreamhosters.com/example.ogg)

---

