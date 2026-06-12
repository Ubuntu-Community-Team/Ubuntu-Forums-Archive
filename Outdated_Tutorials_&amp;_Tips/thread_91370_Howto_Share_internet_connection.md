---
title: "Howto Share internet connection"
date: 2005-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by anaoum on 2005-11-17
Hello,

The following will explain how to share your Internet connection:

Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

    # ifconfig ethX ip      

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

    # iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE       

where ethX is the network card that the Internet is coming from 

    # echo 1 > /proc/sys/net/ipv4/ip_forward

3. Install dnsmasq and ipmasq using apt-get: 

    # apt-get install dnsmasq ipmasq

4. Restart dnsmasq:

    # /etc/init.d/dnsmasq restart

5. Reconfigure ipmasq to start after networking has been started:

    # dpkg-reconfigure ipmasq

6. Repeat steps 1 and 2.

7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

    # gedit /etc/sysctl.conf

8. Reboot. (Optional)

I hope this helps.

Good luck!

---

### Post by Squirreli on 2005-11-17
By following your instructions (after a long while spent at the ages-old art of trial-and-error ;) I got as far as this:

eth0 connects me to the Internet.
eth2 connects me to my winxp machine.
ping gets reply both ways and my winxp is hosting ftp server which is reachable.
winxp firewall is disabled (just in case)

Xp machine, however, does NOT reach Internet. Possible reason for this could be in the way I've set up the xp machine's networking. You did not give specifics as to how those should be set up, but I've tested both fixed ip and DHCP. Also, the networking adapters and cables im using are reliable... Any ideas?

-Squirreli

PS. I do have a slight virus problem on the XP machine's lsass.exe, but it connects to Internet just fine when there's no linux box between it and the Internet, so I don't believe that to be the trouble.

---

### Post by anaoum on 2005-11-18
Hello,

On your winxp machine configure it with a static ip (make it similar to the ip on your server. eg if server ip is 192.168.0.1, then make your ip 192.168.0.10). Also make sure that you set the "Default Gateway" and "Preffered DNS" to the ip on your ubuntu machine (the one that's sharing the internet connection). It should work fine after that.

Good luck

---

### Post by Squirreli on 2005-11-18
Ha! Now it works. 
Setting default gateway didn't help, but didn't do any harm either. Setting preferred DNS server did the trick... So, these XP comp tcp/ip settings made it work.
-fixed ip:192.168.0.1 (subnet mask 255.255.255.0)
-default gateway:192.168.0.2
-preferred DNS server:192.168.0.2

Paljon kiitoksia/Thank you very much ;)

-Squirreli

---

### Post by anaoum on 2005-11-18
No worries. I'm glad it has helped!

---

### Post by nicholaspaul on 2005-12-04
I'm having some fun with this - 
set up is a PPC laptop that needs the internet from a x86 desktop (which gets the internet with ath0 , a wifi adapter, and is sharing with eth0), both running Breezy. Is it a matter of just changing Network settings? 

So far, the laptop can ping x86 when static IP and DNS is set to the x86 IP (192.168.0.2), but cant get to the internet. Also x86  cant get to the internet while eth0 is activated .
Should I also change submasks?

PLUS  when I restart dnsmasq I get : 

Restarting DNS forwarder and DHCP server: dnsmasqstart-stop-daemon: warning: failed to kill 8006: Operation not permitted
rm: cannot remove `/var/run/dnsmasq.pid': Permission denied
dnsmasq: failed to bind listening socket: Permission denied
 (failed to start).

I'm also using a crossover cable - thats right isnt it?

---

### Post by anaoum on 2005-12-04
Hello nicholaspaul,

Make sure that the subnet masks on your ppc are set to 255.255.255.0.

Also make sure that the Default Gateway on the ppc is set to the ip of the x86 (192.168.0.2)

About restarting dnsmasq, are you sure you are executing the command as root user?

---

### Post by nicholaspaul on 2005-12-04
Hi anaoum
Yea... :( tried all that.  x86 still can't get to the internet unless I deactivate eth0 even tho ath0 is the default gateway device. 

So the full story is:
_ x86 _
**ath0: **

Static IP: 192.168.0.102
Subnet: 255.255.255.0
Gateway Address: 192.168.0.1 [the address of my wireless router]

**eth0:**

Static IP: 192.168.0.2
Subnet: 255.255.255.0
Gateway Address: 192.168.0.1 

**Default Gateway Device:** ath0



_PPC Laptop_

**eth0: **

Static IP: 192.168.0.2
Subnet: 255.255.255.0
Gateway Address: 192.168.0.2
DNS: 192.168.0.102
Search domain: home (the name of the intranet)
---------------------------------------------------
Should I change search domains on the PPC?

---

### Post by nicholaspaul on 2005-12-04
[QUOTE=anaoum]

2. Then configure the NAT as follows:

    # iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE       

where ethX is the network card that the Internet is coming from 

    # echo 1 > /proc/sys/net/ipv4/ip_forward
[/QUOTE]
Oh wait a minute - should ethX be the interface that gets x86 the internet, or the one I'm sharing with?

---

### Post by varunus on 2005-12-04
The Firestarter firewall can do all of this for you, by the way...

```
sudo apt-get install firestarter
```

Its just a frontend to iptables.

In its preferences, set "internet connected device" to the internet, and "local network device" to the local device.  Then enable NAT and DHCP if you want...

---

### Post by anaoum on 2005-12-05
[QUOTE=nicholaspaul]Oh wait a minute - should ethX be the interface that gets x86 the internet, or the one I'm sharing with?[/QUOTE]

When executing this command :  # iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

You should use ath0 instead ethx, as it is the network interface that your internet connection is comming from.

---

### Post by stole_mkd on 2005-12-25
Well, i have this big problem. I set up my Ubuntu Pc ( wich has two network cards, one for the internet(eth0) and one for my other XP Pc(eth1)) with masqurade from a forum ([http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/))  but still can't get the xp to get to the internet. Then i saw this forum. Much easyier. But, i cannot download the dnsmasq or the other mentioned file in the tuttorial. Can someone please explain me where to download how to install the files and can the setup i made before get in the way of getting the other computer to the internet. Please.

---

### Post by hatstand on 2006-01-03
Right. Tried all that. Didn't work, though I appreciate your efforts.

Here's my problem. I run Ubuntu and the wife runs XP. We have one wired cable internet connection. We want to share it. I naively thought that buying a switch would simply give me some and her some. Well, whichever computer boots forst gets the connection and the other has none (although XP states "limited connectivity but doesn't connect to anything").

So I looked here. I first ran Firestarter. Great but you cannot have eth0 as both "internet connected Device" and "local network connected device". It instead detects something called sit0 that it promptly says is not ready. I can't find any onformation on how to make it ready.

I installed samba: no change.

Then I tried this handy thread. It assumes that you can have a static IP address. I apparently cannot: as soon as I set a static IP address (192.168.0.1) and the (255. thing follows automatically), I lose the internet, even after reboot. If I change it back to DCHP it works immediately.

SO the question is: how do I get the XP box to access the internet when I am accessing it on ubuntu?

My connection goes like this:

cable modem --- switch --- ubuntu + XP

---

### Post by anaoum on 2006-01-04
Hello,

You have got this set up completely wrong. It is ment to be:

Cable Modem >> Ubuntu >> Switch >> XP

And you must make sure that your ubuntu pc has two network interfaces (one to the modem, and another to the switch).

The way you are currently trying to set up, you could simply use a router instead of a switch:

Cable Modem >> Router >> XP + Ubuntu

This is a lot easier(no need to install any client software), however you must purchase a Router.

Tell me which configuration you would prefer and i can help you out...

---

### Post by anaoum on 2006-01-04
[QUOTE=stole_mkd]Well, i have this big problem. I set up my Ubuntu Pc ( wich has two network cards, one for the internet(eth0) and one for my other XP Pc(eth1)) with masqurade from a forum ([http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/))  but still can't get the xp to get to the internet. Then i saw this forum. Much easyier. But, i cannot download the dnsmasq or the other mentioned file in the tuttorial. Can someone please explain me where to download how to install the files and can the setup i made before get in the way of getting the other computer to the internet. Please.[/QUOTE]

Make sure you have set up your repositories correctly: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by hatstand on 2006-01-04
[QUOTE=anaoum]Hello,

You have got this set up completely wrong. It is ment to be:

Cable Modem >> Ubuntu >> Switch >> XP

And you must make sure that your ubuntu pc has two network interfaces (one to the modem, and another to the switch).

The way you are currently trying to set up, you could simply use a router instead of a switch:

Cable Modem >> Router >> XP + Ubuntu

This is a lot easier(no need to install any client software), however you must purchase a Router.

Tell me which configuration you would prefer and i can help you out...[/QUOTE]

NOW I see!

However, there is only one ethernet entrance to the inux machine.:-( 

I tried it with the USB entrance but although it recognised a "eth1", it did not work under static or DHCP.

---

### Post by anaoum on 2006-01-04
So now you have two options:

1. Buy a new Ethernet card for your ubuntu pc.

2. Buy a router.

I think a router is much simpler to set up. however buying a new ethernet card is cheaper...

it's your decision...

---

### Post by hatstand on 2006-01-04
[QUOTE=anaoum]So now you have two options:

1. Buy a new Ethernet card for your ubuntu pc.

2. Buy a router.

I think a router is much simpler to set up. however buying a new ethernet card is cheaper...

it's your decision...[/QUOTE]

Not what I wanted to hear, but thanks anyway. think I'll do a bit of searching to see if I can use the USB port for the modem before splashing out $140!

---

### Post by anaoum on 2006-01-04
[QUOTE=hatstand]Not what I wanted to hear, but thanks anyway. think I'll do a bit of searching to see if I can use the USB port for the modem before splashing out $140![/QUOTE]

A free ethernet card shouldnt be that hard to find, and even if you were to buy one, it wouldnt cost much more than $15.

A router is a little more expensive, but not as expensive as $140. You should be able to find one for about $50.

Check out: 

[http://www.radioshack.com/product/index.jsp?productId=2104283&cp=&pg=2&kw=ethernet+card&parentPage=search](http://www.radioshack.com/product/index.jsp?productId=2104283&cp=&pg=2&kw=ethernet+card&parentPage=search)

and
 [http://www.radioshack.com/product/index.jsp?productId=2117844&cp=&pg=1&y=8&kw=router&x=14&s=A-StorePrice-RSK&parentPage=search](http://www.radioshack.com/product/index.jsp?productId=2117844&cp=&pg=1&y=8&kw=router&x=14&s=A-StorePrice-RSK&parentPage=search)

Good luck!

---

### Post by stole_mkd on 2006-01-04
[QUOTE=anaoum]Make sure you have set up your repositories correctly: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)[/QUOTE]

Well, i tried that, didn't work, reinstalled it, and did that again, didn't work. I have another information that i didn't shared before. If i don't add these lines there is no internet. In order that i add them:
1. ifconfig eth0 down hw ether 00:0B:6A:9A:FA:AE
2.ifconfig eth0 up
3.route add default gw 172.19.0.1 dev eth0

after that i have internet, but the XP still does not have internet.

Need some help. PLEASE.

---

### Post by stole_mkd on 2006-01-04
Got some luck. Now, when i ping google.com from my XP it resolves it's address but doesen't get pong or replay. It say's Request timed out. How to set up completly the XP computer and the Ubuntu. Where do u think is the problem.

---

### Post by anaoum on 2006-01-04
Hello,

On your XP machine make sure that you set the "Default Gateway" and "Preffered DNS" to the ip on your ubuntu machine. If you could ping google, then you have connection to the internet, but XP doesent know.

---

### Post by hatstand on 2006-01-05
[QUOTE=anaoum]A free ethernet card shouldnt be that hard to find, and even if you were to buy one, it wouldnt cost much more than $15.

A router is a little more expensive, but not as expensive as $140. You should be able to find one for about $50.

Check out: 

[http://www.radioshack.com/product/index.jsp?productId=2104283&cp=&pg=2&kw=ethernet+card&parentPage=search](http://www.radioshack.com/product/index.jsp?productId=2104283&cp=&pg=2&kw=ethernet+card&parentPage=search)

and
 [http://www.radioshack.com/product/index.jsp?productId=2117844&cp=&pg=1&y=8&kw=router&x=14&s=A-StorePrice-RSK&parentPage=search](http://www.radioshack.com/product/index.jsp?productId=2117844&cp=&pg=1&y=8&kw=router&x=14&s=A-StorePrice-RSK&parentPage=search)

Good luck![/QUOTE]


Unfotunately in Mexico the prices are MUCH higher: radioshack only do one router which is $1400MN ($140US) and steren do one for $130US. Que lástima. Voy a buscar una tienda de computación para comprar una tarjeta de ethert, supongo.

---

### Post by hatstand on 2006-01-07
[QUOTE=anaoum]Hello,

You have got this set up completely wrong. It is ment to be:

Cable Modem >> Ubuntu >> Switch >> XP

And you must make sure that your ubuntu pc has two network interfaces (one to the modem, and another to the switch).

The way you are currently trying to set up, you could simply use a router instead of a switch:

Cable Modem >> Router >> XP + Ubuntu

This is a lot easier(no need to install any client software), however you must purchase a Router.

Tell me which configuration you would prefer and i can help you out...[/QUOTE]

OK. I bought and installed an ethernet card (the cheapest wired router here in Mexico is $140 US), so now my Ubuntu box has 2 ethernet cards. They both work on DHCP.

My set up is now:

Cable Modem>>>>Ubuntu eth0>>Ubuntu eth1>>>>Switch>>>>XP Box

All with straight through cables (apart of course from eth0 to eth1!)

Windows XP fins a connection but cannot connect to the internet. When i run ifconfig I get this:

eth0      Link encap:Ethernet  HWaddr 00:A1:B0:00:48:28
          inet addr:10.135.1.97  Bcast:10.135.31.255  Mask:255.255.224.0
          inet6 addr: fe80::2a1:b0ff:fe00:4828/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1051 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1952135 (1.8 MiB)  TX bytes:140228 (136.9 KiB)
          Interrupt:16 Base address:0xa000

mat@ubuntu:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:11:2F:2C:2D:51
          inet6 addr: fe80::211:2fff:fe2c:2d51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10816 (10.5 KiB)  TX bytes:7560 (7.3 KiB)
          Interrupt:23 Base address:0xe400

Do I need a static IP address?

---

### Post by hatstand on 2006-01-07
BUMP!

Please help! I'm going mad!

Using Firsetarter, I can now ping both computers. My eth0 connects to the cable modem. My eth1 gives this under ifconfig eth1:

eth1      Link encap:Ethernet  HWaddr 00:11:2F:2C:2D:51
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe2c:2d51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:32907 (32.1 KiB)  TX bytes:3812 (3.7 KiB)
          Interrupt:23 Base address:0xe400

Where I assigned the address myself.

So the computers are communicating, it seems. So why can't Internet Explorer on the XP box access the internet?

Please help!

---

### Post by hatstand on 2006-01-07
and then it magically worked...

Didn't change anything: I think it just needed time to get t's little head around the fact that it's sharing.

---

### Post by zappa86 on 2006-01-08
I have an ssh server on my computer. and after I did the internet connection sharing I can not ssh into it. what must I do?
My network is set up with a router that connects to the internet. The router has wireless which goes to 2 computers (including the one which I want to ssh from). The router also has a hub which goes to my main computer which I did the ip forwarding on. that computer has 2 eth cards on it. From the 2nd card, it goes  into a hub and goes to 2 old POS computer. After I enabled the ip forwarding I can not ssh from a computer connected to the wireless router to my main computer, or either of the 2 POS computers behind it. However the 2 computers behind my main one (and itself) can both access the internet. Lastly, my main computer can ping the 2 old computers behind it, however it can not ping my wireless router (which it could before) or the other computers connected by wireless.

---

### Post by stole_mkd on 2006-01-08
Can anyone tell me what information do u need me to put here so u can see what the problem might be.

---

### Post by dcstar on 2006-01-29
[QUOTE=anaoum]Hello,

The following will explain how to share your Internet connection:
........
    # echo 1 > /proc/sys/net/ipv4/ip_forward
........[/QUOTE]
And if you want this to "stick" **after a reboot**, edit /etc/sysctl.conf and add the following line:

net.ipv4.ip_forward = 1

---

### Post by anaoum on 2006-01-29
[QUOTE=dcstar]And if you want this to "stick" **after a reboot**, edit /etc/sysctl.conf and add the following line:

net.ipv4.ip_forward = 1[/QUOTE]

i have never had to do this. but if you think it is neccasary i will add it to the how to.

---

### Post by Chris Tucker on 2006-02-11
does this pass DHCP through? in my setup this is going to be essential. 
DHCP server (10.251.81.254 i believe, not positive) --> only one cat5 rout available -> (eth0) linux system for serving some audio/timekeeping purposes -> (eth1) linux system for serving some audio/timekeeping purposes -> windows XP machine that MUST get its IP from 10.251.81.254, and no i dont mean spoofed. the windows systems on this network in question are all on a domain, run by a remote admin, so no configs can be changed on those, so everything must pass through...
i would check myself but i am not at that setup right now, its the weekend.. ive been trying to mockup this setup but so far unsuccessfull because one of the nics i have here at home is causing problems, picking up another today.

---

### Post by anaoum on 2006-02-11
This will not pass through DHCP. Since you have a DHCP server i suggest you buy a switch.

---

### Post by Chris Tucker on 2006-02-11
[QUOTE=anaoum]This will not pass through DHCP. Since you have a DHCP server i suggest you buy a switch.[/QUOTE]
there are dozens of switches on that net, but the building will not shell out money just to give this one system net access... 
perhaps i could make it work O.K. with a static ip.. but i must ask, will this block any standard traffic? like if the PC is transferring files via windows shares through the linux box bridge, to a server named lets say //SWIFT ... would that get interrupted? thats the biggest thing... aswell as domain logins... allthough i dont know if that computer is set up to either.. id have to check it out. long story short that box needs to have complete and uninterrupted access to the network... the software that the secretary runs on that system i cant imagine binds itself to any ports for inbound connections, as very very VERY few ports are forwarded inside this place, only things like VNC to 8 computers, and vidphone/vidphone remote admin. so i dont think that will cause a problem. 

i'll try it anyway.

---

### Post by Rizado on 2006-02-12
Using Firehol makes configurating iptables so much easier.

---

### Post by tymczas on 2006-03-04
How can I set this internet connection sharring automaticly (I am asking about the first post in this topic)? I am using Xubuntu 5.10

---

### Post by halfbakedntx on 2006-03-08
This was hugely helpful for me thanks! 

I bought a cheap Fry's 1 day special GQ PC for 99.00 LOL.. Update the Ram to 392 megs for 30 bux. Bought an Airlink 101 AWLH4030 Wireless Super G PCI card for get this $17.99 (again onsale). Ubuntu detects it immidiately on install. SHWEET! So this GQ pc is plugged in behind my entertainment center. I VNC into it and have the sound card plugged into the RCA input on my stereo. I use StreamTuner to listen to ShoutCasts through the Stereo and record them to Mp3 with Streamripper. Create playlists in XMMS and basically have a jukebox I VNC into from the laptop at the coffee table or Kitchen to play tunes. I plugged in my 250 Gig Maxtor loaded with MP3s and add to the collection recording Shoutcasts.. SWEET! I plan to order a touch screen monitor add on and build a touchscreen interface at the entertainment center to make playlists/downloads there. Gotta find a nice Mp3 jukebox heh.. Ontop of all that I plug in my Xbox into the built in NIC on the 99.00 GQ PC and followed your instructions to route it to the wireless Netgear gateway. I have a verizon FiOS Fiber ISP connect 15mbs down 2mbs up. The damn Xbox wireless nic was 99.00 in itself. Needless to say THIS IS A SHWEET setup. Again thanks for the help! ;-)

---

### Post by george.aprozeanu on 2006-03-24
I managed to get it working without the "ipmasq" package. I understand that "dnsmasq" would enable me to act as a nameserver proxy, but what does ipmasq do (that -j MASQUERADE doesn't do) ?

Other than that, excelent job... worked like a dream!

---

### Post by LordMerlin on 2006-03-27
Hello everyone!

I got the iBurst up and running, with the pppoeconf command :)

So, I setup Linux as a PDC, DHCP, caching DNS server, and want it to route internet traffic for the LAN

My setup is as follows:


iBurst Modem (pppoe connection - get's IP from ISP - 196.2.108.xxx)
              |
              |
              |
eth0 (192.168.0.2)
              ||
Linux box
              ||
eth2 (192.168.10.1 - running DHCP)
              |
              |
              |
24 port hub
          |              |                |                   |     |
XP PC 1         XP PC 2      XP PC 3        etc etc

The XP PC's can ping 192.168.10.1 & 192.168.0.1, but not 196.2.108.xxx, nor for example google.com. I tried running
"iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE", but that doesn't seem todo anyting. In fact, I followed the Howto Share internet connection

Can somone please assit me with this?

---

### Post by B0rsuk on 2006-03-29
[QUOTE=anaoum]
And if you want this to "stick" after a reboot, edit /etc/sysctl.conf and add the following line:

net.ipv4.ip_forward = 1
[/QUOTE]

For some reason it doesn't work for me.
I use ethernet connection with 2 eth cards and a gateway.  I did it right after fresh reinstall, because I messed something up last time and couldn't fix it. *
I did it exactly as described in first post, and the connection is shared...
... but it's gone as soon as I restart. I have to type these commands from root each time, and it got old quickly. What could possibly be wrong ? How to nail it down ?




* I had to reinstall, because I used "ifconfig eth0 192.168.0.1" instead of "ifconfig eth1 192.168.0.1".  As a result, I destroyed my own connection instead of sharing it. I tried to fix it using both GUI from system settings and some old Debian manual. Now it's fixed, because I reinstalled Kubuntu... But how do I fix such humiliating mistake in the future ?

---

### Post by rcmiv on 2006-03-29
[QUOTE=anaoum]Hello,

The following will explain how to share your Internet connection:

<snip>

I hope this helps.

Good luck![/QUOTE]

anaoum - 

Great information.  Worked perfectly on my network, which is no standard setup.

I use a usb cable modem, and after several failed attempts, I have never bothered to drill down to get it working properly in linux.  After reading this thread, I tossed a Dapper FL5 Live CD into the machine which connects to the internet (and still runs win98 so I can use proxy+ share internet - no longer!), and after running through these steps, and modprobing the proper modules for usbnet, I was off.  (ten minutes)

Fantastic.  Brilliant.  You have no idea how helpful this is.  For this family network it is literally a paradigm shift.  Being no networking guru (and having little interest in learning the sqeaky details), I have been proxy serving internet to all of my machines for years, and it's been a real wicked pain.

Wow.  Thanks.

-rcmiv

---

### Post by dcast on 2006-03-30
I had a couple of questions. Am I right in thinking that i would be able to share to more than one computer say one ubuntu and one windows. Also could i do this if I had a usb modem (dsl). Also I dont have a static IP but that won't affect this will it?

---

### Post by rcmiv on 2006-04-01
[QUOTE=dcast]I had a couple of questions. Am I right in thinking that i would be able to share to more than one computer say one ubuntu and one windows. Also could i do this if I had a usb modem (dsl). Also I dont have a static IP but that won't affect this will it?[/QUOTE]

Yes. You have to have an ethernet card in your pc in addition to your cable modem.

I did a fresh install of dapper FL6 on a machine last night and was able to see my usb cable modem as eth1 and my network card as eth0.

I was then able to activate eth1 (the cable modem) with the following:

sudo /sbin/modprobe usbnet
sudo /sbin/modprobe cdc-acm

NOTE: these commands did _not_ work for me on breezy.  Breezy saw only one eth device which was my network card, and I could not get the cable modem to function.

Then I followed the steps in this thread to setup iptables, and voila, all of the machines on my network (windows and linux) on the same hub were able to direct connect to the internet by using the newly installed machine as a router.

The steps in this thread have you set the cable modem eth device to use DHCP to establish ip, in other words it obtains the ip from your isp, and you set the network card to a static ip for the other comps on your network to use.

Brilliant.

-rcmiv

---

### Post by calcium79 on 2006-04-14
Um, okay, I have a weirder situation...
___________________-> Dads Windows PC
ADSL modem -> router
___________________-> My Ubuntu PC -> My Windows PC
I did this guide and the net works through all pcs no problem. My Windows PC can share files with my Ubuntu PC. My Ubuntu PC can share files between my dads PC and my Windows PC. My Dads PC can share files with my Ubuntu PC. However, my Dads PC cannot reach my Windows PC, or vice versa.
Is there something else I need to add onto this?

---

### Post by tomski on 2006-04-14
Hi all,
i was wondering if any of you guys had tried a similar approach to this using a bridge/firewall (server install of ubuntu with shorewall) on the linux box that shares the connection;
  i have successfully set up a router/firewall with a linux box but i need a few pointers with a bridge setup, i have tried it but i think i got it wrong because i could not see the internet from behind the bridge i followed the instructions in the shorewall pdf but no joy

any suggestions

---

### Post by pjebr on 2006-04-27
Hi,

I did these steps and my computer with windows cant access the internet... just some sites like Google. For example, i cant access [www.globo.com](www.globo.com)... but i can ping this site.

In the another computer (with linux) i can access any site without problems. So, what i did wrong?

My network is like this:

*Linux* (computer with adsl and 2 network cards)
**eth0**
ip: xxx.xxx.xxx.xxx
subnet mask: 255.255.0.0
gateway: xxx.xxx.xxx.xxx

**eth1**
ip: 192.168.0.1
subnet mask: 255.255.255.0

*Windows*
**eth0**
ip: 192.168.0.2
subnet mask: 255.255.255.0
gateway: 192.168.0.1

---

### Post by LordMerlin on 2006-04-28
What does your routing table on Linux look like? And can you run a tracert to say google.com on your windows box?

From linux:
```
route -nv
```

From windows:
```
tracert google.com
```

And does your ADSL have NAT?

---

### Post by pjebr on 2006-04-28
Result of route -nv
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
201.14.143.254  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         201.14.143.254  0.0.0.0         UG    0      0        0 ppp0

```

