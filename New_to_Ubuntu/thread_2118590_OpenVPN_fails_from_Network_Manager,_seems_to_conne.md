---
title: "OpenVPN fails from Network Manager, seems to connect from terminal, but no traffic"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by AlecImpy on 2013-02-21
I'm new to Ubuntu (as in, last week!) and really liking the  system, but am having a real problem getting the OpenVPN connection to  work.
  My system:
  
[LIST]
[*]DELL XPS L702X, 8Gb RAM, tested with both WiFi and wired connection.
[*]Ubuntu 12.10 installed on second internal hard disk, updates are current.
[*]OpenVPN + the Gnome-openvpn network manager added.
[/LIST]
  I have a pre-existing configuration and associated certificates +  keys from my Win7 install, which I have copied first to /home/documents  and then (after a bit of reading around) to /etc/openvpn (using sudo).

  That configuration and key set has been working successfully for several years on Windows (work machines).

  Trying Network Manager first, I created a VPN connection of type  OpenVPN, using Certificates (TLS) mode and specified the server  certificate, my certificate, my key, the static key and set the options to use TAP,  etc., (to match the server config), and set Route only for the resources  on that network.

  I exported the configuration to compare to my original one and the  settings seem to match exactly (although it adds "user openvpn" and  "group openvpn").

  Trying to start the VPN from Network Manager I see the padlock "blink" about 4 times then get a "failed" pop-up message.

  Running the conf from the Terminal using either:
  
```
sudo openvpn --config /etc/openvpn/COPE.conf
```or

```
sudo /etc/init.d/openvpn start COPE
```I get the following output, which *looks* remarkably like the connection log from my Win7 install, but isn't working (I have redacted the IP address and email):


  ```

Mon Feb 18 14:09:56 2013 OpenVPN 2.2.1 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Oct  8 2012
Mon Feb 18 14:09:56 2013 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Mon Feb 18 14:09:56 2013 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Mon Feb 18 14:09:56 2013 Control Channel Authentication: using '/etc/openvpn/hmacf-w.key' as a OpenVPN static key file
Mon Feb 18 14:09:56 2013 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Feb 18 14:09:56 2013 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Feb 18 14:09:56 2013 LZO compression initialized
Mon Feb 18 14:09:56 2013 Control Channel MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ]
Mon Feb 18 14:09:56 2013 Socket Buffers: R=[212992->131072] S=[212992->131072]
Mon Feb 18 14:09:56 2013 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
Mon Feb 18 14:09:56 2013 Local Options hash (VER=V4): '13a273ba'
Mon Feb 18 14:09:56 2013 Expected Remote Options hash (VER=V4): '360696c5'
Mon Feb 18 14:09:56 2013 UDPv4 link local: [undef]
Mon Feb 18 14:09:56 2013 UDPv4 link remote: [AF_INET]62.XXX.XXX.XXX:8991
Mon Feb 18 14:09:56 2013 TLS: Initial packet from [AF_INET]62.XXX.XXX.XXX:8991, sid=c1da4711 85037ca7
Mon Feb 18 14:09:56 2013 VERIFY OK: depth=1, /C=UK/ST=Nottinghamshire/L=Nottingham/O=COPE/CN=COPE-CA/emailAddress=X@Y.com
Mon Feb 18 14:09:56 2013 VERIFY OK: depth=0, /C=UK/ST=Nottinghamshire/O=COPE/CN=server/emailAddress=X@Y.com
Mon Feb 18 14:09:56 2013 Replay-window backtrack occurred [1]
Mon Feb 18 14:09:56 2013 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Feb 18 14:09:56 2013 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Feb 18 14:09:56 2013 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Feb 18 14:09:56 2013 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Feb 18 14:09:56 2013 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Mon Feb 18 14:09:56 2013 [server] Peer Connection Initiated with [AF_INET]62.XXx.XXX.XXX:8991
Mon Feb 18 14:09:58 2013 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Mon Feb 18 14:09:58 2013 PUSH: Received control message: 'PUSH_REPLY,route-gateway dhcp,ping 10,ping-restart 120'
Mon Feb 18 14:09:58 2013 OPTIONS IMPORT: timers and/or timeouts modified
Mon Feb 18 14:09:58 2013 OPTIONS IMPORT: route-related options modified
Mon Feb 18 14:09:58 2013 TUN/TAP device tap0 opened
Mon Feb 18 14:09:58 2013 TUN/TAP TX queue length set to 100
Mon Feb 18 14:09:58 2013 /etc/openvpn/update-resolv-conf tap0 1500 1574   init
Mon Feb 18 14:09:58 2013 Initialization Sequence Completed

```... but no ping to the target network works.


