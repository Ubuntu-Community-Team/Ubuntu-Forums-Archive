---
title: "network does not work even after several trials"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by karaju on 2008-05-07
Hello,
I am relatively new to Ubuntu and recently upgraded to 8.04.  I have working internet connection in XP provided by a local isp.  I have been trying to configure the network ever since I first installed Ubuntu without success.  I followed the following posts:

1. Ubuntu Networking for Basic and Advanced Users -- Debian Admin.htm
2. cant connect through VT6102 ethernet card - Ubuntu Forums.htm
3. Can Ping & Lookup but no DNS in FireFox both - Ubuntu Forums.htm
4. How do I connect to Internet (Dumb newbie question) - Ubuntu Forums.htm
5. How To Disable ipv6 on Ubuntu 7_10 “Gutsy Gibbon”  Ubuntu Tutorials  Dapper - Feisty - Gutsy - Hardy.htm
6. Ubuntu Wired Networking Woes Read This Closely ~ Linux Fanatics.htm
7. Ubuntu question #16753 “internet connection”.htm

After following so many threads, it must have a become a big muddle in Ubuntu system files.  THE STRANGEST PART OF THE PROBLEM IS THAT PINGING IS SUCCESSFUL WITH 10.10.45.1 AND 10.10.45.116 (addresses provided by isp).  BUT I AM UNABLE TO ACCESS ANY OTHER ADDRESS.

The following is the out put for lspci and ifconfig:



raju@raju-desktop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:14:85:93:0b:24  

          inet addr:10.10.45.116  Bcast:10.10.45.255  Mask:255.255.255.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:125 errors:0 dropped:0 overruns:0 frame:0

          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0

          collisions:2 txqueuelen:1000 

          RX bytes:24497 (23.9 KB)  TX bytes:6957 (6.7 KB)

          Interrupt:16 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:166 errors:0 dropped:0 overruns:0 frame:0

          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:12224 (11.9 KB)  TX bytes:12224 (11.9 KB)



raju@raju-desktop:~$ lspci

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge

00:09.0 Multimedia audio controller: Yamaha Corporation YMF-724 (rev 05)

00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

raju@raju-desktop:~$ 



Will somebody help me resolve my problem?  I am really frustrated and will reinstall Ubuntu if necessary.

Thanks.

---

### Post by mapes12 on 2008-05-07
Given that you have tried so many solutions it might be a good idea to do a fresh install of ubuntu to see if that clears the problem.

How are you connecting to your isp? Dial up or broadband? If broadband are you connecinting through a wired router or wireless? Or USB modem?

Your IP address is class A which seems strange. Most routers default to class C private addresses which start 192.168.x.x

Does you NIC respond to ping 127.0.0.1?

---