I just tried to access some sites in my windows machine and now its just working fine :confused:

I dont know why wasnt working before... btw, when i restart my computer i need to run "pon dsl-provider" in the terminal... and i configured to start in boot. How can i fix it?

Ah, i forgot to say... my modem is bridge... this will afect something?

---

### Post by CameronCalver on 2006-04-29
Hey this is my problem i have a home computer which runs breezy and it has an eth card which a cable goes to a 7 port hub then i have a computer which i just made which also has a cable going to the hub and it runs breezy 2 and  the home computer has a ktx extenal dial up modem which connects to computer via serial port and i would like to share internet any1 no how i would do it and i dont no the ip address or anything of any of the computers can some1 help me

---

### Post by mybers on 2006-04-30
[QUOTE=anaoum]Hello,

On your winxp machine configure it with a static ip (make it similar to the ip on your server. eg if server ip is 192.168.0.1, then make your ip 192.168.0.10). Also make sure that you set the "Default Gateway" and "Preffered DNS" to the ip on your ubuntu machine (the one that's sharing the internet connection). It should work fine after that.

Good luck[/QUOTE]


Hello 

Kinda still new on this so i hope ud help me as well on this.

Im connected to a wifi/DSL line with gives me a Dynamic IP to my ubuntu (internet sharing server). I followed the earlier post and it did installed everything i hope.

This Ubuntu PC connects to the internet nicely but my Winxp and other Linux PC wont have any access yet. Probably still having problems with what is the right settings I should set up on those workstations?

My eth1=connects to the DSL (set to DHCP), Default gateway
      eth0= connects to the LAN network (set to DHCP)

what should I set in for the Winxp Lan card?
How can I get /validate the DNS server and or the Gateway?:-k 

Thanks a lot! hope this post is understandable...:) 


mybers

---

### Post by sheila on 2006-05-08
hi!!! to tell you the truth, i don't have that much knowledge in networking so please explain to me in simple terms with regards to my problem. i hope you can help me with this.here it is.

we set-up a LAN in our office but the Internet service provider only gave us 1 ip add so the entire network is using only 1 ip add. Now, my boss wanted each pc to have a unique ip add. I tried to reconfigure the router but the result is i cant connect to the internet..

what is the step by step procedure in configuring the router so that each pc can have its own ip add...?

pls help!!!

thanks!!

---

### Post by tuga on 2006-05-16
Thank you anaoum.
After checking "how to start a root shell" with:
sudo -i
I followed your howto and it just worked perfectly.

---

### Post by Braynid on 2006-05-26
Hello,
I have followed the How to until

Install dnsmasq and ipmasq using apt-get:

# apt-get install dnsmasq ipmasq

Then i get:
apt-get install dnsmasq
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package dnsmasq

I really don't know where i could find dnsmasq or ipmasq.
Thanks.

---

### Post by anaoum on 2006-05-26
make sure you have all the repos enabled

---

### Post by smoothunit on 2006-05-31
Hi guys,
Ive followed the fantastic guide on page 1 of this thread and am still experiencing a slight problem.

My windows box can only connect to IP's and not names ie [www.google.com](www.google.com) and also when i reboot all connectivity to xp is lost.

I can gain a connection again by following the steps at the start of the post so no biggie, but I would love to know whats going on with my xp box connecting via ip only.

I can post all settings if needed.

Once again any help would be greatly appreciated.

Alex.

---

### Post by anaoum on 2006-06-01
on the windows box check that the dns server is set to the ip of the ubuntu box

---

### Post by RavenOfOdin on 2006-06-01
Or. . .

You can just use a router and save yourself one heck of a mess. :p

---

### Post by anaoum on 2006-06-01
Yes, a router is very conveniant. BUT using a pc as a router allows you to do much more things......

---

### Post by calande on 2006-06-03
Doesn't work at all :(

charles@ubuntu:~$ ifconfig eth0
eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:13:D4:02:E1:04
          inet end.: 192.168.0.1  Bcast:192.168.0.255  Masc:255.255.255.0
          endereço inet6: fe80::213:d4ff:fe02:e104/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          RX packets:757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:759 errors:0 dropped:0 overruns:0 carrier:0
          colisões:0 txqueuelen:1000
          RX bytes:491663 (480.1 KiB)  TX bytes:119066 (116.2 KiB)
          IRQ:185

charles@ubuntu:~$ iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables v1.3.3: can't initialize iptables table `nat': Permission denied (you m ust be root)
Perhaps iptables or your kernel needs to be upgraded.
charles@ubuntu:~$ sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
Password:
charles@ubuntu:~$ sudo echo 1 > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permissão negada
charles@ubuntu:~$ echo 1 > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permissão negada
charles@ubuntu:~$ chmod 777 /proc/sys/net/ipv4/ip_forward
chmod: mudando permissões de `/proc/sys/net/ipv4/ip_forward': Operação não permi tida
charles@ubuntu:~$ sudo chmod 777 /proc/sys/net/ipv4/ip_forward
charles@ubuntu:~$ echo 1 > /proc/sys/net/ipv4/ip_forward
bash: echo: write error: Operação não permitida
charles@ubuntu:~$ cd /proc/sys/net/ipv4/ip_forward
bash: cd: /proc/sys/net/ipv4/ip_forward: Não é um diretório
charles@ubuntu:~$ cd /proc/sys/net/ipv4/
charles@ubuntu:/proc/sys/net/ipv4$ ls -l
total 0
dr-xr-xr-x 7 root root 0 2006-06-03 16:22 conf
-rw-r--r-- 1 root root 0 2006-06-03 16:22 icmp_echo_ignore_all
-rw-r--r-- 1 root root 0 2006-06-03 16:22 icmp_echo_ignore_broadcasts
-rw-r--r-- 1 root root 0 2006-06-03 16:22 icmp_errors_use_inbound_ifaddr
-rw-r--r-- 1 root root 0 2006-06-03 16:22 icmp_ignore_bogus_error_responses
-rw-r--r-- 1 root root 0 2006-06-03 16:22 icmp_ratelimit
-rw-r--r-- 1 root root 0 2006-06-03 16:22 icmp_ratemask
-rw-r--r-- 1 root root 0 2006-06-03 16:22 igmp_max_memberships
-rw-r--r-- 1 root root 0 2006-06-03 16:22 igmp_max_msf
-rw-r--r-- 1 root root 0 2006-06-03 16:22 inet_peer_gc_maxtime
-rw-r--r-- 1 root root 0 2006-06-03 16:22 inet_peer_gc_mintime
-rw-r--r-- 1 root root 0 2006-06-03 16:22 inet_peer_maxttl
-rw-r--r-- 1 root root 0 2006-06-03 16:22 inet_peer_minttl
-rw-r--r-- 1 root root 0 2006-06-03 16:22 inet_peer_threshold
-rw-r--r-- 1 root root 0 2006-06-03 16:22 ip_autoconfig
-rw-r--r-- 1 root root 0 2006-06-03 16:22 ip_conntrack_max
-rw-r--r-- 1 root root 0 2006-06-03 16:22 ip_default_ttl
-rw-r--r-- 1 root root 0 2006-06-03 16:22 ip_dynaddr
-rwxrwxrwx 1 root root 0 2006-06-03 16:22 ip_forward
-rw-r--r-- 1 root root 0 2006-06-03 16:22 ipfrag_high_thresh
-rw-r--r-- 1 root root 0 2006-06-03 16:22 ipfrag_low_thresh
-rw-r--r-- 1 root root 0 2006-06-03 16:22 ipfrag_secret_interval
-rw-r--r-- 1 root root 0 2006-06-03 16:22 ipfrag_time
-rw-r--r-- 1 root root 0 2006-06-03 16:22 ip_local_port_range
-rw-r--r-- 1 root root 0 2006-06-03 16:22 ip_nonlocal_bind
-rw-r--r-- 1 root root 0 2006-06-03 16:22 ip_no_pmtu_disc
dr-xr-xr-x 6 root root 0 2006-06-03 16:22 neigh
dr-xr-xr-x 2 root root 0 2006-06-03 16:22 netfilter
dr-xr-xr-x 2 root root 0 2006-06-03 16:22 route
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_abc
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_abort_on_overflow
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_adv_win_scale
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_app_win
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_congestion_control
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_dsack
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_ecn
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_fack
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_fin_timeout
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_frto
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_keepalive_intvl
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_keepalive_probes
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_keepalive_time
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_low_latency
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_max_orphans
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_max_syn_backlog
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_max_tw_buckets
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_mem
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_moderate_rcvbuf
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_no_metrics_save
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_orphan_retries
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_reordering
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_retrans_collapse
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_retries1
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_retries2
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_rfc1337
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_rmem
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_sack
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_stdurg
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_synack_retries
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_syncookies
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_syn_retries
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_timestamps
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_tso_win_divisor
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_tw_recycle
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_tw_reuse
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_window_scaling
-rw-r--r-- 1 root root 0 2006-06-03 16:22 tcp_wmem
charles@ubuntu:/proc/sys/net/ipv4$ cat ip_forward
0
charles@ubuntu:/proc/sys/net/ipv4$ sudo nano ip_forward
charles@ubuntu:/proc/sys/net/ipv4$ sudo nano ip_forward
charles@ubuntu:/proc/sys/net/ipv4$ sudo apt-get install dnsmasq ipmasq
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
Pacotes sugeridos :
  resolvconf midentd oidentd mc bridge-utils
Os NOVOS pacotes a seguir serão instalados:
  dnsmasq ipmasq
0 pacotes atualizados, 2 pacotes novos instalados, 0 a serem removidos e 155 não  atualizados.
É preciso fazer o download de 227kB de arquivos.
Depois de desempacotamento, 1118kB adicionais de espaço em disco serão usados.
AVISO : Os pacotes a seguir não podem ser autenticados !
  ipmasq dnsmasq
Instalar estes pacotes sem verificação [s/N] ? s
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper/universe ipmasq 4.0.6
  404 Not Found
Obtendo:1 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper/universe dnsmasq 2.25-1 [150kB]
Baixados 150kB em 20s (7453B/s)
Falha ao baixar [http://br.archive.ubuntu.com/ubuntu/pool/universe/i/ipmasq/ipmas](http://br.archive.ubuntu.com/ubuntu/pool/universe/i/ipmasq/ipmas) q_4.0.6_all.deb  404 Not Found
E: Impossível pegar alguns arquivos, talvez rodar apt-get update ou tentar com - -fix-missing?
charles@ubuntu:/proc/sys/net/ipv4$ sudo apt-get install dnsmasq ipmasq
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
Pacotes sugeridos :
  resolvconf midentd oidentd mc bridge-utils
Os NOVOS pacotes a seguir serão instalados:
  dnsmasq ipmasq
0 pacotes atualizados, 2 pacotes novos instalados, 0 a serem removidos e 155 não  atualizados.
É preciso fazer o download de 76,7kB/227kB de arquivos.
Depois de desempacotamento, 1118kB adicionais de espaço em disco serão usados.
AVISO : Os pacotes a seguir não podem ser autenticados !
  ipmasq dnsmasq
Instalar estes pacotes sem verificação [s/N] ? s
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper/universe ipmasq 4.0.6
  404 Not Found
Falha ao baixar [http://br.archive.ubuntu.com/ubuntu/pool/universe/i/ipmasq/ipmas](http://br.archive.ubuntu.com/ubuntu/pool/universe/i/ipmasq/ipmas) q_4.0.6_all.deb  404 Not Found
E: Impossível pegar alguns arquivos, talvez rodar apt-get update ou tentar com - -fix-missing?
charles@ubuntu:/proc/sys/net/ipv4$ /etc/init.d/dnsmasq restart
bash: /etc/init.d/dnsmasq: Arquivo ou diretório não encontrado
charles@ubuntu:/proc/sys/net/ipv4$ sudo gedit /etc/apt/sources.list
charles@ubuntu:/proc/sys/net/ipv4$ sudo apt-get install dnsmasq ipmasq
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
E: Impossível achar pacote dnsmasq
charles@ubuntu:/proc/sys/net/ipv4$ sudo apt-get install dnsmasq ipmasq
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
E: Impossível achar pacote dnsmasq
charles@ubuntu:/proc/sys/net/ipv4$ sudo apt-get install dnsmasq ipmasq
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
E: Impossível achar pacote dnsmasq
charles@ubuntu:/proc/sys/net/ipv4$ dpkg-reconfigure ipmasq
/usr/sbin/dpkg-reconfigure deve ser rodado como root
charles@ubuntu:/proc/sys/net/ipv4$ sudo dpkg-reconfigure ipmasq
Pacote `ipmasq' não está instalado e não há informações disponíveis.
Use dpkg --info (= dpkg-deb --info) para examinar arquivos do pacote,
e dpkg --contents (= dpkg-deb --contents) para listar seu conteúdo.
/usr/sbin/dpkg-reconfigure: ipmasq não está instalado
charles@ubuntu:/proc/sys/net/ipv4$

---

### Post by anaoum on 2006-06-03
Do not execute commands using sudo!

First change to root user by using "sudo -s- H" then execute the commands.

---

### Post by calande on 2006-06-03
Thank you, actually after updating here it worked fine. Why can't I use sudo? Is it unsecure? :rolleyes:

---

### Post by Gobboman on 2006-06-04
I followed the guide and it worked perfectly.  I had a similar problem as one of the other guys on here.  None of the changes stick.  I have to run all those commands every time after I reboot.

oh.. and is net.ipv4.ip_forward = 1 the same as the commented out line in the sysctl.conf file  net/ipv4/ip_forward=1  ?

](*,)

---

### Post by Nyala on 2006-06-17
Has anyone tried this with a wireless card for the local network? My wireless router died, so I'm trying to set up my Ubuntu PC in its place:

cable modem --> (eth0 lan card) Ubuntu PC (eth1 wifi card) --> several wifi computers on the local net

Seems like it would be fairly common to want to use a linux box as a wireless router, but I can't seem to find any helpful information. As soon as I set wifi eth1 to a static IP address, my Ubuntu box can no longer surf the Net. 

