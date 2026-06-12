---
title: "Internet Connectivity Loss"
date: 2022-08-19
forum: New to Ubuntu
---

### Post by aquaman101 on 2022-08-19
[INDENT]Can anybody help with my internet connectivity issue, connectivity keeps dropping

I have tried lots of things like disabling ipv6 and turning off wifi power save settings but to no avail and I am about to give up on Ubuntu (Ive even upgraded to Jammy Jellyfish with no change)

Error logs show multiple instances across the whole of this morning, below is the latest:



11:38:33 kernel: [UFW BLOCK] IN=wlp3s0 OUT=  MAC=74:c6:3b:7a:38:ed:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1  DST=192.168.1.74 LEN=71 TOS=0x00 PREC=0x00 TTL=64 ID=58530 PROTO=UDP  SPT=58596 DPT=5353 LEN=5           
[/INDENT]

---

### Post by ActionParsnip on 2022-08-19
Have you tried rebooting your router? This is a good first step

---

### Post by aquaman101 on 2022-08-21
Anybody got any ideas before a launch this frustrating laptop in the bin.


Still suffering from problems I listed in post#1


The last 24 hours I've exhausted every idea like:


Trying to find new driver for realtek driver (impossible)
Played with different setting on UFW (no change)
Fixing BBID address (didn't work)
Installing Linux mint (same problem)


Honestly my experience of Linux has been a disaster Ive been messing with this laptop for a month with this one same problem!
Im quickly going to post this before I lose my connectivity (AGAIN!)





[COLOR=#3eb34f]
[/COLOR]

---

### Post by ActionParsnip on 2022-08-21
2nd time. Did you reboot your router....?

---

### Post by aquaman101 on 2022-08-21
Hi, yep I tried that

---

### Post by ActionParsnip on 2022-08-21
Well.... You didn't say. We aren't psychic.
If you run:
```

sudo lshw -C network

```
What is the output please?

---

### Post by aquaman101 on 2022-08-21
Sorry wasn't trying to be unhelpful

Output from command is:
 *-network                 
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 08
       serial: c8:5b:76:1d:2e:ec
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-46-generic firmware=rtl8106e-2_0.0.1 04/23/13 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:18 ioport:4000(size=256) memory:c1104000-c1104fff memory:c1100000-c1103fff
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 00
       serial: 74:c6:3b:7a:38:ed
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=5.15.0-46-generic firmware=N/A ip=192.168.1.74 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:19 ioport:3000(size=256) memory:c1000000-c1003fff

---

### Post by ActionParsnip on 2022-08-21
OK, when you get a disconnection, open a terminal and run
```

dmesg | tail

```
What is the output please?

---

### Post by aquaman101 on 2022-08-21
typical .... I haven't had a disconnection for last 20 mins
When I do get one, I will post the output

Thanks for your help

---

### Post by aquaman101 on 2022-08-21
OK, just lost connectivity.....here's the output

[ 5474.533850] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=31495 DF PROTO=2 
[ 5599.558467] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=45603 DF PROTO=2 
[ 5724.589618] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=52758 DF PROTO=2 
[ 5849.518241] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=43949 DF PROTO=2 
[ 5945.274108] [UFW BLOCK] IN=wlp3s0 OUT= MAC=74:c6:3b:7a:38:ed:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=192.168.1.74 LEN=71 TOS=0x00 PREC=0x00 TTL=64 ID=35041 PROTO=UDP SPT=37066 DPT=5353 LEN=51 
[ 5974.549246] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=10404 DF PROTO=2 
[ 6021.131478] [UFW BLOCK] IN=wlp3s0 OUT= MAC=74:c6:3b:7a:38:ed:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=192.168.1.74 LEN=71 TOS=0x00 PREC=0x00 TTL=64 ID=62374 PROTO=UDP SPT=50052 DPT=5353 LEN=51 
[ 6099.582196] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=49060 DF PROTO=2 
[ 6113.256464] [UFW BLOCK] IN=wlp3s0 OUT= MAC=74:c6:3b:7a:38:ed:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=192.168.1.74 LEN=71 TOS=0x00 PREC=0x00 TTL=64 ID=5048 PROTO=UDP SPT=40461 DPT=5353 LEN=51 
[ 6187.275250] [UFW BLOCK] IN=wlp3s0 OUT= MAC=74:c6:3b:7a:38:ed:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=192.168.1.74 LEN=71 TOS=0x00 PREC=0x00 TTL=64 ID=38440 PROTO=UDP SPT=51381 DPT=5353 LEN=51

---

### Post by SeijiSensei on 2022-08-21
I'd start by disabling UFW. If you're behind a router, you don't really need it.

---

### Post by aquaman101 on 2022-08-25
OK I'm back still looking for help.....internet speed still slowing completely to 120kps until wireless connectivity is turned off and on, or laptop is rebooted.

Trying to find new driver for realtek driver (impossible)
Played with different setting on UFW (no change)
Fixing BBID address (didn't work)
Complete re-install (same problem)
Rebooted router (Didn't work -  suggested by action parsnip)
Turned Firewall Off (no difference)

Anyone PLEASE help

---

### Post by QIII on 2022-08-25
Do you have an RJ45 connection and an ethernet cable to connect to your router with?

It could be that there is simply no Linux driver for your hardware.  But there is this, from May 2020:  [https://github.com/ghostrider-reborn/realtek-r8101-linux-driver](https://github.com/ghostrider-reborn/realtek-r8101-linux-driver)

I cannon vouch for the developer, so try this at your own risk.

---

### Post by aquaman101 on 2022-08-25
Thanks, but I came to ubuntu for security so don't fancy downloading something from an untrusted source

---

### Post by QIII on 2022-08-25
My suggestion at this point is diagnosis.  Will the problem persist if you use a wired connection?

The answer to that would be diagnostic.

---

### Post by aquaman101 on 2022-08-28
Hi, So as QIII suggested I have been running the laptop with a wired connection for a couple of days and it works fine.

So, obviously it must be the wireless connection.

Does anybody know a trusted source to get the correct driver, or is it true that there may not be a driver available in Linux for my laptop?

---

### Post by ActionParsnip on 2022-08-28
Try:
```

echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be_fix.conf > /dev/null

```
Reboot to test. If its still no better then run
```

sudo rm /etc/modprobe.d/rtl8723be_fix.conf

```
Then reboot again

---

### Post by aquaman101 on 2022-08-29
Brave attempt ActionParsnip, and thanks for your help - after running both your commands I had a stable couple of hours.
But again this morning within 15 minutes the same issue returns.

(One thing I did notice after the fault occurred, and I did the usual dis & reconnect the wireless connection - the connection was super-fast!)

Could you recommend any other non-debian distros in the hope it may fix this wireless adapter issue?

---

### Post by ActionParsnip on 2022-08-29
Fedora is decent IMHO

---

### Post by aquaman101 on 2022-08-29
> **ActionParsnip said:**
> Fedora is decent IMHO

Thanks

I think a change of distro is the only solution

---

