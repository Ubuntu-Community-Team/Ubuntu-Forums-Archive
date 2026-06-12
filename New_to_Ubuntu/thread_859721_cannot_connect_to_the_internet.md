---
title: "cannot connect to the internet"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by zomw on 2008-07-14
Hi. I finally got Ubuntu 8.04 installed after the installer would not recognize my partitions correctly, only to figure out that I can't connect to the internet with a wired ethernet connection. I have a cable modem hooked up to a wireless router that I get my internet connection through. I multi-boot XP, Vista, and Ubuntu 8.04. The internet works flawlessly on XP and Vista. I've had previous versions of Ubuntu installed on my computer before, and the internet has worked most of the time, but sometimes not at all. I made [COLOR="Blue"]_[a thread almost exactly like this one]("http://ubuntuforums.org/showthread.php?t=445349")_[/COLOR] a while ago when I was having problems with Edgy. I fixed it by installing Feisty, but now I am having the same problems with Hardy. I have already tried most of the suggestions from my old thread, reinstalled four times (with 32/64bit and regular/alternate install CDs), and restarted my computer and modem/router setup countless times.

Any suggestions?

---

### Post by Melk79 on 2008-07-14
When you installed Ubuntu, did you first boot into the LiveCD and just use it for a bit?  I find it works best to do that and get the internet working before doing the full install.  If you're using ethernet, it really should work unless you're using something funky.  Post your CPU and setup details too.  Just for fun you could plug the ethernet in directly and bypass the router.

---

### Post by zomw on 2008-07-14
> **Melk79 said:**
> When you installed Ubuntu, did you first boot into the LiveCD and just use it for a bit?  I find it works best to do that and get the internet working before doing the full install.  If you're using ethernet, it really should work unless you're using something funky.  Post your CPU and setup details too.  Just for fun you could plug the ethernet in directly and bypass the router.

Yeah, I've tried to get the internet working before doing the full install but it has not worked. Basic setup details:

Motherboard - Nvidia nForce 680i SLI
CPU - Intel Core 2 Duo E6600
RAM - 2GB Corsair DDR2
Graphics - EVGA GeForce 8800GTS
Audio - Creative SB X-Fi
HDD - Western Digital Caviar 320GB

Forgot to mention it, but I've already tried plugging the ethernet cord directly into my computer (it didn't work). I was hoping that the router would be the problem, but I guess not.

**EDIT: BTW, my router is a Linksys Wireless-G 2.4GHz 54Mbps broadband router.**

---

### Post by fenian on 2008-07-14
Lets try to get it working with the wired connection first.Plug in the ethernet cord and rebooot then run the following command and post the results...

> ifconfig

---

### Post by zomw on 2008-07-14
> **fenian said:**
> Lets try to get it working with the wired connection first.Plug in the ethernet cord and rebooot then run the following command and post the results...

Output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:04:4b:00:d4:cd  

          inet addr:169.254.7.236  Bcast:169.254.255.255  Mask:255.255.0.0

          inet6 addr: fe80::204:4bff:fe00:d4cd/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:4869 (4.7 KB)

          Interrupt:221 Base address:0x2000 



eth1      Link encap:Ethernet  HWaddr 00:04:4b:00:d4:cb  

          inet addr:169.254.7.236  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:220 Base address:0x2000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2608 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2608 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:130400 (127.3 KB)  TX bytes:130400 (127.3 KB)


```

---

### Post by fenian on 2008-07-14
That doesn't seem correct.Can you boot into windows and check the ip address from there?

---

### Post by fenian on 2008-07-14
Also run the command...

> gedit /etc/network/interfaces 

and post the output.

---

### Post by zomw on 2008-07-14
> **fenian said:**
> That doesn't seem correct.Can you boot into windows and check the ip address from there?

IP Address: 71.82.0.219

---

### Post by zomw on 2008-07-14
> **fenian said:**
> Also run the command...and post the output.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

```

---

### Post by fenian on 2008-07-14
That also seems incorrect if you are connecting to a router.It should be something like 192.168.1.100  or 192.168.2.100

what happens if you open firefox and in the address bar enter...

