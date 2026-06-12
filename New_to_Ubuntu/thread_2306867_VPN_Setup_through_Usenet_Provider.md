---
title: "VPN Setup through Usenet Provider"
date: 2015-12-19
forum: New to Ubuntu
---

### Post by eddiefiggie on 2015-12-19
My Usenet provider offers a VPN service that I've been attempting to configure.  Following their instructions, i get as far as importing the .ovpn file thorugh the network manager but none of the keys import with it.  Then i came by this:  [https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/606365](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/606365)

So the above sounds like a bug within the Network Manager.

Moving along...

Following that bug thread everyone seemed to be working fin using the command line:

```
sudo openvpn --config client.ovpn
```

I did the same, and it all started to connect up perfectly following me applying my credentials.  Then it barfs out with the following:

> user@system:~/Documents$ sudo openvpn --config '/home/user/Documents/lon-a01.ovpn' 
Sat Dec 19 12:14:53 2015 OpenVPN 2.3.7 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jul  8 2015
Sat Dec 19 12:14:53 2015 library versions: OpenSSL 1.0.2d 9 Jul 2015, LZO 2.08
Enter Auth Username: ***************
Enter Auth Password: ***************
Sat Dec 19 12:15:03 2015 Socket Buffers: R=[212992->131072] S=[212992->131072]
Sat Dec 19 12:15:03 2015 UDPv4 link local: [undef]
Sat Dec 19 12:15:03 2015 UDPv4 link remote: [AF_INET]81.171.97.65:1194
Sat Dec 19 12:15:03 2015 TLS: Initial packet from [AF_INET]81.171.97.65:1194, sid=cdc0e81e 7548bc29
Sat Dec 19 12:15:03 2015 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Sat Dec 19 12:15:04 2015 VERIFY OK: depth=1, C=US, ST=VPN, L=VPN, O=VPN, OU=VPN, CN=VPN, name=VPN, emailAddress=VPN
Sat Dec 19 12:15:04 2015 Validating certificate key usage
Sat Dec 19 12:15:04 2015 ++ Certificate has key usage  00a0, expects 00a0
Sat Dec 19 12:15:04 2015 VERIFY KU OK
Sat Dec 19 12:15:04 2015 Validating certificate extended key usage
Sat Dec 19 12:15:04 2015 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
Sat Dec 19 12:15:04 2015 VERIFY EKU OK
Sat Dec 19 12:15:04 2015 VERIFY OK: depth=0, C=US, ST=VPN, L=VPN, O=VPN, OU=VPN, CN=vpn, name=VPN
Sat Dec 19 12:15:11 2015 Data Channel Encrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Sat Dec 19 12:15:11 2015 Data Channel Encrypt: Using 256 bit message hash 'SHA256' for HMAC authentication
Sat Dec 19 12:15:11 2015 Data Channel Decrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Sat Dec 19 12:15:11 2015 Data Channel Decrypt: Using 256 bit message hash 'SHA256' for HMAC authentication
Sat Dec 19 12:15:11 2015 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Sat Dec 19 12:15:11 2015 [vpn] Peer Connection Initiated with [AF_INET]81.171.97.65:1194
Sat Dec 19 12:15:13 2015 SENT CONTROL [vpn]: 'PUSH_REQUEST' (status=1)
Sat Dec 19 12:15:13 2015 AUTH: Received control message: AUTH_FAILED
Sat Dec 19 12:15:13 2015 SIGTERM[soft,auth-failure] received, process exiting



Can someone help?


EDIT::