### Post by MaindotC on 2008-05-07
The 10.x.x.x addresses are non-routable and I'm assuming he's connected to an access point (I can't ping either of those addresses and there is no nslookup for them).  It doesn't seem to be a connectivity issue between your NIC and the access point, so it seems like you have an address or naming issue with your access point (commonly referred to as a home router).  Please give us a physical description of your network layout especially the points mapes12 just asked.

---

### Post by karaju on 2008-05-07
Hello,
Thanks for the quick replies.  

Yes the ping to 127.0.01 is good.  My connection is local cable network connected directly to mother board ethernet card VT6102 RHINE II.  I know nothing about addresses and their meaning and so can not give you any info on them.

Any help would be highly appreciated.  Thanks.

---

### Post by MaindotC on 2008-05-07
Pinging the loopback address won't really help him :(  Karaju - are you connected to an access point?

---

### Post by mapes12 on 2008-05-07
You mention you have a working XP connection to the internet. To help me out please could you post the response you get from a command line in XP to: ipconfig

I know its windoze but I understand some of these responses a little better.

---

### Post by karaju on 2008-05-07
Thanks once again for quick replies.
To Mr. Stralan's question: I do not know what is access point.  I get my connection through a cable run by isp.  I have to access my account by typing my user name and password after typing the address: [http://10.10.45.1:800](http://10.10.45.1:800) in the address bar.  Once the authentication is over, I can browse in IE or any other browser.  
To Mr. Mapes12's question: I tried to run ipconfig in command prompt, but unfortunately, a dos window opens for few millionths of a second and closes abruptly.
Now for the next step if any please.  Thanks.

---

### Post by MaindotC on 2008-05-07
Sorry - what he meant was open the DOS prompt (the black window) then type:

```

ipconfig /all

```

and post the output.

---

### Post by lazyart on 2008-05-07
Turn the modem off, count to 10, then turn it back on.  Count to 10 again, then try in linux what you do in xp to connect.

---

### Post by karaju on 2008-05-07
This is the output fo ipconfig /all:

Windows IP configuration

Host Name..................................: Karaju
Primary DNS suffix.........................:
Node Type..................................: Unknown
IP Routing Enabled.........................: No
WINS Proxy Enabled.........................: No

Ethernet Adapter Local Area Connection

Connection-specific DNS Suffix.............: 
Description................................: VIA compatible fast ethernet adapter.

Physical address...........................: 00-14-85-93-0B-24
DHCP enabled...............................: No
IP address.................................: 10.10.45.116
Subnet mask................................: 255.255.255.0
Default Gateway............................: 10.10.45.1
DNS servers................................: 10.10.45.1

Now to the next step please.  Thanks

---

### Post by hyper_ch on 2008-05-07
post the output of:
```

cat /etc/network/interfaces

```

```

cat /etc/hosts

```

```

cat /etc/resolv.conf

```

```

iwconfig

```

```

ifconfig

```

---

### Post by MaindotC on 2008-05-07
> **karaju said:**
> Thanks once again for quick replies.
To Mr. Stralan's question: I do not know what is access point.  I get my connection through a cable run by isp.  I have to access my account by typing my user name and password after typing the address: [http://10.10.45.1:800](http://10.10.45.1:800) in the address bar.  Once the authentication is over, I can browse in IE or any other browser.  


Does the cable from your computer plug into the cable modem or does it plug into a little box with about 4 ports on them?

---

### Post by mapes12 on 2008-05-07
At the DOS prompt: ping 10.10.45.1 and post the output.

Do you know your ISP's IP address?

What model router are you connected to?

Are there any hubs or switches between your machine and router?

Are you attached to a corporate LAN or a home based configuration?

Anything to do with the physical set up will help.

---

### Post by MaindotC on 2008-05-07
ISP's don't really have an address...more like a host of addresses...

---

### Post by mapes12 on 2008-05-07
Yeh, 10.10.45.1 is a private address with switch :800 indicating some kind of port within the router. So I think [http://10.10.45.1:800](http://10.10.45.1:800) is a router authentication which then allows access through the things gateway to the net.

---

### Post by karaju on 2008-05-07
I thank you all for trying to help me.
To Mr. hyper_ch:  this is the out put:

raju@raju-desktop:~$ cat /etc/network/interfaces

auto lo

iface lo inet loopback



# The primary network interface

auto eth0

iface eth0 inet static

	address 10.10.45.116

	gateway 10.10.45.1

	netmask 255.255.255.0

	network 10.10.45.0

	broadcast 10.10.45.255

raju@raju-desktop:~$ cat /etc/hosts

127.0.0.1	localhost

127.0.1.1	raju-desktop



# The following lines are desirable for IPv6 capable hosts

::1     ip6-localhost ip6-loopback

fe00::0 ip6-localnet

ff00::0 ip6-mcastprefix

ff02::1 ip6-allnodes

ff02::2 ip6-allrouters

ff02::3 ip6-allhosts

raju@raju-desktop:~$ cat /etc/resolv.conf

cat: /etc/resolv.conf: No such file or directory

raju@raju-desktop:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



raju@raju-desktop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:14:85:93:0b:24  

          inet addr:10.10.45.116  Bcast:10.10.45.255  Mask:255.255.255.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:5 errors:0 dropped:0 overruns:0 frame:0

          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:498 (498.0 B)  TX bytes:2839 (2.7 KB)

          Interrupt:18 Base address:0xe000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:66 errors:0 dropped:0 overruns:0 frame:0

          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:4204 (4.1 KB)  TX bytes:4204 (4.1 KB)



raju@raju-desktop:~$ 


To Mr. Stralan:  The cable from comes into the house and is connected to a little box with ports in them which isp guy calls it as HUB.  One wire goes out of this box to ethernet card in Mother Board.

To Mr. Mapes12: 1) ping 10.10.45.1 yielded the following:

Pinging 10.10.45.1 with 32 bytes of data:

Reply from 10.10.45.1: bytes=32 time<1ms TTL=64
Reply from 10.10.45.1: bytes=32 time<1ms TTL=64
Reply from 10.10.45.1: bytes=32 time<1ms TTL=64
Reply from 10.10.45.1: bytes=32 time<1ms TTL=64

Ping statistics for 10.10.45.1:
     Packets: sent = 4, Recieved = 4, Lost = 0 (0% lost)
Approximate round trip times in milli-seconds:
     Minimum= 0ms, Maximum= 0ms,  Average= 0ms 

2) There is HUB at CPU.
3) ISP is a corporate entity here in India.

