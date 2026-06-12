---
title: "Installing a Ethernet Adapter's Drivers."
date: 2008-06-24
forum: New to Ubuntu
---

### Post by DM was on fire! on 2008-06-24
...here we go again. XD
After finding an Encore 10/100Mbps Fast Ethernet PCI Adapter, my dad installed it and returned our Linksys Wireless G Adapter to the media computer in the living room.
I reactivated the eth2 card in my Networking (after disabling it in an attempt to get the wireless to work), set it as my default gateway...thing, and the interwebs are still not working. :\

There are drivers for Linux on the CD, and I attempted to compile them...emphasis on attempted.

I dragged the directory which the drivers are in (/media/cdrom0/Driver/ENL832_TX_ICNT/Linux) to my desktop (making it /home/ashleigh1992/Desktop/Linux) and ran the commands which it lists in the 2.6.x instructions:

>  #make all
      #insmod ./sundance.ko (or sundance.o)
      #ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy
            eth0 is your network adapter,use dmesg to check it, ex: eth0, eth1...
            xxx  is your ip address, ex: 192.168.102.211
            yyy  is your netmask address, ex:255.255.255.0  

When I run make all, I get some sort of error which I was too lazy to write down.
And technically, there is no sundance.ko or sundance.o files. :\
Help?

---

### Post by ibuclaw on 2008-06-24
sundance.ko would be made **after** you run make all. (Remember, "make all" compiles the sourcecode and outputs a kernel object file).

So you are missing some dependancies for which the driver must be compiled against. (This is usually some C compile libs and your current kernel header files).

Try
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

And run make all again.

Regards
Iain

---

### Post by cariboo on 2008-06-24
From the looks of it your nic is based on the rtl8139 chipset, it should be automatically detected and the module loaded. Shut you computer down, and maybe try unplugging it and then plugging it back in again and restart the computer.

Jim

---

### Post by pytheas22 on 2008-06-24
I'd be surprised if there's not already a driver for your ethernet card in the kernel.  Do you know which chipset it uses?  If not, what's the output of:
```

lspci
sudo lshw -C Network
```

I'd check on this before trying to compile from source.  Virtually every ethernet card in the world should "just work" in Linux now; if yours isn't I'd suspect some kind of configuration problem, not a missing module.

---

### Post by pytheas22 on 2008-06-24
> From the looks of it your nic is based on the rtl8139 chipset

If this is true and rebooting the computer doesn't fix the problem, try:
```

sudo rmmod 8139cp
sudo modprobe 8139too
```

and see if it works.  If it still doesn't, try:
```

sudo rmmod 8139too
sudo modprobe 8139cp
```

and see again.  I learned the other day that there are two different modules for the rtl 8139 chipset, and apparently sometimes the one that's used by default doesn't work.

It would still be nice to see lspci output to confirm that you do indeed have an 8139 chipset (why do you think that Jim)?

---

### Post by DM was on fire! on 2008-06-25
tinivole - Can't quite apt-get right now since I have no internet connection on this computer. :\
Only way for me to get it would be to install the .debs and save them on a floppy disk or have my dad burn them to a CD.

cariboo907 - I can't begin to tell you how many times I restarted that thing. :\

pytheas22 - Thank you. I will try those. :)

P.S.: To be honest with you, I have no clue in hell what the chipset is. XD

---

### Post by DM was on fire! on 2008-06-25
Okey dokey.
Terminal output, ahoy!

> ashleigh1992@ubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:0d.0 Ethernet controller: Sundance Technology Inc: Unknown device 0200 (rev 31)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
ashleigh1992@ubuntu:~$ sudo lshw -C Network
Password:
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: Sundance Technology Inc
       vendor: Sundance Technology Inc
       physical id: d
       bus info: pci@00:0d.0
       version: 31
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: ioport:d000-d07f iomemory:ef000000-ef0001ff irq:11
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth2
       version: 74
       serial: 00:01:29:42:9c:56
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:e800-e8ff iomemory:ef002000-ef0020ff irq:11


And then...

> ashleigh1992@ubuntu:~$ sudo rmmod 8139cp
ERROR: Module 8139cp does not exist in /proc/modules
ashleigh1992@ubuntu:~$ sudo modprobe 8139too


The latter command did NOT give me an output, and when I entered the next two you gave me, those did not give an output either. 
Still couldn't get online, though.

EDIT -

> sundance.ko would be made after you run make all. (Remember, "make all" compiles the sourcecode and outputs a kernel object file).

Whenever I ran make all, I got some sort of error output. I didn't think to copy it, though.

---

### Post by pytheas22 on 2008-06-25
After rereading your original post, I think I'm a little confused as to what you tried to do exactly.  I'm also increasingly inclined to believe that your problem is a configuration issue, not a driver problem. 
> 
I reactivated the eth2 card in my Networking (after disabling it in an attempt to get the wireless to work), set it as my default gateway...thing, and the interwebs are still not working. :\

First, what are eth0 and eth1?  Are they active?

Second, what do you mean by "default gateway?"  When the Network utility asks you what your gateway is, it doesn't mean an ethernet card on your computer.  It means the IP address of the gateway between your local network and the Internet, most likely your router.

