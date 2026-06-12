---
title: "Consistently unable to connect to PPTP VPN - need help resolving issue"
date: 2013-08-19
forum: New to Ubuntu
---

### Post by Donna_Harris on 2013-08-19
Hi all,

I recently purchased an Acer C7 ChromeBook for the sole intention of dual booting Ubuntu for remoting into other environments.  Basically, I wanted a thin client for traveling.

At the moment, I have Ubuntu 12.10 installed (originaly installed 13.04, but reverted in case that helped resolve my problems -- it didn't) which was accomplished using the Chrubuntu script.

I don't appear to have any issues with setting up the client connection for my work PPTP VPN (the #1 important connection to get working) --- I am hitting the VPN server, and it complains when I give it incorrect credentials.  After I provide the creds, I get "VPN Connection Error:  The VPN connection <name of connection> failed."

The system log says all kinds of different things, depending on which settings I choose -- but at the end of the day there are several messages in the log file that I don't know how to resolve, or if I even need to.  I have search around online for about a week and have more questions than answers.

Anybody who is willing to help me through this, I'd be very grateful.  I'm open to trying anything.  But I'd prefer to be trying things with direction from somebody with more know-how than I currently have in the Linux world.  I've included more specifics below.  Thanks!!

~~~~~~

Here are the current settings -- they line up with VPN settings I have on other devices, which are functional:

[ATTACH=CONFIG]245491[/ATTACH]

Live logging using "tail -f /var/logs/syslog" resulted in the following being recorded:


Aug 19 23:13:49 chrubuntu NetworkManager[549]: <info> Starting VPN service 'pptp'...
Aug 19 23:13:49 chrubuntu NetworkManager[549]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 1837
Aug 19 23:13:49 chrubuntu NetworkManager[549]: <info> VPN service 'pptp' appeared; activating connections
Aug 19 23:14:00 chrubuntu NetworkManager[549]: <info> VPN plugin state changed: starting (3)
Aug 19 23:14:00 chrubuntu NetworkManager[549]: <info> VPN connection 'VPN connection 1' (Connect) reply received.
Aug 19 23:14:00 chrubuntu pppd[3228]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Aug 19 23:14:00 chrubuntu pppd[3228]: pppd 2.4.5 started by root, uid 0
Aug 19 23:14:00 chrubuntu NetworkManager[549]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 19 23:14:00 chrubuntu NetworkManager[549]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Aug 19 23:14:00 chrubuntu NetworkManager[549]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Aug 19 23:14:00 chrubuntu pppd[3228]: Using interface ppp0
Aug 19 23:14:00 chrubuntu pppd[3228]: Connect: ppp0 <--> /dev/pts/1
Aug 19 23:14:00 chrubuntu pptp[3237]: nm-pptp-service-1837 log[main: pptp.c:314]: The synchronous pptp option is NOT activated
Aug 19 23:14:00 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Aug 19 23:14:00 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:739]: Received Start Control Connection Reply
Aug 19 23:14:00 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:773]: Client connection established.
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:858]: Received Outgoing Call Reply.
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 51541).
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 warn[ctrlp_disp: pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Aug 19 23:14:01 chrubuntu pppd[3228]: LCP terminated by peer (9M-^^kM-^S^@<M-Mt^@^@^BM-3)
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 warn[ctrlp_disp: pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:912]: Received Call Clear Request.
Aug 19 23:14:04 chrubuntu pppd[3228]: Connection terminated.
Aug 19 23:14:04 chrubuntu avahi-daemon[252]: Withdrawing workstation service for ppp0.
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <warn> VPN plugin failed: 1
Aug 19 23:14:04 chrubuntu NetworkManager[549]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 19 23:14:04 chrubuntu pppd[3228]: Modem hangup
Aug 19 23:14:04 chrubuntu pptp[3237]: nm-pptp-service-1837 warn[decaps_hdlc: pptp_gre.c:204]: short read (-1): Input/output error
Aug 19 23:14:04 chrubuntu pptp[3237]: nm-pptp-service-1837 warn[decaps_hdlc: pptp_gre.c:216]: pppd may have shutdown, see pppd log
Aug 19 23:14:04 chrubuntu pptp[3254]: nm-pptp-service-1837 log[callmgr_main: pptp_callmgr.c:234]: Closing connection (unhandled)
Aug 19 23:14:04 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Aug 19 23:14:04 chrubuntu pptp[3254]: nm-pptp-service-1837 log[call_callback: pptp_callmgr.c:79]: Closing connection (call state)
Aug 19 23:14:04 chrubuntu pppd[3228]: Exit.
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <warn> VPN plugin failed: 1
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <warn> VPN plugin failed: 1
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <info> VPN plugin state changed: stopped (6)
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <info> VPN plugin state change reason: 0
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <info> Policy set 'impresario' (wlan0) as default for IPv4 routing and DNS.
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Aug 19 23:14:10 chrubuntu NetworkManager[549]: <info> VPN service 'pptp' disappeared

---

### Post by sandyd on 2013-08-19
> **Donna_Harris said:**
> Hi all,

I recently purchased an Acer C7 ChromeBook for the sole intention of dual booting Ubuntu for remoting into other environments.  Basically, I wanted a thin client for traveling.

At the moment, I have Ubuntu 12.10 installed (originaly installed 13.04, but reverted in case that helped resolve my problems -- it didn't) which was accomplished using the Chrubuntu script.

I don't appear to have any issues with setting up the client connection for my work PPTP VPN (the #1 important connection to get working) --- I am hitting the VPN server, and it complains when I give it incorrect credentials.  After I provide the creds, I get "VPN Connection Error:  The VPN connection <name of connection> failed."

The system log says all kinds of different things, depending on which settings I choose -- but at the end of the day there are several messages in the log file that I don't know how to resolve, or if I even need to.  I have search around online for about a week and have more questions than answers.

Anybody who is willing to help me through this, I'd be very grateful.  I'm open to trying anything.  But I'd prefer to be trying things with direction from somebody with more know-how than I currently have in the Linux world.  I've included more specifics below.  Thanks!!

~~~~~~

Here are the current settings -- they line up with VPN settings I have on other devices, which are functional:

[ATTACH=CONFIG]245491[/ATTACH]

Live logging using "tail -f /var/logs/syslog" resulted in the following being recorded:


Aug 19 23:13:49 chrubuntu NetworkManager[549]: <info> Starting VPN service 'pptp'...
Aug 19 23:13:49 chrubuntu NetworkManager[549]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 1837
Aug 19 23:13:49 chrubuntu NetworkManager[549]: <info> VPN service 'pptp' appeared; activating connections
Aug 19 23:14:00 chrubuntu NetworkManager[549]: <info> VPN plugin state changed: starting (3)
Aug 19 23:14:00 chrubuntu NetworkManager[549]: <info> VPN connection 'VPN connection 1' (Connect) reply received.
Aug 19 23:14:00 chrubuntu pppd[3228]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Aug 19 23:14:00 chrubuntu pppd[3228]: pppd 2.4.5 started by root, uid 0
Aug 19 23:14:00 chrubuntu NetworkManager[549]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 19 23:14:00 chrubuntu NetworkManager[549]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Aug 19 23:14:00 chrubuntu NetworkManager[549]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Aug 19 23:14:00 chrubuntu pppd[3228]: Using interface ppp0
Aug 19 23:14:00 chrubuntu pppd[3228]: Connect: ppp0 <--> /dev/pts/1
Aug 19 23:14:00 chrubuntu pptp[3237]: nm-pptp-service-1837 log[main: pptp.c:314]: The synchronous pptp option is NOT activated
Aug 19 23:14:00 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Aug 19 23:14:00 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:739]: Received Start Control Connection Reply
Aug 19 23:14:00 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:773]: Client connection established.
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:858]: Received Outgoing Call Reply.
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 51541).
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 warn[ctrlp_disp: pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Aug 19 23:14:01 chrubuntu pppd[3228]: LCP terminated by peer (9M-^^kM-^S^@<M-Mt^@^@^BM-3)
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 warn[ctrlp_disp: pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:912]: Received Call Clear Request.
Aug 19 23:14:04 chrubuntu pppd[3228]: Connection terminated.
Aug 19 23:14:04 chrubuntu avahi-daemon[252]: Withdrawing workstation service for ppp0.
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <warn> VPN plugin failed: 1
Aug 19 23:14:04 chrubuntu NetworkManager[549]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 19 23:14:04 chrubuntu pppd[3228]: Modem hangup
Aug 19 23:14:04 chrubuntu pptp[3237]: nm-pptp-service-1837 warn[decaps_hdlc: pptp_gre.c:204]: short read (-1): Input/output error
Aug 19 23:14:04 chrubuntu pptp[3237]: nm-pptp-service-1837 warn[decaps_hdlc: pptp_gre.c:216]: pppd may have shutdown, see pppd log
Aug 19 23:14:04 chrubuntu pptp[3254]: nm-pptp-service-1837 log[callmgr_main: pptp_callmgr.c:234]: Closing connection (unhandled)
Aug 19 23:14:04 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Aug 19 23:14:04 chrubuntu pptp[3254]: nm-pptp-service-1837 log[call_callback: pptp_callmgr.c:79]: Closing connection (call state)
Aug 19 23:14:04 chrubuntu pppd[3228]: Exit.
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <warn> VPN plugin failed: 1
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <warn> VPN plugin failed: 1
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <info> VPN plugin state changed: stopped (6)
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <info> VPN plugin state change reason: 0
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <info> Policy set 'impresario' (wlan0) as default for IPv4 routing and DNS.
Aug 19 23:14:04 chrubuntu NetworkManager[549]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Aug 19 23:14:10 chrubuntu NetworkManager[549]: <info> VPN service 'pptp' disappeared

```

Aug 19 23:14:00 chrubuntu pptp[3237]: nm-pptp-service-1837 log[main: pptp.c:314]: **The synchronous pptp option is NOT activated**
Aug 19 23:14:00 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Aug 19 23:14:00 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:739]: Received Start Control Connection Reply
Aug 19 23:14:00 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:773]: Client connection established.
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_rep: pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:858]: Received Outgoing Call Reply.
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 51541).
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 log[ctrlp_disp: pptp_ctrl.c:953]: send_accm is 00000000, recv_accm is FFFFFFFF
Aug 19 23:14:01 chrubuntu pptp[3254]: nm-pptp-service-1837 warn[ctrlp_disp: pptp_ctrl.c:956]:** Non-zero Async Control Character Maps are not supported!**
```

Have you tried [http://ubuntuforums.org/showthread.php?t=1095546&p=7002673&viewfull=1#post7002673](http://ubuntuforums.org/showthread.php?t=1095546&p=7002673&viewfull=1#post7002673) ?
AFAKI, PPTP isn't secure, so I havent used it for a year now, but that was the post that got it working for me.

---

### Post by Donna_Harris on 2013-08-20
Hi - thanks for your reply. :)

Yes, I have heard that PPTP is considered less secure.  Unless I misunderstand the way VPNs work, that's what my office uses so I thought it was necessary to create a connection for the same.  They might change it eventually, but while it's still the old way it would be awesome to connect to it.

Thanks for the link - yes, I had stumbled on to that one before.  After installing gconf-editor, I didn't have any "networking/connections" path under "system" so I couldn't continue.  I could not manually find the paths or the files being referred to.  Reference is made throughout the thread of a way to configure this using the terminal, but that option doesn't get explored.

I did find this [https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN) which has a section about VPN setup at the command line.  I followed these instructions (although I didn't know what to provide as the subnet info, so I just stuck with the default values provided... I'd need to touch base with somebody at the office who'll know.)  I also tried setting up a connection using the "PPTP VPN Configuration" instructions later on.  BOTH of these attempts failed, but with some different errors in the logs to what I posted earlier, for example:

```

...
Aug 20 00:26:23 chrubuntu pppd[1956]: CHAP authentication succeeded
[B]Aug 20 00:26:23 chrubuntu pppd[1956]: kernel does not support PPP filtering
Aug 20 00:26:23 chrubuntu pppd[1956]: MPPE required, but kernel has no support.[/B]
Aug 20 00:26:23 chrubuntu pppd[1956]: sent [LCP TermReq id=0x2 "MPPE required but not available"]
Aug 20 00:26:23 chrubuntu pppd[1956]: rcvd [CCP ConfReq id=0x4 <mppe +H +M +S +L -D +C>]
Aug 20 00:26:23 chrubuntu pppd[1956]: Discarded non-LCP packet when LCP not open
Aug 20 00:26:23 chrubuntu pppd[1956]: rcvd [IPCP ConfReq id=0x5 <addr 192.168.168.164>]
Aug 20 00:26:23 chrubuntu pppd[1956]: Discarded non-LCP packet when LCP not open
Aug 20 00:26:23 chrubuntu pptp[1967]: anon log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Aug 20 00:26:23 chrubuntu pptp[1967]: anon log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
**Aug 20 00:26:23 chrubuntu pptp[1967]: anon warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!**
Aug 20 00:26:23 chrubuntu pppd[1956]: rcvd [LCP TermAck id=0x2 "MPPE required but not available"]
Aug 20 00:26:23 chrubuntu pppd[1956]: Connection terminated.
Aug 20 00:26:23 chrubuntu avahi-daemon[501]: Withdrawing workstation service for ppp0.
...

```

I've read around about these errors too, and have still been perplexed.  If it is true that I need to enable modules, or even recompile a kernel, that's fine.  But I don't actually know what needs to be done to address the issue, or the best way to approach trying any of these things for the first time.  So I'm all ears/eyes.

Thanks!!

---