Thanks once again for trying to help to you all.

---

### Post by hyper_ch on 2008-05-07
(1) put outupt code and stuff into [noparse]```

```[/noparse] tags

(2) > **karaju said:**
> cat: /etc/resolv.conf: No such file or directory
That is not good....

(a) run ```
sudo nano /etc/resolv.conf
```
(b) put that into the file:
```
nameserver 10.10.45.1
```
(c) save it
(d) restart the network:
```
sudo /etc/init.d/networking restart
```

---

### Post by karaju on 2008-05-07
Thank you Mr.hyper_ch.
I am an ordinary computer user enamoured by Ubuntu.  I do know only basic things in Ubuntu.  Your point by point directions are welcome but I could not follow them.  Point (1) put outupt code and stuff into ```

``` tags: I am not sure how to do it.  (2) a, b, c and d also needs a bit elucidation for me.  Please consider me a novice and elucidate please.
Thanks

---

### Post by MaindotC on 2008-05-07
> To Mr. Stralan:  The cable from comes into the house and is connected to a little box with ports in them which isp guy calls it as HUB.  One wire goes out of this box to ethernet card in Mother Board.

I knew it!  This is an issue on the router/hub (it can't be a hub if it is assigning him an address), not his Ubuntu configuration.  He should have DHCP on the "HUB" which should send him all the information necessary to connect to the internet.  However, when he posted the ouptut of ipconfig from his windows box it concerned me that it said DHCP was not enabled.

Karaju - what is the name of the "HUB" you have?  Please tell me the brand and any numbers associated with it.  I'm am curious to learn about this authentication you described.

---

### Post by mapes12 on 2008-05-07
So how come his XP OS can access the internet??

I agree about there being no DHCP service but it may be a static DNS address assigned to the router. As you say it can't be a hub or a switch as my understanding is that they do not have IP addresses assigned. But why on earth not use a normal router with DHCP services. Beats me:confused:

---

### Post by MaindotC on 2008-05-07
Well it's difficult to verify until he gives us a more descriptive detail of his PHYSICAL layout, but my understanding is he has XP on a separate box.  If that's the case, his router (I believe it's a home router which is actually a layer 3 switch) may not be employing the proper address scheme for any number of reasons.  What I want to do is find out what kind of router he has so I can learn about this authentication process.

You're correct about it not being a switch or a hub because they do not deal with IP addresses and it seems he's being assigned an internal, non-routable address of 10.x.x.x which you correctly stated is a class A address which means he must be connecting to a home router.

Regarding DNS, typically under DHCP the router will say "use me as a place to send your DNS requests" and then the router handles those requests and sends them onto the ISP's DNS server and it comes back and you know how that works.  

However, I'm wondering if for some reason his router does not have DHCP enabled and the XP box is using an address previously assigned.  He mentioned something about a technician coming to his home, so I wonder if the guy not only set up the IP addresses but provided the home router and disabled DHCP.  He said he received the 10.x.x.x addresses from the ISP - I'm wondering if that means he called them and they told him that over the phone (which would be even more reason to suspect that DHCP is not enabled).

So hopefully he can disect some of our questions and reply with some answers.  Sure is taking him a long time, though.

---

### Post by hyper_ch on 2008-05-07
there is no nameserver in the resolv.conf so when querying for a domain ubuntu does not know where to query to and hence it will not work. That's why I said to edit (and also create) the /etc/resolv.conf) and enter the ip address of the router as nameserver.

> **karaju said:**
> Thank you Mr.hyper_ch.
I am an ordinary computer user enamoured by Ubuntu.  I do know only basic things in Ubuntu.  Your point by point directions are welcome but I could not follow them.  Point (1) put outupt code and stuff into ```

``` tags: I am not sure how to do it.  (2) a, b, c and d also needs a bit elucidation for me.  Please consider me a novice and elucidate please.
Thanks

Well, when you are asked to post some output from the terminal or something (e.g. "df -l") then do write it in the forums like this:
[noparse]```
df -l
```[/noparse]
and it will appear as this: ```
df -l
```
That makes the output easier to read ;)

and with regard to (2): Where do you need help there? Saving and exiting nano can be done with "ctrl-x". You will then be asked if you want to save and where yuo want to save it to... just read at the bottom of nano, there it will say so. Otherwies you have to be more specific about your problems.

---

### Post by mapes12 on 2008-05-07
As I mentioned in one of my previous posts because so many fixes have been tried something has become corrupted and as hyper_ch says the etc/resolv.conf file is missing. 

hyper-ch provided good instructions on how to create this with the correct nameserver IP. But if that's too difficult I'm wondering if a complete reinstallation would be too much trouble?? Somewhat crude I know but would be a lot quicker than keeping this thread going forever. ](*,)

