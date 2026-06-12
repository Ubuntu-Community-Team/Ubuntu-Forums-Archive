---
title: "OpenVPN on Ubuntu 12.04"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by Houmie on 2013-03-25
Hi there,

I have setup a VPN server on my Ec2 instance successfully and can see ifconfig tun0.  The port 1194 is also free.

However my client can't access the server.  I have already created the certificates. Somehow the handshake fails and i dont understand why.

On the server log, I can see the incoming call from my client. So the port is perfectly fine.

Can a pro help me please?


```
Mon Mar 25 06:52:55 2013 OpenVPN 2.2.1 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Oct  8 2012
Mon Mar 25 06:52:55 2013 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Mon Mar 25 06:52:55 2013 LZO compression initialized
Mon Mar 25 06:52:55 2013 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Mon Mar 25 06:52:55 2013 Socket Buffers: R=[212992->131072] S=[212992->131072]
Mon Mar 25 06:52:55 2013 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Mon Mar 25 06:52:55 2013 Local Options hash (VER=V4): '41690919'
Mon Mar 25 06:52:55 2013 Expected Remote Options hash (VER=V4): '530fdded'
Mon Mar 25 06:52:55 2013 UDPv4 link local: [undef]
Mon Mar 25 06:52:55 2013 UDPv4 link remote: [AF_INET]107.21.249.172:1194
Mon Mar 25 06:52:56 2013 TLS: Initial packet from [AF_INET]107.21.249.172:1194, sid=dfd84013 f1883b8a
Mon Mar 25 06:53:55 2013 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Mon Mar 25 06:53:55 2013 TLS Error: TLS handshake failed
Mon Mar 25 06:53:55 2013 TCP/UDP: Closing socket
Mon Mar 25 06:53:55 2013 SIGUSR1[soft,tls-error] received, process restarting
Mon Mar 25 06:53:55 2013 Restart pause, 2 second(s)
Mon Mar 25 06:53:57 2013 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Mon Mar 25 06:53:57 2013 Re-using SSL/TLS context
Mon Mar 25 06:53:57 2013 LZO compression initialized
Mon Mar 25 06:53:57 2013 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Mon Mar 25 06:53:57 2013 Socket Buffers: R=[212992->131072] S=[212992->131072]
Mon Mar 25 06:53:57 2013 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Mon Mar 25 06:53:57 2013 Local Options hash (VER=V4): '41690919'
Mon Mar 25 06:53:57 2013 Expected Remote Options hash (VER=V4): '530fdded'
Mon Mar 25 06:53:57 2013 UDPv4 link local: [undef]
Mon Mar 25 06:53:57 2013 UDPv4 link remote: [AF_INET]107.21.249.172:1194
Mon Mar 25 06:53:57 2013 TLS: Initial packet from [AF_INET]107.21.249.172:1194, sid=fbbd3714 03d9e3bf



grep -i vpn /var/log/syslog

Mar 25 06:50:29 tp ovpn-client[1757]: SIGUSR1[soft,tls-error] received, process restarting
Mar 25 06:50:29 tp ovpn-client[1757]: Restart pause, 2 second(s)
Mar 25 06:50:31 tp ovpn-client[1757]: NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Mar 25 06:50:31 tp ovpn-client[1757]: Re-using SSL/TLS context
Mar 25 06:50:31 tp ovpn-client[1757]: LZO compression initialized
Mar 25 06:50:31 tp ovpn-client[1757]: Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Mar 25 06:50:31 tp ovpn-client[1757]: Socket Buffers: R=[212992->131072] S=[212992->131072]
Mar 25 06:50:31 tp ovpn-client[1757]: Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Mar 25 06:50:31 tp ovpn-client[1757]: Local Options hash (VER=V4): '41690919'
Mar 25 06:50:31 tp ovpn-client[1757]: Expected Remote Options hash (VER=V4): '530fdded'
Mar 25 06:50:31 tp ovpn-client[1757]: UDPv4 link local: [undef]
Mar 25 06:50:31 tp ovpn-client[1757]: UDPv4 link remote: [AF_INET]107.21.249.172:1194
Mar 25 06:50:32 tp ovpn-client[1757]: TLS: Initial packet from [AF_INET]107.21.249.172:1194, sid=2f118173 6fcb3803
Mar 25 06:51:31 tp ovpn-client[1757]: TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Mar 25 06:51:31 tp ovpn-client[1757]: TLS Error: TLS handshake failed
Mar 25 06:51:31 tp ovpn-client[1757]: TCP/UDP: Closing socket
Mar 25 06:51:31 tp ovpn-client[1757]: SIGUSR1[soft,tls-error] received, process restarting
Mar 25 06:51:31 tp ovpn-client[1757]: Restart pause, 2 second(s)
Mar 25 06:51:33 tp ovpn-client[1757]: NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Mar 25 06:51:33 tp ovpn-client[1757]: Re-using SSL/TLS context
Mar 25 06:51:33 tp ovpn-client[1757]: LZO compression initialized
Mar 25 06:51:33 tp ovpn-client[1757]: Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Mar 25 06:51:33 tp ovpn-client[1757]: Socket Buffers: R=[212992->131072] S=[212992->131072]
Mar 25 06:51:33 tp ovpn-client[1757]: Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Mar 25 06:51:33 tp ovpn-client[1757]: Local Options hash (VER=V4): '41690919'
Mar 25 06:51:33 tp ovpn-client[1757]: Expected Remote Options hash (VER=V4): '530fdded'
Mar 25 06:51:33 tp ovpn-client[1757]: UDPv4 link local: [undef]
Mar 25 06:51:33 tp ovpn-client[1757]: UDPv4 link remote: [AF_INET]107.21.249.172:1194
Mar 25 06:51:34 tp ovpn-client[1757]: TLS: Initial packet from [AF_INET]107.21.249.172:1194, sid=8add2908 4270be64
```

---

### Post by Adi Krishnan on 2013-03-25
Hi, 

Seems to me like a TLS Handshake issue.

```
Mar 25 06:51:31 tp ovpn-client[1757]: TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Mar 25 06:51:31 tp ovpn-client[1757]: TLS Error: TLS handshake failed
```

Try this on the client browser: 

```
openssl s_client -connect host:port -tls1
```

If you are able to connect, I'm not sure what could be the problem but if you aren't, certainly your browser is sending TLSv1 encryption but your server cannot handle it. To confirm that you can try these:

```

openssl s_client -connect host:port -ssl3
openssl s_client -connect host:port -ssl2
```

Where the browser will try to connect using SSLv3 and SSLv2 encryption respectively.

Hope this helps.

---

### Post by Houmie on 2013-03-25
Thanks for you replay.

What is s_client in this context? And do you mean running this on the terminal right?

```
openssl s_client -connect host:port -tls1


```

---

