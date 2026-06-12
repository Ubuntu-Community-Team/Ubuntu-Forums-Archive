---
title: "update problems"
date: 2005-03-04
forum: Repositories &amp; Backports
---

### Post by primeirocrime on 2005-03-04
I've intalled Ubuntu Hoary today

first I had prblems in the install where the installer searches for the repositories and hangs at half, like it couldn't download anything. So I had to re-install without Internet.
I'm using a Router/modem conected to a realtek gigabit NIC. I have another PC conected to the web, running XP and a Live CDs - ubuntu, knoppix, DyneBolic.

I can use the web after install, but not during the install process or else it will hang.
I've also had issues with [COLOR=DarkRed]IPv6[/COLOR] but did all the things and nothing improved except the disabling of ipv6 in about:config in firefox.

when I try to use Synaptic to update or change :
[CENTER][B]
[SIZE=2]synaptic[/SIZE] [/B][/CENTER]
> W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)



[CENTER][SIZE=2]**apt-get**[/SIZE][/CENTER]
> root@ubuntu:/home/mongrel # apt-get update
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha i386 Binary-1 (20050204) unstab le Release.gpg
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha i386 Binary-1 (20050204) unstab le Release
66% [Connecting to archive.ubuntu.com (1.0.0.0)]

[RIGHT]then it freezes..[/RIGHT]
I must state that I was a previous FC3 user and had the same issues when I changed to the router/modem ethernet thing, I was previously connected through speedtouch 330 usb and I used synaptic in fedora with no problems.

the router is configured through DHCP and It has firewall. Id this a case of inserting a port forwarding rule in the router??? if so what are the ports used by synaptic/apt-get? or is this the[COLOR=DarkRed] IPv6[/COLOR] issue???


[CENTER]
[SIZE=2]**ifconfig**[/SIZE][/CENTER]
> mongrel@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:FC:EB:D4:DD
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:feeb:d4dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:781772 (763.4 KiB)  TX bytes:266114 (259.8 KiB)
          Interrupt:11 Base address:0xf00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2392205 (2.2 MiB)  TX bytes:2392205 (2.2 MiB)




.
please help this poor guy that really likes ubuntu so I can update-

---

### Post by primeirocrime on 2005-03-04
and I've just tried DMZ rule on the firewall, and that didn't help...what is happening here? this is really strange.



[edit]

everything was fixed once I introduced the nameservers from the ISP on 

/etc/ resolv.conf and comented out the routers nameserver that clinged on by default. also I disabled Ipv6 in firefox and in gnome.

all is well here.
:-\"

---

### Post by djmaxmalta on 2008-04-15
hey all i am running gutsy gibbin and i got this message on updates adremove etc...

> Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

i done the sudo and synaptic and this what came

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

and i do it in terminal and this came 
> dpkg: requested operation requires superuser privilege

so what do i doo?

---

### Post by SnakeHips on 2008-04-15
```
sudo dpkg --configure -a
``` ?

---

### Post by djmaxmalta on 2008-04-16
:lolflag: that is a command that should run something and most probebly fix it but as usal there aint a linux for dummies book out yet and if there is it hasn't come in front of me!

---

### Post by SnakeHips on 2008-04-17
have you tried 

```
sudo apt-get update 
```

---

