---
title: "PPPTP client connection fault"
date: 2020-09-03
forum: New to Ubuntu
---

### Post by tymon82 on 2020-09-03
Hello im trying to connect with Windows vpn server and got same error either i use cli client or gui:

```
Sep  3 09:54:49 dev-station-one NetworkManager[722]: <info>  [1599119689.9380] audit: op="connection-activate" uuid="5130c429-c71f-420a-a9f4-9616ab2ea408" name="VPNMarkConnection" pid=1504 uid=1000 result="success"Sep  3 09:54:49 dev-station-one NetworkManager[722]: <info>  [1599119689.9453] vpn-connection[0x55b82dad2360,5130c429-c71f-420a-a9f4-9616ab2ea408,"VPNMarkConnection",0]: Started the VPN service, PID 25931
Sep  3 09:54:49 dev-station-one NetworkManager[722]: <info>  [1599119689.9513] vpn-connection[0x55b82dad2360,5130c429-c71f-420a-a9f4-9616ab2ea408,"VPNMarkConnection",0]: Saw the service appear; activating connection
Sep  3 09:54:49 dev-station-one NetworkManager[722]: <info>  [1599119689.9548] vpn-connection[0x55b82dad2360,5130c429-c71f-420a-a9f4-9616ab2ea408,"VPNMarkConnection",0]: VPN connection: (ConnectInteractive) reply received
Sep  3 09:54:49 dev-station-one NetworkManager[722]: <info>  [1599119689.9562] vpn-connection[0x55b82dad2360,5130c429-c71f-420a-a9f4-9616ab2ea408,"VPNMarkConnection",0]: VPN plugin: state changed: starting (3)
Sep  3 09:54:49 dev-station-one pppd[25935]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
Sep  3 09:54:49 dev-station-one NetworkManager[722]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
Sep  3 09:54:49 dev-station-one pppd[25935]: pppd 2.4.7 started by root, uid 0
Sep  3 09:54:49 dev-station-one pppd[25935]: Using interface ppp0
Sep  3 09:54:49 dev-station-one NetworkManager[722]: Using interface ppp0
Sep  3 09:54:49 dev-station-one NetworkManager[722]: Connect: ppp0 <--> /dev/pts/3
Sep  3 09:54:49 dev-station-one pppd[25935]: Connect: ppp0 <--> /dev/pts/3
Sep  3 09:54:49 dev-station-one NetworkManager[722]: <info>  [1599119689.9619] manager: (ppp0): new Ppp device (/org/freedesktop/NetworkManager/Devices/155)
Sep  3 09:54:49 dev-station-one pptp[25940]: nm-pptp-service-25931 log[main:pptp.c:353]: The synchronous pptp option is NOT activated
Sep  3 09:54:49 dev-station-one systemd-udevd[25939]: link_config: autonegotiation is unset or enabled, the speed and duplex are not writable.
Sep  3 09:54:49 dev-station-one NetworkManager[722]: <info>  [1599119689.9705] devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep  3 09:54:49 dev-station-one NetworkManager[722]: <info>  [1599119689.9705] device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Sep  3 09:54:49 dev-station-one pptp[25953]: nm-pptp-service-25931 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 1 'Start-Control-Connection-Request'
Sep  3 09:54:50 dev-station-one pptp[25953]: nm-pptp-service-25931 log[ctrlp_disp:pptp_ctrl.c:781]: Received Start Control Connection Reply
Sep  3 09:54:50 dev-station-one pptp[25953]: nm-pptp-service-25931 log[ctrlp_disp:pptp_ctrl.c:815]: Client connection established.
Sep  3 09:54:50 dev-station-one pptp[25953]: nm-pptp-service-25931 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 7 'Outgoing-Call-Request'
Sep  3 09:54:51 dev-station-one pptp[25953]: nm-pptp-service-25931 log[ctrlp_disp:pptp_ctrl.c:900]: Received Outgoing Call Reply.
Sep  3 09:54:51 dev-station-one pptp[25953]: nm-pptp-service-25931 log[ctrlp_disp:pptp_ctrl.c:939]: Outgoing call established (call ID 17497, peer's call ID 21504).
Sep  3 09:54:56 dev-station-one gnome-shell[1504]: [AppIndicatorSupport-FATAL] unable to lookup icon for Slack1_64
Sep  3 09:54:56 dev-station-one gnome-shell[1504]: [AppIndicatorSupport-FATAL] unable to lookup icon for Slack1_64
Sep  3 09:55:21 dev-station-one pptp[25953]: nm-pptp-service-25931 log[pptp_read_some:pptp_ctrl.c:586]: read returned zero, peer has closed
Sep  3 09:55:21 dev-station-one pptp[25953]: nm-pptp-service-25931 log[callmgr_main:pptp_callmgr.c:269]: Closing connection (shutdown)
Sep  3 09:55:21 dev-station-one NetworkManager[722]: Modem hangup
Sep  3 09:55:21 dev-station-one NetworkManager[722]: Connection terminated.
Sep  3 09:55:21 dev-station-one pptp[25953]: nm-pptp-service-25931 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 12 'Call-Clear-Request'
Sep  3 09:55:21 dev-station-one pptp[25953]: nm-pptp-service-25931 log[pptp_read_some:pptp_ctrl.c:586]: read returned zero, peer has closed
Sep  3 09:55:21 dev-station-one pptp[25953]: nm-pptp-service-25931 log[call_callback:pptp_callmgr.c:84]: Closing connection (call state)
Sep  3 09:55:21 dev-station-one pppd[25935]: Modem hangup
Sep  3 09:55:21 dev-station-one pppd[25935]: Connection terminated.
Sep  3 09:55:21 dev-station-one NetworkManager[722]: <warn>  [1599119721.2166] vpn-connection[0x55b82dad2360,5130c429-c71f-420a-a9f4-9616ab2ea408,"VPNMarkConnection",0]: VPN plugin: failed: connect-failed (1)
Sep  3 09:55:21 dev-station-one NetworkManager[722]: <info>  [1599119721.2167] vpn-connection[0x55b82dad2360,5130c429-c71f-420a-a9f4-9616ab2ea408,"VPNMarkConnection",0]: VPN plugin: state changed: stopping (5)
Sep  3 09:55:21 dev-station-one NetworkManager[722]: <info>  [1599119721.2185] vpn-connection[0x55b82dad2360,5130c429-c71f-420a-a9f4-9616ab2ea408,"VPNMarkConnection",0]: VPN plugin: state changed: stopped (6)
Sep  3 09:55:21 dev-station-one gnome-shell[1504]: Removing a network device that was not added
Sep  3 09:55:21 dev-station-one NetworkManager[722]: <info>  [1599119721.2224] devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep  3 09:55:21 dev-station-one NetworkManager[722]: <info>  [1599119721.2233] vpn-connection[0x55b82dad2360,5130c429-c71f-420a-a9f4-9616ab2ea408,"VPNMarkConnection",0]: VPN service disappeared
Sep  3 09:55:21 dev-station-one pppd[25935]: Exit.

```