Third, why did you use the Network utility to configure your card?  Unless you need to use a static IP or have other special requirements, you should just check the box to enable roaming mode and let Network Manager take care of your connection.  Is there anything unusual about your network, or do you have a normal setup using dhcp?

If the card is in roaming mode, does Network Manager say that you're connected and you just can't load web pages?  Or are you not connected at all?

If you post the output of these commands, it would be helpful for clarifying what's going on:
```

ifconfig -a
cat /etc/network/interfaces
dmesg | grep eth
```

---

### Post by DM was on fire! on 2008-06-25
eth0 and eth1 do not exist. The only two in the Network Admin are ppo0 and eth2. 
And by default gateway, I meant the little part on the bottom of the Network Admin where you pick your card...thing.
I think that's what it's called. ^^;;

The card...I *doubt* is in roaming mode, because it's not wireless. 
And whenever I try to ping anything, it says there's no connection (I fail to remember the exact words).
I'll try those and see what I get.

P.S.: Apologies for sounding so confusing. ^^;;

---

### Post by DM was on fire! on 2008-06-25
> ashleigh1992@ubuntu:~$ ifconfig -a
eth2      Link encap:Ethernet  HWaddr 00:01:29:42:9C:56
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ashleigh1992@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp


iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth3 inet static
address 192.168.2.100
netmask 255.255.255.0
wireless-essid RID0617
wireless-key 27B25843EO
gateway 192.168.2.1

auto eth3

auto eth2
ashleigh1992@ubuntu:~$ dmesg | grep eth
[17179598.012000] eth0: VIA Rhine II at 0x1e800, 00:01:29:42:9c:56, IRQ 11.
[17179598.012000] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[17179600.424000] eth2: link down
[17179640.760000] ADDRCONF(NETDEV_UP): eth2: link is not ready

(eth3 is no longer hooked up. I couldn't get it to work anyway. XD)

---

### Post by pytheas22 on 2008-06-25
There is a "roaming mode" for wired interfaces too (see my screenshot).  Check this box and see if NM will connect you.  If not, please try this and post output (you should only see something for the last command):
```

sudo -s
echo 'blacklist ipv6' >> /etc/modprobe.d/blacklist
dhclient eth2
```

---

### Post by DM was on fire! on 2008-06-27
That must've been something they did post-Dapper, because I don't have the option to turn on Roaming Mode.
I'll run those commands in a few minutes and post what I get. ^^

---

### Post by DM was on fire! on 2008-06-27
Alright.

> ashleigh1992@ubuntu:~$ sudo -s
Password:
root@ubuntu:~# echo 'blacklist ipv6' >> /etc/modprobe.d/blacklist
root@ubuntu:~# dhclient eth2
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth2/00:01:29:42:9c:56
Sending on   LPF/eth2/00:01:29:42:9c:56
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

### Post by pytheas22 on 2008-06-27
hmmmm

I'm not really sure where to go next.  I don't know why it's not working (I also didn't know you were still on Dapper; if there's any way to upgrade, that might fix the problem altogether).

I do notice, from the output of lshw -C Network, that you seem to have two ethernet cards (or possibly just one ethernet and one unused wireless).  It's a dumb question, but are you sure you have the cable plugged into the right one?

The only other thing I can suggest is that you try using [wicd]("http://wicd.sourceforge.net") to connect (make sure you specify in preferences the correct interface to use, eth2).  There's no particular reason why I think it will solve the problem, but wicd just tends to be "smarter" than the tools that come by default with Ubuntu.  But from all the output you've given me, I don't see where the problem is.

It's clearly not an issue of missing a driver, as you had originally thought, because if that were the case you wouldn't be able to bring the eth2 interface up at all.

I don't see anything in /etc/network/interfaces that would be causing a problem...although it might not hurt to remove the section at the end about eth3.

Everything seems to work; you just can't get an IP address.  Unless your router is screwing up and failing to give you one (did you try rebooting it and double checking that dhcp is turned on?), then I don't know where else to look.

---

### Post by DM was on fire! on 2008-06-28
I'd upgrade to Hardy like the rest of you peeps, but my video card has had a history of causing X to freeze on Gutsy, so I haven't taken a chance. :\
As for an upgrade to atleast Feisty, the only way for me to go about it would be to get a disk, but I don't believe there's an upgrade option on the LiveCD.

I'll try the other options you gave me...but in the meantime, I'll check into getting a flash drive to back up all my files and get a Feisty disk.

Thank you for all your help, Pytheas.

---

### Post by pytheas22 on 2008-06-28
Which video card do you have?  I'm sure that with a little research you could figure out whether or not there are problems with it in Hardy, and if so how to work around or solve them.  Keep in mind that Feisty support ends this October and Dapper ends next June; after that you're not going to be able to get updates or install software from the Ubuntu repositories.  Hardy support lasts till 2011.

The normal live CD doesn't have an upgrade option, but if you download the alternative CD (you just have to check a box for this on the download page), it comes with an option to upgrade an existing installation.  That said, I'm not sure that upgrading from Dapper to Hardy would go very smoothly; you might be better off with a clean install.

---

