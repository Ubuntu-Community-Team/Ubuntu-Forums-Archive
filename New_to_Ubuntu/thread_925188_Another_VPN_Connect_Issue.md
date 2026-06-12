---
title: "Another VPN Connect Issue"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by VirtualEdgar on 2008-09-20
Hi, n00b here! I need help on connecting to the VPN at work (Microsoft Server using GRE) using my laptop which runs Hardy. Yes, I have done my homework on searching for all possible solutions by searching sites especially this one, but no luck so far!

Here's my connection setup... at home I am connected to the internet via a wireless router meaning I am using wlan0. I already did allowed most ports that is used to connect to a VPN (IPSec, PPTP, LT2*, etc). I can ping my IP at work (using Ubuntu) and I can connect flawlessly to it using a Windows box. I've tried using network-manager-pptp and Kvpnc tried all possible ways to connect, yet all my efforts are in vain. Always getting a "Could not start the VPN connection 'MyVPN' due to a connection error. VPN Connection failed." message in pptp. Kvpnc always say "Remote modem was hung up. Connection was terminated." The hell what that means. And yes, I have placed the correct IP address and the login name and password.

By the way, if logs would help... here it is!

Plugin nm-pppd-plugin.so loaded.
nm-pppd-plugin: plugin initialized.
pppd 2.4.4 started by root, uid 0
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
nm-pppd-plugin: CHAP check hook.
Terminating on signal 15
Child process /usr/sbin/pptp xxx.xxx.xxx.xxx --nolaunchpppd (pid 850 terminated with signal 15
Modem hangup
Connection terminated.
Exit.


xxx.xxx.xxx.xxx = my work vpn server address

Thank you!

---

### Post by VirtualEdgar on 2008-09-20
Anyone please? Thanks!

---

### Post by RogueEntity on 2008-09-25
I have a similar issue... and I have gotten no help over the past week at all. It feels like PPTP is some taboo subject that no one seems to know anything about. Im trying to forward PPTP connections through a Ubuntu-based gateway/firewall machine.. and you are trying to connect directly to a PPTP (VPN) server. Perhaps the issue stopping my setup from working, is also the reason you cant connect out... a missing kernel module perhaps.

---