I'm also not sure if setting an ESID and password in the networking control panel, which is usually used when ubuntu is a client of a wifi network, will work when it's acting as the wifi router.

Thanks for any info or helpful pointers you can provide.

-Dustin-

---

### Post by donotspamme on 2006-06-21
Hi folks!
Could someone please help me with this one:

I have used my linux box (with mandrake) as a proxy server for quite a some time, but I got fed up with mandarin's log filling problem I couldn't fix.

Now I'm trying to get the network shared with breezy. The setup is following:

ADSL modem-->(DHCP,eth0)_ubuntu computer_(192.168.0.1,eth1)-->scwitch-->
(192.168.0.x)several computers (with static ips)

The problem is: IT IS NOT WORKING GODDAMMIT!!! ](*,)  I have tried everything mentioned on this thread as well in other similar threads, It has took me sweat, time and blood, but still nothing. I'd like to know what could be wrong. all the computers are able to ping each other, but the inner computers simply can't reach the internet. I'm getting a little frustrated here... :confused: 

please help me, I need to get this to work... many angry people are standing behind me and waiting... :(

---

### Post by BrowneR on 2006-06-29
Great HOW-TO! Thankfully after much messing around and about an hour of tweaking i have it working for me.

My question however is **why!?** i would love to understand the dynamics of how it all works under the hood.

from what I can gather...
      1) we have added a rule to iptables which forwards packets from one subnet (eth1) to the internet (eth0) - acting as a NAT
      2) dnsmasq listens for dns lookups on the ubuntu router pc and forwards them to my isp's dns servers - ie. acting as the gateway
      3) ipmasq does something to do with translating ip's between the two interfaces...? however i cant really see why this is needed if packets are already being forwarded by an iptables rule?

If anyone can clear this up for me that would be great :)

TIA

Chris

---

### Post by BrowneR on 2006-06-29
also as a second thought could something similar not be acheived by simply bridging the two interfaces (apparently this is easy with the bridge-utils package?) as long as you are either using static ip's or running a dhcp server as well.

---

### Post by mchojrin on 2006-07-30
I'm trying to share my internet connection but when I use the command apt-get install dnsmasq ipmasq I get the message E: Couldn't find package dnsmasq
 :(

---

### Post by tuga on 2006-08-06
mchojrin,
You have to enable the repositories:
System->Administration->Synaptic->Settings->Repositories...

---

### Post by rrsarge on 2006-08-09
Lost newbie -

I have a Ubuntu laptop w/ wireless to internet (eth1) and unused ethernet (eth0). Would like to plug IP phone into unused ethernet (eth0) and get to internet via wireless (eth1). I tried the instructions at the beginning of this post - seemed to have no problems executing commands in root term, but still no worky.

I found after following the instructions (and reboot) my unused ethernet (eth0) still had DHCP selected - shouldn't it have been assigned the ip I put in 'ifconfig eth0 ip'?

Also, eth0 shows no network connection, even though I've plugged it into a router and another PC via crossover.

Please help!

---

### Post by TheGamingPit on 2006-08-10
Thank you very much...I have been trying to do this for over a week now.  This one finally did it and the only difference I could find was that in yours you had ```
net.ipv4.ip_forward = 1
``` instead of ```
net/ipv4/ip_forward=1
```
I hope this helps others.

---

### Post by DeonaLyn on 2006-08-11
Hi - this is the same set-up that we have here (except that we have Ubuntu 6.06 loaded on)... we are able to get the internet working with the 'how-to listed'.. finally after struggling with trying to do it on our own for a week, see [post 1367460 ]("http://ubuntuforums.org/showthread.php?p=1367460")](*,) ; but having to use the dynamic IP set on the windows XP boxes.  The dynamic IPs is a better option because we have LAN parties where folks bring their PCs and hook up to our system and the Linux machine should be handing out IPs for them, rather than us having to manually configure all the machines every time. Has anyone got a fix for why the DHCP portion of this code isn't working?  We are pppoe dependent and don't have a static IP from our ISP. I am a real newbie to Linux, but my techie employees convinced me that Linux & Ubuntu is the way to go!! Reading the forums, the help guides and the literature I agree - but there is quite a learning curve :) 

Also, each time we load firestarter to add in the firewall protection, the whole system crashes, so will be trying the direct format, rather than the gui - unless someone has a better suggestion based on our structure...

As a side note - I am really impressed by the support and community that the Ubuntu community shows.  It beats the heck out of what I have seen in the 'other' community! :D 

Deanna

> **LordMerlin said:**
> Hello everyone!

I got the iBurst up and running, with the pppoeconf command :)

So, I setup Linux as a PDC, DHCP, caching DNS server, and want it to route internet traffic for the LAN

My setup is as follows:


iBurst Modem (pppoe connection - get's IP from ISP - 196.2.108.xxx)
              |
              |
              |
eth0 (192.168.0.2)
              ||
Linux box
              ||
eth2 (192.168.10.1 - running DHCP)
              |
              |
              |
24 port hub
          |              |                |                   |     |
XP PC 1         XP PC 2      XP PC 3        etc etc

The XP PC's can ping 192.168.10.1 & 192.168.0.1, but not 196.2.108.xxx, nor for example google.com. I tried running
"iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE", but that doesn't seem todo anyting. In fact, I followed the Howto Share internet connection

Can somone please assit me with this?

---

### Post by dagothempirius on 2006-08-24
I can't get firestarter to download, I want to share my internet connection to my lan. I'm using Dapper 6.06

---

### Post by dagothempirius on 2006-08-24
Is this still functioning under dapper? Because I can't download firestarter, I want to share my internet connection to my lan.

---

### Post by anaoum on 2006-08-24
$ sudo apt-get install firestarter

---

### Post by dagothempirius on 2006-08-24
> **dagothempirius said:**
> Is this still functioning under dapper? Because I can't download firestarter, I want to share my internet connection to my lan.

Already did that, am I missing something?

---

### Post by .Danny on 2006-08-31
Thanks for the great guide. It worked without problems. However I'm left with 1 problem that doesn't seem to work. I can ping all websites fine, and they work in my browser. However as soon as I try to open a https website it doesn't work.

Any idea why?

---

### Post by BrowneR on 2006-08-31
if there is no problem surfing to standard http sites then i dont think the problem is related to the nat you have just setup on your router.

you will want to make sure there are no restrictions in place on port 443 on any firewalls you are using (dont see why there would be though).

failing that more likely there is a problem with the browser you are using. make sure it is setup to use TLS and SSL (usually in the browsers options). what browser are you using? you could possibly try with another and see if that sorts things out.

you may also like to try directly connecting the effected pc to the internet (without the router) and see if that fixes your problems at least that way we can possibly rule it out.

---

### Post by .Danny on 2006-08-31
When it's connected to the internet directly all pages work fine. I tried with both Safari and Firefox. I can also view all pages fine when browsing via Firefox in Ubuntu, it's just that when I go through Ubuntu then I don't see https pages.

Anyway I'm getting a router tomorrow so I'm not gonna have to route it through Ubuntu and it should work fine then.

---

### Post by happosai on 2006-09-02
I'm not of expert of linux, but I had the same problem.
I solved it just installing shorewall (apt-get install shorewall) and configuring it with webmin.
So u can make an ubuntu box "router" with 
 -ip sharing (echo 1 > /proc/sys/net/ipv4/ip_forward);
 -ip masquerading
 -vpn tunneling
 -firewall

I paste mu configuration files and I hope it would be helpfull
Shorewall configuration files are stored in /etc/shorewall.

#zones
fw	firewall
net	ipv4
loc	ipv4

#masq (i have an ADSL modem)
ppp0    eth0

#interfaces
net	ppp0	detect
loc	eth0	detect
loc	eth1	detect

#policy
loc	net	ACCEPT
loc	fw	ACCEPT
fw	loc	ACCEPT
fw	net	ACCEPT
net	all	DROP	info
all	all	REJECT	info

#tunnels
gre	loc
ipsec	loc

#rules
ACCEPT	net	fw	tcp	80,22,21,110,8080
ACCEPT	net	fw	icmp
ACCEPT	loc	fw	tcp	80,22,21,110,8080
ACCEPT	loc	fw	icmp

Good luck!
Bye!

---

### Post by gils0040 on 2006-09-03
im having problems with the dns. this is my setup

College network -->eth1 (131.212.146.145) | ubuntu dapper | eth0 (192.168.0.1) --> xbox

**xbox**
ip: 192.168.0.2
dns: 192.168.0.1

i can not access the internet from the xbox. the xbox live trouble shooter fails at dns check.

can anyone see anything wrong with what im doing? 

also when doing dpkg-reconfigure ipmasq should PPP connections recomputer firewall? should ipmasq be started after network interfaces are brought up or after network services have been started? 

any help is greatly appreciated

edit: for some reason ipmasq was not started, so i fired it up and problem solved. thanks for the help

---

### Post by BrowneR on 2006-09-04
i presume you have the dnsmasq package installed and configured to provide dns forwarding and dhcp on eth0? i would check your dnsmasq.conf for errors or post it and i'll take a look.
Also check your ubuntu box has the correct dns servers in its /etc/resolv.conf for your college network.

---

### Post by Viskovitz on 2006-09-05
OH MY GOD!
This little howto helped me connect my ipaq with familiar to the Internet, something I hadn't managed before with specific HOWTOs. Thanks a lot!!!

---

### Post by KuruOujou on 2006-09-10
this is perhaps the most unreasonable, unreliable how to I have ever seen. I did it and now my ubuntu laptop is royally screwed. It cannot connect to the internet and my windows computer cannot connect to it. This thing screwed it up so bad I fear I may have to wipe and reinstall ubuntu in order to get internet running on my computer again. Thanks alot, dumba55, you just screwed up my whole life. F*CK YOU!


EDIT: Ok, a few years later, but I just remembered I made this post, and as my first post no doubt. I wanted to apologize to the author and all of the members of the forums who have read this, I was a real n00b. I haven't been on this forum for a while, idk why. It's a great forum. But yes, I was a stupid dumbass, not the person who wrote this great how to. I followed the same howto last week, not even noticing this post (I didn't travel this far back), and it worked perfectly. Sorry everyone.

---

### Post by BrowneR on 2006-09-11
> **KuruOujou said:**
> this is perhaps the most unreasonable, unreliable how to I have ever seen. I did it and now my ubuntu laptop is royally screwed. It cannot connect to the internet and my windows computer cannot connect to it. This thing screwed it up so bad I fear I may have to wipe and reinstall ubuntu in order to get internet running on my computer again. Thanks alot, dumba55, you just screwed up my whole life. F*CK YOU!
well simply undo the steps if it didn't work for you - no need to take it out on the poster - all how-to's are performed at your own risk and there is a level of risk involved with all of them. you should only attempt something if you are confident you can undo the damage.
personally i have used this how-to as a base setup for a couple of systems without problems - i believe most of the issues are with people misunderstanding the instructions or their own network topology.

> Thanks alot, dumba55, you just screwed up my whole life. F*CK YOU! and that was totally uncalled for.

just do the following:


Change the line "net.ipv4.ip_forward = 1" in /etc/sysctl.conf to read "net.ipv4.ip_forward = 0"

then

```
echo 0 > /proc/sys/net/ipv4/ip_forward
```

then

```
iptables -t nat -D POSTROUTING -o ethX -j MASQUERADE
``` remember to substitude ethX for your interface.

then

```
sudo aptitude purge dnsmasq ipmasq
```

now make sure your /etc/network/interfaces file reads correctly. if in doubt just set it up for dhcp by adding the following for each interface (ethX):
```
iface ethX inet dhcp

```

restart.

check your /etc/resolv.conf contains the correct DNS servers.

---

### Post by Kurdt on 2006-09-11
Hi, i am sharing internet with this guide, gtalk, skype and browsing works on my mom's windows computer but live messenger won't any clues ?

---

### Post by fishfillet on 2006-09-11
I would like to share my experience on sharing our internet connection with IPKUNGFU.  Story is here: [http://teqnix.blogspot.com/2006/06/ipkungfu-kicks-firestarter-out-of-my.html](http://teqnix.blogspot.com/2006/06/ipkungfu-kicks-firestarter-out-of-my.html)

To install ipkungfu:

sudo apt-get install ipkungfu

edit accordingly the portions below in your /etc/ipkungfu/ipkungfu.conf: 

$ sudo gedit /etc/ipkungfu/ipkungfu.conf

portions to be edited...

# IP Range of your internal network. Use "127.0.0.1"
# for a standalone machine. Default is a reasonable
# guess.
LOCAL_NET="192.168.1.0/255.255.255.0"

# Set this to 0 for a standalone machine, or 1 for
# a gateway device to share an Internet connection.
# Default is 1.
GATEWAY=1

These changes specifies the IP and subnet mask of the LAN and if you want to make your PC a Gateway aka share internet connection.

On the client side, make sure you have the same ip range (192.168.0.X) and subnet mask as with the PC sharing the internet.  Also, make sure that the gateway IP specified is the PC that is sharing the internet.. on the DNS or nameserver, i use OpenDNS (208.67.222.222 and 208.67.220.220).  Remember, this is on the client side.

After that, edit /etc/defaults/ipkungfu and replace "IPKFSTART = 0" with "IPKFSTART=1".

Fireaway ipkungfu!  

$ sudo ipkungfu

That's it :)

---

### Post by blkdragon on 2006-09-21
i need to configure my pc so i can use it as a gateway.

my connection goes as follows:

modem-->PC (windows xp)-->Linux laptop

i've got two Ethernet ports on my pc, and one on my lappy.

using a crossover cable to connect the two computers, and a normal CAT5 to connect the PC and modem, how would i be able to go on the internet with both computers at the same time, and still be able to share files?

---

### Post by blkdragon on 2006-09-21
soz for the double post, but problem solvered.

follow:

[http://ubuntuforums.org/showthread.php?p=1528164](http://ubuntuforums.org/showthread.php?p=1528164)

instructions to the letter, even if you dont have wireless,and it should work fine.

oh, and i didnt set the eth0 to DHCP.

i had to manually set static ip addy and gateway.

oh and windows xp automatically set up a network bridge, which seemed to help.

---

### Post by esaym on 2006-12-06
what is the best way to get dhcp on both netcards?

---

### Post by BrowneR on 2006-12-06
you need to be more specific.

do you want a dhcp server on both cards or a client on both cards or a mix!?

what set-up are you trying to achieve?

---

### Post by esaym on 2006-12-06
Oh sorry.  I was hoping it wouldn't be that complex :D

What I am thinking about doing is converting my web server in to a gateway with squid on it.  So the wan netcard will be plugging into my router and the local network card with be running into a switch with a couple of computers on it.  So for convenience I would like dhcp to automatically give out ip addresses on the local network side.

---

### Post by BrowneR on 2006-12-07
alright that shouldnt be a problem. the only complication is getting the dhcp server to broadcast your domain name servers (dns) to the clients.

one option is to specify these explicitly in the dhcp server configuration however this means that if they ever change then you will need to manually update your config.

another option is to setup your router as a dns relay as well as a dhcp server. this way you can just publish your routers ip as the dns server and then it will forward requests on to the internet.

the second option is more robust but does require some extra packages.
i will talk you through that option below.

from now on i will refer to your local network card as ethLAN and your internet facing card (to your modem) as ethWAN. you will obviously need to substitute the correct numbers in.

lets setup your interfaces first and decide on a network subnet to use. assuming your modem is using 192.168.1.1/255.255.255.0 we will use something else to avoid problems. (192.168.2.1/255.255.255.0)

```
 sudo nano /etc/network/interfaces
```

edit to read as follows...
```

auto ethLAN

iface ethLAN inet static
address 192.168.2.1
netmask 255.255.255.0

auto ethWAN
iface ethWAN inet dhcp

```

this sets your router ip to a fixed value of 1982.168.2.1 for the local network and connects to your modem via dhcp.

now your going to want to install the dhcp server package using apt.
```

sudo apt-get install dhcp3-server

```

now we have the code installed it just needs configuring. take a look at the following file in your favourite editor (eg nano)
```

sudo nano /etc/dhcp3/dhcpd.conf

```

there are plenty of comments in there to help you along with the configuration you need. for a simple configuration you could just add the following to the end of the file:

```

subnet 192.168.2.0 netmask 255.255.255.0 {
    range 192.168.2.10 192.168.2.254;
    option domain-name-servers 192.168.2.1;
    option routers 192.168.2.1;
 }
```

now we need to tell the server which interfaces to listen on:
```

sudo nano /etc/default/dhcp3-server
```
and add your interface ethLAN between the quotes so the line reads
```

INTERFACES="ethLAN"

```

now clients are expecting us to forward dns queries so we should set that up...

install the packages ```
 sudo apt-get install bind9
```

the default configuration should work fine for us so that is all we need to do.

now we just need to bring up the interfaces and start the dhcp server. (or a restart would do).

```

sudo ifdown -a && sudo ifup -a
sudo /etc/init.d/dhcp3-server restart

```
if you get errors when trying to start the dhcp server then go back and check you have configured it correctly and specified the correct interface.

let me know if you have any problems as ive just been doing this from memory and i may have overlooked something.

this setup does not involve squid at all - im afraid i have no experience with that.
maybe there is another thread on that.
i think you will want to add an iptables rule to forward web requests to your local squid port. something along the lines of... ```

iptables -t nat -A PREROUTING -i ethLAN -p tcp --dport 80 -j REDIRECT --to-port 3128
```...for a transparent setup :confused:

---

### Post by esaym on 2006-12-07
You're the man!

Give me about a month and I will post back the results.  The "router" that I am talking about is a WRT54GL wireless running in client mode and it is pulling internet from a relative's house next door.  I might stick a wireless card in the server box and do away with the router all together.  I just bought it and I hate to throw money around like that though.

As far as the squid config I have it running on a smoothwall box that I am no longer using.  I plan on just copying the configs right over.  I have been using squid for awhile and know it pretty well so there should be no problems :D

---

### Post by Vegettex on 2006-12-11
Weird, I've tried it on a clean install of ubuntu 6.06 but it didn't work. Must have missed something.

This is what I eventually want:
modem -> ubuntu (eth0 nic to the world, eth1 to my home network) -> switch -> computers (preferd with dhcp)

Like I've said, I just did a clean install with 6.06, updated my apt and then started with the guide.

> 1. Start by configuring the network card that interfaces to the other computers on you network:

# ifconfig ethX ip 
I did: ifconfig eth1 192.168.2.1

> 2. Then configure the NAT as follows:

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE 
I did: iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

The other things are pretty straight forward (I chose the default values with the ipmasq reconfigure).

My /etc/network/interfaces contained:
```
auto eth0
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0
```

but now it doesn't work any more... I couldn't ping anything outside, so I commented the eth1 lines in the interfaces file, restarted my network but... no difference.

I hope somebody can lend me a hand over here :-)

Thanks in advance!

---

### Post by BrowneR on 2006-12-12
Do you mean the Ubuntu box itself cannot access the internet or the other computers on your lan?

First you may want to check the interfaces are configured and up:
```
ifconfig
```

You also want to check that ip forwarding is on:
```
cat /proc/sys/net/ipv4/ip_forward 
```
you should get a result of 1.

Then check your iptables rules are ok by running the following:
```

sudo iptables -t nat -L
```
you should only see the one rule which you added.

If you post the output's of these commands i will take a look.

---

### Post by Vegettex on 2006-12-12
Sorry, my post wasn't clear enough, I cannot connect to the internet anymore from my server to the internet.

My ifconfig says:
```
eth0: addr 192.168.1.65, Bcast 192.168.1.255, Mask ,255.255.255.0
```

My /proc/..ip_forward gives indeed a '1'

And the iptables command gives me:
```
Chain PREROUTING(policy ACCEPT)
target prot opt source destination

Chain POSTROUTING(policy ACCEPT)
target prot opt source destination

Chain OUTPUT(policy ACCEPT)
target prot opt source destination

```

I hope you can get me a little further :)

Thanks :-D

---

### Post by BrowneR on 2006-12-12
thats strange. you seem to be connected to your modem ok.

it may be a dns problem. that would mean that you could not ping [www.google.com](www.google.com) but could ping 66.249.85.99 (a google ip). you should also be able to ping your modem eg. 192.168.1.1

in which case you want to make sure that the correct dns servers are listed in your /etc/resolv.conf
however i would have thought these would be set by your modem via dhcp...

your iptables output shows that the rule you added is no longer there but that shouldn't effect your internet access at all.

i suppose it's possible you mistyped the iptables rule and added something else instead? unlikely though.

by default you shouldn't have any rules in any of the tables.

to be honest im not really sure. maybe someone else has some ideas?

---

### Post by mapalma on 2006-12-17
Dont work :( 

pc1: 192.168.0.1 255.255.255.0
pc2: 192.168.0.2

dns:
root@pchome-desktop:/home/pchome# cat /etc/resolv.conf
nameserver 200.42.97.110
nameserver 200.42.0.110


root@pchome-desktop:/home/pchome# sudo iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  192.168.0.0/24       anywhere            
MASQUERADE  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by albuemil on 2006-12-19
EDIT : sorry for double post, pressed the submit button twice

---

### Post by albuemil on 2006-12-19
Hy. 
I've got a similar problem, i can't manage to make the Internet connection sharing work. 
I did manage to get a "hack" so temporarily it does work, but it's not the best way.

OK, so first of all, here's my setup :

INet > PPPoe connection > ppp0 on eth1 > [Ubuntu Server] > eth0 -> switch -> XP1 and XP2

I tried this :
```
ifconfig eth0 192.168.1.1 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward
/etc/init.d/dnsmasq restart
ifconfig eth0 192.168.1.1 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
```
but the **/etc/init.d/dnsmasq restart** line gives an error ```
Restarting DNS forwarder and DHCP server: dnsmasqdnsmasq: failed to create listening socket: Address already in use
 (failed to start).

```

The really strange thing is that without that line, if i stop and restart the PPPoe (poff -a followed by pon dsl-provider) then the internet connection is shared. But when i restart the server I have to do all this again.

For now, i modified /etc/rc.local file and added this lines```
# stop PPPoe connection
poff -a

# make the IP masquerade
ifconfig eth0 192.168.1.1 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward
#/etc/init.d/dnsmasq restart
ifconfig eth0 192.168.1.1 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 

# restart the pppoe
pon dsl-provider

```, but it's not what i wanted :???: 

Also, I'd like to forward a port (for example 4130) to a certain IP address (ex : 192.168.1.10)  but i didn't manage to do that neither :-( 

Any help would be welcomed, since i don't want to change the server to any other distro, i like Ubuntu too much :-)

P.S. i tried understanding the iptables program, but don't exactly understand how to use it. Could i use the Webmin interface to configure this up, and if so how ?

Thanx in advance, and sorry for the long post.

---

### Post by djberndt on 2006-12-26
hi!

someone else have asked the same question earlier in the thread but he got no answer, so I'm trying;

is it possible to share internet via the wireless network card, using this guide?
I'm wired to the internet, and I want to share my internet connection with my girlfriends laptop running XP. I've got an on board wireless network card (i945). I've also patched it for promiscous mode, if that is necessary..

thanks in advance.
/daniel

---

### Post by john_spiral on 2007-01-20
Hi,

I've got one Ubuntu machine on an USB ADSL Internet connection and another linux box (Damm Small Linux) on a ethernet connection.

The other linux machine (DSL) is attempting to connect to the Internet through eth0 on the Ubuntu box. 

Followed the howto but my DSL box doesn't get an ip address from the Ubuntu box?

My only deviation from the howto was on line 2:

iptables -t nat -A POSTROUTING -o [COLOR="Red"]ppp0[/COLOR] -j MASQUERADE 

any ideas?

---

### Post by john_spiral on 2007-01-21
I've got it working! Thanks for the howto.

Just needed to use the **DSLpanel** > **Netcardconfig** tool to assign a static ip address of 192.168.0.2 to the DSL box with the ubuntu box as the gateway.

voila!

---

### Post by BigIslandVegan on 2007-01-22
How might one share the internet connection that I have through a USB-Bluetooth adapter with my EDGE (T-Mobile) phone with another computer connected via ethernet, through a router?

Thanks so much in advance for the help.

---

### Post by john_spiral on 2007-01-22
> **BigIslandVegan said:**
> How might one share the internet connection that I have through a USB-Bluetooth adapter with my EDGE (T-Mobile) phone with another computer connected via ethernet, through a router?

Thanks so much in advance for the help.

Hi BigIslandVegan,

run a **ifconfig** on the machine with the 'USB-Bluetooth adapter with my EDGE (T-Mobile) phone'

post your results.

what OS is the other machine using?

---

### Post by BigIslandVegan on 2007-01-23
Thanks for the response. Here is what I got:

*******@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7181613 (6.8 MiB)  TX bytes:7181613 (6.8 MiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:72.250.2.86  P-t-P:192.200.1.21  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:21014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:19615382 (18.7 MiB)  TX bytes:2067134 (1.9 MiB)

---

### Post by BigIslandVegan on 2007-01-23
Most likely the OS of the other computer will be Ubuntu / Xubuntu as well.

I gotta figure out what will work best. The other machine is in flux a little bit right now. We have only an old machine with 64 mb or ram but we may receive a better machine this weekend from a friend that doesn't want it. Regardless, the next machine will also have a Linux OS.

Thanks again!

---

### Post by Abhi Kalyan on 2007-01-25
Worked like a charm
Thank you Bro

---

### Post by bullit on 2007-01-28
Hi

I've read the stuff discussed here. Tried the solution. It seemed to work, only on one end. 

Here's the story.

I've using an ubuntu box and I want to set it up as a gateway/proxy for our home network; a wireless connection with an XP box. 

I've tried the solution on the 1st page. It seemed to work because XP detects the wireless network connection but isn't able to get onto the internet. 

My setup is like this: 

Ubuntu > wireless router (connected by a cable because it's right next my machine) > wirelessly to XP.

I've been tearing my hair over the past 7 hours (according to my wife) over this thing. 

The default gateway and preferred DNS have been set to 192.168.0.1. If I get this correctly, do I even have to change the IP and port on the browsers to get connected?

I would love to get some your opinion on this. 

Thanks in advance.

---

### Post by john_spiral on 2007-01-28
> **BigIslandVegan said:**
> Thanks for the response. Here is what I got:

*******@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7181613 (6.8 MiB)  TX bytes:7181613 (6.8 MiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:72.250.2.86  P-t-P:192.200.1.21  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:21014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:19615382 (18.7 MiB)  TX bytes:2067134 (1.9 MiB)

Hi BigIslandVegan,

Looks like your eth0 (ethernet) port has not been activated.

Activated through the GUI.

Then  give it an exciting address like 192.168.0.1

Follow the howto.

start off with:

**sudo su**

to give you root access

change setp 2 to:

iptables -t nat -A POSTROUTING -o 
**ppp0** -j MASQUERADE 

Give the other system an ip address of 192.168.0.2 and set it's gateway as 192.168.0.1

give it a try 

Johne

---

### Post by lonetree on 2007-01-29
Could someone write an working example for this?

---

### Post by john_spiral on 2007-01-29
> **bullit said:**
> Hi

I've read the stuff discussed here. Tried the solution. It seemed to work, only on one end. 

Here's the story.

I've using an ubuntu box and I want to set it up as a gateway/proxy for our home network; a wireless connection with an XP box. 

I've tried the solution on the 1st page. It seemed to work because XP detects the wireless network connection but isn't able to get onto the internet. 

My setup is like this: 

Ubuntu > wireless router (connected by a cable because it's right next my machine) > wirelessly to XP.

I've been tearing my hair over the past 7 hours (according to my wife) over this thing. 

The default gateway and preferred DNS have been set to 192.168.0.1. If I get this correctly, do I even have to change the IP and port on the browsers to get connected?

I would love to get some your opinion on this. 

Thanks in advance.

can both machines ping each other?

---

### Post by uboltun on 2007-02-12
I have seen people installing both dnsmasq and dhcp3-server. Isn't dnsmasq has the DHCP server already ? Or there is a hidden reason behind this...
I was able to run internet with DHCP by changing /etc/dnsmasq.conf
I think uncommenting the line : 
dhcp-range=192.168.0.50,192.168.0.150,255.255.255.0,12h
would work just fine.

---

### Post by computerjunkie on 2007-02-12
Hey Sorry to butt in on this thread but I was wondering if anyone had any ideas of how I could network my PS3 through my ubuntu laptop so I can play my games online and get the updates for the ps3 (I want to do this because right now my college does not allow us to hook up a ps3 to the network in the dorms)

I do not want my computer to be used permanently as a server for the ps3 or even every day. and when I'm not using my console I do not want my computer to have to the ability to share its internet connection.

My question: is there an easier way to do this so I can turn it on and off when I choose?

---

### Post by Frenzy-br on 2007-03-16
now how would i go about doing that with one network card???

---

### Post by Melophobic on 2007-03-21
Works great for me!

Nice and simple how to, Thanks.

---

### Post by alexgieg on 2007-03-21
My cable modem is connected to my Ubuntu box in eth1. Another network card, eth0 (static address: 192.168.0.1), connects to a Windows XP machine (static address: 192.168.0.2). I've followed many of the suggestions offered in this thread, but so far the XP machine cannot connect well to the Internet. I can ping Internet IP addresses directly with it (and both computers ping each other, of course), but whenever I try to access a server by name, it doesn't work.

And by "not work" I mean: at all. I can set the XP to use the DNS of my Ubuntu machine (192.168.0.1), the 2 DNS addresses from my ISP (200.162.196.29 and 200.162.192.29), the 2 DNS addresses from OpenDNS (208.67.222.222 and 208.67.220.220), but no matter which one I set, it seems to simply not access server names. And doing a manual "nslookup google.com" in Command Prompt gives timeouts.

So, what I think is that the Ubuntu box is for some reason blocking access to DNS servers. I've tried changing Firestarter's policies a little by explicitly allowing connections coming from the 192.168.0.2 machine and by explicitly permitting DNS (port 53) accesses both from the LAN and that machine, but nothing helped either.

So, I'm completely lost here. How do I make Ubuntu, or iptables, or the Firestarter firewall, or whatever, allow DNS queries coming from the LAN connected to eth0, or at least from the 192.168.0.2 machine? I think once I have this working the remaining will be easy...

---

### Post by uboltun on 2007-04-04
I have a similar setup on my box. I am connected to the internet on eth1 through USB cable modem and eth0, wlan0 goes to either wireless or ethernet connection of WinXp computer. It has been a while , but I think all you got to do is this:
1 install dnsmasq , ipmasq , sudo apt-get install dnsmasq ipmasq
2. then run sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
3  Set eth0 to 192.168.0.1 ( sudo ifconfig eth0 192.168.0.1)
4  Edit /etc/dnsmasq.conf and find the line
#dhcp-range=192.168.0.50,192.168.0.150,255.255.255.0,12h
uncomment it
5 Reboot

On WinXp you can just set DHCP connection and it worked for me.
Good luck

---

### Post by sfine on 2007-04-16
Well first, thanks for all the replies on any kind of problems here :P

So to my situation
cable modem -> switch -> ubuntu (cable modem knows my mac and gives me the ip via dhcp)
_________________________-> winxp (it gets nothing i have only 1 ip i can get from the modem)

so i need the winxp get http access thats all well and i rly dont wanna buy anything :)
and i cant touch the settings in the cable modem

---

### Post by stnever on 2007-04-16
@alexgeig

I'm no expert, but I'm beggining to understand a few things. I'm assuming your Ubuntu box has no problems surfing the Internet.

Are you running dnsmasq in the ubuntu box as instructed in the howto? Can your XP box ping the DNS servers as well? You can try "forcing" a certain DNS by typing (in an XP command prompt):

```
nslookup www.google.com 200.184.26.3
```

This will force the machine to use the DNS server 200.184.26.3. If you get a normal response (for this case, 64.233.161.104 is one of Google's addresses), you can access the site directly:

[http://64.233.161.104/](http://64.233.161.104/)

If you are still having problems, perhaps there really are some rules on the Ubuntu box preventing some traffic. But I don't know where would they be. Can anyone help us some more?

---

### Post by iceman504 on 2007-04-17
so how would i use this to connect my computer to my xbox so i can play online games on my xbox...My setup is two network cards (eth0: DSL modem to computer w/ ethernet cable and Eth1: my computer to my xbox with crossover cable. Im trying to play online with Xlink kai and playing on  xbconnect and Xlink worked fine with windows if that helps.
I tried this once but i keep getting this error when issuing this command "/etc/init.d/dnsmasq restart " :
Restarting DNS forwarder and DHCP server: dnsmasqdnsmasq: failed to bind listening socket for 192.168.1.97: Address already in use
 (failed to start).

---

### Post by all4spl on 2007-04-18
here is my setup... modem >linux > out of linux to vista.... i got internet working on both of them... but the only thing is, how do i forward ports for vista???

---

### Post by Quinn5219 on 2007-04-26
Is it me??  Have I grown to accustomed to ease of opereation and hooking up to the Internet at the punch of a button.  I finally got Ubunto 6.06 installed and to get instructions on how to install to the internet looks like special codes in making a nuclear reactor.
I really like the Ubuntu, but it took me 6 months to understand and figure out how to install it, when a few sentences would have shown me how to do this in a matter of minutes.
 I have XP Media Center installed and installed my Ubuntu along with it.  Works great, but, now to share a dial up ISP connection, I am lost.   Later I will install DSL, but if it will not hook up to dial up, it will not hook up to DSL.
I have said it before, how can something so great as Linux Ubuntu   yet be so incredibly hard to get things 
done.  Guess I should not have missed the last meeting.  Any suggestions?

---

### Post by mvochin on 2007-04-28
Hello! I have an ICS problem: I cannot use it in Win XP (by using their wizard I only get ftp acess from the client) and I also tried in Ubuntu the Firestarter, and the tutorial from this post's first page.
    In windows, I can acces the internet on the client only by running a small proxy server program called CC Proxy or Proxyi (with static ip's) (but I'm limited by other applications proxy support).
    Someone told me that the ICS does not work because my ISP verifies the TTL of the network packages, and it can determine those from the client.
    Does anyone know a method to enable ICS in UBUNTU, or a similar proxy method?

    Note: I have a wired internet connection (Lan with fixed ip and fixed MAC )

---

### Post by ebichu on 2007-05-12
Hello, I'm trying to share Internet connection from my desktop computer to my laptop, I did exactly like the howto said, but my laptop still doesn't connect to the Internets. Please help. : )

---

### Post by bornakke on 2007-05-13
Worked without a single problem!

Thanx dude!:guitar:

---

### Post by freduardo on 2007-05-17
Hi,

Here's my problem:

It works! :)

Only not anymore after a reboot. :(
I have to run dpkg-reconfigure ipmasq (on the "server") every time after a reboot to get internet access on my other computers (the "clients"). After that it works again.

Is there some way to get past this?
I can't put dpkg-reconfigure ipmasq in a startup script, as it requires interaction (pressing enter).

Thanks in advance,

Freduardo

---

### Post by plech.d on 2007-05-24
I've got the opposite problem.
I have a machine running winXP that shares an internet connection and I can't get my Ubuntu machine connected to it. I've set the static IP and subnet mask and I've set the gateway to the IP of my winXP machine and I've set the DNS servers to the ones that my winXP machine uses. I can connect to the network, but I can't connect to the internet using the winXP machine's connection.

---

### Post by spleecho on 2007-06-13
ok i spent hours trying to do all this, my situation is a bit more complicated, i use evdo card as my internet, can you please tell me how to undo all these settings for the ethernet interface?
thanks

---

### Post by kromagg on 2007-06-29
This post is so full of misinformation I just had to reply. Author please fix your post.

A list of problems:
[LIST]
[*]First of, configure your network by editing /etc/network/interfaces (makes changes permanent) and ifup the interfaces.
[*]Turning IP forwarding on is unnecessary and possibly insecure. DO NOT DO THIS.
[*]The iptables line is completely unnecessary as ipmasq does this for you
[*]dnsmasq is cool, however even a beginning user should take a look at /etc/dnsmasq.conf just to make sure it sort of does what he wants to. Just read through it from beginning to end, possibly set some variables.
[*]If both your interfaces were up at the time you installed ipmasq there should be no problems. Rebooting is completely unnecessary. Possibly restart ipmasq (/etc/init.d/ipmasq restart) or reconfigure (dpkg-reconfigure ipmasq)
[/LIST]

I'd also like to point out while dnsmasq combines dhcp and dns you might find other setups around the internet. Most notably, you could run bind for simple dns caching and dhcp3-server for dhcp. Do not run two dhcp or two dns servers at the same time or you'll get some weird problems.

Also whenever you install **any** software, go to /usr/share/doc/<packagename> and read the README.Debian, it usually includes a lot of useful information.

A last tip is that when you are debugging a problem, the following parts affect how your network work:
[LIST]
[*]iptables configuration (iptables -L -t nat and iptables -L will list current rules)
[*]configured ips (checkable with ifconfig)
[*]configured routes, if any ("route" command)
[/LIST]

And of course if you installed dnsmasq, the dnsmasq config.

---

### Post by Aessa on 2007-07-02
Thanks for pointing out this:
/etc/network/interfaces

I've dabbled there before with WPA...but never realised that ifconfig simply means to change that file. Would have saved me a few rants...I'm trying the standard server thing and after an hour of static IP setting hell (they just kept disappearing) I noticed avahi (shudder)...I then found enough info: avahi mentions IP addresses. OK, killed ahavi. No gain. OK, removed avahi, some gain. OK, completely remove avahi related libs...damn, lost KDE (using kubuntu). I almost lost it. Happily recovery went smooth with a simple apt-get install kubuntu-desktop, and I somehow kept the static IPs. So, I'm still not sure what avahi is and why on earth everything depends so strongly on it (get a lot of script errors along the way in feisty now), but I suppose there is no need to slaughter it like I tried to.

Quick question then: With all this ip forwarding, would you get the same effect with shorewall set up to manage traffic in the same manner? I'm trying to use all the Webmin related software so that other users can configure what they need to easily (our company is  all of 6 people :) ).
Later on, what trouble can I then expect with Squid? With the current server (a mess) only http traffic works, and I think Squid blocks ftp (or there is yet another firewall I have to discover and turn off - we are behind several hardware firewalls of simple routers).

---

### Post by Alsvartr on 2007-07-05
Hi. I have a desktop computer with Ubuntu 7.04 and vpn connection on it and I have a notebook with Win XP. I followed this instruction to share Ubuntu internet connection, but after installing dnsmasq and ipmasq I have lost internet vpn connection - it doesn't work nor at Ubuntu nor at Windows. BUT. The local network of my provider is work correctly on a both computers. Any suggestions?

---

### Post by AlFigue on 2007-07-05
Thank you very much.

It was extremely useful your guide, i was fighting against windows for hours before a got here.

Thank you

---

### Post by Tim3L0rd on 2007-07-07
Well here I am after trying to do this for the past 3 days.  Read all 14 pages and sometimes it just makes it more confusing.

First off, I've done the steps listed on page one probably 10 times, and a few others, like firestarter and webmin but nothing has worked yet.

I have this linux box w/ubuntu, it has 5 nic cards on it.  I've tested each cards connectivity individually and they all work.  For my setup I'm only utilizing 2 cards, eth0 and eth1.

eth0 is connected to my router which is connected to the internet.  eth1 is the interface I want to connet my XP laptop to.

UBUNTU BOX
eth0      Link encap:Ethernet  HWaddr 00:01:02:68:61:DA  
              inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          

eth1      Link encap:Ethernet  HWaddr 00:B0:D0:29:A8:2B  
              inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0

XP LAPTOP
IP	       192.168.0.3
Subnet	 255.255.255.0
GW	    192.168.0.2
DNS	    192.168.0.2
          

the gateway and nameserver for eth0 is 192.168.0.1 (router address)
the gateway for eth1 is 192.168.0.2 (address of eth0)

I'm not sure how to figure out the nameserver for eth1, I assume that the IP and/or name that's listed in the /etc/resolv.conf file is used on eth1 too.

Internet works fine on the ubuntu box (eth0) but nothing on the XP laptop.  Pinging from ubuntu to XP doesn't really resolve anything, I mean, I get replies but I can unplug the ethernet cord and still get replies when I ping 192.168.0.3.

Is the addressing correct?  What else am I missing?  BTW, when I do this ...

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

I assign eth0 as the ethx.  correct?  Any help appreciated.

---

### Post by cbuhka on 2007-07-13
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
can't initialize ip tables table 'nat' : Permission denied (you must be root)

How to become the root? In this topic [http://ubuntuforums.org/showthread.php?t=327228](http://ubuntuforums.org/showthread.php?t=327228) is written only about sudo. I've changed LINUS pass, like written there [http://my.opera.com/Contrid/blog/show.dml/486617](http://my.opera.com/Contrid/blog/show.dml/486617) but login root does'nt worl, " Administrator can't connect from this screen"

---

### Post by willyram on 2007-07-18
Hi, I'm having exactly the same problem that freduardo talks about. Is there anything I should set up to solve it? I would like to have these definitions for Internet  Connection Sharing permanent, as I am always connecting my Win XP laptop to the Kubuntu "server". 
Tks in advance, Willy.

> **freduardo said:**
> Hi,

Here's my problem:

It works! :)

Only not anymore after a reboot. :(
I have to run dpkg-reconfigure ipmasq (on the "server") every time after a reboot to get internet access on my other computers (the "clients"). After that it works again.

Is there some way to get past this?
I can't put dpkg-reconfigure ipmasq in a startup script, as it requires interaction (pressing enter).

Thanks in advance,

Freduardo

---

### Post by octaedro7 on 2007-07-24
> **Tim3L0rd said:**
> 

UBUNTU BOX
eth0      Link encap:Ethernet  HWaddr 00:01:02:68:61:DA  
              inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          

eth1      Link encap:Ethernet  HWaddr 00:B0:D0:29:A8:2B  
              inet addr:**192.168.0.3**  Bcast:192.168.0.255  Mask:255.255.255.0

XP LAPTOP
IP	       **192.168.0.3**
Subnet	 255.255.255.0
GW	    192.168.0.2
DNS	    192.168.0.2
          

the gateway and nameserver for eth0 is 192.168.0.1 (router address)
the gateway for eth1 is 192.168.0.2 (address of eth0)

I'm not sure how to figure out the nameserver for eth1, I assume that the IP and/or name that's listed in the /etc/resolv.conf file is used on eth1 too.

Internet works fine on the ubuntu box (eth0) but nothing on the XP laptop.  Pinging from ubuntu to XP doesn't really resolve anything, I mean, I get replies but I can unplug the ethernet cord and still get replies when I ping 192.168.0.3.



I'm not an expert at all but aren't you repeating IP's on your eth1 and xp?, so that's why you get replies even unpluging XP

---

### Post by octaedro7 on 2007-07-24
**anaoum**: I've followed your post to connect 2 ubuntu boxes, one with wireless connection to internet. I could only managed to reach this :

```
Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

# ifconfig ethX ip

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

where ethX is the network card that the Internet is coming from

# echo 1 > /proc/sys/net/ipv4/ip_forward

```

At this point I lost internet connection.  Tried disconnecting and reconnecting but nothing.  My wireless card is in roaming mode and I cannot change it even if I'm root .

Can you please tell me how to leave every thing as it was (default).

---

### Post by dannyboy79 on 2007-07-24
> **octaedro7 said:**
> **anaoum**: I've followed your post to connect 2 ubuntu boxes, one with wireless connection to internet. I could only managed to reach this :

```
Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

# ifconfig ethX ip

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

where ethX is the network card that the Internet is coming from

# echo 1 > /proc/sys/net/ipv4/ip_forward

```

At this point I lost internet connection.  Tried disconnecting and reconnecting but nothing.  My wireless card is in roaming mode and I cannot change it even if I'm root .

Can you please tell me how to leave every thing as it was (default).
well you can clear all iptables rules with this command:
sudo iptables -F
BUT this will also remove ALL your other firewall rules. So this will just remove the one that was added above:
sudo iptables -t nat -D POSTROUTING -o ethX -j MASQUERADE

then just make sure that your /etc/network/interfaces  file has the basics for getting your internet to work.
you can edit that file by using the System, Admin, Networking dialog box, then just enter what you did in the begining to get this to work.

---

### Post by ashokcm on 2007-07-24
I connect to the internet from my ubuntu machine using VPN. When I enable the masquerading, the vpn does not work anymore. The internet connection goes dead. Is there something special I need to do for VPN connections? My setup is as follows

Machine1:Connects to internet using VPN
Ubuntu

eth1: ethernet which connects to the network which grants internet connection. 
ppp0: the vpn connection. has a dynamic IP
etho: the card that I use to connect to the windows xp box.

Machine2:
Windows XP

Somebody please help :(

---

### Post by dannyboy79 on 2007-07-25
and you're sure you used the correct ethX interface's within the masquerading command?

Also, I am not sure I understand, if ppp0 is the connection that is to the internet, than what is the eth1 for? I don't know how VPN ties into all this but you should have internet coming into Ubuntu on 1 interface, what you're doing is forwarding the internet from the ppp0 connection to the eth0 connection so that windows xp can use it also.

---

### Post by octaedro7 on 2007-07-25
dannyboy79:
do you know why my wireless connection is fixed in roaming mode?
(when I uncheck the roaming mode box the ok button becomes unavailable)
If I use your fix, will it also fix this issue?

BTW: many thaks for the info

---

### Post by dannyboy79 on 2007-07-25
i don't know why? all I am suggesting is to remove the iptables rule that you added (POSTROUTING -o ethX -j MASQUERADE)

Have you tried to unplug your wireless card, then rename your /etc/network/interfaces file to something like interfaces-test, then shutdown your machine, then plug in your wireless card, then restart your machine. the system should recreate the interfaces file, then if you still don't have internet, you need to check the Networking setup box within System, Admin, to see if everything is configured correctly. Good luck

---

### Post by ashokcm on 2007-07-26
> **dannyboy79 said:**
> and you're sure you used the correct ethX interface's within the masquerading command?.

First I tried with eth0 and then I removed all the rules and tried again for ppp0. Apparently it does not work for either case. In both cases it kills my internet connection.

> **dannyboy79 said:**
> 
Also, I am not sure I understand, if ppp0 is the connection that is to the internet, than what is the eth1 for? I don't know how VPN ties into all this but you should have internet coming into Ubuntu on 1 interface, what you're doing is forwarding the internet from the ppp0 connection to the eth0 connection so that windows xp can use it also


my ifconfig looks like this.
```

ifconfig
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: xxxx::xxx:xxxx:xxxx:acc5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10570 errors:4 dropped:0 overruns:0 frame:4
          TX packets:15151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1048951 (1.0 MiB)  TX bytes:15775149 (15.0 MiB)

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.xx.xx  Bcast:192.168.xx.255  Mask:255.255.254.0
          inet6 addr: xxxx:xxx:xxx:xx:xxx:xxxx:xxxx:xxxx/64 Scope:Global
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41488852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33453975 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1350269 (1.2 MiB)  TX bytes:4176860955 (3.8 GiB)
          Interrupt:19 Base address:0x8900 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2404008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2404008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1261015328 (1.1 GiB)  TX bytes:1261015328 (1.1 GiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:212.201.xx.xx  P-t-P:192.168.x.41  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1486  Metric:1
          RX packets:87989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:30012516 (28.6 MiB)  TX bytes:144681309 (137.9 MiB)


```

The IP of ppp0 is my external IP (i can connect to my comp using this IP even from outside the network)
The IP of eth1 is my internal IP in the network. And I dont mean my home network but the network of the university.

My setup is such that I am connected to the uni network through which I access the internet through VPN. I also have a home network using 2 computers. I am trying to share the internet between these 2 computers.

Thanks for taking the trouble :)

---

### Post by dannyboy79 on 2007-07-26
check out this thread
[http://ubuntuforums.org/showthread.php?t=508724](http://ubuntuforums.org/showthread.php?t=508724)
and read post number 5.

---

### Post by ArkaniKarin on 2007-07-28
I'm having a problem following the instructions given. I'm really new to all of this, but I really need to get this system to start working as a server and as a bridge.

When I try to configure the network, I get this:

arkani@arkani-desktop:~$ ifconfig eth2 192.168.1.223
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied

Can anyone tell me what I'm doing wrong here?

---

### Post by ashokcm on 2007-07-30
Thanks a ton dannyboy79. I followed the link from that post and finally managed to get internet connection sharing between my ubuntu machine and my windows xp machine. 
I used the instructions from [this]("https://help.ubuntu.com/community/InternetConnectionSharing")  page. Everything works fine now.
Thanks again for all the help. Ubuntu rocks!!!

---

### Post by dannyboy79 on 2007-07-31
> **ArkaniKarin said:**
> I'm having a problem following the instructions given. I'm really new to all of this, but I really need to get this system to start working as a server and as a bridge.

When I try to configure the network, I get this:

arkani@arkani-desktop:~$ ifconfig eth2 192.168.1.223
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied

Can anyone tell me what I'm doing wrong here?

ifconfig requires sudo because it's an administrative task. you can either switch to the root user temp by issuing sudo -i (then enter your sudo password) OR just use sudo before the commands.

---

### Post by southernman on 2007-08-07
dannyboy79 - I want to thank you for your contribution to this thread. You had maybe the most insightful post(s) throughout it... other than the person that blasted the OP (of which who probably did nothing more than c&p their little ill-constrcted howto from another site I found from the Ubuntu Feisty Wiki. Damn, was that all one sentence? :p

Seriously Danny... Thanks! You helped me undo the mess.

I was being lazy, not wanting to run another wire back to the router. So I tried this bleeping howto! *raspberry* After a good many honest efforts, I gave up and broke out the crimpers!

Man, I thought I was doing so good with Ubuntu, then this fiasco had to put me in my place! Another time - another place, for sure!

---

### Post by usultis on 2007-08-11
for those who have problems with the terminal handling a small screencast of firestarter [http://wikisos.org/wiki/Ubuntu_7.04:How_to_setup_Internet_connection_sharing](http://wikisos.org/wiki/Ubuntu_7.04:How_to_setup_Internet_connection_sharing)

---

### Post by tman-ph on 2007-08-20
Thank Anaoum! It works like a charm! 

I've tried this using firestarter but I struggled and didn't win.

---

### Post by julian67 on 2007-09-28
I just set up ICS using network-manager and Firestarter based on the [Firestarter howto]("http://www.fs-security.com/docs/connection-sharing.php"). It's extremely easy this way. The internet facing network adapter  on the server stays configured as before and the LAN facing adapter  given a static ip address and subnet mask with the gateway address left blank. This is easily done by clicking the network manager applet and selecting manual configuration. Then reboot (or sudo /etc/init.d networking restart) and follow the firestarter howto.  It's then a good idea to have a look at [How-To: Firestarter on startup (better & safer way)]("http://ubuntuforums.org/showthread.php?t=542756") and follow the advice given and you're done. This method will be the easiest for many people whose internet facing PC/laptop has a  desktop environment i.e. is not a server with only command line.  It's quick and simple and all the different settings can be quickly seen and managed from gui.

---

### Post by dimsum_linux on 2007-10-28
> **julian67 said:**
> I just set up ICS using network-manager and Firestarter based on the [Firestarter howto]("http://www.fs-security.com/docs/connection-sharing.php"). It's extremely easy this way. The internet facing network adapter  on the server stays configured as before and the LAN facing adapter  given a static ip address and subnet mask with the gateway address left blank. This is easily done by clicking the network manager applet and selecting manual configuration. Then reboot (or sudo /etc/init.d networking restart) and follow the firestarter howto.  It's then a good idea to have a look at [How-To: Firestarter on startup (better & safer way)]("http://ubuntuforums.org/showthread.php?t=542756") and follow the advice given and you're done. This method will be the easiest for many people whose internet facing PC/laptop has a  desktop environment i.e. is not a server with only command line.  It's quick and simple and all the different settings can be quickly seen and managed from gui.

i've had tried firestarter but once i set it to static ip i lose the internet connection.

---

### Post by Pekz0r on 2007-11-02
Thanks for the guide!

But step 3/4 fails. dnsmasq fails to start.
I got this error message when i ran the APT-GET:
> Unpacking dnsmasq (from .../dnsmasq_2.37-1_i386.deb) ...
Setting up ipmasq (4.0.8-2ubuntu1) ...

Setting up dnsmasq (2.37-1) ...
Starting DNS forwarder and DHCP server: dnsmasqdnsmasq: failed to create listening socket: Address already in use
 (failed).
invoke-rc.d: initscript dnsmasq, action "start" failed.


I get a similar error message when i run "/etc/init.d/dnsmasq restart"
> Restarting DNS forwarder and DHCP server: dnsmasqdnsmasq: failed to create listening socket: Address already in use
 (failed to start).


Is the issue that i'm using the SUDO command. I don't have mush choise since i'm running ubuntu server without X.
What should i do?

Thanks in advance!

---

### Post by Pekz0r on 2007-11-07
Anyone knows how to solve this?

I'm getting desperate now!

---

### Post by Abhi Kalyan on 2007-11-23
This has helped me a load and much more,
Thank you for this howto,
Have a doubt though,
can i make and use squid in transparent mode without doing what has been given in this howto?
Is there any Link which might point me in the right direction.
Sincerely
Abhi Kalyan

---

### Post by levis on 2007-11-24
I connect to internet using wire network (eth0) and want to share internet to another notebook using wireless (eth1). I've already setted up ip and sharing like 1st post but my 2nd notebook doesnot recognize the 1st notebook. In windows i can create an ad-hoc network from 1st notebook the 2nd notebook can recognize and connect to this network. How can i make the 2nd notebook recognize and connect to 1st notebook? Thanks!

---

### Post by levis on 2007-12-12
Can somebody help me? Thanks!

---

### Post by zimmerj on 2007-12-13
Using the internet sharing guide at the beginning of the post I attempted to setup a small network between two computers.  However, I failed to do that and now I have lost internet.  Internet is still connected, and I can ping my ICP, but I don't seem to be able to do anything else.  Is there a way to get back to the default settings so that I can restablish my orginial connection?

---

### Post by levis on 2007-12-14
I've already done but ubuntu cannot connect to both networks (wire and wireless) at once. If i create and connect to wireless network, ubuntu will disconnect the wire network first.

---

### Post by holepunch on 2007-12-26
After many frustrating issues, going round in a lot of circles and reading numerous posts on the subject I started with a fresh 7.10 installation and used the instructions on this post:

[http://ubuntuforums.org/showthread.php?p=3713684](http://ubuntuforums.org/showthread.php?p=3713684)

The only issue I still had was that the host stopped doing that masquerade thing after each reboot and I had to type in two lines of code to get it started again.  My problem was solved by then installing Firestarter.

P.S. As suggested early on in this post I had tried installing Firestarter initially but it didn't help.  The solution for me only came from following the instructions in the link above first, then installing Firestarter.

I hope this helps.

---

### Post by acidpaul17 on 2008-01-02
Hello everyone!

I've followed these steps to share my internet connection in Linux to my other pc which is WinXP.
It worked, but when I restart my Ubuntu, the WinXP machine won't connect to the internet.

Any advice would be helpful!
Thanks!


1. Start by configuring the network card that interfaces to the other computers on you network:

# ifconfig ethX ip

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

where ethX is the network card that the Internet is coming from

# echo 1 > /proc/sys/net/ipv4/ip_forward

3. Install dnsmasq and ipmasq using apt-get:

# apt-get install dnsmasq ipmasq

4. Restart dnsmasq:

# /etc/init.d/dnsmasq restart

5. Reconfigure ipmasq to start after networking has been started:

# dpkg-reconfigure ipmasq

6. Repeat steps 1 and 2.

7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

# gedit /etc/sysctl.conf

8. Reboot. (Optional)

---

### Post by pyrodrake on 2008-01-11
Thank you SOOO much!  I've been trying to get Masquerading working properly for the past 4 days, following almost every guide I've found, and for some reason, nothing was working right.  After a re-installation and just going through this once, everything was up and running in a matter of 5 minutes.

---

### Post by mahasmb on 2008-01-12
How do I undo everything I did in this How To?

I tried it it didn't work and now my internet is giving me major problems

---

### Post by silver89 on 2008-01-24
Greetings, just a linux newbie with another networking problem... heehee

I have cable and a 4 port router, all was well.. I had 4 computers, all was well.. I added computer #5 and all was not well.  One of my computers has a dual port NIC.  I figured that rather than buy a switch and branch off the router, I would just plug into the spare port on the NIC.  I've tried following all of the info I could find and I'm still not having much luck.  My newness to command line terminals is a problem.

I downloaded firestarter, and it keeps telling me that eth0 or eth1 is "not ready" depending on how I've been putzing with the settings.

Cable _
Router _
| | | |
Box4, Box3, Box2, Box1_
|
Box5

the router has an IP assigned for each of the boxes - I had the 5th (new one) hooked up to get it online, so the IP is in the DHCP Active IP Table in the router.. I'm just at a loss as to how to tweak the settings on box 4 (the one with the dual port NIC) and box 5 - the new machine...  both box 4 and 5 are running current Ubuntu 7.10 distros.


Can anyone point me in the right direction? I feel like I'm close but I cant figure out what the steps are.](*,)

---

### Post by medien on 2008-01-28
Guys anybody could help me,im a newbie of linux,please help i want to share my internet i have an ubuntu server it has 2 ethernet card one from the ISP and one for the Lan i have 24workstations on my cybercafe the workstations running windows xp.What should i do first to share my internet connection to my workstations?thank you

---

### Post by hevi on 2008-02-06
hy! i want to share my internet connection, but when i try to set up the IP adress (the first step) it says to me "Permission denied".
what can i do?

---

### Post by stairwayoflight on 2008-02-07
> **hevi said:**
> hy! i want to share my internet connection, but when i try to set up the IP adress (the first step) it says to me "Permission denied".
what can i do?

;-) I think a careful read of the directions will show you need to do this as a root user. If you have not configured a root account, enter
sudo su -
enter your login password and hit enter. your $ in the terminal should now be a #. Thats why the # is there in the instructions.

Good luck!

---

### Post by stairwayoflight on 2008-02-07
Hello,
I have followed the howto and ended up here:
I have an ubuntu laptop sharing wireless internet via ethernet to my router. The router is set to bridge all ethernet ports. Also I have a desktop dualbooting winxp and ubuntu server.

When the desktop has xp running, it can display web pages etc., so I believe the internet sharing is setup ok on the laptop.

When I boot into ubuntu on the desktop, I can't ping domain names but I can ping their addresses. I have set up the interface with:

iface eth0 inet static
  address 192.168.0.10
  netmask 255.255.255.0
  gateway 192.168.0.11
dns-nameservers 192.168.0.11

The dns-nameservers entry hasn't gotten me too far; I have tried adding both the default gateway's ip as above, and the ip for the dns listed on the dns tab of the ubuntu network manager running on my laptop (the gateway machine).

I also tried firestarter, and went through the wizard to share my connection. Firestarter is now stopped.

Any ideas?

---

### Post by klecu on 2008-02-07
This worked perfectly. Very simple and very quick. Thanks.

---

### Post by luvinit on 2008-02-08
I tried the how to and it seemed to work yesterday, but not today no matter what I do. The guy who suggests this 

[http://teqnix.blogspot.com/2006/06/ipkungfu-kicks-firestarter-out-of-my.html](http://teqnix.blogspot.com/2006/06/ipkungfu-kicks-firestarter-out-of-my.html)

seems to know what he is talking about. It worked perfectly for me with no alterations to the config file. We will see if it stays that way.

---

### Post by DiegoVH on 2008-02-20
> **mahasmb said:**
> How do I undo everything I did in this How To?

I tried it it didn't work and now my internet is giving me major problems

I'm seconding this... sort of. I could set the connection for sharing and have had no problemas with the internet connection on the Ubuntu machine (so thank you very much!). However, for some reason, airodump-ng now won't detect any networks. 

I already tried stopping dnsmasq and ipmasq, and deleting the POSTROUTING rules from iptables, but still no go. Any hints? I'm just tinkering with linux, don't have a lot of experience yet.

---

### Post by madtom1999 on 2008-03-12
This may sound silly but I am resurecting a few old machines with dial up on them and giving them to low end users (email once a week etc)
Rather than download upgrades down a 56k modem I'd like to know how to set up a laplink/parallel port connection to share another PC's internet connection.

---

### Post by sir4taye on 2008-03-14
how do I login as root on gutsy? I've switched to the command line using alt+f2 but username root will not do any good with the password I set in the install. Can you help?

---

### Post by nlfb on 2008-03-15
Hello everyone, I hope you can help my to solve my problem, i've done the way that you wrote, but it didn't word, Ubuntu PC can not access to Internet after i config iptables, i don't know why, here is iptales -L
> root@ubuntu-server:~# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
LOG        0    --  127.0.0.0/8          anywhere            LOG level warning 
DROP       0    --  127.0.0.0/8          anywhere            
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  192.168.0.0/24       anywhere            
ACCEPT    !tcp  --  anywhere             224.0.0.0/4         
DROP       0    --  anywhere             224.0.0.1           
LOG        0    --  anywhere             anywhere            LOG level warning 
DROP       0    --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
DROP       0    --  anywhere             224.0.0.1           
LOG        0    --  anywhere             anywhere            LOG level warning 
DROP       0    --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  anywhere             192.168.0.0/24      
ACCEPT    !tcp  --  anywhere             224.0.0.0/4         
DROP       0    --  anywhere             224.0.0.1           
LOG        0    --  anywhere             anywhere            LOG level warning 
DROP       0    --  anywhere             anywhere           

And this is ifconfig
> root@ubuntu-server:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:47:93:BE:1C  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fe93:be1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1486 (1.4 KB)  TX bytes:2304 (2.2 KB)

eth1      Link encap:Ethernet  HWaddr 00:03:47:E3:24:C2  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5335 (5.2 KB)  TX bytes:5335 (5.2 KB)


As you can see the eth0 have an DHCP, but not connect internet until i remove iptables.
**Edited:** Now i try to reconfigure ipmasq and it can connect to internet, no need to remove iptables, but XP machine still can't connect to Internet. :confused:
> root@ubuntu-server:~# apt-get remove iptables
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firestarter ipmasq iptables
0 upgraded, 0 newly installed, 3 to remove and 7 not upgraded.
Need to get 0B of archives.
After unpacking 3936kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 92802 files and directories currently installed.)
Removing firestarter ...
Removing ipmasq ...
Removing iptables ...

I don't know why, plz help me, thanks

---

### Post by wandalalakers on 2008-03-15
Internet sharing is working for me!  Thx guys!

---

### Post by duze on 2008-04-04
Thanks for the guide, needed it to get a connection for my xbox =)

---

### Post by AWerner32 on 2008-04-06
I know there are a myriad of other posts on this subject and i have been reading them all night, i cant make this work. I have a desktop running ubuntu with an atheros wireless card running the madwifi driver and its interface is ath0. on the same computer there is a wired interface eth0. from eth0 we are plugged into another desktop which dual boots windows xp and ubuntu we can call his interface "other". I've tried the firestarter method but that always failed, i've tried i think everything and i cannot get the second computer to see anything at all. I am going to post every piece of information i can think of. my ubuntu desktop has a DHCP reservation IP of 192.168.1.2. the router is 192.168.1.1. I have as per the instructions of everything i've read set up the eth0 as 192.168.0.1.
here is ifconfig
> ath0      Link encap:Ethernet  HWaddr 00:11:50:d5:35:67  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fed5:3567/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5531 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5051 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4552770 (4.3 MB)  TX bytes:710488 (693.8 KB)

eth0      Link encap:Ethernet  HWaddr 00:0c:f1:c8:9d:60  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fec8:9d60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21724 (21.2 KB)  TX bytes:3066 (2.9 KB)
          Base address:0xdf40 Memory:fbfe0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66700 (65.1 KB)  TX bytes:66700 (65.1 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-50-D5-35-67-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37565 errors:0 dropped:0 overruns:0 frame:1517
          TX packets:5404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:7486512 (7.1 MB)  TX bytes:878188 (857.6 KB)
          Interrupt:20 


 here is my /etc/network/interfaces

> auto lo
iface lo inet loopback

auto eth0 
iface eth0 inet static
address 192.168.0.1
subnet 255.255.255.0

auto ath0 
iface ath0 inet dhcp
wireless-essid ****
wireless-key ************************



all of my networking there comes up beautifully upon booting.

after > iptables -t nat -A POSTROUTING -o ath0 -j MASQUERADEgives me > Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      for my iptables nat configuration.

my dnsmasq configuration is > # Configuration file for dnsmasq.
#
# Format is one option per line, legal options are the same
# as the long options legal on the command line. See
# "/usr/sbin/dnsmasq --help" or "man 8 dnsmasq" for details.

# The following two options make you a better netizen, since they
# tell dnsmasq to filter out queries which the public DNS cannot
# answer, and which load the servers (especially the root servers)
# uneccessarily. If you have a dial-on-demand link they also stop
# these requests from bringing up the link uneccessarily.

# Never forward plain names (without a dot or domain part)
#domain-needed
# Never forward addresses in the non-routed address spaces.
#bogus-priv


# Uncomment this to filter useless windows-originated DNS requests
# which can trigger dial-on-demand links needlessly.
# Note that (amongst other things) this blocks all SRV requests,
# so don't use it if you use eg Kerberos, SIP, XMMP or Google-talk.
# This option only affects forwarding, SRV records originating for
# dnsmasq (via srv-host= lines) are not suppressed by it.
#filterwin2k

# Change this line if you want dns to get its upstream servers from
# somewhere other that /etc/resolv.conf
#resolv-file=

# By  default,  dnsmasq  will  send queries to any of the upstream
# servers it knows about and tries to favour servers to are  known
# to  be  up.  Uncommenting this forces dnsmasq to try each query
# with  each  server  strictly  in  the  order  they   appear   in
# /etc/resolv.conf
#strict-order

# If you don't want dnsmasq to read /etc/resolv.conf or any other
# file, getting its servers from this file instead (see below), then
# uncomment this.
#no-resolv

# If you don't want dnsmasq to poll /etc/resolv.conf or other resolv
# files for changes and re-read them then uncomment this.
#no-poll

# Add other name servers here, with domain specs if they are for
# non-public domains.
#server=/localnet/192.168.0.1

# Example of routing PTR queries to nameservers: this will send all 
# address->name queries for 192.168.3/24 to nameserver 10.1.2.3
#server=/3.168.192.in-addr.arpa/10.1.2.3

# Add local-only domains here, queries in these domains are answered
# from /etc/hosts or DHCP only.
#local=/localnet/

# Add domains which you want to force to an IP address here.
# The example below send any host in doubleclick.net to a local
# webserver.
#address=/doubleclick.net/127.0.0.1

# --address (and --server) work with IPv6 addresses too.
#address=/www.thekelleys.org.uk/fe80::20d:60ff:fe36:f83

# You can control how dnsmasq talks to a server: this forces 
# queries to 10.1.2.3 to be routed via eth1
# --server=10.1.2.3@eth1

# and this sets the source (ie local) address used to talk to
# 10.1.2.3 to 192.168.1.1 port 55 (there must be a interface with that
# IP on the machine, obviously).
# --server=10.1.2.3@192.168.1.1#55

# If you want dnsmasq to change uid and gid to something other
# than the default, edit the following lines.
#user=
#group=

# If you want dnsmasq to listen for DHCP and DNS requests only on
# specified interfaces (and the loopback) give the name of the
# interface (eg eth0) here.
# Repeat the line for more than one interface.
#interface=
# Or you can specify which interface _not_ to listen on
#except-interface=
# Or which to listen on by address (remember to include 127.0.0.1 if
# you use this.)
#listen-address=
# If you want dnsmasq to provide only DNS service on an interface,
# configure it as shown above, and then use the following line to
# disable DHCP on it.
#no-dhcp-interface=

# On systems which support it, dnsmasq binds the wildcard address,
# even when it is listening on only some interfaces. It then discards
# requests that it shouldn't reply to. This has the advantage of
# working even when interfaces come and go and change address. If you
# want dnsmasq to really bind only the interfaces it is listening on,
# uncomment this option. About the only time you may need this is when
# running another nameserver on the same machine.
#bind-interfaces

# If you don't want dnsmasq to read /etc/hosts, uncomment the
# following line.
#no-hosts
# or if you want it to read another file, as well as /etc/hosts, use
# this.
#addn-hosts=/etc/banner_add_hosts

# Set this (and domain: see below) if you want to have a domain
# automatically added to simple names in a hosts-file.
#expand-hosts

# Set the domain for dnsmasq. this is optional, but if it is set, it
# does the following things.
# 1) Allows DHCP hosts to have fully qualified domain names, as long
#     as the domain part matches this setting.
# 2) Sets the "domain" DHCP option thereby potentially setting the
#    domain of all systems configured by DHCP
# 3) Provides the domain part for "expand-hosts"
#domain=thekelleys.org.uk

# Uncomment this to enable the integrated DHCP server, you need
# to supply the range of addresses available for lease and optionally
# a lease time. If you have more than one network, you will need to
# repeat this for each network on which you want to supply DHCP
# service.
dhcp-range=192.168.0.102,192.168.0.255

# This is an example of a DHCP range where the netmask is given. This
# is needed for networks we reach the dnsmasq DHCP server via a relay
# agent. If you don't know what a DHCP relay agent is, you probably
# don't need to worry about this.
#dhcp-range=192.168.0.50,192.168.0.150,255.255.255.0,12h

# This is an example of a DHCP range with a network-id, so that
# some DHCP options may be set only for this network.
#dhcp-range=red,192.168.0.50,192.168.0.150

# Supply parameters for specified hosts using DHCP. There are lots
# of valid alternatives, so we will give examples of each. Note that
# IP addresses DO NOT have to be in the range given above, they just
# need to be on the same network. The order of the parameters in these
# do not matter, it's permissble to give name,adddress and MAC in any order

# Always allocate the host with ethernet address 11:22:33:44:55:66
# The IP address 192.168.0.60
#dhcp-host=00:0c:f1:c8:9d:60,192.168.0.1

# Always set the name of the host with hardware address
# 11:22:33:44:55:66 to be "fred"
#dhcp-host=11:22:33:44:55:66,fred

# Always give the host with ethernet address 11:22:33:44:55:66
# the name fred and IP address 192.168.0.60 and lease time 45 minutes
#dhcp-host=11:22:33:44:55:66,fred,192.168.0.60,45m

# Give the machine which says its name is "bert" IP address
# 192.168.0.70 and an infinite lease
#dhcp-host=bert,192.168.0.70,infinite

# Always give the host with client identifier 01:02:02:04
# the IP address 192.168.0.60
#dhcp-host=id:01:02:02:04,192.168.0.60

# Always give the host with client identifier "marjorie"
# the IP address 192.168.0.60
#dhcp-host=id:marjorie,192.168.0.60

# Enable the address given for "judge" in /etc/hosts
# to be given to a machine presenting the name "judge" when
# it asks for a DHCP lease.
#dhcp-host=judge

# Never offer DHCP service to a machine whose ethernet
# address is 11:22:33:44:55:66
#dhcp-host=11:22:33:44:55:66,ignore

# Ignore any client-id presented by the machine with ethernet
# address 11:22:33:44:55:66. This is useful to prevent a machine
# being treated differently when running under different OS's or
# between PXE boot and OS boot.
#dhcp-host=11:22:33:44:55:66,id:*

# Send extra options which are tagged as "red" to
# the machine with ethernet address 11:22:33:44:55:66
#dhcp-host=11:22:33:44:55:66,net:red

# Send extra options which are tagged as "red" to
# any machine with ethernet address starting 11:22:33:
#dhcp-host=11:22:33:*:*:*,net:red

# Ignore any clients which are specified in dhcp-host lines
# or /etc/ethers. Equivalent to ISC "deny unkown-clients".
# This relies on the special "known" tag which is set when 
# a host is matched.
#dhcp-ignore=#known

# Send extra options which are tagged as "red" to any machine whose
# DHCP vendorclass string includes the substring "Linux"
#dhcp-vendorclass=red,Linux

# Send extra options which are tagged as "red" to any machine one
# of whose DHCP userclass strings includes the substring "accounts"
#dhcp-userclass=red,accounts

# Send extra options which are tagged as "red" to any machine whose
# MAC address matches the pattern.
#dhcp-mac=red,00:60:8C:*:*:*

# If this line is uncommented, dnsmasq will read /etc/ethers and act
# on the ethernet-address/IP pairs found there just as if they had
# been given as --dhcp-host options. Useful if you keep
# MAC-address/host mappings there for other purposes.
#read-ethers

# Send options to hosts which ask for a DHCP lease.
# See RFC 2132 for details of available options.
# Common options can be given to dnsmasq by name: 
# run "dnsmasq --help dhcp" to get a list.
# Note that all the common settings, such as netmask and
# broadcast address, DNS server and default route, are given
# sane defaults by dnsmasq. You very likely will not need 
# any dhcp-options. If you use Windows clients and Samba, there
# are some options which are recommended, they are detailed at the
# end of this section.

# Override the default route supplied by dnsmasq, which assumes the
# router is the same machine as the one running dnsmasq.
#dhcp-option=3,1.2.3.4

# Do the same thing, but using the option name
#dhcp-option=option:router,1.2.3.4

# Override the default route supplied by dnsmasq and send no default
# route at all. Note that this only works for the options sent by
# default (1, 3, 6, 12, 28) the same line will send a zero-length option 
# for all other option numbers.
#dhcp-option=3

# Set the NTP time server addresses to 192.168.0.4 and 10.10.0.5
#dhcp-option=option:ntp-server,192.168.0.4,10.10.0.5

# Set the NTP time server address to be the same machine as
# is running dnsmasq
#dhcp-option=42,0.0.0.0

# Set the NIS domain name to "welly"
#dhcp-option=40,welly

# Set the default time-to-live to 50
#dhcp-option=23,50

# Set the "all subnets are local" flag
#dhcp-option=27,1

# Send the etherboot magic flag and then etherboot options (a string).
#dhcp-option=128,e4:45:74:68:00:00
#dhcp-option=129,NIC=eepro100

# Specify an option which will only be sent to the "red" network
# (see dhcp-range for the declaration of the "red" network)
# Note that the net: part must precede the option: part.
#dhcp-option = net:red, option:ntp-server, 192.168.1.1

# The following DHCP options set up dnsmasq in the same way as is specified
# for the ISC dhcpcd in
# [http://www.samba.org/samba/ftp/docs/textdocs/DHCP-Server-Configuration.txt](http://www.samba.org/samba/ftp/docs/textdocs/DHCP-Server-Configuration.txt)
# adapted for a typical dnsmasq installation where the host running
# dnsmasq is also the host running samba.
# you may want to uncomment them if you use Windows clients and Samba.
dhcp-option=19,0           option ip-forwarding off
dhcp-option=44,0.0.0.0     set netbios-over-TCP/IP nameserver(s) aka WINS server(s)
#dhcp-option=45,0.0.0.0     netbios datagram distribution server
#dhcp-option=46,8           netbios node type
#dhcp-option=47             empty netbios scope

# Send RFC-3397 DNS domain search DHCP option. WARNING: Your DHCP client
# probably doesn't support this......
#dhcp-option=option:domain-search,eng.apple.com,marketing.apple.com

# Send RFC-3442 classless static routes (note the netmask encoding)
#dhcp-option=121,192.168.1.0/24,1.2.3.4,10.0.0.0/8,5.6.7.8

# Send vendor-class specific options encapsulated in DHCP option 43. 
# The meaning of the options is defined by the vendor-class so
# options are sent only when the client supplied vendor class
# matches the class given here. (A substring match is OK, so "MSFT" 
# matches "MSFT" and "MSFT 5.0"). This example sets the
# mtftp address to 0.0.0.0 for PXEClients.
#dhcp-option=vendor:PXEClient,1,0.0.0.0

# Send microsoft-specific option to tell windows to release the DHCP lease
# when it shuts down. Note the "i" flag, to tell dnsmasq to send the
# value as a four-byte integer - that's what microsoft wants. See
# [http://technet2.microsoft.com/WindowsServer/en/library/a70f1bb7-d2d4-49f0-96d6-4b7414ecfaae1033.mspx?mfr=true](http://technet2.microsoft.com/WindowsServer/en/library/a70f1bb7-d2d4-49f0-96d6-4b7414ecfaae1033.mspx?mfr=true)
#dhcp-option=vendor:MSFT,2,1i

# Send the Encapsulated-vendor-class ID needed by some configurations of
# Etherboot to allow is to recognise the DHCP server.
#dhcp-option=vendor:Etherboot,60,"Etherboot"

# Send options to PXELinux. Note that we need to send the options even
# though they don't appear in the parameter request list, so we need
# to use dhcp-option-force here. 
# See [http://syslinux.zytor.com/pxe.php#special](http://syslinux.zytor.com/pxe.php#special) for details.
# Magic number - needed before anything else is recognised
#dhcp-option-force=208,f1:00:74:7e
# Configuration file name
#dhcp-option-force=209,configs/common
# Path prefix
#dhcp-option-force=210,/tftpboot/pxelinux/files/
# Reboot time. (Note 'i' to send 32-bit value)
#dhcp-option-force=211,30i

# Set the boot filename for BOOTP. You will only need 
# this is you want to boot machines over the network and you will need
# a TFTP server; either dnsmasq's built in TFTP server or an
# external one. (See below for how to enable the TFTP server.)
#dhcp-boot=pxelinux.0

# Boot for Etherboot gPXE. The idea is to send two different
# filenames, the first loads gPXE, and the second tells gPXE what to
# load. The dhcp-match sets the gpxe tag for requests from gPXE.
#dhcp-match=gpxe,175 # gPXE sends a 175 option.
#dhcp-boot=net:#gpxe,undionly.kpxe
#dhcp-boot=mybootimage
 
# Enable dnsmasq's built-in TFTP server
#enable-tftp

# Set the root directory for files availble via FTP.
#tftp-root=/var/ftpd

# Make the TFTP server more secure: with this set, only files owned by
# the user dnsmasq is running as will be send over the net.
#tftp-secure

# Set the boot file name only when the "red" tag is set.
#dhcp-boot=net:red,pxelinux.red-net

# An example of dhcp-boot with an external server: the name and IP
# address of the server are given after the filename.
#dhcp-boot=/var/ftpd/pxelinux.0,boothost,192.168.0.3

# Set the limit on DHCP leases, the default is 150
#dhcp-lease-max=150

# The DHCP server needs somewhere on disk to keep its lease database.
# This defaults to a sane location, but if you want to change it, use
# the line below.
#dhcp-leasefile=/var/lib/misc/dnsmasq.leases

# Set the DHCP server to authoritative mode. In this mode it will barge in
# and take over the lease for any client which broadcasts on the network,
# whether it has a record of the lease or not. This avoids long timeouts
# when a machine wakes up on a new network. DO NOT enable this if there's
# the slighest chance that you might end up accidentally configuring a DHCP
# server for your campus/company accidentally. The ISC server uses
# the same option, and this URL provides more information:
# [http://www.isc.org/index.pl?/sw/dhcp/authoritative.php](http://www.isc.org/index.pl?/sw/dhcp/authoritative.php)
#dhcp-authoritative

# Run an executable when a DHCP lease is created or destroyed.
# The arguments sent to the script are "add" or "del", 
# then the MAC address, the IP address and finally the hostname
# if there is one. 
#dhcp-script=/bin/echo

# Set the cachesize here.
#cache-size=150

# If you want to disable negative caching, uncomment this.
#no-negcache

# Normally responses which come form /etc/hosts and the DHCP lease
# file have Time-To-Live set as zero, which conventionally means
# do not cache further. If you are happy to trade lower load on the
# server for potentially stale date, you can set a time-to-live (in
# seconds) here.
#local-ttl=

# If you want dnsmasq to detect attempts by Verisign to send queries
# to unregistered .com and .net hosts to its sitefinder service and
# have dnsmasq instead return the correct NXDOMAIN response, uncomment
# this line. You can add similar lines to do the same for other
# registries which have implemented wildcard A records.
#bogus-nxdomain=64.94.110.11

# If you want to fix up DNS results from upstream servers, use the
# alias option. This only works for IPv4.
# This alias makes a result of 1.2.3.4 appear as 5.6.7.8
#alias=1.2.3.4,5.6.7.8
# and this maps 1.2.3.x to 5.6.7.x
#alias=1.2.3.0,5.6.7.0,255.255.255.0


# Change these lines if you want dnsmasq to serve MX records.

# Return an MX record named "maildomain.com" with target
# servermachine.com and preference 50
#mx-host=maildomain.com,servermachine.com,50

# Set the default target for MX records created using the localmx option.
#mx-target=servermachine.com

# Return an MX record pointing to the mx-target for all local
# machines.
#localmx

# Return an MX record pointing to itself for all local machines.
#selfmx

# Change the following lines if you want dnsmasq to serve SRV
# records.  These are useful if you want to serve ldap requests for
# Active Directory and other windows-originated DNS requests.
# See RFC 2782.
# You may add multiple srv-host lines.
# The fields are <name>,<target>,<port>,<priority>,<weight>
# If the domain part if missing from the name (so that is just has the
# service and protocol sections) then the domain given by the domain=
# config option is used. (Note that expand-hosts does not need to be
# set for this to work.)

# A SRV record sending LDAP for the example.com domain to
# ldapserver.example.com port 289
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389

# A SRV record sending LDAP for the example.com domain to
# ldapserver.example.com port 289 (using domain=)
#domain=example.com
#srv-host=_ldap._tcp,ldapserver.example.com,389

# Two SRV records for LDAP, each with different priorities
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389,1
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389,2

# A SRV record indicating that there is no LDAP server for the domain
# example.com
#srv-host=_ldap._tcp.example.com

# The following line shows how to make dnsmasq serve an arbitrary PTR
# record. This is useful for DNS-SD. (Note that the
# domain-name expansion done for SRV records _does_not
# occur for PTR records.)
#ptr-record=_http._tcp.dns-sd-services,"New Employee Page._http._tcp.dns-sd-services"

# Change the following lines to enable dnsmasq to serve TXT records.
# These are used for things like SPF and zeroconf. (Note that the
# domain-name expansion done for SRV records _does_not
# occur for TXT records.)

#Example SPF.
#txt-record=example.com,"v=spf1 a -all"

#Example zeroconf
#txt-record=_http._tcp.example.com,name=value,paper=A4


# For debugging purposes, log each DNS query as it passes through
# dnsmasq.
#log-queries

# Log lots of extra information about DHCP transactions.
#log-dhcp

# Include a another lot of configuration options.
#conf-file=/etc/dnsmasq.more.conf
#conf-dir=/etc/dnsmasq.d

which to my knowlege and understanding ought to be serving dhcp clients.

my ip_forward in /proc/sys/net/ipv4/ip_forward is set to 1

ipmasq is set to load after the interfaces are activated
i feel like my error is in the DHCP of the dnsmasq, if anybody can tell me how to just make that work with "other" being static that would be fine, i just need internet on "other".
also i know the ethernet cord is good and all the hardware is good because the Ubuntu computer is also a dual boot and ICS in windows it works fine but i need the linux to work. 
somebody please tell me what i'm doing wrong

---

### Post by wingmanjd on 2008-04-29
Will this work for rndis connections to connect to the Internet via an eth connection?  I'm attempting to share my desktop's internet connection with my PDA which connects via rndis.  I can ping between the two devices, but the PDA cannot reach out to the router/ internet.

Desktop:
Eth: x.x.111.16
rndis0: 169.254.2.2

PDA:
IP: 169.254.2.2

Any help would be appreciated.

---

### Post by T4K on 2008-05-01
> **john_spiral said:**
> Hi BigIslandVegan,

Looks like your eth0 (ethernet) port has not been activated.

Activated through the GUI.

Then  give it an exciting address like 192.168.0.1

Follow the howto.

start off with:

**sudo su**

to give you root access

change setp 2 to:

iptables -t nat -A POSTROUTING -o 
**ppp0** -j MASQUERADE 

Give the other system an ip address of 192.168.0.2 and set it's gateway as 192.168.0.1

give it a try 

Johne

I know this is an odd thread. I've tried what you said. As soon as I do that the eth0 is at 192.168.0.1. An for some reason wvdial won't let me redial says "Unable to kill process" checked the pid and it's not running. It also won't get dnsmasq and ipmasq. This is on a Dell 1520. EVDO Novatel 5700. I'm kinda stomped because I can't turn off the static ip I put on the nic for the server address so now I have no internet at all on the laptop.

---

### Post by metaphorm on 2008-06-08
I followed all these instructions without any issues. However, I still cannot seem to share the connection on my ubuntu (7.10) machine.

eth0 - internet (DSL)
eth1 - LAN (192.168.0.1)

The winXP machines can ping my ubuntu machine fine. But no connection to the net from them. I have setup static IPs on the XP machines, but still no luck.

Any suggestions?



> **anaoum said:**
> Hello,

The following will explain how to share your Internet connection:

Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

    # ifconfig ethX ip      

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

    # iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE       

where ethX is the network card that the Internet is coming from 

    # echo 1 > /proc/sys/net/ipv4/ip_forward

3. Install dnsmasq and ipmasq using apt-get: 

    # apt-get install dnsmasq ipmasq

4. Restart dnsmasq:

    # /etc/init.d/dnsmasq restart

5. Reconfigure ipmasq to start after networking has been started:

    # dpkg-reconfigure ipmasq

6. Repeat steps 1 and 2.

7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

    # gedit /etc/sysctl.conf

8. Reboot. (Optional)

I hope this helps.

Good luck!

---

### Post by wbgraphy on 2008-07-06
Thanks for the good post. now I am able to share my ppp0 dial-up modem YAY! :popcorn:

---

### Post by Mirmil on 2008-07-10
I messed up my network connection and now I'm trying to fix things up... AS in many examples before my ubuntu is on eth1 conect4ed to internet, winxp is on eth0. XP can see ubuntu but cannot see internet. When I try using 
sudo ifconfig eth1 ip
I get answer that 
sudo: unable to resolve host mirmil
(mirmil is name of my computer)
I HAD that problem before, just now I have no idea how did i fixed it...
I tried to use Firestarter but it crashes when I try to switch from eth0 to eth1 during configuration on second screen


EDIT: 
I fixed that finally, using help from this bug [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/195308]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/195308")

---

### Post by abish on 2008-07-11
> **anaoum said:**
> Hello,

The following will explain how to share your Internet connection:

Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

    # ifconfig ethX ip      

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

    # iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE       

where ethX is the network card that the Internet is coming from 

    # echo 1 > /proc/sys/net/ipv4/ip_forward

3. Install dnsmasq and ipmasq using apt-get: 

    # apt-get install dnsmasq ipmasq

4. Restart dnsmasq:

    # /etc/init.d/dnsmasq restart

5. Reconfigure ipmasq to start after networking has been started:

    # dpkg-reconfigure ipmasq

6. Repeat steps 1 and 2.

7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

    # gedit /etc/sysctl.conf

8. Reboot. (Optional)

I hope this helps.

Good luck!

Well, when i
echo 1 > /proc/sys/net/ipv4/ip_forward
i get: bash: /proc/sys/net/ipv4/ip_forward: Permission denied
even with sudo, i get the same thing...
how do i move forward?

---

### Post by Mirmil on 2008-07-11
Try
sudo su

---

### Post by mpn_1990 on 2008-07-21
I have a network configured like so:

Cable modem is connected by wire into a Linksys WRT54G wireless-G router.
Two windows XP machines are connected into the router by wire.
One, my Ubuntu Linux machine, is connected by wireless.

I have an old Windows 2000 PC connected to the TV set I'd like to put on the internet by linking it and the Linux machine that is hooked up wirelessly. As in, I'd like to plug in the Windows 2000 machine to my Linux machine using ethernet and have internet shared to the Windows 2000 machine. 

My interfaces that show up in ifconfig are eth0, lo, and wlan0. wlan0 is my USB adapter that connects this computer to the internet; eth0 is unused and I'd like to use that to share my connection with the TV machine.

How can I do this? Where do I substitute ethX for wlanX? And will doing this screw up any of my other machines (the two plugged right into the back of the router?)

---

### Post by mpn_1990 on 2008-07-21
This guide is a joke.

I set it up and it hosed my internet until i PURGED dnsmasq and ipmasq.

It also didn't mention how to resolve the problem of my computer keep trying to connect to eth0 WHICH IS THE ONE I WANT TO USE TO SHARE NOT THE ONE THAT CONNECTS TO THE INTERNET. wlan0 IS THE WIRELESS THAT CONNECTS TO THE INTERNET WHY WON'T IT STAY CONNECTED AFTER I PLUG IN THE WIRE.

---

### Post by jreinis on 2008-07-24
> **mpn_1990 said:**
> this guide is a joke.

I set it up and it hosed my internet until i purged dnsmasq and ipmasq.

It also didn't mention how to resolve the problem of my computer keep trying to connect to eth0 which is the one i want to use to share not the one that connects to the internet. Wlan0 is the wireless that connects to the internet why won't it stay connected after i plug in the wire.

i agree completly!!!!!!!!!!
This is a joke - do not use the guide!!!!!!!!!!!!!

---

### Post by WillemToerien on 2008-08-02
I've used this guide and it works perfectly. I have 3 pc's here at my home. One pc is a pc that acts like a proxy. It uses the E220 modem with the wvdial hsdpa to connect to the internet. I have one question, how can I see statistics? :popcorn:

---

### Post by WillemToerien on 2008-08-02
> **jreinis said:**
> i agree completly!!!!!!!!!!
This is a joke - do not use the guide!!!!!!!!!!!!!

This guide worked for me. If you're not happy with this guide, then do not use it.

---

### Post by qwerti on 2008-08-05
This worked for me ! thanks a lot !

---

### Post by CKyle22 on 2008-08-16
I have the "changes aren't sticking after reboot" problem.

---

### Post by Bachstelze on 2008-08-16
> **mpn_1990 said:**
> This guide is a joke.

It is also pretty old... If there's many people interested in this, I could write another one, though.

---

### Post by CKyle22 on 2008-08-17
> **HymnToLife said:**
> It is also pretty old... If there's many people interested in this, I could write another one, though.
Do it do it do it! :D

---

### Post by WillemToerien on 2008-08-17
> **HymnToLife said:**
> It is also pretty old... If there's many people interested in this, I could write another one, though.

I agree it is old. However, I am using a E220 data card to connect to the internet. And I use this guide to set up a proxy at home. Im still way too inexperienced to try and figure out how exactly to set up squid on a ubuntu-server. I've read a lot of stuff, but this howto is really easy. If you would write another one, I would try it out on a virtual ubuntu pc.

Also, would it be possible to be able to see statistics on this internet sharing? For example:
PC 1 = 30MB
PC 2 = 120MB

---

### Post by Sleepy-zz-John on 2008-08-26
> **WillemToerien said:**
> I've used this guide and it works perfectly. I have 3 pc's here at my home. One pc is a pc that acts like a proxy. It uses the E220 modem with the wvdial hsdpa to connect to the internet. I have one question, how can I see statistics? :popcorn:

I'm encouraged to know that you have cracked internet sharing of your E220.   In my case I'm trying to allow my internet radio (fixed IP 192.168.0.23 on wired connection Eth0)  to see the internet that's coming in on ppp0,  but as a beginner I'm afraid I'm struggling a bit with anaoum's explanation  :)

D'you think you could post some of the significant code you used in your case so as to set me and other beginners on the right track?   :?:

---

### Post by WillemToerien on 2008-08-27
> **Sleepy-zz-John said:**
> I'm encouraged to know that you have cracked internet sharing of your E220.   In my case I'm trying to allow my internet radio (fixed IP 192.168.0.23 on wired connection Eth0)  to see the internet that's coming in on ppp0,  but as a beginner I'm afraid I'm struggling a bit with anaoum's explanation  :)

D'you think you could post some of the significant code you used in your case so as to set me and other beginners on the right track?   :?:

Im going to give you my setup:
```

sudo su
ifconfig eth0 192.168.0.1
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
apt-get install dnsmasq ipmasq
/etc/init.d/dnsmasq restart
dpkg-reconfigure ipmasq
ifconfig eth0 192.168.0.1
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
gedit /etc/sysctl.conf

```

Add the line *net.ipv4.ip_forward = 1* at the bottom of the file, save and close it.

And you're done.

Remember to make the other pc's dns the ip 192.168.0.1 and their gateway. Im not sure. But play around.:guitar:

---

### Post by ub78 on 2008-08-27
Hey all,

first of all, thanks to anaoum for the help. I really appreciated and helped completing the puzzle!

I've put my experience in here:
[http://ubuntuforums.org/showthread.php?t=902293](http://ubuntuforums.org/showthread.php?t=902293)

and now I'm struggling to get ICS over bluetooth working...
Any help would be greatly appreciated! Thx!

---

### Post by lincoln32 on 2008-08-27
I have been fighting this for a long time. any ideas would help. I want the wireless for internet and lan to feed x box 360 fire starter stops the lan and have not seen a workable post to fix it is there a simple way to do this
or go back to win would need. It would need dchp and then straight or crossed lan cord to x box since I will not need a router or switch

---

### Post by Sleepy-zz-John on 2008-08-31
> **WillemToerien said:**
> Im going to give you my setup:
```

sudo su
ifconfig eth0 192.168.0.1
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
apt-get install dnsmasq ipmasq
/etc/init.d/dnsmasq restart
dpkg-reconfigure ipmasq
ifconfig eth0 192.168.0.1
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
gedit /etc/sysctl.conf

```

Add the line *net.ipv4.ip_forward = 1* at the bottom of the file, save and close it.

And you're done.

Remember to make the other pc's dns the ip 192.168.0.1 and their gateway. Im not sure. But play around.:guitar:

OK,  Many thanks for the above.   It took me a while but I've finally cracked it and got it working :D

I set my internet radio (and the same would no doubt apply to another computer) to the fixed IP address 192.168.0.23, and its gateway and dns to 192.168.0.1,   Subnet mask 255.255.255.0  

But the main secret was in Network Settings,  I had to go there and set the wired connection eth0 which I'd connected my internet radio to,  to "Address: ipv4ll"   (Local Zeroconf network).  Not to Static IP or to DHCP.   Without this setting the system was trying to look for internet connectivity via my LAN and radio, instead of via ppp0.    In other words it was trying to make my LAN work in the reverse direction. 

Anyway,  thanks!   Got it in the end  :D

---

### Post by lincoln32 on 2008-09-03
so this would not have dhcp routing? I guess I need to see if i can set the IP in the xbox manually

---

### Post by Alex22 on 2008-10-21
Lincoln, it's hard to read your English, but what do you need the DHCP for?
It's always better not to use it, if one can.

It's good only for big networks, and you have 2 computers at your home to connect.

---

### Post by lincoln32 on 2008-10-21
I have over 10 pc's on network and change them often so DCHP is a good thing
also the x-box is used at several other locations so a dchp server will make it so we do not have to change ip"s each time we move it

---

### Post by zandovalsdesk on 2008-11-01
UBUNTU 8.10 DESKTOP INTREPID 10/2008 
Notes from (Set up Internet sharing UBUNTU Feisty Fawn  July 2007)

Set up the computer with Internet first - Don't bother with any settings for the LAN - Just get the INTERNET connection working first.

I PUT THE LOCAL SWITCH ON ETH0 AND THE CABLE MODEM ON ETH1...


           # Eth1 TULIPDHCP Cable Modem
           #
Computer####
           #
           # Eth0 VIA SWITCH LAN (don't set up yet LEAVE UNCHECKED)

Up date the install using the icon on the panel

Goto Add Remove applications

Set to All Applications in the upper right hand corner

Do search and Install SAMBA

Do search and install FIRE STARTER

CANT REMEMBER - (Disable Eth1???... MAYBE NOT)

Set up the LAN on Eth0 - Don't use DHCP yet just assign the LAN an IP address like 192.168.0.1 - DO THIS IN SYSTEM> PREF> NETWORK - LOOKS SCREWY - WILL SEE AUTO ETH1 AND AUTO ETH0 - AT AUTO ETH0 GOTO YOUR SETTINGS FOR IPv4 - EDIT - ADD -  AND SET ADDRESS: 192.168.0.1  MASK: 255.255.255.0  GATE: 0.0.0.0 AND SAVE

OPEN NAUTILUS UNDER ROOT TO MAKE A SHARED FILE
Make a file on the Desk top and set up sharing with that file via SAMBA in properties

Now you can go to anther computer and run it using a PUPPY LINUX CD - Use its wizard to set up the net connection - Don't use DHCP and just use a IP address like 192.168.0.5

Test to see if the Puppy computer can see the main computer by using Linneiborhood search for 192.168.0.1 - If it can see the computer that's good

           # Eth1 DHCP Cable Modem (UNCHECK)
           #
Computer####
           #
           # Eth0 VIA SWITCH LAN 192.168.0.1 to 192.168.0.5

Go back to the the main computer and enable Eth1 - Check to see if you can connect to the Internet

Start up Fire Starter and set up Eth1 as DHCP Internet and Eth1 as LAN 192.168.0.1

After this is done you can go back and run the Fire Starter wizard again and set up the LAN with DHCP - Some time during all of this Fire Starter Will ask to install added DHCP IP tables - You must do this in order for DHCP to work on the LAN

After you get to this point yo can go back to the Puppy computer and restart the net work wizard to fine the main computer using DHCP and with that share the Internet



           # Eth1 DHCP Cable Modem
           #
Computer####
           #
           # Eth0 VIA SWITCH LAN 192.168.0.1 to DHCP

ZANDOVAL IN BASTROP TEXAS USA...

---

### Post by cptnff on 2008-11-30
I've been trying to undo the damage done by this guide for hours, and could really use some help. I was trying to connect to xbox live via ethernet cord and after many different tutorials I found this one. I followed all the directions, and now I have no internet connection. my computer is telling me that I'm connected to the wireless network that I'm always connected to, and everything looks normal, but when I open firefox it acts as if there is no connection.:confused:

 at this point I'm willing to give up hope on ever connecting to xbox live through ubuntu, but I still need to be able to connect to the internet. anybody know how to completely undo the changes brought about by following this guide. or even better how to fix this problem, and get my xbox to get past the dns test that it keeps failing.


okay so I fixed my connection problem. now if I could only get my xbox to connect

---

### Post by cheeseburgerman1 on 2009-01-06
> **anaoum said:**
> Hello,

The following will explain how to share your Internet connection:

Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

    # ifconfig ethX ip      

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

    # iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE       

where ethX is the network card that the Internet is coming from 

    # echo 1 > /proc/sys/net/ipv4/ip_forward

3. Install dnsmasq and ipmasq using apt-get: 

    # apt-get install dnsmasq ipmasq

4. Restart dnsmasq:

    # /etc/init.d/dnsmasq restart

5. Reconfigure ipmasq to start after networking has been started:

    # dpkg-reconfigure ipmasq

6. Repeat steps 1 and 2.

7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

    # gedit /etc/sysctl.conf

8. Reboot. (Optional)

I hope this helps.

Good luck!

i have a problem as soon as i hit step one. it says access denied or something like that.

---

### Post by tednumber8 on 2009-01-11
How to do this exact thing with wireless? please somebody point me in right direction. Im running 8.10 Intrepid. Nowhere have I found a tutuorial to ICS over wirless network card. Im ready to kick the computer, the nearest person and maybe even myslef.


PLEASE PLEASE PLEASE

---

### Post by Abhi Kalyan on 2009-01-12
> **tednumber8 said:**
> How to do this exact thing with wireless? please somebody point me in right direction. Im running 8.10 Intrepid. Nowhere have I found a tutuorial to ICS over wirless network card. Im ready to kick the computer, the nearest person and maybe even myslef.


PLEASE PLEASE PLEASE

> **tednumber8 said:**
> How to do this exact thing with wireless? please somebody point me in right direction. Im running 8.10 Intrepid. Nowhere have I found a tutuorial to ICS over wirless network card. Im ready to kick the computer, the nearest person and maybe even myslef.


PLEASE PLEASE PLEASE

Couple of things that really screwed my brain and dried my stomach was that
"I forgot to set my DNS / GATEWAY (etc), all else was working fine"
try
sudo sysctl.conf -p
flush all chains and rules before going into this tutorial.

Using this info you can:
create NAT
configure wireless
make squid transparent
(i.e) withour configuring Proxy in the browser, you can direct all 80 traffic to 8080 dansguardian.
Its 2340 IST now,
moving home
WIll come tomorow and write a complete tutorial as an extension of this post that had helped me a ton.

Thank you Guys!!

---

### Post by toferdelachris on 2009-03-20
so i am a super ubuntu/linux noob.

i used sudo lshw -c net

and got this:

-laptop:~$ sudo lshw -C net
  *-network:0             
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wifi0
       version: 01
       serial: 00:0e:9b:55:d7:c7
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) ip=192.168.1.104 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 10
       serial: 00:01:4a:07:b8:9c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s


it seems pretty obvious that the one that says "wireless interface" under description is my wireless network card, so what do i type for ethX? "wifi0"?

thanks for the help...

---

### Post by toferdelachris on 2009-03-20
> **cptnff said:**
> I've been trying to undo the damage done by this guide for hours, and could really use some help. I was trying to connect to xbox live via ethernet cord and after many different tutorials I found this one. I followed all the directions, and now I have no internet connection. my computer is telling me that I'm connected to the wireless network that I'm always connected to, and everything looks normal, but when I open firefox it acts as if there is no connection.:confused:

 at this point I'm willing to give up hope on ever connecting to xbox live through ubuntu, but I still need to be able to connect to the internet. anybody know how to completely undo the changes brought about by following this guide. or even better how to fix this problem, and get my xbox to get past the dns test that it keeps failing.


okay so I fixed my connection problem. now if I could only get my xbox to connect

so i kno exactly what you're talking about with firefox not bringing up any webpages - you're having DNS trouble, i've had the same issue on my windows machine... for that i just reboot and it fixes the DNS. i have no idea what to do on ubuntu, but maybe knowing that your problem is most likely DNS-related might give you a jumping off point.

i too have been trying to share my internet with my xbox, let me know if you figure it out cause it ain't workin for me...

---

### Post by Gvidas S. on 2009-03-24
Hello,
I'll begin with saying that I'm a new to Ubuntu, I love it, though.

Here's my problem: after I complete all steps, not only do I not get internet on guest XP via Virtualbox, but I lose it on host Ubuntu. I had to disable ipmasq to get it back again. I've followed everything step by step and did everything right, the only difference being that I've installed ipmasq and dnsmasq manually instead of the 3rd step, because after I start configuring network card there's no internet until I reboot the system.

Here's what I just got with lshw -c net, if it helps:
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:c7:f1:53:c6:68
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Any help is appreciated.


EDIT: Problem gone.

---

### Post by maxesanu on 2009-03-24
Dear all,

I am new to Ubuntu and I have tried to perform these steps but now I cannot connect to Internet at all. Is there any way I can reverse these steps? Please help me do something so that I do not reinstall Ubuntu after it took me good couple of hours to get my Atheros card working with madwifi.

I connect to the internet via PPPoE and my LAN card is eth0 and I have applied the following rules till step 5 for eth0 and then I have figured it out that it is my wireless card with which I will create an Ad-Hoc network between Ubuntu machine and the other computer that I have to configure and I have reperformed the steps for wifi0. (I know, this is extrmely dumb of me, I shouldn't even be writing this), but if anyone can help me, this would spare long hours reinstalling Ubuntu and reconfiguring things.

Thank you,

Max.

---

### Post by waster on 2009-04-05
> **varunus said:**
> The Firestarter firewall can do all of this for you, by the way...

```
sudo apt-get install firestarter
```

Its just a frontend to iptables.

It's certainly better than trying to configure network manager to share a connection, but has its own problems. 

1) it only lets you share with one other interface.
2) it spews an enormous amount of logging, and it is very difficult to turn this off permenantly
3) it adds additional restrctive firewall rules which do things like stop your virtual machine networking working.

I highly recommend, for desktop PCs sharing internet connections to:

1) uninstall network manager and firestarter
2) use hostapd to make a base station instead of using ad-hoc wireless connections (if hardware permits)
3) configure manually using /etc/network/interfaces and dnsmasq (which can provide a DHCP service with this single change to the default config file:

dhcp-range=192.168.0.20,192.168.0.254,255.255.255.0
(and add a line "except-interface ethX" to give out IP addresses on ethX, e.g. if it connected to someone else's LAN)

4) "resolvconf" takes a little getting used to, but is actually a well integrated system, and should be installed.

---

### Post by waster on 2009-04-05
> **cheeseburgerman1 said:**
> i have a problem as soon as i hit step one. it says access denied or something like that.

Indeed. You need to use sudo otherwise nothing in the instructions will work.

---

### Post by cox377 on 2009-04-08
Hello all

Is it possible, using 

# sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE

&

# sudo iptables -A FORWARD -i eth0 -j ACCEPT

&

# # echo 1 > /proc/sys/net/ipv4/ip_forward

To get the connection to bridge over, inclusive of the IP range / routers DHCP?

Much appreciated

CoXen

---

### Post by haueterb on 2009-04-28
good info

---

### Post by modmadmike on 2009-05-06
Had to set up R.I.P on my 2nd router for my netshares to work.

---

### Post by cworkman29729 on 2009-05-11
i can't get past step 1 it gives me 

SIOCSIFADDR: Permission denied

:confused::confused::confused::confused:

---

### Post by dannybuntu on 2009-05-16
IT WORKS IT WORKS IT WORKS!!!!! YAHOO!!!! Date is 05-16-09 7:01 PM. Yeah Yeah! 

Sameless self-promotion but related nevertheless! 

[http://dannybuntu.blogspot.com/2009/05/day-998-some-internet-connection.html](http://dannybuntu.blogspot.com/2009/05/day-998-some-internet-connection.html)

---

### Post by jago25_98 on 2009-05-22
According to this great little howto [this ]("http://www.billauer.co.il/ipmasq-html.html") forward is better than masquerade. You can forward everything on an interface (as easy as brctl addif eth0 eth1)

---

### Post by noobdood on 2009-06-27
I did this and now I can't use the internet on my linux computer. How do I undo this?

---

### Post by SKiLLsSoLoN on 2009-07-04
> **noobdood said:**
> I did this and now I can't use the internet on my linux computer. How do I undo this?

I had the same thing happen to me... I guess back to Windows.

If anyone can tell me how to reset ifconfig so I can get the internet back I would be happy :)


i did ipconfig wlan0 192.168.0.103 then turned around and did ipconfig wmaster0 192.168.0.103

I think it might of been the iptable that messed me up tho.

iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE 

and

iptables -t nat -A POSTROUTING -o wmaster0 -j MASQUERADE 


any help would be nice. When i reconnect to the wireless connection I can get internet for about 5 seconds then it stops.


I really like Ubuntu and want to use it but I have to use VB .Net for school and need the internet on virtualbox!

---

### Post by naddix on 2009-07-08
to undo i always did 

sudo apt-get remove iptables

sudo apt-get install iptables 

this will get your internet back

---

### Post by hejp on 2009-07-14
You can configure internet connection sharing with the** NetworkManager Applet** (which is installed by default with gnome at least), the nice **UI** makes it easy to configure.

Here's what to do:

Right click on it in the system tray.
Click 'Edit Connections...'
Select the connection you are sharing with.
Set 'Method' to 'Shared to other computers' which is under the 'IPv4 Settings'

[Here's an explanation with screenshots!]("http://hejp.freei.me/blog/how-to/simple-ics-internet-connection-sharing-on-ubuntu-with-screenshots/")

---

### Post by dbanie on 2009-07-14
kinda try and error thing when setting up the internet sharing but i already have my best solution, try klik the link on my sig or u can try surf to my site [http://jizzomaru.kwebserv.info](http://jizzomaru.kwebserv.info)

:guitar: thks for all ubuntu forum members... keep in supporting ):P

---

### Post by majkelpl on 2009-07-16
How to revert this??

> **anaoum said:**
> Hello,

The following will explain how to share your Internet connection:

Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

    # ifconfig ethX ip      

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

    # iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE       

where ethX is the network card that the Internet is coming from 

    # echo 1 > /proc/sys/net/ipv4/ip_forward

3. Install dnsmasq and ipmasq using apt-get: 

    # apt-get install dnsmasq ipmasq

4. Restart dnsmasq:

    # /etc/init.d/dnsmasq restart

5. Reconfigure ipmasq to start after networking has been started:

    # dpkg-reconfigure ipmasq

6. Repeat steps 1 and 2.

7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

    # gedit /etc/sysctl.conf

8. Reboot. (Optional)

I hope this helps.

Good luck!

The NAT service isn't needed any more in my network, besides, I've lost my internet connection...

Any hints?

---

### Post by Abhi Kalyan on 2009-07-17
> **majkelpl said:**
> How to revert this??



The NAT service isn't needed any more in my network, besides, I've lost my internet connection...

Any hints?

sudo apt-get remove --purge dnsmasq ipmasq
Add # infront of the line "net.ipv4.ip_forward = 1" in /etc/sysctl.conf
echo 1 > /proc/sys/net/ipv4/ip_forward
sudo iptables -X
sudo iptables -F
sudo shutdown -r now

That does the reversal. and removes all the iptables.

---

### Post by jarrarist on 2009-08-02
Okay I messed things up,

I did everything you said, I forgot that I had another active connection [other than the two connections i'm configuring] that was using ip 192.168.0.1 
so the request to restart that dnamsq failed

I realized the mistake, deleted the three network cards, added the three again, now it won't even connect to the internet

The only unusual about my case is that I am sharing the internet over eth0, but my internet comes from Mobile Broadband [called it usbinternet ], after doing all what you said now the mobile broadband won't even connect to the internet

i'm dual booting with Ubuntu 9.08 and XP. On XP the computer connects normally and shares normally (the other two computers on the network are linux, and I wanna get rid of XP in my network completely)

I need to know first how to restart the settings of the cards, I tried deleting and adding them again and it still wouldn't connect anymore. [It used to connect to usbinternet up until I entered the code you suggested]

Help please :)

p.s: consider me a big fat stupid n00b, I've been using linux for few weeks only, so explain everything please... for example I didnt know and had to search to find out how to become root in the first place.

---

### Post by Bloodhound2922 on 2009-08-10
Hey, I'm currently dual booting WinVista/Ubuntu and am considering cutting the vista and going to full Ubuntu install....

The thing is, I play Xbox 360 online and I use my computer as a router to get the 360 to the net.
I connect the ethernet cable to the xbox and the computer, and I have the computer on Wi-Fi to my router in the kitchen. I then Right click on my Wireless Connection in Vista and tick the 'share this network' box, allowing my xbox to connect to the internet..............

Is this essentially what this method does? Or would this allow my xbox to connect to the internet?


If so, how would I go about finding my network card and what part of that would I type into terminal (possibly an example?)?

Thanks in advance.

---

### Post by toolfan202 on 2009-08-12
Hello

I am running a Ubuntu/Vista setup with my linux box providing internet (or trying to) to the vista machine. Ubuntu connects to the internet just fine, however, the second network adapter sends out IP: 10.42.43.1 for the Vista machine to use, which it can't.  Any help as to why it's doing this and how I can get it to connect.

Thanks.

Also, ifconfig for either connection gives me

```
insipid@Laconic:~$ ifconfig eth1 131.230.51.39
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
insipid@Laconic:~$ ifconfig eth2 10.42.43.1
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied

```

---

### Post by brk3 on 2009-08-16
toolfan202, you need to run ifconfig as root.

---

### Post by toolfan202 on 2009-08-16
It seems I didn't have to do any of this.  I just had to switch the IPv4 settings on both Ethernet adapters to *shared to other computers* and everything is working great.

---

### Post by kwikshot on 2009-08-26
Ok I have a problem with static ip.

My Internet connection: wlan0
```

wlan0     Link encap:Ethernet  HWaddr 00:30:bd:f7:33:99  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fef7:3399/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43845 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104877026 (104.8 MB)  TX bytes:3658205 (3.6 MB)
```

This is redirecting the correct traffic to eth0
```

eth0      Link encap:Ethernet  HWaddr 00:16:17:22:1f:75  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe22:1f75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2543835 (2.5 MB)  TX bytes:97895571 (97.8 MB)
          Interrupt:20 Base address:0xde00 
```

I manually set the 'inet addr' with:
```
sudo ifconfig eth0 192.168.0.1
```

And then while I am using the device the inet addr will dissapear.
```

eth0      Link encap:Ethernet  HWaddr 00:16:17:22:1f:75  
          inet6 addr: fe80::216:17ff:fe22:1f75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2600314 (2.6 MB)  TX bytes:97916423 (97.9 MB)
          Interrupt:20 Base address:0xde00 
```

This stops the client from connecting to 192.168.0.1


I have not enabled any ethernet in Network Manager as doing it in network manager requires you to specify a default gateway for the adapter, which is stupid cuz it IS the gateway.

---

### Post by gecko91 on 2009-08-29
I have a USB mobile broadband connection on my linux box. I would like to share the internet through the wired network and if possible the wireless network. How should I go about this?

Thanks,
Nathan

---

### Post by agx2123 on 2009-08-29
> **toolfan202 said:**
> It seems I didn't have to do any of this.  I just had to switch the IPv4 settings on both Ethernet adapters to *shared to other computers* and everything is working great.
 

This worked for me as well.  I have to wonder though if I'm missing anything by going the easy way.  Does the more involved method work more efficiently or something, or is it just for people who can't get it working like I did?

---

### Post by offbyte on 2009-09-08
a tip from 2006 but still serving me good ;)
that was one of the best tings in linux once you know command line it's a friend forever!

---

### Post by gwydionwaters on 2009-10-07
i followed the instructions, i have an active connection on wlan0 and want to share it through eth0. when i use the instructions my computer can no longer use the internet, although it does connect to my network. and my xbox say's there is no network connection. i had to undo the steps to get connectivity back

---

### Post by renedejager on 2009-10-11
Hello 
(this is my first post)

I've try'd this on Ubuntu Server 9.04 to connect my client pc to it. But after i did all this my internet connection is not woking anymore on the server and ofcaurce also not on the client pc. I was thinking i did something wrong with the pkgk-reconfigure dnsmasq.

My setup is (expirimental) in Virtualbox

Internet > Wireless router > Host pc > virtualbox nat(10.0.15.0) > Ubuntu Server > Ubuntu.

---

### Post by Albert Clarke on 2009-10-11
There are two basic ways to share a Net connection. Way one is via a  		proxy server, way two is via Network Address Translation (NAT). Serious  		network-oriented operating systems like Linux can do bulletproof Internet  		sharing out of the box, but it's possible to get it happening on Windows  		as well, and you don't need to be a propellorhead to do it.

---

### Post by wootah on 2009-10-23
> **hejp said:**
> You can configure internet connection sharing with the** NetworkManager Applet** (which is installed by default with gnome at least), the nice **UI** makes it easy to configure.

Here's what to do:

Right click on it in the system tray.
Click 'Edit Connections...'
Select the connection you are sharing with.
Set 'Method' to 'Shared to other computers' which is under the 'IPv4 Settings'

[Here's an explanation with screenshots!]("http://hejp.freei.me/blog/how-to/simple-ics-internet-connection-sharing-on-ubuntu-with-screenshots/")

Pretty close, a few more things need to happen for an Xbox to connect through the computer. I wrote on your blog (?) the additional steps required.

Take a look everyone, it's a pretty decent walk through.

Oh, if you use this guide to allow another computer to connect through the bridge, it's basically the same setup. If it's for another Linux machine, don't forget to set the DNS to the gateway. This should apply to a Windows machine as well. These options can be set through network-manager (applet) or even in /etc/network/interfaces.

interfaces example:
```

#Using eth0 to connect to another eth0 that is bridged to wlan0 (set to share in network-manager (applet)
auto eth0
iface eth0 inet static
  address 192.168.1.10
  network 192.168.1.0
  gateway 192.168.1.1
  netmask 255.255.255.0
  dns-nameservers 192.168.1.1

```Don't forget that the gateway address of Machine two is the IP address of the connection interface of Machine one.

Good luck :D

---

### Post by october1917 on 2009-10-29
In my situation the problem can't be solved using the tutorial of the 1st post.

I have an Ubuntu machine with 2 ehternet cards.

It is connected to the switch using the eht0 and it HAS internet connection using STATIC IP from the central server of the University.

Then i plug the 2d ethernet card (eth1) to the switch and all the hosts are connected to the switch as well.

1) Is it necessary to use the 2d ethernet in order to share the connection or not? 

2) Is there something i have to change in the steps of the 1st post in order to finally achieve the connection sharing?

---

### Post by alexsand on 2009-12-30
These two links helped me to share internet connection between a karmic and an intrepid: [http://www.cyberciti.biz/faq/linux-share-internet-connection/](http://www.cyberciti.biz/faq/linux-share-internet-connection/) and [http://www.asim.pk/2009/01/22/ubuntu-setting-default-gateway-ip-etc/](http://www.asim.pk/2009/01/22/ubuntu-setting-default-gateway-ip-etc/). You might want to ping not a domain name but an IP address firstly, though.

---

### Post by jirayam on 2010-03-16
> **varunus said:**
> The Firestarter firewall can do all of this for you, by the way...

```
sudo apt-get install firestarter
```Its just a frontend to iptables.

In its preferences, set "internet connected device" to the internet, and "local network device" to the local device.  Then enable NAT and DHCP if you want...No matter what I set in the Firestarter preferences, it still keeps recognizing the Internet card as local and the local as Internet.

Whenever I activate the local connection, the machine will pick the local connection for Internet access. I have to turn the local off to get access.

---

### Post by AdrianNitescu on 2010-03-23
Hello there,

Behind eth0's ip I have routed a subnet. I use one of the ips on a winxp machine.
Some web pages don't work at all, some do, and I don't know why.
Can you please help?

Thanks

---

### Post by MS-Hater on 2010-03-28
OK, here's my network setup (or what I'm hoping to get it to be);

WAY the heck ancient computer connecting to sprint wireless boradband (using ubuntu 9.10 server with non-pae kernel) AND acting as a router for the network it shares the 'net connection TO;

Ubuntu 9.10 desktop and windows XP home clients (I plan on making it a Kubuntu box when windows bombs out once again), with a FreeNAS box running as a file server for both ICS clients (will set it up to do RSYNC of certain files I want updated across machines when I can UTFM).

My question is; can this be done as I'm envisioning it? If so, plz tell how. If not, plz tell why.

TIA.

---

### Post by MS-Hater on 2010-03-31
Nevermind. after a good bit of bashing, I found that I don't have the needed hardware for that setup.

---

### Post by metaltroubador on 2010-05-23
When I try the first step I get

ip: Unknown host
ifconfig: `--help' gives usage information

---

### Post by metaltroubador on 2010-05-23
Nevermind I figured out what I was doing wrong but when use apt-get for ipmasq it doesn't work says that the package has no installation file.

---

### Post by alejandroguille on 2010-11-02
see [http://www.excedesoft.com/blog/lang/esp/nat-con-ubuntu-nat-with-ubuntu-and-iptables/](http://www.excedesoft.com/blog/lang/esp/nat-con-ubuntu-nat-with-ubuntu-and-iptables/)

---

### Post by RajendraAlaria on 2010-12-13
switch on your wi-fi
left click on network icon
click on create new wireless connection
give a network name
choose wireless security: WEP 128-bit Passphrase
give any key
done.

now check this network in the computer to which u want to share.
and give the same key.

---

### Post by DeltaFee on 2011-03-17
I have tried this on my Ubuntu 10.10 sharing it with a windows 7 computer but it hasn't work. I not sure what to do.

---

