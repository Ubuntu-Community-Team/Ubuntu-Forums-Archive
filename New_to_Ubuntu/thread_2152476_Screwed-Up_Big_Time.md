---
title: "Screwed-Up Big Time"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by krby0 on 2013-06-07
so i installed ubuntu on my laptop  from a CD, and i did so in a manner to wipe my old Windows OS because there werent any files i necessarily NEEDED to save. I was made aware that i should install some updates and such so i needed to connect to the internet next.

i cannot detect a wireless connection nor can i detect an ethernet cable. after fuddling around with this problem i came to the conclusion that i might have a driver missing or something, so i decided to reinstall the whole OS.



i loaded the CD In only to find that it wont boot from the CD drive nor from USB. it just boots straight to the hard drive. im at my wits end and i just dont know what to do anymore

but most importantly: I DONT KNOW IF FIXING THE ETHERNET PROBLEM IS WHERE I SHOULD FOCUS... or if reinstalling is the better bet... please help 



ill be checking back daily to post any other information or specs needed to aid me



thanks in advance!!

---

### Post by tgalati4 on 2013-06-07
First focus on a wired ethernet connection.  Open a terminal and examine the output of:

```
lspci | grep Ethernet
```

It might look like:

tgalati4@Mint14-Extensa ~ $ lspci | grep Ethernet
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI

We need to know your ethernet card before we can offer suggestions.

With the Live CD, one would normally check out the ethernet connectivity before installing.  Many times wireless will not work without fiddling, but wired tends to work OK.  If you have connectivity problems running the Live CD, then installing to a hard disk will be problematic.  As you have discovered.

This is a minor problem.  A much bigger problem is people accidently wiping out their Windows partition that they intended to keep.

---

### Post by krby0 on 2013-06-07
the result is as follows:
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet Controller (rev 05)

---

### Post by ahallubuntu on 2013-06-07
~

---

### Post by carl4926 on 2013-06-07
It would actually help to see the result of this
```
lspci -nnk | grep -iA2 net
```

---

### Post by krby0 on 2013-06-08
here is what "lshw -c network" gets me:

Description: Ethernet interface
Product: RTL8101E/RTL8102E PCI Express Fast Ethernet Controller
Vendor: Realtek Semiconductor Co., Ltd.
pshyical id: 0
bus info:. pci@0000:05:00.0
logical name: eth0
version: 05
serial:18:03:73:58:28:7f
size: 1GB/s
capacity:1GB/s
width: 64 bits
clock: 33MHz
Capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet pysical fire 1000bt-fd autonegotiation
Configuration:autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no module=r8169 multicast=yes port=fibre speed=1GB/s
*-network unclaimed
description: Network controller
product: Intel Corporation
vendor: Intel Corporation
physical id:0
bus info:. pci@0000:09:00.0
version:34
version:34
width 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration :latency=0
*network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: f6:45:b7:0e:6f:c4
capabilities: ethernet physical
configuration:broadcast= yes driver=bridge driverversion=2.3 firmware=N/A link= yes multicast=yes

---

### Post by krby0 on 2013-06-08
and here is what "lspci -nnk | grep -iA2 net" gets me

05:00.0 Ethernet controller [0200] : Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet Controller [10ec:8136] (rev 05)
Kernel driver in use: r8169
kernel modules: r8169
09:00.0 Network controller [0280]: intel Corporation Device [8086:008a] (rev 34)
0b:00.0 USB Controller [0c03]: NEC Corporation Device [1033:0194] (rev 04)

---

### Post by carl4926 on 2013-06-08
Looks like the hardwire is OK

---

### Post by ahallubuntu on 2013-06-08
~

---

### Post by krby0 on 2013-06-08
the result of ifconfig is:

eth0    Link encap:ethernet HWaddr 18:03:73:58:28:7f
          UP BROADCAST MULTICAST MTU: 1500 Metric:1
          RX packets: 83 errors: 0 dropped: 0 overruns: 0 frame: 0
          TX packets: 0 errors: 0 Dropped: 0 Overruns: 0 carrier: 0
          collisions: 0 txqueuelen: 1000
          RX bytes: 20142 (20.1 KB) TX bytes: 0 (0.0 B)
          Interrupt: 245 Base adress: 0xc000