---

### Post by mlentink on 2008-05-07
Might I ask karaju one question?

In XP, do you use webmail or do you use a separate e-mail program like Outlook or Thunderbird?



Edit: I see Karaju is off-line, so this may have to wait. But after Hyperswiss's q&a I'm beginning to suspect that the 'HUB' is actually precisely that, and not a router at all.

---

### Post by MaindotC on 2008-05-07
Can you just type:

```

sudo dhclient

```

and see if you get an IP address and try connecting?

---

### Post by mlentink on 2008-05-07
> **strAlan said:**
> Can you just type:

```

sudo dhclient

```

and see if you get an IP address and try connecting?

In view of what he posted as outcome of his windows ipconfig /all, I'd be amazed if we got anything out of this. He doesn't have dhcp...

---

### Post by karaju on 2008-05-08
HELLO,
SUCCESS AT LAST!!!!
NETWORK IS IN FULL FORCE IN UBUNTU 8.04..........
Thank you all for your kind help.  I followed the instructions on page of this post by hyper_ch and bingo!!!  
Sorry for delay in replying because I have re-installed the 8.04 afresh and followed those instructions.  One thing I would like to say is I do not know that ctrl x saves files.  These tips in detail will certainly help lay people like me.  Therefore, I request hyper_ch to consider all help requests as requests from absolute novices like me, and give detailed instructions in future.  
Thanks to You All.

---

### Post by karaju on 2008-05-13
Thanks

---

### Post by hyper_ch on 2008-05-13
> **karaju said:**
> One thing I would like to say is I do not know that ctrl x saves files.  These tips in detail will certainly help lay people like me.  Therefore, I request hyper_ch to consider all help requests as requests from absolute novices like me, and give detailed instructions in future.

I disagree

(1) If you have a look at nano, you will see the most often used command displayed at the bottom.

(2) If you can't your way around, use google

(3) If google can't help, ask here in the forums

It is not too much asked if I demand a bit of brain usage on your part instead of spoon-feeding you. You don't need solutions you need ways to help yourself. If you know how you can help yourself you can solve most problems/issues arising.
Just giving you straight the solution that has been published on the net many thousand times won't do any good.

Yes, you are a novice and there is some learning curve... but you only learn and progress if you put some effort into it yourself. Of course I understand that it's much more confortable to be presented by a solution itself than pointed to way where to find one... but in the end, what helps you more?

---

