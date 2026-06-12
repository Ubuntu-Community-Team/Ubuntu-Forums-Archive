---
title: "can't connect to the internet"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by mclinda on 2008-04-22
I need help, please!
I am VERY green, so please try to give lots of details in helping me figure this out... I do not know what I am doing.

I have Xubuntu (I think 7.10) on an old laptop (used to run Win97). It works great except that I cannot get it to connect to the internet. 

I am using DSL and going through a linksys router that has 4 slots on it, and the other 2 computers in the house (one windows, one Ubuntu) have no problems. But the lights on the box will not light up for my computer, even when I try to use one of the slots the other computers were using (thus it isn't a problem with the router slots). 

I have tried going into network settings, and using the dhcp thing, tried setting it up as a static IP by typing in the info I could find, and have tried running some things from terminal that I really don't understand (my brother told me what to type). I can "ping" myself, thus he says it is talking to the router. But I cannot "ping" the other computers nor can I get firefox to connect to any sites. I have run ifconfig and it says the eth0 is up and gives IP address, etc.

I am having trouble finding what else I need to try, as everything I have read seems to say that if it is all plugged in, it should be working...but it isn't. I have no idea what I am doing wrong or what else to try.

Please help!

---

### Post by Ub1476 on 2008-04-22
Maybe you missed a few steps [here]("http://doc.ubuntu.com/ubuntu/internet/C/index.html")?

If the problem goes deeper, post the output of:

```
lspci
```

This code might get you on net though (it has worked for me on other Linux distros):

```
sudo dhcpcd eth0
```

---

### Post by HunterThomson on 2008-04-22
Does it work with the live cd?

---

### Post by mclinda on 2008-04-28
In the link, it says that a wired ethernet connection (which I think is what I am trying to do, but...I know very little) should work automatically. I will go through the stuff on the "tools to help with network connection problems" and post what I get, if that would help? I am sorry to be so ignorant, but...I don't know what I am doing and this is the only way I know to learn it.

ifconfig gets the following information:
> eth0  link encap: Ethernet HWaddr 00:01:02:7B:ED:6E
      UP BROADCAST MULITCAST MTU:1500 Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
      Interrupt: 11 Base address:0x6000

eth0:avah Link encap: Ethernet HWaddr 00:01:02:7B:ED:6E
          inet addr: 169.254.7.81 Bcast:169.254.255.255 Mask:255.255.0.0
          UP BROADCAST MULTICAST MTU:1500 Metric:1
          Interrupt:11 Base address:0x6000

lo    Link encap: local loopback
      inet addr: 127.0.0.1 Mask 255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING MTU:16436 Metric:1
      RX packets: 872 errors:0 dropped:0 overruns:0 frame:0
      TX packets: 872 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
      RX bytes: 69540 (67.9KiB) TX bytes: 69540 (67.9KiB)

I attempted to ping 82.211.81.158 as instructed on the linked page...all attempts came back "destiantion host unreachable" and all the packets transmited (9) were lost...it also noted "+6 errors" and "time 8025ms, pipe 3". 

in response to the lspci I got:
> 00:00.0 host bridge: Intel Corportation 440BX/ZX/DX - 82443BX/ZX/DX host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 44BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420
00:03.1 CardBus bridge: Texas Instruments PCI1420
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE(rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08:0 Multimedia Audio Controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
00:10:0 Communication controller: Agere Systems WinModem 56k (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
06:00.0 Ethernet controller: 3Com Corporation 3cCFE575CT CardBus [Cyclone] (rev 10)

For the second suggestion, it did not recognize the command dhcpcd, so it didn't do anything.

Embarrassing as it is...I can't find my live CD. I put it somewhere "safe" and I am sure it is still very safe there. I can make another one, but I don't have the time to do it right now, as I am travelling. When I have a chance to try it, I will let you know what it does. Thanks!

---

### Post by dearingj on 2008-04-28
I think your brother was wrong when he said your computer could talk to the router. The fact that your computer can ping itself means little; all computers can ping themselves AFAIK. The fact that the lights don't light up, combined with the fact that your computer thinks its IP address is 169.254.7.81 (home networks like yours usually use 192.168.1.* ), leads me to believe that there is something wrong with either the cable connecting your computer to the router, or with the computer's network card. Have you tried replacing either?

---

### Post by mclinda on 2008-04-28
I have tried other cables, so I know the cable isn't the issue. Haven't replaced anything else, but... that would explain why this is being so difficult, wouldn't it? 

Is there any way for me to check if the network card is the problem without actually replacing it? I don't want to buy something that isn't going to work. 

The router is able to run the other two computers through any of the 4 slots, so I suspect it is not the problem, but if there is something I should be trying with regard to it, let me know. 

Thanks!

---

### Post by dearingj on 2008-04-28
You could try switching cards a working computer. Unfortunately that's the kind of thing I can't really help you with without being there :(

Anyone else have any ideas?

---

### Post by OffAxis on 2008-04-28
169.254.x.x is the address that is 'assigned' to a connection when it can't reach a DHCP server.

---

### Post by OffAxis on 2008-04-28
> The fact that your computer can ping itself means little;
It actually means a lot. Being able to ping itself tells us that it's working, so the problem is somewhere in the physical connection between the computer and the router.

Make sure the cable is really jammed in there good, and try a different (known working if you can) port on the router.
If the link light is still not turning on, you may have a bad receptacle on your wired card (damaged pin, etc).

Also make sure that the cable you're using isn't a crossover cable (used for directly connecting two computers).
You may also be using the 'uplink' port on the router; don't do that.

---

### Post by ghostdog2402 on 2008-04-28
Maybe the network port on the motherboard is damaged. try diferent network card.

---

### Post by ghostdog2402 on 2008-04-28
Maybe the network port on the motherboard is damaged. try diferent card.

---

