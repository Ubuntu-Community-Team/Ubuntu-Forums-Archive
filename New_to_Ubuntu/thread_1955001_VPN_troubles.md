---
title: "VPN troubles"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by modernknight91 on 2012-04-09
Hey all, I'm fairly new to Ubuntu (hence my posting in here). I've been trying to connect to my VPN for hours now, and no matter what I try, the connection always fails. It's not a router problem because I tried it on my Win7 PC and it connected just fine (yes, I disconnected before trying to reconnect through Ubuntu :p). I've tried every one of the VPN company's tutorials as well as numerous Ubuntu forum threads, and can't seem to find a solution. I've checked the password, username, and gateway a million times. Even copied and pasted them. I'm running 12.04 LTS. Thanks so much for your help!

Exact issue: I create my VPN connection, connect to it, the wifi symbol will flash the lock for about 30 seconds, and then a window pops up saying that the connection has failed. Gives no reason.

---

### Post by mojorising on 2012-04-09
Hi, there. 

In order to help, we would need to know what type of VPN you are connecting to. Can you tell us that? 

You might be able to see error messages on the connection attempt by typing the following at the command line:
```

sudo tail -n 50 -f /var/log/syslog

```

Leave that command line window up and try connecting to the VPN. Then go back to your command console and see if any error messages related to the VPN have printed there. That might point you in the right direction. 

It's also important to consider the fact you are running beta software. It is possible you are running into a bug. The tutorials may not completely apply to this new version as well. 


Hope that helps!
Mike

---

### Post by modernknight91 on 2012-04-09
I'm running a PPTP VPN (trying to at least hah)

```
Apr  9 17:03:49 daniel NetworkManager[911]: <info> Starting VPN service 'pptp'...
Apr  9 17:03:49 daniel NetworkManager[911]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 2554
Apr  9 17:03:49 daniel NetworkManager[911]: <info> VPN service 'pptp' appeared; activating connections
Apr  9 17:03:49 daniel NetworkManager[911]: <info> VPN plugin state changed: init (1)
Apr  9 17:03:49 daniel NetworkManager[911]: <info> VPN plugin state changed: starting (3)
Apr  9 17:03:50 daniel NetworkManager[911]: <info> VPN connection 'StrongVPN3' (Connect) reply received.
Apr  9 17:03:50 daniel pppd[2558]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Apr  9 17:03:50 daniel pppd[2558]: pppd 2.4.5 started by root, uid 0
Apr  9 17:03:50 daniel pppd[2558]: Using interface ppp0
Apr  9 17:03:50 daniel pppd[2558]: Connect: ppp0 <--> /dev/pts/2
Apr  9 17:03:50 daniel pptp[2561]: nm-pptp-service-2554 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Apr  9 17:03:50 daniel NetworkManager[911]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr  9 17:03:50 daniel NetworkManager[911]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Apr  9 17:03:50 daniel pptp[2569]: nm-pptp-service-2554 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Apr  9 17:03:51 daniel pptp[2569]: nm-pptp-service-2554 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Apr  9 17:03:51 daniel pptp[2569]: nm-pptp-service-2554 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Apr  9 17:03:51 daniel pptp[2569]: nm-pptp-service-2554 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Apr  9 17:03:52 daniel pptp[2569]: nm-pptp-service-2554 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Apr  9 17:03:52 daniel pptp[2569]: nm-pptp-service-2554 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 54473).
Apr  9 17:04:21 daniel pppd[2558]: LCP: timeout sending Config-Requests
Apr  9 17:04:21 daniel pppd[2558]: Connection terminated.
Apr  9 17:04:21 daniel avahi-daemon[913]: Withdrawing workstation service for ppp0.
Apr  9 17:04:21 daniel NetworkManager[911]: <warn> VPN plugin failed: 1
Apr  9 17:04:21 daniel NetworkManager[911]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr  9 17:04:21 daniel pppd[2558]: Modem hangup
Apr  9 17:04:21 daniel pptp[2561]: nm-pptp-service-2554 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Apr  9 17:04:21 daniel pptp[2561]: nm-pptp-service-2554 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Apr  9 17:04:21 daniel pppd[2558]: Exit.
Apr  9 17:04:21 daniel NetworkManager[911]: <warn> VPN plugin failed: 1
Apr  9 17:04:21 daniel NetworkManager[911]: <warn> VPN plugin failed: 1
Apr  9 17:04:21 daniel NetworkManager[911]: <info> VPN plugin state changed: stopped (6)
Apr  9 17:04:21 daniel NetworkManager[911]: <info> VPN plugin state change reason: 0
Apr  9 17:04:21 daniel pptp[2569]: nm-pptp-service-2554 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Apr  9 17:04:21 daniel pptp[2569]: nm-pptp-service-2554 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Apr  9 17:04:21 daniel pptp[2569]: nm-pptp-service-2554 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Apr  9 17:04:21 daniel NetworkManager[911]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Apr  9 17:04:21 daniel NetworkManager[911]: <info> Policy set 'Petoria 1' (wlan0) as default for IPv4 routing and DNS.
Apr  9 17:04:26 daniel NetworkManager[911]: <info> VPN service 'pptp' disappeared

```

---

