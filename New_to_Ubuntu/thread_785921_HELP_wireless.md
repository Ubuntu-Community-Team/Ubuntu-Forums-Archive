---
title: "HELP wireless"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by hazman on 2008-05-07
hi,
got so far with trying to get my belkin wireless g notebook card working. I have the original driver installed from windows cd. So when I open terminals and issue following commands I get
sudo ndiswrapper -l
blkwgnv7 : driver installed 
        device (1799:701F) present 
sudo lshw  -C network
 *-network UNCLAIMED     
       description: Ethernet controller 
       product: Belkin 
       vendor: Belkin 
       physical id: 0 
       bus info: pci@0000:05:00.0 
       version: 20 
       width: 32 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=0 maxlatency=64 mingnt=32
iwconfig
lo        no wireless extensions. 

irda0     no wireless extensions. 
ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:510 (510.0 b)  TX bytes:510 (510.0 b) 
gone through sudo ndiswrapper -m, sudo modprobe ndiswrapper but still no wireless connection PLEASE HELP am I missing something.i cannot even get lights to light up

---

### Post by miwaypet on 2008-05-07
Try this:

Open terminal and type: 

sudo modprobe ndiswrapper

wait till prompt returns then type:

sudo bash -c 'echo "ndiswrapper" >> /etc/modules'

Afterward shutdown (not restart).

When you bring it back up go to System>Administration>Network 

open it

see if it shows wireless. if it does you are in buisness.

Hope it helps.

---