192.168.1.1

or

192.168.2.1

---

### Post by fenian on 2008-07-14
That also seems incorrect if you are connecting to a router.It should be something like 192.168.1.100  or 192.168.2.100

what happens if you open firefox and in the address bar enter...

192.168.1.1

or

192.168.2.1

---

### Post by zomw on 2008-07-15
> **fenian said:**
> That also seems incorrect if you are connecting to a router.It should be something like 192.168.1.100  or 192.168.2.100

what happens if you open firefox and in the address bar enter...

192.168.1.1

or

192.168.2.1

In Ubuntu, Firefox says "Failed to connect." In Vista, Firefox asks for a username and password to connect to "WRT54G," which I'm guessing is my router?

---

### Post by dhughes on 2008-07-15
> **zomw said:**
> In Ubuntu, Firefox says "Failed to connect." In Vista, Firefox asks for a username and password to connect to "WRT54G," which I'm guessing is my router?

 Yes a WRT54G is a Linksys router, for the username try admin and for the password try nothing, blank if that doesn't work try it the other way around.

 Maybe someone, a neighbour, accessed your setup screen and changed the password. In that case press the reset button on the back of the router to go back to the default settings. And then encrypt or shut off wifi or the simple quick way just unscrew the antennas.

 Did you try just restarting the network?

 **sudo /etc/init.d/networking restart**

---

### Post by fenian on 2008-07-15
Yes 192.168.1.1 is the address of your router,it hands out addresses to connected computers ,these addresses would be like 192.168.1.100 or 192.168.1.101 (the last set of numbers changes for each computer).

In ubuntu go to the menu System>Administration>Network
Click the unlock button
Highlight Wired connection and click properties
Unncheck Enable Roaming
Set Configuration to Automatic Configuration (DHCP)

---

### Post by zomw on 2008-07-15
> **dhughes said:**
> Yes a WRT54G is a Linksys router, for the username try admin and for the password try nothing, blank if that doesn't work try it the other way around.

 Maybe someone, a neighbour, accessed your setup screen and changed the password. In that case press the reset button on the back of the router to go back to the default settings. And then encrypt or shut off wifi or the simple quick way just unscrew the antennas.

 Did you try just restarting the network?

 **sudo /etc/init.d/networking restart**

Ok, I tried that username and password and they worked. I did a firmware upgrade on the router just in case the router is the problem (although I don't think so because bypassing the router by plugging the modem directly into my computer didn't work). And yes, I've already tried that command countless times.

---

### Post by zomw on 2008-07-15
> **fenian said:**
> Yes 192.168.1.1 is the address of your router,it hands out addresses to connected computers ,these addresses would be like 192.168.1.100 or 192.168.1.101 (the last set of numbers changes for each computer).

In ubuntu go to the menu System>Administration>Network
Click the unlock button
Highlight Wired connection and click properties
Unncheck Enable Roaming
Set Configuration to Automatic Configuration (DHCP)

I've already tried that many times, but it has not worked. Thanks for the suggestion though.

---

### Post by zomw on 2008-07-15
bump

---

### Post by zomw on 2008-07-15
bump

---

### Post by zomw on 2008-07-15
Anyone?

---

### Post by zomw on 2008-07-15
bump

---

### Post by dhughes on 2008-07-15
> **zomw said:**
> Ok, I tried that username and password and they worked. I did a firmware upgrade on the router just in case the router is the problem (although I don't think so because bypassing the router by plugging the modem directly into my computer didn't work). And yes, I've already tried that command countless times.


 OK bypassing the router completely and it still doesn't work is important to know, ignore the router it's quite possible it's your ethernet card (or your ISP cancelled your account!) but I don't know what to tell you.

 The previous info you posted, the *ifconfig* output showing eth0 and eth1 with the same IP address was very odd. Maybe try **ifdown eth1** which would leave eth0 as the only network interface to see if that helps, maybe there is a conflict?

 If that doesn't work pretty much what I would do is, and you did most already:
 reboot, it never hurts
 check to see if the network card is recognized
 restart networking
 manually assign an IP but I'd do that with a router (your ISP may not like that!) **ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up**