Also, listing ifconfig, there is no sign of the tap0 connection device.


  I have tried using Gufw to add a rule to allow anything from my source server, but that made no difference.


  I have tried commenting out all of the script in update-resolv-conf  (thinking being that I didn't use this in Windows, so maybe not needed  for my connection type?) - but this made no difference.

I have tried to start from scratch with a VM install (on my work PC, in side the LAN the VPN server is on), but this also failed.  The only clear error message I saw on the Syslog in that case was to do with the update-resolv-conf script (which on the VM Ieft untouched).

I have also noticed that OpenVPN seems to start as a service (daemon?) on boot-up, as I am able to execute the sudo openvpn ... stop command, but checking ifconfig first doesn't show any tap0 connection device.

Again tonight if I stop the Daemon version, then try to manually start the connection through Network Manager, I get the following:

```

alec@alec-XPS-L702X:~$ tail -f /var/log/syslog
Feb 21 18:34:15 alec-XPS-L702X ovpn-COPE[1174]: Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Feb 21 18:34:15 alec-XPS-L702X ovpn-COPE[1174]: Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Feb 21 18:34:15 alec-XPS-L702X ovpn-COPE[1174]: Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Feb 21 19:17:01 alec-XPS-L702X CRON[6138]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 21 19:25:39 alec-XPS-L702X ovpn-COPE[1174]: event_wait : Interrupted system call (code=4)
Feb 21 19:25:39 alec-XPS-L702X ovpn-COPE[1174]: TCP/UDP: Closing socket
Feb 21 19:25:39 alec-XPS-L702X ovpn-COPE[1174]: Closing TUN/TAP interface
Feb 21 19:25:39 alec-XPS-L702X NetworkManager[963]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tap0, iface: tap0)
Feb 21 19:25:39 alec-XPS-L702X ovpn-COPE[1174]: /etc/openvpn/update-resolv-conf tap0 1500 1574   init
Feb 21 19:25:39 alec-XPS-L702X ovpn-COPE[1174]: SIGTERM[hard,] received, process exiting
Feb 21 19:26:39 alec-XPS-L702X NetworkManager[963]: <info> Starting VPN service 'openvpn'...
Feb 21 19:26:39 alec-XPS-L702X NetworkManager[963]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 6242
Feb 21 19:26:39 alec-XPS-L702X NetworkManager[963]: <info> VPN service 'openvpn' appeared; activating connections
Feb 21 19:26:39 alec-XPS-L702X NetworkManager[963]: <info> VPN plugin state changed: starting (3)
Feb 21 19:26:39 alec-XPS-L702X NetworkManager[963]: <info> VPN connection 'COPE' (Connect) reply received.
Feb 21 19:26:39 alec-XPS-L702X nm-openvpn[6245]: OpenVPN 2.2.1 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Oct  8 2012
Feb 21 19:26:39 alec-XPS-L702X nm-openvpn[6245]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Feb 21 19:26:39 alec-XPS-L702X nm-openvpn[6245]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Feb 21 19:26:39 alec-XPS-L702X nm-openvpn[6245]: Control Channel Authentication: using '/etc/openvpn/hmacf-w.key' as a OpenVPN static key file
Feb 21 19:26:39 alec-XPS-L702X nm-openvpn[6245]: LZO compression initialized
Feb 21 19:26:39 alec-XPS-L702X nm-openvpn[6245]: UDPv4 link local: [undef]
Feb 21 19:26:39 alec-XPS-L702X nm-openvpn[6245]: UDPv4 link remote: [AF_INET]62.XXX.XXX.XXX:8991
Feb 21 19:26:40 alec-XPS-L702X nm-openvpn[6245]: [server] Peer Connection Initiated with [AF_INET]62.XXX.XXX.XXX:8991
Feb 21 19:26:42 alec-XPS-L702X nm-openvpn[6245]: TUN/TAP device tap0 opened
Feb 21 19:26:42 alec-XPS-L702X nm-openvpn[6245]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper tap0 1500 1574   init
Feb 21 19:26:42 alec-XPS-L702X NetworkManager[963]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tap0, iface: tap0)
Feb 21 19:26:42 alec-XPS-L702X NetworkManager[963]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tap0, iface: tap0): no ifupdown configuration found.
Feb 21 19:26:42 alec-XPS-L702X NetworkManager[963]: <warn> /sys/devices/virtual/net/tap0: couldn't determine device driver; ignoring...
Feb 21 19:26:42 alec-XPS-L702X NetworkManager[963]: <warn> VPN plugin failed: 2
Feb 21 19:26:42 alec-XPS-L702X nm-openvpn[6245]: WARNING: Failed running command (--up/--down): external program exited with error status: 1
Feb 21 19:26:42 alec-XPS-L702X nm-openvpn[6245]: Exiting
Feb 21 19:26:42 alec-XPS-L702X NetworkManager[963]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tap0, iface: tap0)
Feb 21 19:26:42 alec-XPS-L702X NetworkManager[963]: <warn> VPN plugin failed: 1
Feb 21 19:26:42 alec-XPS-L702X NetworkManager[963]: <info> VPN plugin state changed: stopped (6)
Feb 21 19:26:42 alec-XPS-L702X NetworkManager[963]: <info> VPN plugin state change reason: 0
Feb 21 19:26:42 alec-XPS-L702X NetworkManager[963]: <info> Policy set 'mywifi' (wlan0) as default for IPv4 routing and DNS.
Feb 21 19:26:42 alec-XPS-L702X NetworkManager[963]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Feb 21 19:26:47 alec-XPS-L702X NetworkManager[963]: <info> VPN service 'openvpn' disappeared

```I'm stumped.  So far as I can tell I have configured Network Manager  (and my /etc/openvpn/COPE.conf file) correctly to match my server.
  

Is this a problem for 12.10?
  

My server is running ovpn 2.2.2 (on Windows 2003) and I do not explicitly indicate cipher type (uses defaults).


  I've been reading all the other posts for days and  nothing has given a solution (although I've learned a fair amount!)


  All help suggestions very much appreciated.


  Thanks

---

### Post by Seifeddine on 2013-08-12
Hello, i was about to open a new thread but i found this one talking about the same problem. I know it's a little bit old post, but it's the newer one considering this issue and it hasn't been answered. So i wil just dump the pragraph i prepared.
         i'm trying to play around with virtual machines. I set up a  network of VMs accessible via nat gateway (a VM too) and a openvpn.  everything works fine in windows 7. But in ubuntu 13.04 it only works  when i use the terminal (with sudo of course) to connect to the server.
Here is the real problem : when i import the config file to the network  manager it connects to the vpn gateway but no traffic. I found that the  reason of that is a route that gnome network manager adds in the route  table. It is :                 192.168.56.101  my.wifi.router  255.255.255.255 UGH   0      0      0 wlan0 . Mainly gnm is routing all  traffic going to 192.168.56.1 which is my virtual router (using host  only mode) to the wifi interface, after i deleted this route all works  fine.
Now comes the question, why is the network manager adding this route ?? I hope i explained my self clearly with a correct English language.

---

