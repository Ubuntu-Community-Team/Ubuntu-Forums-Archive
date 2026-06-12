---
title: "Problems connecting to PPTP VPN from terminal pptp-linux"
date: 2016-06-10
forum: New to Ubuntu
---

### Post by Joel_Rinkol on 2016-06-10
So I've been looking online for many answers but nothing has come up so I thought I'd make my own forum post
I'm using ubuntu 14.04 and running this on the terminal and connecting through the Ethernet connection on my raspberry pi 2

After entering the command:
> 
sudo pon vpnname

Here is the syslog output

> 
JUN 10  14:51:39 ubuntu pppd[1654]: Using interface pp0
JUN 10  14:51:39 ubuntu pppd[1654]: Connect: ppp0<--> /dev/pts/0
JUN 10  14:51:39 ubuntu NetworkManager[491]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
JUN 10  14:51:39 ubuntu NetworkManager[491]:   SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/pp0, iface: ppp0)
JUN 10  14:51:39 ubuntu NetworkManager[491]    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/pp0, iface: ppp0, iface: pp0): no ifupdown configuration found.
JUN 10  14:51:39 ubuntu pptp[1806]: anon log[main:pptp.c:314]: The synchronous pptp option is NOT activated
JUN 10  14:51:40 ubuntu pptp[1807]: anon warn[open-inetsock:pptp_callmgr.c:329]: connect: NO route to host
JUN 10  14:51:40 ubuntu pptp[1807]: anon fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to  10.40.150.208
JUN 10  14:51:40 ubuntu pptp[1806]: anon fatal[open_callmgr:pptp.c:487]: Call manager exited with errror 256
JUN 10  14:51:40 ubuntu pppd[1654]: Modem hangup
JUN 10  14:51:40 ubuntu pppd[1654]: Connection terminated.
JUN 10  14:51:40 ubuntu NetworkManager[491]:     SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/pp0, iface: ppp0)
JUN 10  14:51:40 ubuntu pppd[1654]: Exit

I used the following guide and set up the files to connect my server
[http://www.networkinghowtos.com/howto/connect-to-a-pptp-vpn-server-from-ubuntu-linux/](http://www.networkinghowtos.com/howto/connect-to-a-pptp-vpn-server-from-ubuntu-linux/)

I don't know what to do I've searched each error separately and tried many solutions that worked for others but i get the same set of errors every time

---