---

### Post by zomw on 2008-07-16
> **dhughes said:**
> OK bypassing the router completely and it still doesn't work is important to know, ignore the router it's quite possible it's your ethernet card (or your ISP cancelled your account!) but I don't know what to tell you.

 The previous info you posted, the *ifconfig* output showing eth0 and eth1 with the same IP address was very odd. Maybe try **ifdown eth1** which would leave eth0 as the only network interface to see if that helps, maybe there is a conflict?

 If that doesn't work pretty much what I would do is, and you did most already:
 reboot, it never hurts
 check to see if the network card is recognized
 restart networking
 manually assign an IP but I'd do that with a router (your ISP may not like that!) **ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up**

Just to clarify, I multi-boot XP, Vista, and Ubuntu 8.04. The internet is working just fine in XP and Vista, so I don't think that it is a problem with the two integrated ethernet ports on my motherboard (and not a cancellation of my service either). I'll try **ifdown eth1** and manually assigning an IP address and get back to you.

---

### Post by dhughes on 2008-07-16
It's just a guess about the two network cards sharing an IP address, but I can't really see how that would happen, then again I don't know if it that's a problem or not.

 The hardware on your system obviously works since you dual boot (or triple boot I guess it is) Vista, XP and Ubuntu so if it's all good in Windows it's some sort of configuration or driver problem in Ubuntu but finding it shouldn't be this hard. Unless it all come down to a bad install since you did say *"I finally got Ubuntu 8.04 installed after the installer would not recognize my partitions correctly"*.

 You may be better off posting your question in the Network and Wireless section or maybe a mod will move this thread over there for you.

---

### Post by zomw on 2008-07-16
> **dhughes said:**
> It's just a guess about the two network cards sharing an IP address, but I can't really see how that would happen, then again I don't know if it that's a problem or not.

 The hardware on your system obviously works since you dual boot (or triple boot I guess it is) Vista, XP and Ubuntu so if it's all good in Windows it's some sort of configuration or driver problem in Ubuntu but finding it shouldn't be this hard. Unless it all come down to a bad install since you did say *"I finally got Ubuntu 8.04 installed after the installer would not recognize my partitions correctly"*.

 You may be better off posting your question in the Network and Wireless section or maybe a mod will move this thread over there for you.

I tried **ifdown eth1** and manually assigning an IP address and they didn't work. Just in case it was a bad install, I'm going to reinstall for the fifth time. 

Also, can a mod please move this thread over to the Network and Wireless section?

---

### Post by seagullplayer77 on 2008-07-16
Just for kicks, do you have any way of trying to get a wireless connection up? I don't think it'll happen if you can't get a wired one up and running, but you never know--it *is* Linux, after all :-)!

---

### Post by johnaaronrose on 2008-07-17
I am able to connect wirelessly using WPA2 on Hardy. I was able to connect wired using Gutsy. Not able to connect wired using Hardy. I've notified bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/243154](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/243154)

---

### Post by zomw on 2008-07-18
Ok, I tried reinstalling again and it didn't work. seagullplayer77, yes, I do have a way of trying to get a wireless connection up. I have a PCI-E Abit Airpace wireless card installed, but I've heard that it is hard to get working in Ubuntu. johnaaronrose, thanks for notifying the bug on Launchpad. Just to let everyone know, I am going on vacation tomorrow for several days and will most likely not be able to respond to any posts. But if anyone has any ideas and would like to post them, please do so that I can read them when I get back home.

---

### Post by zomw on 2008-07-23
Hey guys, I'm back home. Does anyone have an idea?

---

### Post by zomw on 2008-07-23
bump

---

### Post by gandaran on 2008-07-23
I don't know if this can help you, but it won't hurt to try.
sometime ago my isp give me a new speedtouch router, I made the pppoe setup in xp Internet explorer, it worked fine in windows, but when I booted ubuntu it didn't work. well I quickly fixed that, I reseted the router to factory settings, I typed the router configuration IP in ubuntu/firefox and setup the connection there, and you know what? it worked in both windows and ubuntu!
if it doesn't work try this using the live cd.
one question, you haven't installed a firewall, like firestarter?