lo       Link encap: Local Loopback
         inet addr: 127.0.0.1 Mask: 255.0.0.0
         inet6 addr: ::1/128 Scope:host
         UP LOOPBACK RUNNING MTU: 16436 Metric: 1
         RX packets; 12 errors: 0 dropped: 0 overrun: 0 frame: 0
         TX packets: 12 errors: 0 dropped: 0 overruns: 0 carrier: 0
         Collisions: 0 txqueuelen: 0 
         RX bytes: 720 (720.0 B) TX bytes: 720 (720.0 B)

---

### Post by Sef on 2013-06-08
> [COLOR=#000000]eth0 Link encap:ethernet HWaddr 18:03:73:58:28:7f[/COLOR]
[COLOR=#000000]UP BROADCAST MULTICAST MTU: 1500 Metric:1[/COLOR]

Between those two lines, there should be an internet address, broadcast address and subnet mask.

Was a cable plugged in or were you on wireless?

---

### Post by krby0 on 2013-06-09
i ran the command a few extra times with the same result as i posted.

yes the cable is plugged in. and also yes i do have wireless in the house and so do my neighbors. yet the network manager cant seem to detect any, let alone the cable plugged in

---

### Post by steeldriver on 2013-06-09
what is the cable plugged in *to*? is it a router or a modem? normally Ubuntu is good at setting up a default wired connection if there's a router that supplies a basic configuration via DHCP, but if you don't have that then some manual intervention may be required to set a valid IP address and so on

---

### Post by krby0 on 2013-06-10
its connected to a cable that runs through the house and that cable leads to a router which all the other computers connect to

---

### Post by steeldriver on 2013-06-10
well there should be some relevant messages in the dmesg log, so try this command in a terminal

```
dmesg | grep eth0
```

and if possible post back the output (I realize it's hard without a network connection - but you can redirect it to a file and then attach that via a usb stick or something)

```
dmesg | grep eth0 > dmesg.eth0
```

---

### Post by krby0 on 2013-06-11
the result of the first code is:
[      8.609033] eth0: RTL8169 at 0xf7c7c000, 18:03:73:58:28:7f, XID 40a00000 IRQ 2293
[     22.989038] r8169; eth0: link down
[     22.989113] ADDRCONF (NETDEV UP): eth0: link is not ready
[    244.608889] r8169: eth0: link down
[    246.973440] r8169: eth0: link down
[    249.254002] r8169: eth0: link down

the result for the other code never came up. i tried the eth0 > dmesg.eth0 but nothing happens.
also i would save the lines to a USB drive and transfer the info to my desktop... however i cant open the USB drive on my laptop... wont let me mount it :/

---

### Post by krby0 on 2013-06-15
is there any way i can bump this thread?

bump

---

### Post by steeldriver on 2013-06-15
Well the dmesg output suggests the eth0 interface is just not coming up - I don't know much about that Realtek device, it *may* be one of those that happily loads the r8169 driver but actually needs r8168 (which you may need to install manually, I'm not sure)

---

### Post by krby0 on 2013-06-16
sooo what does that mean? i mean... what should i do?

---

### Post by carl4926 on 2013-06-17
Just going back to the start - before you installed...
Did the eth0 wired connection work in the live session?

---

### Post by krby0 on 2013-06-17
I dont know what you mean by live session but the eth0 has never worked in Ubuntu on this laptop. the wired and wireless connections however did work on this laptop when it ran Windows Vista. my connectivity stopped when i installed Ubuntu over the default Windows OS

---

### Post by carl4926 on 2013-06-17
> **krby0 said:**
> I dont know what you mean by live session but the eth0 has never worked in Ubuntu on this laptop. the wired and wireless connections however did work on this laptop when it ran Windows Vista. my connectivity stopped when i installed Ubuntu over the default Windows OS

The Live session is what you experience when you boot the CD before you have actually installed.
You might actually see the option: [https://dl.dropboxusercontent.com/u/10573557/Ubuntu/ubuntu_boot/2013-02-10%2008.42.25.jpg](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/ubuntu_boot/2013-02-10%2008.42.25.jpg)
When you Try it, which you should. You get to see what works or Not. It can help you decide if Ubuntu is a good choice for a particular machine.

---

### Post by GregA on 2013-06-17
Here's a link to a Ubuntu forum thread, dealing with ethernet connectivity issue, for users with the same network hardware you have.   Note that there are "two" separate solutions in this thread.  Read closely and try each one.  

[http://ubuntuforums.org/archive/index.php/t-975406.html](http://ubuntuforums.org/archive/index.php/t-975406.html)

If this works - the next step is to fix wireless.  I would first try the Ubuntu application that is usually titled:  "Additional Drivers" (sometimes called "restricted drivers").  In Kubuntu, it's located at "Kmenu>System>Additional Drivers" . . . not sure where at in Ubuntu, but just search for it.

Another solution for easy wireless connectivity is to get a Linux compatible "USB Wireless Adapter" (cost is between 7 or 8 usd to about 25 usd for better models.)   See the graphic below:

[[IMG]http://imageshack.us/scaled/large/6/6xk.png[/IMG]](http://imageshack.us/photo/my-images/6/6xk.png/)

In your case, I would first try the Airlink AWL5088 - - for wireless, it works great in Ubuntu and is plug and play.  (get via amazon or similar source).

Kindly advise your progress . . . .

---

### Post by krby0 on 2013-06-23
ok so i tried the :
dkpg -i <linux-kernel>
command but the terminal only returned that there was no such directory, so i tried replacing the "linux-kernel" part with "ubuntu-9.04" and "ubuntu9.04" and alot of other combonations. i even removed the brackets to make sure everything went according to syntax. but all with the same outcome. so when i input the "eth0 up" command nothing happened.

so i tried the second solution of editing my network interface by replacing the lines: 
auto lo
iface lo inet loopback

with the lines

auto eth0
iface eth0 inet dhcp

still nothing...

---

### Post by zrdc28 on 2013-06-23
ifconfig eth0 essid networkname
dhcpcd -d eth0

Should get your eth0 going, then "apt-get update" and apt-get upgrade" after that we will get wireless going.

When you did the install you should always get the network going before the install, look for it in the top right
hand corner and click on it.

---

### Post by krby0 on 2013-06-24
i tried the fist command and the output was 

essid: unknown host

then just for kicks i tried the "dhcpcd" command, and the output was

dhcpcd is currently not installed, you csn install it by typing: sudo apt-get install dhcpcd

but when i did that the output was: "couldnt find package dhcpcd"

---

### Post by krby0 on 2013-06-26
look if you guys think i really screwed up im not opposed to wiping everything on the laptop and starting back at square one :-<

---

### Post by VMC on 2013-06-26
> **krby0 said:**
>  ...
i **cannot detect a wireless connectio**n nor can i detect an ethernet cable. after fuddling around with this problem i came to the conclusion that i might have a driver missing or something, so i decided to reinstall the whole OS.

i loaded the CD In only to find that **it wont boot from the CD drive nor from USB**. it just boots straight to the hard drive. im at my wits end and i just dont know what to do anymore

...!

Going back to the first post, have you checked your BIOS settings? Maybe they got changed in all this mess.  Find if there are any disable feature on the wireless, also check about devices that may be turned off, cd, usb, etc.

---

### Post by krby0 on 2013-06-27
I just checked my BIOS settings and nothing butUSB wake support and computrace seem to be disabled...

---

### Post by krby0 on 2013-06-30
i really dont know what else to do :/

---

### Post by steeldriver on 2013-06-30
I recommend you start a new thread in the Networking and wireless subsection, including your lspci and lshw outputs - you can include a link to this thread if you like. Also what version of Ubuntu you installed (maybe I missed that).

I had a quick look at the link that GregA posted but I couldn't tell if it was relevant to your situation - and it seemed like it might be out of date (~2008). In any case it's not clear exactly what steps you performed or what deb file you downloaded - it's important to be EXACT with the commands you type and if they don't work post back with the EXACT error message(s)

You will also need to change back your /etc/network/interfaces file since removing the lo definition will break a lot of stuff

```

auto lo
iface lo inet loopback

```

Your problems booting from CD / USB are BIOS issues not Ubuntu issues

---

