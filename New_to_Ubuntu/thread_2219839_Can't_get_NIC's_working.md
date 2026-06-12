---
title: "Can't get NIC's working"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by karnival8 on 2014-04-25
I have an ubuntu server with a Intel S2400SC motherboard. The motherboard took a dump and so I ordered the same board again and replaced.

Everything works fine except now, I can't get network up. It's the exact same configuration and the exact same hardware. My /etc/network/interfaces is the same, hasn't changed.

When I do a ifconfig, it doesn't show any eth's.

When I do a ifconfig eth0 up I get No such device.

I am too new to Linux to solve this on my own, would someone be willing to list the steps for me?

Dying over here!

---

### Post by SysBoot on 2014-04-25
Give us the output of lspci and ifconfig or ip addr

---

### Post by karnival8 on 2014-04-25
lspci says:
05.00.0 Ethernet controller: Intel Corp 82574L Gigabit
05.00.0 (same thing) - i have 2

ifconfig only shows the lo

ip addr shows both eth0 and eth1 as DOWN

---

### Post by suprleg on 2014-04-25
Might be helpful to know which ubuntu server is installed and possibly the hardware environment.
Can you post: sudo /sbin/ifconfig -a
Also take a look at the results of: sudo dmesg | grep -i eth0

---

### Post by SeijiSensei on 2014-04-25
Intel adapters are usually rock solid.  Can you bring up an adapter manually with "sudo ifconfig eth0 up"? Try that, followed by "ifconfig eth0". Eth0 should be listed but without an IP address.

From lspci ("list PCI") I have a 
```
02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
```

It uses the e1000 driver which is included with the Linux kernel. I can see that it is loaded with the lsmod ("list modules") tool:
```

[Seiji@GhostWorld]$ sudo lsmod | grep e1000
e1000                 120285  0

```
It is 120K in size and used by no other processes ("0").  If you don't see the e1000 driver loaded, then Linux didn't detect your adapters.  Check the BIOS settings and make sure they are not somehow disabled at the hardware level.

---

### Post by karnival8 on 2014-04-26
my dmesg gives me "link is not ready" for eth0 and eth1 (i have 2 nic cards)
ifconfig eth0 up gives me no such device
lsmod shows e1000e 199273 0

---

