---
title: "VPN not staying connected!!"
date: 2019-04-03
forum: New to Ubuntu
---

### Post by paxdriver on 2019-04-03
I keep trying to connect to a VPN using the configuration files provided by my VPN provider but my system won't stay connected. It forced me to set up dozens of connections so I can more easily "trial-and-error" find one that will stick and stay open while I use the internet. 

Is this a problem with my VPN, proxy or protocol ( UDP vs TCP?) settings or is this a Linux problem? The included details below show the connection being established, working, then timing out and finally the service "disappearing". It does this with tons of different VPN server connections I try from all different countries and regions, all set up the same way; using config files from the VPN provider and double checking them manually for inconsistencies.

The journalctl log shows an error then just says the service disappeared when trying to reestablish a connection (I think, see below) and it doesn't seem to be consistent about which connection I choose for it to stay connected. For context, the logs below are done while actively streaming radio and browsing the web testing the connection to ready this post.

Please help! I don't understand the logs / error codes I'm getting and my VPN provider is not very helpful. THANK YOU!


journalctl -f -u NetworkManager
-- Logs begin at Wed 2019-01-23 14:24:28 CST. --
Apr 03 08:55:42 Kris NetworkManager[919]: <info>  [1554299742.1389] device (tun1): state change: config -> ip-config (reason 'none', sys-iface-state: 'external')
Apr 03 08:55:42 Kris NetworkManager[919]: <info>  [1554299742.1389] device (tun1): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'external')
Apr 03 08:55:42 Kris NetworkManager[919]: <info>  [1554299742.1392] device (tun1): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'external')
Apr 03 08:55:42 Kris NetworkManager[919]: <info>  [1554299742.1393] device (tun1): state change: secondaries -> activated (reason 'none', sys-iface-state: 'external')
Apr 03 08:55:42 Kris NetworkManager[919]: <info>  [1554299742.1434] device (tun1): Activation: successful, device activated.
Apr 03 08:56:12 Kris NetworkManager[919]: <info>  [1554299772.1169] connectivity: (tun1) timed out
Apr 03 08:57:47 Kris NetworkManager[919]: <info>  [1554299867.1159] connectivity: (tun1) timed out
Apr 03 09:02:47 Kris NetworkManager[919]: <info>  [1554300167.1167] connectivity: (tun1) timed out
Apr 03 09:07:47 Kris NetworkManager[919]: <info>  [1554300467.1164] connectivity: (tun1) timed out
Apr 03 09:12:47 Kris NetworkManager[919]: <info>  [1554300767.1154] connectivity: (tun1) timed out
Apr 03 09:15:27 Kris NetworkManager[919]: <info>  [1554300927.5742] audit: op="connection-deactivate" uuid="f83b1870-6129-40d4-90b1-6b4a38236d0f" name="ipvanish-US-New-York-nyc-a02" pid=1662 uid=1000 result="success"
Apr 03 09:15:27 Kris nm-openvpn[16745]: SIGTERM received, sending exit notification to peer
Apr 03 09:15:27 Kris NetworkManager[919]: <info>  [1554300927.5799] device (tun1): state change: activated -> unmanaged (reason 'connection-assumed', sys-iface-state: 'external')
Apr 03 09:15:27 Kris NetworkManager[919]: <info>  [1554300927.5860] vpn-connection[0x5650752f67b0,f83b1870-6129-40d4-90b1-6b4a38236d0f,"ipvanish-US-New-York-nyc-a02",0]: VPN plugin: state changed: stopping (5)
Apr 03 09:15:27 Kris NetworkManager[919]: <info>  [1554300927.5860] vpn-connection[0x5650752f67b0,f83b1870-6129-40d4-90b1-6b4a38236d0f,"ipvanish-US-New-York-nyc-a02",0]: VPN plugin: state changed: stopped (6)
Apr 03 09:15:29 Kris NetworkManager[919]: <info>  [1554300929.5876] devices removed (path: /sys/devices/virtual/net/tun1, iface: tun1)
Apr 03 09:15:30 Kris NetworkManager[919]: <info>  [1554300930.3823] audit: op="connection-activate" uuid="dcff9b1e-1f4e-4516-bb9d-90d483953ba1" name="ipvanish-US-Dallas-dal-a06" pid=1662 uid=1000 result="success"
Apr 03 09:15:30 Kris NetworkManager[919]: <info>  [1554300930.3882] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",0]: Started the VPN service, PID 20081
Apr 03 09:15:30 Kris NetworkManager[919]: <info>  [1554300930.3939] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",0]: Saw the service appear; activating connection
Apr 03 09:15:30 Kris NetworkManager[919]: <info>  [1554300930.4800] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",0]: VPN plugin: state changed: starting (3)
Apr 03 09:15:30 Kris NetworkManager[919]: <info>  [1554300930.4800] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",0]: VPN connection: (ConnectInteractive) reply received
Apr 03 09:15:30 Kris nm-openvpn[20087]: WARNING: --keysize is DEPRECATED and will be removed in OpenVPN 2.6
Apr 03 09:15:30 Kris nm-openvpn[20087]: OpenVPN 2.4.4 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Sep  5 2018
Apr 03 09:15:30 Kris nm-openvpn[20087]: library versions: OpenSSL 1.1.0g  2 Nov 2017, LZO 2.08
Apr 03 09:15:30 Kris nm-openvpn[20087]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Apr 03 09:15:30 Kris nm-openvpn[20087]: TCP/UDP: Preserving recently used remote address: [AF_INET]209.107.216.4:443
Apr 03 09:15:30 Kris nm-openvpn[20087]: UDP link local: (not bound)
Apr 03 09:15:30 Kris nm-openvpn[20087]: UDP link remote: [AF_INET]209.107.216.4:443
Apr 03 09:15:30 Kris nm-openvpn[20087]: NOTE: chroot will be delayed because of --client, --pull, or --up-delay
Apr 03 09:15:30 Kris nm-openvpn[20087]: NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Apr 03 09:15:31 Kris nm-openvpn[20087]: [dal-a06.ipvanish.com] Peer Connection Initiated with [AF_INET]209.107.216.4:443
Apr 03 09:15:32 Kris nm-openvpn[20087]: Option 'explicit-exit-notify' in [PUSH-OPTIONS]:6 is ignored by previous <connection> blocks
Apr 03 09:15:32 Kris nm-openvpn[20087]: TUN/TAP device tun1 opened
Apr 03 09:15:32 Kris nm-openvpn[20087]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper --debug 0 20081 --bus-name org.freedesktop.NetworkManager.openvpn.Connection_23 --tun -- tun1 1500 1553 172.21.22.43 255.255.254.0 init
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4282] manager: (tun1): new Tun device (/org/freedesktop/NetworkManager/Devices/13)
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4363] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",0]: VPN connection: (IP Config Get) reply received.
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4377] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: VPN connection: (IP4 Config Get) reply received
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4386] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: Data: VPN Gateway: 209.107.216.4
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4386] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: Data: Tunnel Device: "tun1"
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4386] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: Data: IPv4 configuration:
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4387] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: Data:   Internal Gateway: 172.21.22.1
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4387] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: Data:   Internal Address: 172.21.22.43
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4387] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: Data:   Internal Prefix: 23
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4387] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: Data:   Internal Point-to-Point Address: 172.21.22.43
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4387] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: Data:   Static Route: 0.0.0.0/0   Next Hop: 172.21.22.1
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4388] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: Data:   Static Route: 172.21.22.0/23   Next Hop: 0.0.0.0
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4388] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: Data:   Internal DNS: 198.18.0.1
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4388] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: Data:   Internal DNS: 198.18.0.2
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4388] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: Data:   DNS Domain: '(none)'
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4388] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: Data: No IPv6 configuration
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4392] devices added (path: /sys/devices/virtual/net/tun1, iface: tun1)
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4392] device added (path: /sys/devices/virtual/net/tun1, iface: tun1): no ifupdown configuration found.
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4392] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: VPN plugin: state changed: started (4)
Apr 03 09:15:32 Kris nm-openvpn[20087]: chroot to '/var/lib/openvpn/chroot' and cd to '/' succeeded
Apr 03 09:15:32 Kris nm-openvpn[20087]: GID set to nm-openvpn
Apr 03 09:15:32 Kris nm-openvpn[20087]: UID set to nm-openvpn
Apr 03 09:15:32 Kris nm-openvpn[20087]: Initialization Sequence Completed
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4418] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: VPN connection: (IP Config Get) complete
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4420] device (tun1): state change: unmanaged -> unavailable (reason 'connection-assumed', sys-iface-state: 'external')
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4510] keyfile: add connection in-memory (7f71c4c8-26e3-4984-b6a6-c7e926c37d92,"tun1")
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4515] device (tun1): state change: unavailable -> disconnected (reason 'connection-assumed', sys-iface-state: 'external')
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4523] device (tun1): Activation: starting connection 'tun1' (7f71c4c8-26e3-4984-b6a6-c7e926c37d92)
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4531] device (tun1): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'external')
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4534] device (tun1): state change: prepare -> config (reason 'none', sys-iface-state: 'external')
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4536] device (tun1): state change: config -> ip-config (reason 'none', sys-iface-state: 'external')
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4537] device (tun1): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'external')
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4539] device (tun1): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'external')
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4541] device (tun1): state change: secondaries -> activated (reason 'none', sys-iface-state: 'external')
Apr 03 09:15:32 Kris NetworkManager[919]: <info>  [1554300932.4584] device (tun1): Activation: successful, device activated.
Apr 03 09:16:03 Kris NetworkManager[919]: <info>  [1554300963.1164] connectivity: (tun1) timed out
qhisotryApr 03 09:16:12 Kris nm-openvpn[20087]: [dal-a06.ipvanish.com] Inactivity timeout (--ping-restart), restarting
Apr 03 09:16:12 Kris nm-openvpn[20087]: SIGUSR1[soft,ping-restart] received, process restarting
^XApr 03 09:16:17 Kris nm-openvpn[20087]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Apr 03 09:16:17 Kris nm-openvpn[20087]: TCP/UDP: Preserving recently used remote address: [AF_INET]209.107.216.4:443
Apr 03 09:16:17 Kris nm-openvpn[20087]: UDP link local: (not bound)
Apr 03 09:16:17 Kris nm-openvpn[20087]: UDP link remote: [AF_INET]209.107.216.4:443
Apr 03 09:16:17 Kris nm-openvpn[20087]: [dal-a06.ipvanish.com] Peer Connection Initiated with [AF_INET]209.107.216.4:443
Apr 03 09:16:18 Kris nm-openvpn[20087]: Option 'explicit-exit-notify' in [PUSH-OPTIONS]:6 is ignored by previous <connection> blocks
Apr 03 09:16:18 Kris nm-openvpn[20087]: Preserving previous TUN/TAP instance: tun1
Apr 03 09:16:18 Kris nm-openvpn[20087]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper --debug 0 20081 --bus-name org.freedesktop.NetworkManager.openvpn.Connection_23 --tun -- tun1 1500 1553 172.21.22.43 255.255.254.0 restart
Apr 03 09:16:18 Kris nm-openvpn[20087]: WARNING: Failed running command (--up/--down): could not execute external program
Apr 03 09:16:18 Kris nm-openvpn[20087]: Exiting due to fatal error
Apr 03 09:16:18 Kris NetworkManager[919]: <info>  [1554300978.9106] device (tun1): state change: activated -> unmanaged (reason 'unmanaged', sys-iface-state: 'removed')
Apr 03 09:16:18 Kris NetworkManager[919]: <info>  [1554300978.9177] devices removed (path: /sys/devices/virtual/net/tun1, iface: tun1)
Apr 03 09:16:18 Kris NetworkManager[919]: <warn>  [1554300978.9300] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: VPN plugin: failed: connect-failed (1)
Apr 03 09:16:18 Kris NetworkManager[919]: <info>  [1554300978.9301] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13tun1)]: VPN plugin: state changed: stopping (5)
Apr 03 09:16:18 Kris NetworkManager[919]: <info>  [1554300978.9301] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",13:(tun1)]: VPN plugin: state changed: stopped (6)
Apr 03 09:16:18 Kris NetworkManager[919]: <info>  [1554300978.9379] vpn-connection[0x5650752f63b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",0]: VPN service disappeared
^C
kris@Kris:/$ ifconfig
enp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.0.189  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 2604:3d09:a581:400:49d3:7f68:ac3b:6e0e  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::5065:835:124c:2634  prefixlen 64  scopeid 0x20<link>
        inet6 2604:3d09:a581:400:7c34:6aaa:f955:978a  prefixlen 64  scopeid 0x0<global>
        inet6 2604:3d09:a581:400::4c52  prefixlen 128  scopeid 0x0<global>
        ether b4:2e:99:1c:08:96  txqueuelen 1000  (Ethernet)
        RX packets 656169  bytes 837168308 (837.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 367520  bytes 52917754 (52.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 8595  bytes 891101 (891.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8595  bytes 891101 (891.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 172.21.21.79  netmask 255.255.254.0  destination 172.21.21.79
        inet6 fe80::4d79:4450:5c63:1e75  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 580549  bytes 724460031 (724.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 317614  bytes 23871910 (23.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


kris@Kris:/$ ping [www.google.com]("http://www.google.com")
PING [www.google.com(lga25s60-in-x04.1e100.net]("http://www.google.com(lga25s60-in-x04.1e100.net") (2607:f8b0:4006:814::2004)) 56 data bytes
64 bytes from lga25s60-in-x04.1e100.net (2607:f8b0:4006:814::2004): icmp_seq=1 ttl=53 time=42.7 ms
64 bytes from lga25s60-in-x04.1e100.net (2607:f8b0:4006:814::2004): icmp_seq=2 ttl=53 time=43.1 ms
64 bytes from lga25s60-in-x04.1e100.net (2607:f8b0:4006:814::2004): icmp_seq=3 ttl=53 time=42.0 ms
64 bytes from lga25s60-in-x04.1e100.net (2607:f8b0:4006:814::2004): icmp_seq=4 ttl=53 time=42.1 ms
64 bytes from lga25s60-in-x04.1e100.net (2607:f8b0:4006:814::2004): icmp_seq=5 ttl=53 time=42.7 ms
64 bytes from lga25s60-in-x04.1e100.net (2607:f8b0:4006:814::2004): icmp_seq=6 ttl=53 time=43.6 ms
^C
--- [www.google.com]("http://www.google.com") ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5006ms
rtt min/avg/max/mdev = 42.042/42.749/43.637/0.604 ms
kris@Kris:/$ ping [www.facebook.com]("http://www.facebook.com")
PING [www.facebook.com(edge-star-mini6-shv-01-atl3.facebook.com]("http://www.facebook.com(edge-star-mini6-shv-01-atl3.facebook.com") (2a03:2880:f111:83:face:b00c:0:25de)) 56 data bytes
64 bytes from edge-star-mini6-shv-01-atl3.facebook.com (2a03:2880:f111:83:face:b00c:0:25de): icmp_seq=1 ttl=54 time=45.3 ms
64 bytes from edge-star-mini6-shv-01-atl3.facebook.com (2a03:2880:f111:83:face:b00c:0:25de): icmp_seq=2 ttl=54 time=43.9 ms
64 bytes from edge-star-mini6-shv-01-atl3.facebook.com (2a03:2880:f111:83:face:b00c:0:25de): icmp_seq=3 ttl=54 time=44.0 ms
64 bytes from edge-star-mini6-shv-01-atl3.facebook.com (2a03:2880:f111:83:face:b00c:0:25de): icmp_seq=4 ttl=54 time=44.6 ms
64 bytes from edge-star-mini6-shv-01-atl3.facebook.com (2a03:2880:f111:83:face:b00c:0:25de): icmp_seq=5 ttl=54 time=44.5 ms
64 bytes from edge-star-mini6-shv-01-atl3.facebook.com (2a03:2880:f111:83:face:b00c:0:25de): icmp_seq=6 ttl=54 time=43.6 ms
64 bytes from edge-star-mini6-shv-01-atl3.facebook.com (2a03:2880:f111:83:face:b00c:0:25de): icmp_seq=7 ttl=54 time=45.8 ms
64 bytes from edge-star-mini6-shv-01-atl3.facebook.com (2a03:2880:f111:83:face:b00c:0:25de): icmp_seq=8 ttl=54 time=43.9 ms
^C
--- [www.facebook.com]("http://www.facebook.com") ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7009ms
rtt min/avg/max/mdev = 43.625/44.503/45.825/0.715 ms
kris@Kris:/$ ifconfig
enp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.0.189  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 2604:3d09:a581:400:49d3:7f68:ac3b:6e0e  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::5065:835:124c:2634  prefixlen 64  scopeid 0x20<link>
        inet6 2604:3d09:a581:400:7c34:6aaa:f955:978a  prefixlen 64  scopeid 0x0<global>
        inet6 2604:3d09:a581:400::4c52  prefixlen 128  scopeid 0x0<global>
        ether b4:2e:99:1c:08:96  txqueuelen 1000  (Ethernet)
        RX packets 657329  bytes 838277292 (838.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 368432  bytes 53097587 (53.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 8667  bytes 898045 (898.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8667  bytes 898045 (898.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 172.21.21.79  netmask 255.255.254.0  destination 172.21.21.79
        inet6 fe80::4d79:4450:5c63:1e75  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 581455  bytes 725430216 (725.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 318358  bytes 23966456 (23.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


tun1: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 172.21.25.177  netmask 255.255.254.0  destination 172.21.25.177
        inet6 fe80::896f:9ce9:73f1:7a4d  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 9  bytes 492 (492.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


kris@Kris:/$ journalctl -f -u NetworkManager
-- Logs begin at Wed 2019-01-23 14:24:28 CST. --
Apr 03 09:26:10 Kris nm-openvpn[20828]: Preserving previous TUN/TAP instance: tun1
Apr 03 09:26:10 Kris nm-openvpn[20828]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper --debug 0 20822 --bus-name org.freedesktop.NetworkManager.openvpn.Connection_25 --tun -- tun1 1500 1553 172.21.25.177 255.255.254.0 restart
Apr 03 09:26:10 Kris nm-openvpn[20828]: WARNING: Failed running command (--up/--down): could not execute external program
Apr 03 09:26:10 Kris nm-openvpn[20828]: Exiting due to fatal error
Apr 03 09:26:10 Kris NetworkManager[919]: <info>  [1554301570.3222] device (tun1): state change: activated -> unmanaged (reason 'unmanaged', sys-iface-state: 'removed')
Apr 03 09:26:10 Kris NetworkManager[919]: <info>  [1554301570.3277] devices removed (path: /sys/devices/virtual/net/tun1, iface: tun1)
Apr 03 09:26:10 Kris NetworkManager[919]: <warn>  [1554301570.3444] vpn-connection[0x5650752f61b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",14tun1)]: VPN plugin: failed: connect-failed (1)
Apr 03 09:26:10 Kris NetworkManager[919]: <info>  [1554301570.3444] vpn-connection[0x5650752f61b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",14tun1)]: VPN plugin: state changed: stopping (5)
Apr 03 09:26:10 Kris NetworkManager[919]: <info>  [1554301570.3444] vpn-connection[0x5650752f61b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",14:(tun1)]: VPN plugin: state changed: stopped (6)
Apr 03 09:26:10 Kris NetworkManager[919]: <info>  [1554301570.3524] vpn-connection[0x5650752f61b0,dcff9b1e-1f4e-4516-bb9d-90d483953ba1,"ipvanish-US-Dallas-dal-a06",0]: VPN service disappeared
^C
kris@Kris:/$ ping [www.yahoo.com]("http://www.yahoo.com")
PING [www.yahoo.com(media-router-fp1.prod1.media.vip.bf1.yahoo.com]("http://www.yahoo.com(media-router-fp1.prod1.media.vip.bf1.yahoo.com") (2001:4998:58:1836::10)) 56 data bytes
64 bytes from media-router-fp1.prod1.media.vip.bf1.yahoo.com (2001:4998:58:1836::10): icmp_seq=1 ttl=54 time=36.9 ms
64 bytes from media-router-fp1.prod1.media.vip.bf1.yahoo.com (2001:4998:58:1836::10): icmp_seq=2 ttl=54 time=37.9 ms
^C
--- [www.yahoo.com]("http://www.yahoo.com") ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 36.943/37.449/37.955/0.506 ms

---

### Post by TheFu on 2019-04-03
Please wrap log and cmd output using "code tags" to make things readable. - my sig has a redirection link about this.

I do things differently.  I'm on 16.04, don't have any IPv6 enabled, don't use network-manager, only start VPNs using a shell script and have never used ip-vanish. With all that said, I have a few things you can try and look into.

Looks like you have IPv6 enabled. [https://community.openvpn.net/openvpn/wiki/IPv6](https://community.openvpn.net/openvpn/wiki/IPv6) Looks like your setup is mixed with ifup/ifdown expected, but not existing. I don't know if this matters or not.

First thing in asking questions here is to always include the specific ubuntu release being used.  Networking has changed over the last 10 yrs with each release changing something important.

---

