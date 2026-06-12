---
title: "Vnc and filebrowsing"
date: 2015-10-11
forum: New to Ubuntu
---

### Post by Hakan__Venderlof on 2015-10-11
Hello
I have  a lan with 2 wincomputers and and new installed with
Ubuntu 15.4.
How do I install VNC on it (viewer and server)?
How can i make the ubuntu computer seen on my lan?
ATM i cant even ping it...
Greetings   
Zdubair

---

### Post by TheFu on 2015-10-11
I can't tell how much you know about networking. Hopefully this is helpful.

If the Linux machine cannot be pinged - why not? 
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has troubleshooting steps.

Simplified explanations:
IP is the networking used by Unix. It has been around since the 1970s and is a world-wide standard for almost all platforms with networking.

TCP/IP - which you've probably heard of before is what VNC uses.  TCP requires connections between the 2 systems. That means for "A" to contact "B", it needs to either use the IP address or have some sort of "phone book" to lookup the name and return the IP address. That is performed using either **DNS** or through an on-system lookup file, /etc/hosts.  Windows has this file too - actually, every networked OS has a file with exactly the same format - iOS, Android, BeOS, OS/2, DOS, .... and all flavors of Unix and Linux and OSX. 

On linux systems, please use **sudoedit /etc/hosts** to modify the hosts file.  Other methods may not be as safe.

[http://www.howtogeek.com/howto/27350/beginner-geek-how-to-edit-your-hosts-file/](http://www.howtogeek.com/howto/27350/beginner-geek-how-to-edit-your-hosts-file/)  is a professionally written article that might help. Please ignore their suggestion to use any GUI tool to edit hosts files. This can be very dangerous.  You can set the EDITOR variable and use  sudoedit with any editor, however. That is safe.

Of course, you'll want each of these machines to have static IPs on your LAN. [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) explains a way to let your home router do this while leaving DHCP enabled. Enjoy.

For anything you don't understand, wikipedia has an article with a good explanation. Or ask us.

---

### Post by Hakan__Venderlof on 2015-10-11
Tx for you answer  :-)

Ping to my router works,  also 8.8.8.8 and DNS works.


When I do this
```
dmesg |grep eth[0-9]
sudo lshw -C network
ifconfig -a
more /etc/resolv.conf
route 
```

i get this:

```
description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:24:21:5a:ad:fb
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.139 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:25 ioport:de00(size=256) memory:fdbff000-fdbfffff memory:fdb00000-fdb1ffff
zdubair@Tanzany:~$ 

```

Well, i dont understand much of that  lol

Greetings  Zdubair

---

### Post by TheFu on 2015-10-11
a) please use code tags - edit the post above
b) please copy/paste the command AND the output. We need to see the exact command.
c) Please provide the other command outputs.

Looks like your ubuntu system is working perfectly.  Can you ping the windows machines and can the windows machines ping the linux machine by IP and by name?  Copy/paste output please and explain which machine is which.

---

### Post by Hakan__Venderlof on 2015-10-11
about > [COLOR=#000000]Looks like your ubuntu system is working perfectly. Can you ping the windows machines and can the windows machines ping the linux machine by IP and by name? Copy/paste output please and explain which machine is which.

Yes  all  seems ok in ubuntu computer and also in my windows computers -  only problem is they dont see each other.
I cant get ping response in any direction.[/COLOR]

---

### Post by Hakan__Venderlof on 2015-10-11
[COLOR=#000000]What is code tags?    a) please use code tags - edit the post above[/COLOR]
[COLOR=#000000]
This puzzels me:
b) please copy/paste the command AND the output. We need to see the exact command.[/COLOR]
[COLOR=#000000]c) Please provide the other command outputs.


I though i pasted all but i will do it again...

[/COLOR]

---

### Post by Hakan__Venderlof on 2015-10-11
i write in terminal:
```
#dmesg |grep eth[0-9]

sudo lshw -C network

ifconfig -a

more /etc/resolv.conf

route#
```


i get answer

```
#  

zdubair@Tanzany:~$ dmesg |grep eth[0-9]
[    0.956500] r8169 0000:01:00.0 eth0: RTL8101e at 0xf8426000, 00:24:21:5a:ad:fb, XID 94200000 IRQ 25
[   24.621187] r8169 0000:01:00.0 eth0: link down
[   24.622830] r8169 0000:01:00.0 eth0: link down
[   26.188539] r8169 0000:01:00.0 eth0: link up
zdubair@Tanzany:~$ 
zdubair@Tanzany:~$ sudo lshw -C network
[sudo] password for zdubair: 
Sorry, try again.
[sudo] password for zdubair: 
sudo: 1 incorrect password attempt
zdubair@Tanzany:~$ ^C
zdubair@Tanzany:~$ 

#

```
and
```

#

*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:24:21:5a:ad:fb
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.139 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:25 ioport:de00(size=256) memory:fdbff000-fdbfffff memory:fdb00000-fdb1ffff

#
```

---

### Post by bapoumba on 2015-10-11
Code tags : [http://ubuntuforums.org/faq.php?faq=vb3_reading_posting#faq_vb3_basic_bb_code](http://ubuntuforums.org/faq.php?faq=vb3_reading_posting#faq_vb3_basic_bb_code)
From the FAQ in Quick Links :)

Edit : and it is better to post each full output under each relevant command.

---

### Post by Hakan__Venderlof on 2015-10-11
Somehow i got pings and file transfer working...  tx for your help.

Still trying to make VNC work.

---

