---
title: "fire fox problems HELP!"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by kobra_877 on 2008-09-02
i just got linux and ive been trying to get my wireless to work and when i did the internet stoped working. every time i serch a website fire fox says that seb site does not exist or cannot be found and it has only started to show that since i was tinkring with the wireless settings. the internet worked fine when it was wired but now it works with neather. please help i need my laptop for school and fast

---

### Post by knattlhuber on 2008-09-02
Seems that your wireless card isn't recognized. People here can surely help you set it up but we need a bit more information on your system.

What Ubuntu version are you using?
Can you please type 

```
lspci -v
ifconfig
```

in a terminal and post the output?

---

### Post by kobra_877 on 2008-09-02
lspci -v output

01:05.0 vga compatible controler: ATI tech.. inc. Radion express 200m 5955
system hewlett-packard company unknowen device 30ae
flags bus master 66mhz medium devsel latency 255 irq 16
memory at c8000000 (32 bit non prefetchable) 
expancion rom at c0120000

06:02,0 network controler: broadcom corp bcm4318 802.11g wireless lan controler
subsystem hp corp broadcom 802.11b/g wlan
flags: bus master fast devsel latency 64 irq 18
memory at c0200000

06:06.0 ethernet controler  realtek semiconductor co. ltd. rtl 8139/8139c/8139c+
subsystem hp corp broadcom 802.11b/g wlan
flags: bus master fast devsel latency 64 irq 18
memory at c0200000

ifconfig output

eth0  link encap: ethernet  hwaddr 00:16:d4:03:80:64
up broadcast mulicast mtu:1500 metric:1
rx packets:0 errors:0 dropped:0 overrun:0 frame: 0
tx packets:0 errors:0 dropped:0 overrun:0 carrier:0 collisions:0 txqueulen:0
rx bytes:0 (o.0 B) tx bytes:0 (0.0b)
interrupt:19 bass address:0xa000

lo  link encap: local loopback
inet adde:127.0.0.1  mask: 255.0.0.0
inet6 addr:  : :1/128 scope:host
up loopback running mtu:16436 metric:1
rx packets:1160 errors:0 dropped:0 overrun:0 frame: 0
tx packets:1160 errors:0 dropped:0 overrun:0 carrier:0 collisions:0 txqueulen:0
rx bytes:58000 (56.6 kb)  tx bytes:58000 (56.6kb)

---

### Post by knattlhuber on 2008-09-02
OK, you've got a card with a Broadcom 4318 chipset, which should be natively supported by Hardy.

Does your laptop have a switch to turn on the WLAN card? I know that my HP Pavilions has one and I spent quite some time trying to get my wireless working before I realized it's not switched on...

---

### Post by kobra_877 on 2008-09-02
yes it does have a switch and it does work cuz i can search for networks but and the main computer shows that i am on the network but fire fox is showing that there is no inter net could the router be blocking me out or is fire fox the reason

---

### Post by knattlhuber on 2008-09-02
Judged from your ifconfig output, you are not connected to any network as eth0 shows no IP address or anything.

I have to go offline for a while, maybe someone else can please take it from here?

Thanks.

---

