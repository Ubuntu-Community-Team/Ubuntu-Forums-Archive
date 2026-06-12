---
title: "Wireless Card Help (Terminal Output analysis)"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by ergonomicdesign on 2008-05-25
Hi, I'm new to using Ubuntu, only installed it maybe...two days ago. 

So, I wanted to install my wireless card and make it work...but that didn't happen. I went on the net and found a guide (in addition to the wiki one) about how to use ndiswrapper. So I tried it. I successfully found the driver, added it, checked to make sure it's enabled, but when I checked for errors...(tail var/log/errors) I found a lot...I think anyway. What should I do based off of this output? 

v2@v-t-ubu:~$ ndiswrapper -l
net8187b : driver installed
	device (0BDA:8197) present
v2@v-t-ubu:~$ sudo depmod -a
v2@v-t-ubu:~$ sudo modprobe ndiswrapper
v2@v-t-ubu:~$ tail /var/log/messages
May 25 12:29:13 v-t-ubu kernel: [10906.974453] usbcore: registered new interface driver ndiswrapper
May 25 12:29:49 v-t-ubu kernel: [10943.701975] sky2 eth0: Link is down.
May 25 12:31:16 v-t-ubu kernel: [11029.811965] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
May 25 12:31:16 v-t-ubu kernel: [11029.815219] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 25 12:31:20 v-t-ubu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
May 25 12:31:20 v-t-ubu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May 25 12:31:20 v-t-ubu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
May 25 12:31:20 v-t-ubu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
May 25 12:32:31 v-t-ubu pulseaudio[5795]: sink-input.c: Failed to create sink input: too many inputs per sink.
May 25 12:33:03 v-t-ubu pulseaudio[5795]: sink-input.c: Failed to create sink input: too many inputs per sink.

---