I was already trying many solutions (eq. ufw, mtu) but no one helps.

---

### Post by TheFu on 2020-09-03
PPTP is useless as a VPN. Anyone can decrypt the traffic with 15 yr old computers quickly.

FYI:  [https://www.youtube.com/watch?v=IPPHJBp3bXU](https://www.youtube.com/watch?v=IPPHJBp3bXU) - hacking PPTP - jump to 5:25 into the video.
[https://resources.infosecinstitute.com/the-pptp-vpn-protocol-is-it-safe/](https://resources.infosecinstitute.com/the-pptp-vpn-protocol-is-it-safe/)

> What security flaws have been identified with PPTP?

Almost from the very start of its life, PPTP has been bugged by allegations that it simply isn&#8217;t secure, and one man is primarily responsible for this reputation. In 1998, security analyst Bruce Schneier published an important paper on PPTP, and it made grisly reading for users. Or at least it should have.

---

### Post by SeijiSensei on 2020-09-03
[OpenVPN](https://community.openvpn.net/openvpn/wiki/Easy_Windows_Guide?__cf_chl_jschl_tk__=111fe6843466904c599a2ebbc59b287d8a8be53e-1599148071-0-ASy5SzIg8VyUBxP-k4xBAU1KzEjp3vp517RIj8Yk_tI3fDu1gyWueZJyt64HWrUfQboYH6vUcCP9GxJVUEX5MoPHBCNYH6ecv-6yBqNowDM4D5pxmCm74E5WqbUHSeko43LUqjzv25s12vpkJeUvFKAzyAjJ6_cK-7hYpdvbSRtapgIJnkW1Yq6sC544vI5A5VG6sMnLDrK88cm-ZvZ6M4ZRdP5L6g7HVB2aRwHhpCRitNy7-D9vKX1eKj5lEVo9cb_hkJ3HlhrPgXSE4ycc0qjNrI0SF9pRx7PrSTkzI8rNeGiHiHe6nfGyzWuG4n-UCg) runs on both Windows and Linux.

---