This is interesting.  I found this possible work around:  [http://howto.praqma.net/ubuntu/vpn/openvpn-access-server-client-on-ubuntu](http://howto.praqma.net/ubuntu/vpn/openvpn-access-server-client-on-ubuntu)

When I open my client.ovpn file provided by my service provider it is missing <key>, <cert>, and <tls-auth> tags...  Is this normal?  it does contain the <ca> tags however.

---

### Post by sandyd on 2015-12-19
IPVanish (your VPN provider) has published new instructions that include the separate CA file instead of embedding it in the config

See [https://www.ipvanish.com/visualguides/OpenVPN/Ubuntu/](https://www.ipvanish.com/visualguides/OpenVPN/Ubuntu/)

---

### Post by eddiefiggie on 2015-12-19
I suppose the VPN can be provided by another company...  But it's offered by newshosting.com.  What leads you to beleive it is IPVanish?  before I follow the guide, i figured I best touble check.

---

### Post by sandyd on 2015-12-19
> user@system:~/Documents$ sudo openvpn --config '/home/user/Documents/lon-a01.ovpn' 
Sat Dec 19 12:14:53 2015 OpenVPN 2.3.7 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jul  8 2015
Sat Dec 19 12:14:53 2015 library versions: OpenSSL 1.0.2d 9 Jul 2015, LZO 2.08
Enter Auth Username: ***************
Enter Auth Password: ***************
Sat Dec 19 12:15:03 2015 Socket Buffers: R=[212992->131072] S=[212992->131072]
Sat Dec 19 12:15:03 2015 UDPv4 link local: [undef]
Sat Dec 19 12:15:03 2015 UDPv4 link remote: [AF_INET][COLOR="#FF0000"]81.171.97.65[/COLOR]:1194
Sat Dec 19 12:15:03 2015 TLS: Initial packet from [AF_INET][COLOR="#FF0000"]81.171.97.65[/COLOR]:1194, sid=cdc0e81e 7548bc29
Sat Dec 19 12:15:03 2015 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Sat Dec 19 12:15:04 2015 VERIFY OK: depth=1, C=US, ST=VPN, L=VPN, O=VPN, OU=VPN, CN=VPN, name=VPN, emailAddress=VPN
Sat Dec 19 12:15:04 2015 Validating certificate key usage
Sat Dec 19 12:15:04 2015 ++ Certificate has key usage  00a0, expects 00a0
Sat Dec 19 12:15:04 2015 VERIFY KU OK
Sat Dec 19 12:15:04 2015 Validating certificate extended key usage
Sat Dec 19 12:15:04 2015 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
Sat Dec 19 12:15:04 2015 VERIFY EKU OK
Sat Dec 19 12:15:04 2015 VERIFY OK: depth=0, C=US, ST=VPN, L=VPN, O=VPN, OU=VPN, CN=vpn, name=VPN
Sat Dec 19 12:15:11 2015 Data Channel Encrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Sat Dec 19 12:15:11 2015 Data Channel Encrypt: Using 256 bit message hash 'SHA256' for HMAC authentication
Sat Dec 19 12:15:11 2015 Data Channel Decrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Sat Dec 19 12:15:11 2015 Data Channel Decrypt: Using 256 bit message hash 'SHA256' for HMAC authentication
Sat Dec 19 12:15:11 2015 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Sat Dec 19 12:15:11 2015 [vpn] Peer Connection Initiated with [AF_INET][COLOR="#FF0000"]81.171.97.65[/COLOR]:1194
Sat Dec 19 12:15:13 2015 SENT CONTROL [vpn]: 'PUSH_REQUEST' (status=1)
Sat Dec 19 12:15:13 2015 AUTH: Received control message: AUTH_FAILED
Sat Dec 19 12:15:13 2015 SIGTERM[soft,auth-failure] received, process exiting


Going through some VPN server lists, your IP shows up [here]("https://github.com/Luen/IPVanish-Server-List/blob/master/ipvanish-allowlist.txt")

```

$ dig lon-a01.wlvpn.com

; <<>> DiG 9.8.3-P1 <<>> lon-a01.wlvpn.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15570
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;lon-a01.wlvpn.com.		IN	A

;; ANSWER SECTION:
lon-a01.wlvpn.com.	900	IN	A	81.171.97.65

;; Query time: 38 msec
;; SERVER: 192.168.2.2#53(192.168.2.2)
;; WHEN: Sat Dec 19 17:30:51 2015
;; MSG SIZE  rcvd: 51
```
Go to [http://wlvpn.com](http://wlvpn.com), you will see it is owned by ipvanish

---

### Post by eddiefiggie on 2015-12-19
Following those instructions I get a VPN failed to connect.  "missing VPN secrets" hehe Strange error message.

---

### Post by sandyd on 2015-12-19
Have you tried using the file directly?
i.e.
```

sudo openvpn --config /path/to/file
```

---