---

### Post by halitech on 2008-07-23
> **gandaran said:**
> I don't know if this can help you, but it won't hurt to try.
sometime ago my isp give me a new speedtouch router, I made the pppoe setup in xp Internet explorer, it worked fine in windows, but when I booted ubuntu it didn't work. well I quickly fixed that, I reseted the router to factory settings, I typed the router configuration IP in ubuntu/firefox and setup the connection there, and you know what? it worked in both windows and ubuntu!
if it doesn't work try this using the live cd.
one question, you haven't installed a firewall, like firestarter?

Good point, I bet most people don't think about PPPoE on connections most of the time. 

OP, what is the brand of your router/internet modem?

---

### Post by zomw on 2008-07-23
> **gandaran said:**
> I don't know if this can help you, but it won't hurt to try.
sometime ago my isp give me a new speedtouch router, I made the pppoe setup in xp Internet explorer, it worked fine in windows, but when I booted ubuntu it didn't work. well I quickly fixed that, I reseted the router to factory settings, I typed the router configuration IP in ubuntu/firefox and setup the connection there, and you know what? it worked in both windows and ubuntu!
if it doesn't work try this using the live cd.
one question, you haven't installed a firewall, like firestarter?

gandaran, I've already tried doing that, but it didn't work. No, I haven't installed a firewall. Thanks for the suggestion though.

---

### Post by zomw on 2008-07-23
> **halitech said:**
> Good point, I bet most people don't think about PPPoE on connections most of the time. 

OP, what is the brand of your router/internet modem?

halitech, my modem is an Ambit modem my ISP gave me. My router is a Linksys WRT54G wireless router.

---

### Post by zomw on 2008-07-23
bump

---

### Post by stevoo on 2008-07-23
Let see 
the ip you get mean that you are not getting an ip .... 
the 169.
So on windows you get an ip
IP Address: 71.82.0.219
That means you connected directly to the internet.

So when you connect the computer is it on the router or on the modem ?

EDIT : 
Also try :
System -> Administration -> Network

Unlock that, by pressing unlock :dah:

There should be a tick by the Wired Connection
So select the Wired Connect and click Properties
Make sure the tick is there again and that the selected value is 
Automatic Configuration (DHCP)

---

### Post by zomw on 2008-07-23
> **stevoo said:**
> Let see 
the ip you get mean that you are not getting an ip .... 
the 169.
So on windows you get an ip
IP Address: 71.82.0.219
That means you connected directly to the internet.

So when you connect the computer is it on the router or on the modem ?

EDIT : 
Also try :
System -> Administration -> Network

Unlock that, by pressing unlock :dah:

There should be a tick by the Wired Connection
So select the Wired Connect and click Properties
Make sure the tick is there again and that the selected value is 
Automatic Configuration (DHCP)

I connect my computer to the internet via my wireless router. I tried the suggestion in your edit, but it didn't work. Thanks for the suggestion.

---

### Post by fenian on 2008-07-23
> IP Address: 71.82.0.219

This is not an address that would typically be assigned by a router (they usually begin with numbers like 192.168.1... or 192.168.2...)
This looks more like an address assigned by a modem directly.
So a few questions...

How does your modem connect to your router?
Do you have a static or Dynamic (DHCP)  I.P. address? (It is more common to have a Dyamic IP address.)

---

### Post by zomw on 2008-07-24
> **fenian said:**
> This is not an address that would typically be assigned by a router (they usually begin with numbers like 192.168.1... or 192.168.2...)
This looks more like an address assigned by a modem directly.
So a few questions...

How does your modem connect to your router?
Do you have a static or Dynamic (DHCP)  I.P. address? (It is more common to have a Dyamic IP address.)

Oops, that was my router's WAN IP address. I looked at my router's DHCP clients table, and the LAN IP address given to me by my router is 192.168.1.100.

---

### Post by halitech on 2008-07-24
open the terminal
```
ping 192.168.1.1
```
and
```
ping www.google.com
```

and post the info back here

---

