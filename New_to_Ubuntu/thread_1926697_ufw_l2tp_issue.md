---
title: "ufw l2tp issue"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by 4traveler on 2012-02-16
I am somewhat new to Ubuntu, a little familiar, but still a beginner.  I recently installed openswan (v 2.6.37 [I think]) & l2tp VPN on Ubuntu 10.04.  Took me a while to get the configuration right by researching it on the net.  I got it working fine, except for the ufw rules.  I have added the following ufw rules:
50/tcp                     ALLOW       Anywhere
500/udp                    ALLOW       Anywhere
4500/udp                   ALLOW       Anywhere
1701/udp                   ALLOW       Anywhere

If I disable the ufw I can get in, connect and work normally, but when enabled I keep getting these error messages in the /var/log/messages file:
Feb 15 19:07:30 Ubuntu-Share kernel: [270428.761722] [UFW BLOCK] IN=eth0 OUT= MAC=00:1b:fc:9c:4b:fe:00:22:43:7f:41:f7:08:00 SRC=10.10.10.73 DST=10.10.10.68 LEN=168 TOS=0x00 PREC=0x00 TTL=128 ID=25938 PROTO=ESP SPI=0xc02ebf69
Feb 15 19:07:56 Ubuntu-Share kernel: [270454.395533] [UFW BLOCK] IN=eth0 OUT= MAC=00:1b:fc:9c:4b:fe:00:22:43:7f:41:f7:08:00 SRC=10.10.10.73 DST=10.10.10.68 LEN=168 TOS=0x00 PREC=0x00 TTL=128 ID=25947 PROTO=ESP SPI=0x787364a7
Feb 15 19:08:11 Ubuntu-Share kernel: [270469.384792] [UFW BLOCK] IN=eth0 OUT= MAC=00:1b:fc:9c:4b:fe:00:22:43:7f:41:f7:08:00 SRC=10.10.10.73 DST=10.10.10.68 LEN=168 TOS=0x00 PREC=0x00 TTL=128 ID=25951 PROTO=ESP SPI=0x787364a7


and I can NOT connect at all.  The strange part is that if I disable ufw, connect to l2tp, disconnect, enable ufw and try to connect again I CAN connect for a while.  After a couple of connection tries I start seeing above error messages, but can still connect.  If I wait a while (tried next day) then I can NOT connect anymore unless I disable ufw, connect, disconnect and enable ufw again.

I tried adding the rules for ESP protocol like similar to this:
ufw allow to 10.0.0.1 proto esp
I keep getting an error message that the command is invalid.

Any idea what rule I need to add or what I need to do to get ufw to behave properly and let the traffic through?  I've spent hours looking online and have not found any suggestions that work.  Would appreciate any help.

---

### Post by lechien73 on 2012-02-17
Hi and welcome to the forums,

What version of Ubuntu are you running and - specifically - what version of ufw?

There was a bug [recorded here]("https://bugs.launchpad.net/ufw/+bug/606997"), where ufw would block the esp protocol. You can check what version of ufw you're running by opening a terminal window and typing:

```
ufw --version
```

You need to have 0.30.0-1 or above.

---

### Post by 4traveler on 2012-02-18
My versions are:
[FONT=Courier New][SIZE=2]$ ufw --version
ufw 0.30pre1-0ubuntu2
Copyright 2008-2010 Canonical Ltd.
$ uname -r
2.6.32-31-generic
$ uname -v
#61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011[/SIZE][/FONT]

  I was not sure if the ufw was the latest or not so I ran a sudo apt-get upgrade ufw command.  It ran for a while, but afterwards I am still at the same version.  So I guess I have the latest version.  Seems like I'm missing a rule, but not sure for what.:(

---

### Post by 4traveler on 2012-02-21
Well it keeps getting worse.  I was searching online for help.  Came across some pages that indicated the original version on l2tp that comes with Ubuntu has some bugs & needed to be upgraded.  I saved my configs.  Upgraded the xl2tp to the latest version 1.2.8, restarted xl2tp.  Could not connect.  Verified my configs.  They are all the same as before.  Disabled firewall, still could not connect.  I've played around with the config files for hours and tried all kinds of variations no luck with or without firewall.  All I get is:
"L2TP"[5] 10.10.10.71 #543: received Delete SA(0xe6e29c6f) payload: deleting IPSEC State #547
"L2TP"[5] 10.10.10.71 #543: received and ignored informational message
"L2TP"[5] 10.10.10.71 #543: the peer proposed: 10.10.10.68/32:17/1701 -> 10.10.10.71/32:17/1701
"L2TP"[5] 10.10.10.71 #543: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
"L2TP"[5] 10.10.10.71 #549: responding to Quick Mode proposal {msgid:06000000}
"L2TP"[5] 10.10.10.71 #549:     us: 10.10.10.68<10.10.10.68>[+S=C]:17/1701---10.10.10.65
"L2TP"[5] 10.10.10.71 #549:   them: 10.10.10.71[+S=C]:17/1701
"L2TP"[5] 10.10.10.71 #549: keeping refhim=4294901761 during rekey
"L2TP"[5] 10.10.10.71 #549: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
"L2TP"[5] 10.10.10.71 #549: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
"L2TP"[5] 10.10.10.71 #549: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
"L2TP"[5] 10.10.10.71 #549: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
"L2TP"[5] 10.10.10.71 #549: STATE_QUICK_R2: IPsec SA established transport mode {ESP/NAT=>0x410c0546 <0x4c2dd011 xfrm=AES_128-HMAC_SHA1 NATOA=10.10.10.71 NATD=10.10.10.71:4500 DPD=none}
"L2TP"[5] 10.10.10.71 #543: received Delete SA(0xc739013d) payload: deleting IPSEC State #548
"L2TP"[5] 10.10.10.71 #543: received and ignored informational message
"L2TP"[5] 10.10.10.71 #543: received Delete SA(0x410c0546) payload: deleting IPSEC State #549
"L2TP"[5] 10.10.10.71 #543: received and ignored informational message
"L2TP"[5] 10.10.10.71 #543: received Delete SA payload: deleting ISAKMP State #543
"L2TP"[5] 10.10.10.71: deleting connection "L2TP" instance with peer 10.10.10.71 {isakmp=#0/ipsec=#0}
packet from 10.10.10.71:4500: received and ignored informational message


  Are these guys getting lessons from Microsoft or what?  ](*,)

---

### Post by 4traveler on 2012-03-13
No replies.  This is more help than I can handle. :)  There is definitely a big bug in ufw (or in my case it is a cfw).
Well I added the following two firewall rules:
[FONT=Courier New]Anywhere/tcp               ALLOW       Anywhere/tcp
Anywhere/udp               ALLOW       Anywhere/udp[/FONT]

And guess what?  It still does NOT work unless I disable the firewall.  Two weeks now and no help.  Anybody out there.  ](*,)](*,)](*,)

---

