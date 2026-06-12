---
title: "VPN DNS Issues"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by d4m1r on 2012-05-11
Hey guys, so I did a clean install of 12.04 last week and suddenly I can't connect to 2 different VPN's I setup and maintain. I haven't touched them and I confirmed they are working on other PC's. Under Ubuntu 12.04 however, they connect, but I cannot really access the internet as DNS names don't resolve :confused: I can ping individual IPs, but not google.com for example...

From doing a bit of reading, apparently there have been major changes to how DNS works under 12.04....I instituted a temporary workaround by disabled a new feature called **dnsmasq** as described [HERE]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/") and [HERE]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/994575"). Can anyone elaborate on what this dnsmasq package is or what it does? Should I re-enable it, and if so, what is an alternative method to browsing the internet through my VPNs?

Thanks in advance gurus!

---

### Post by d4m1r on 2012-05-11
p.s: I don't know if it helps, but find a snippet of my syslog's below specifically around the time I was connecting to my VPNs....Note I manually changed all the real IPs to xxx:

```
May 11 20:22:26 damir-ubuntu NetworkManager[2730]: <info> Starting VPN service 'openvpn'... 
May 11 20:22:26 damir-ubuntu NetworkManager[2730]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 31879 
May 11 20:22:26 damir-ubuntu NetworkManager[2730]: <info> VPN service 'openvpn' appeared; activating connections 
May 11 20:22:26 damir-ubuntu NetworkManager[2730]: <info> VPN plugin state changed: init (1) 
May 11 20:22:26 damir-ubuntu nm-openvpn[31882]: OpenVPN 2.2.1 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Mar 30 2012 
May 11 20:22:26 damir-ubuntu NetworkManager[2730]: <info> VPN plugin state changed: starting (3) 
May 11 20:22:26 damir-ubuntu NetworkManager[2730]: <info> VPN connection 'xxx' (Connect) reply received. 
May 11 20:22:26 damir-ubuntu nm-openvpn[31882]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info. 
May 11 20:22:26 damir-ubuntu nm-openvpn[31882]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts 
May 11 20:22:26 damir-ubuntu nm-openvpn[31882]: WARNING: file '/home/damir/VPN/vps2/client1.key' is group or others accessible 
May 11 20:22:26 damir-ubuntu nm-openvpn[31882]: LZO compression initialized 
May 11 20:22:26 damir-ubuntu nm-openvpn[31882]: UDPv4 link local: [undef] 
May 11 20:22:26 damir-ubuntu nm-openvpn[31882]: UDPv4 link remote: [AF_INET]xxx:1194 
May 11 20:22:26 damir-ubuntu nm-openvpn[31882]: [server] Peer Connection Initiated with [AF_INET]xxx:1194 
May 11 20:22:29 damir-ubuntu nm-openvpn[31882]: TUN/TAP device tun0 opened 
May 11 20:22:29 damir-ubuntu nm-openvpn[31882]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper tun0 1500 1542 10.8.0.6 10.8.0.5 init 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0) 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found. 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]: <info> VPN connection 'xxx' (IP Config Get) reply received. 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]: <info> VPN Gateway: xxx 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]: <info> Internal Gateway: 10.8.0.5 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]: <info> Tunnel Device: tun0 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]: <info> Internal IP4 Address: 10.8.0.6 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]: <info> Internal IP4 Prefix: 32 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]: <info> Internal IP4 Point-to-Point Address: 10.8.0.5 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]: <info> Maximum Segment Size (MSS): 0 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]: <info> Static Route: 10.8.0.1/32   Next Hop: 10.8.0.1 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]: <info> Forbid Default Route: no 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]: <info> Internal IP4 DNS: 10.8.0.1 
May 11 20:22:29 damir-ubuntu NetworkManager[2730]: <info> DNS Domain: '(none)' 
May 11 20:22:29 damir-ubuntu nm-openvpn[31882]: Initialization Sequence Completed 
May 11 20:22:30 damir-ubuntu NetworkManager[2730]: <info> DNS: starting dnsmasq... 
May 11 20:22:30 damir-ubuntu dnsmasq[22709]: exiting on receipt of SIGTERM 
May 11 20:22:30 damir-ubuntu NetworkManager[2730]: <info> (tun0): writing resolv.conf to /sbin/resolvconf 
May 11 20:22:30 damir-ubuntu dnsmasq[31944]: started, version 2.59 cache disabled 
May 11 20:22:30 damir-ubuntu dnsmasq[31944]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN 
May 11 20:22:30 damir-ubuntu dnsmasq[31944]: using nameserver 10.8.0.1#53 
May 11 20:22:30 damir-ubuntu NetworkManager[2730]: <info> VPN connection 'xxx' (IP Config Get) complete. 
May 11 20:22:30 damir-ubuntu NetworkManager[2730]: <info> Policy set 'xxx' (tun0) as default for IPv4 routing and DNS. 
May 11 20:22:30 damir-ubuntu NetworkManager[2730]: <info> VPN plugin state changed: started (4) 
May 11 20:22:30 damir-ubuntu dbus[955]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper) 
May 11 20:22:30 damir-ubuntu dbus[955]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher' 
May 11 20:23:03 damir-ubuntu NetworkManager[2730]: <warn> (11) failed to find interface name for index 
May 11 20:23:03 damir-ubuntu NetworkManager[2730]: nm_system_iface_flush_routes: assertion `iface != NULL' failed 
May 11 20:23:03 damir-ubuntu NetworkManager[2730]: <warn> (11) failed to find interface name for index 
May 11 20:23:03 damir-ubuntu NetworkManager[2730]: <info> DNS: starting dnsmasq... 
May 11 20:23:03 damir-ubuntu dnsmasq[31944]: exiting on receipt of SIGTERM 
May 11 20:23:03 damir-ubuntu NetworkManager[2730]: <info> (tun0): writing resolv.conf to /sbin/resolvconf 
May 11 20:23:03 damir-ubuntu dnsmasq[32642]: started, version 2.59 cache disabled 
May 11 20:23:03 damir-ubuntu dnsmasq[32642]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN 
May 11 20:23:03 damir-ubuntu dnsmasq[32642]: using nameserver 192.168.1.1#53 
May 11 20:23:04 damir-ubuntu NetworkManager[2730]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS. 
May 11 20:23:04 damir-ubuntu dbus[955]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper) 
May 11 20:23:04 damir-ubuntu NetworkManager[2730]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0) 
May 11 20:23:04 damir-ubuntu dbus[955]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher' 
May 11 20:23:04 damir-ubuntu nm-openvpn[31882]: SIGTERM[hard,] received, process exiting 
May 11 20:23:09 damir-ubuntu NetworkManager[2730]: <info> VPN service 'openvpn' disappeared
```^Taken prior to me disabling dnsmasq, and I also noticed that even after connecting to the VPN, resolveconf was not being changed....

---

### Post by d4m1r on 2012-05-12
Is nobody else experiencing DNS issues when they connect to a VPN? :confused:

---

### Post by SeijiSensei on 2012-05-12
The changes to DNS in 12.04 are supposed to [improve compatibility with VPNs](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/).

If you want to specify DNS servers with the resolvconf scheme, add them to /etc/network/interfaces.  See "man resolvconf" for details.

---

### Post by d4m1r on 2012-05-12
> **SeijiSensei said:**
> The changes to DNS in 12.04 are supposed to [improve compatibility with VPNs]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/").

If you want to specify DNS servers with the resolvconf scheme, add them to /etc/network/interfaces.  See "man resolvconf" for details.

Thanks but you linked me to an article that I linked to myself in my first post...

Anyway, no I don't believe it is supposed to improve compatibility with VPNs as it has done the exact opposite, it has broken all 3 of the ones I was using. Obviously when I'd like to surf the internet through a VPN, I'd like to use the VPN servers DNS instead of my own local so why dnsmasq/resolveconf default to local ones is beyond me....

Basically, dnsmasq is a new feature in 12.04 that tries to enhance security related to a few minor DNS vulnerabilities (ones I was never concerned with in the first place) so I will leave it disabled....Not sure why this is installed by default in 12.04 because it will break **ALL** VPN connections that were previously working in older versions of Ubuntu, but I guess most people on here just don't use VPNs...

---

### Post by ogilvierothchild on 2012-05-12
I am having the same issue with a Cisco VPN.  I couldn't get the builtin networkmanager VPN setup to work.

Running "vpnc" from the command line as root worked just fine, however.

---

### Post by d4m1r on 2012-05-12
> **ogilvierothchild said:**
> I am having the same issue with a Cisco VPN.  I couldn't get the builtin networkmanager VPN setup to work.

Running "vpnc" from the command line as root worked just fine, however.

If you disable dnsmasq, it will work through network-manager as well (I confirmed and tested it last night). However, it is weird how using vpnc or openvpn through command line (for example) bypasses dnsmasq and allows us to use your VPNs DNS servers instead of local ones...

---

### Post by dsn42 on 2012-05-14
I notice that when I connect with vpnc, the contents of 
/var/run/nm-dns-dnsmasq.conf are modified to have a
couple of lines of server=addr, where addr is the ip address
of a dns server appropriate for the vpn.  When I connect to
the vpn with network manager, /var/run/nm-dns-dnsmasq.conf
is empty

---

### Post by danvis on 2012-05-15
Thanks you for the help!

With the vpnc command in the console I finally got it working. 
With the gui/systemtray panel of the networkmanager in KDE the vpn didn't work with the disabled dnsmasq. Or does it work with some addtional settings? If this would be working I even would more happier. :)
I used the same cisco config files with vpnc and to import the settings in the networkmanager gui.

visdan

OS: Kubuntu Precise Pangolin
KDE Version: 4.8.3

---

### Post by daniele.depetrini on 2012-05-15
I think I found a nicer wka: in kde-knetwork-manager, editing a VPN connection, there is a tab "IPv4 Address".  In "Basic settings", the default method is "Automatic(VPN)". Changing to ""Automatic(VPN) address only", the dialog let you specify DNS server and local domains. Once specified, internal domain resolution should work as a charm!

Hint: VPN  DNS are written into syslog once connected

Will be nice to be able to specify as another option internal domains only and let the connection to use connection provided DNS servers.

Daniele.

---

### Post by linuchsan on 2012-05-15
echo 1 > /proc/sys/net/ipv4/ip_forward

---

### Post by vangop on 2012-05-22
This issue is annoying. 
I have 2 vpns, one is working fine, the other doesn't. (both work with vpnc-connect, but they just bypass dnsmasq)
Can someone explain or point to the answers
1. why vpnc-connect bypasses dnsmasq
2. why dnsmasq+nm works for some, doesn't for others

---

### Post by d4m1r on 2012-05-22
> **vangop said:**
> This issue is annoying. 
I have 2 vpns, one is working fine, the other doesn't.

Are you using "use only for resources on its network" for one of them? This seems to bypass dnsmasq...

---