### Post by zomw on 2008-07-24
> **halitech said:**
> open the terminal
```
ping 192.168.1.1
```
and
```
ping www.google.com
```

and post the info back here

Output of **ping 192.168.1.1**:
```
Destination Host Unreachable
```

Output of **ping [www.google.com](www.google.com)**:
```
Unknown Host [www.google.com](www.google.com)
```

---

### Post by halitech on 2008-07-24
do an ifconfig and see what you have for an IP address

---

### Post by zomw on 2008-07-24
> **halitech said:**
> do an ifconfig and see what you have for an IP address

Output of **ifconfig**:
```
eth0      Link encap:Ethernet  HWaddr 00:04:4b:00:d4:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:04:4b:00:d4:cb  
          inet6 addr: fe80::204:4bff:fe00:d4cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6503 (6.3 KB)
          Interrupt:253 Base address:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:04:4b:00:d4:cd  
          inet addr:169.254.7.236  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:252 Base address:0x6000 

eth1:avahi Link encap:Ethernet  HWaddr 00:04:4b:00:d4:cb  
          inet addr:169.254.7.226  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:253 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:172284 (168.2 KB)  TX bytes:172284 (168.2 KB)
```

---

### Post by OhioYJ on 2008-07-24
Did you disable IPv6, thats the first thing I do after fresh installs.

Run this in the terminal:

> sudo gedit /etc/modprobe.d/aliases

About the tenth line down you'll see the ...something... IPv6, delete "IPv6" and type "off". Save that file.

Then type this in:

> sudo gedit /etc/modprobe.d/blacklist

At the bottom of that file, add "blacklist ipv6", save it and restart Ubuntu. I think you'll find it works fine after that. (Of course this is 8.04, which I really don't think was ready for release yet......)

---

### Post by zomw on 2008-07-24
> **OhioYJ said:**
> Did you disable IPv6, thats the first thing I do after fresh installs.

Run this in the terminal:



About the tenth line down you'll see the ...something... IPv6, delete "IPv6" and type "off". Save that file.

Then type this in:



At the bottom of that file, add "blacklist ipv6", save it and restart Ubuntu. I think you'll find it works fine after that. (Of course this is 8.04, which I really don't think was ready for release yet......)

Thanks for the suggestion OhioYJ, but the internet is still not working. Do you have any other ideas?

---

### Post by halitech on 2008-07-26
you still don't have a valid IP address so the internet will not work

---

### Post by zomw on 2008-07-26
> **halitech said:**
> you still don't have a valid IP address so the internet will not work

Do you know how I could get a valid IP address?

---

### Post by halitech on 2008-07-26
your router or ISP should be giving you a valid IP. if its not, there are various reasons why it might not. have you checked the cables, the router lights (if you have one) rebooted the computer?

---

### Post by zomw on 2008-07-31
> **halitech said:**
> your router or ISP should be giving you a valid IP. if its not, there are various reasons why it might not. have you checked the cables, the router lights (if you have one) rebooted the computer?

Yes, I've checked everything and rebooted my computer countless times. Sorry for the delayed response; I've been busy recently.

---

### Post by dentaku65 on 2008-07-31
> **zomw said:**
> Do you know how I could get a valid IP address?

```
sudo dhclient
```

---

### Post by dave.com on 2008-11-11
I'm having this problem too. Only info I can add is that internet works (Hardy LiveCD desktop) at the boot-strapped Ubuntu installation. However, after that the system updates the kernel and installed packages: my internet clapped out thenceforth. 

Gnome reports an error at startup, the popup takes forever to 'solidify' (so I can close it), I assume this is a lack of net connection. There's something about smb shares and 'networking' that makes no sense to me, I can't navigate my way around the setup because I don't know wtf it is I am supposed to know.

My comp runs x1 realtek 100mb/s Ethernet into a 4-Port ADSL Modem-Router with wifi LAN through to cable out Wired wall-to-node. My comp also too runs XP on another drive as well and net connection, as you can see, is fine.

I have formatted and re-installed Ubuntu, the problem has repeated itself from the point at which it began previously without the long interval of fully functioning Ubuntu. I suspect whatever it is came in an update.

---

