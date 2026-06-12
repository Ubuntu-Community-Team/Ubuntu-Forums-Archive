---
title: "[SOLVED] another wireless Q"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by andybloke on 2008-12-02
hi all very new to ubuntu but love what iv seen so far 
so decided to get shot of vista on my laptop

every thing has installed well all drivers ok and the drivers you have to accept wich includes the gfx driver and the atheros wireless lan driver
i think iv put the details in right for the wireless how ever i get no light on the front to say wireless is on or off and no icon up near the clock (as read in other threds) i figure i must be missing something but have no idea what any help or advice would be very welcome 
cheers guys

---

### Post by Idefix82 on 2008-12-02
Welcome! Please open the terminal and post the output from
```
lshw -C network
```
and
```
ifconfig -a
```
here.

---

### Post by andybloke on 2008-12-02
hi hope this is what your after 

[lshw -C network]
WARNING: you should run this program as super-user.

  *-network               

       description: Ethernet interface

       product: MCP65 Ethernet

       vendor: nVidia Corporation

       physical id: 6

       bus info: pci@0000:00:06.0

       logical name: eth0

       version: a3

       serial: 00:1e:68:5f:83:9f

       width: 32 bits

       clock: 66MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes

  *-network UNCLAIMED

       description: Ethernet controller

       product: AR242x 802.11abg Wireless PCI Express Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:03:00.0

       version: 01

       width: 64 bits

       clock: 33MHz

       capabilities: cap_list

       configuration: latency=0

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: 4e:22:9d:fa:bc:6c

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes




[ifconfig -a]
eth0      Link encap:Ethernet  HWaddr 00:1e:68:5f:83:9f  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:20 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:268 errors:0 dropped:0 overruns:0 frame:0

          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:17136 (17.1 KB)  TX bytes:17136 (17.1 KB)



pan0      Link encap:Ethernet  HWaddr 4e:22:9d:fa:bc:6c  

          BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


hope this helps 
cheers

---

### Post by Idefix82 on 2008-12-02
Please try this guide and see if it works:
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/]("http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/")
Report back and let me know whether it worked.

---

### Post by andybloke on 2008-12-02
hi there ref the above link yes it worked 
how ever once it had downloaded the updates i had to go thro it all again 
thank you for your help 
cheers andy

---

