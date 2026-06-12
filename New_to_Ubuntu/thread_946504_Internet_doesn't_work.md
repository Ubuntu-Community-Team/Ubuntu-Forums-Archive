---
title: "Internet doesn't work"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Crayboff on 2008-10-13
I recently installed Firestarter thinking it'd be a decent firewall, but it sort of messed things up so I uninstalled it completely and deleted it from Session. However, now I cannot get onto the internet anymore via Hardy Heron. I have FIOS for internet and it was working fine before, it is temperamental on my Vista but works fine after some bashing it into the table a few times.

---

### Post by OldGrey on 2008-10-13
Firestarter isn't a firewall as such it is a front end GUI for IPtables which is the firewall that comes preinstalled with Ubuntu. It could be that you have done something to the settings using Firestarter, which would remain even when you have uninstalled it.

---

### Post by SteveNorman on 2008-10-13
whats the output of```
$ifconfig
```?

---

### Post by iponeverything on 2008-10-13
Fix up your rules and purge firestarter..

sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT

sudo apt-get purge firestarter

---

### Post by Crayboff on 2008-10-13
*I'm sorry I just realized that I accidentally posted this thread twice so I will post the solution in both. Vista was spazzing when I posted it.*

Anyway, thanks for the people who helped me. Here is what I did:


```
sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -X

sudo apt-get purge firestarter
```

also here are what I have for the $ifconfig:
**Before sudo iptables:**
```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:a4:76:9d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7000 (6.8 KB)  TX bytes:7000 (6.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:8c:31:74:6e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1535 (1.4 KB)  TX bytes:5405 (5.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-8C-31-74-6E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
[B]
After sudo iptables:[/B]
```

eth0      Link encap:Ethernet  HWaddr 00:1d:09:a4:76:9d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7000 (6.8 KB)  TX bytes:7000 (6.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:8c:31:74:6e  
          inet6 addr: fe80::21e:8cff:fe31:746e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1847 (1.8 KB)  TX bytes:6717 (6.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-8C-31-74-6E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by Crayboff on 2008-10-13
Crap, now it isn't working anymore. All i did was install Foxmarks add on to Firefox and shut down the computer then later I turned it back on and the internet doesn't want to work again :(

---

### Post by iponeverything on 2008-10-13
Something is restoring the the iptables rules..

sudo apt-get remove --purge firestarter

reset your rules again then try a:

iptables-save

---

### Post by Crayboff on 2008-10-14
unfourtanatly reseting my rules again by doing the code in posts above, didn't work.

---

### Post by Crayboff on 2008-10-15
Also, I have partitioned my harddrive using Wubi. Internet works fine in Vista

---

### Post by Crayboff on 2008-10-15
I ran the code that PMT gave me and I post exactly the output it gave me:

```
boff@boff-laptop:~$ grep -i iptables /etc/init.d/* /etc/rc.local 
/etc/init.d/ufw:    if iptables -L ufw-user-input -n >/dev/null 2>&1 ; then 
/etc/init.d/ufw:        execs="iptables" 
/etc/init.d/ufw:    execs="iptables" 

boff@boff-laptop:~$ grep -i iptables /etc/init.d/* 
/etc/init.d/ufw:    if iptables -L ufw-user-input -n >/dev/null 2>&1 ; then 
/etc/init.d/ufw:        execs="iptables" 
/etc/init.d/ufw:    execs="iptables" 

boff@boff-laptop:~$ grep -i iptables /etc/rc.local 

boff@boff-laptop:~$ 
``` Note that I know the last two inputs were unnecessary, but I did it anyway, to show what I got.



Also i ran ifconfig again, incase anything changed since last time it was working. Keep in mind that I saved the resetted iptables:

```
boff@boff-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1d:09:a4:76:9d   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:22  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:8800 (8.5 KB)  TX bytes:8800 (8.5 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:1e:8c:31:74:6e   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:1483 (1.4 KB)  TX bytes:5242 (5.1 KB) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-1E-8C-31-74-6E-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by Stebalien on 2008-10-15
Please post the output of ```
sudo iptables --list
```

---

### Post by Crayboff on 2008-10-16
here is the output of $sudo iptables --list

```
boff@boff-laptop:~$ sudo iptables --list
[sudo] password for boff: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

```




UPDATE: I brought my computer to my school and the internet is working properly. I assume that this and the fact vista works with the wireless network at home mean that it is the settings between my computer and my home router are messed up. I'm looking at the wireless Networks preference thing in Network Manager and do not see how I could have screwed anything up. The only thing that I'm not sure  what it means is the "bssids: 00:18:01:EB:73:CE"

---

### Post by Crayboff on 2008-10-16
Strike the update I put in the last comment. It stopped working again :( I restarted my computer to test if it would stay and Network Manager said it got signal, but I tried accessing a website, and it wouldn't connect to the internet. Then I tried reconnecting to the network and it failed. augh!

---

### Post by Stebalien on 2008-10-16
Is your networks DHCP turned on.  Your ifconfig output showed neither a wireless nor a wired IP address.
Edit: Your Second ifconfig output (your first had an IP address).

---

### Post by Crayboff on 2008-10-17
It is not on, I have Roaming mode enabled. Should I enable And for some reason, I can access the internet at my school. even after restarting the computer. I have no clue what this means. but I will test the internet connection at home later tonight when I get home. Here is my current ifconfig output incase anything changed from previous times:


```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:a4:76:9d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10870 (10.6 KB)  TX bytes:10870 (10.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:8c:31:74:6e  
          inet addr:10.1.21.78  Bcast:10.1.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21e:8cff:fe31:746e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3978944 (3.7 MB)  TX bytes:137727 (134.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-8C-31-74-6E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by Stebalien on 2008-10-17
Was this last output from school or home?  Was your Internet connection working when you got this output?  If so it would appear that your home network is not assigning you an IP address.  You may be able to correct this by turning your home network's DHCP on.  If your home network's DHCP is already on, check to see if your DHCP client is running by running ```
ps -e |grep -i dh
``` (the output should contain something like dhcdbd or dhclient).  Good luck.

---

### Post by Stebalien on 2008-10-17
If all else fails you could try using [wicd]("http://wicd.net").

---

### Post by Crayboff on 2008-10-17
Yes, the last output was from school, with the internet working.

I'm wondering with this DHCP thing, am I supposed to be turning it on from the Manual Configuration option when you click on the Network Manager applet? If so, then the DHCP thing doesn't work.

I copy and pasted the code and this is what it gave me:

```
boff@boff-laptop:~$ ps -e |grep -i dh 
 5573 ?        00:00:00 dhcdbd 
 7139 ?        00:00:00 dhclient3 
 7493 ?        00:00:00 dhclient-script 
```

Tomorrow I'm going to be going back to school and if I remember my computer I will download the wicd, hopefully that would work better than network manager.

EDIT: I tried accessing the internet here at home by using an ethernet cable and attaching it to the modem. This worked for one page load, then stopped working. weird.

---

### Post by Stebalien on 2008-10-18
> **Crayboff said:**
> Yes, the last output was from school, with the internet working.

I'm wondering with this DHCP thing, am I supposed to be turning it on from the Manual Configuration option when you click on the Network Manager applet? If so, then the DHCP thing doesn't work.

I copy and pasted the code and this is what it gave me:

```
boff@boff-laptop:~$ ps -e |grep -i dh 
 5573 ?        00:00:00 dhcdbd 
 7139 ?        00:00:00 dhclient3 
 7493 ?        00:00:00 dhclient-script 
```

Tomorrow I'm going to be going back to school and if I remember my computer I will download the wicd, hopefully that would work better than network manager.

EDIT: I tried accessing the internet here at home by using an ethernet cable and attaching it to the modem. This worked for one page load, then stopped working. weird.
This means that your DHCP client is running.  Try accessing your router/modems configuration page (are you using one?).  To get there, run ```
route
``` and find the line that starts with "default".  Go to the non-zero IP address listed on this line (i.e. the IP address that is not 0.0.0.0).  If the page will not load or route does not give a line with "default", try wicd.

---

### Post by Crayboff on 2008-10-18
I do not know if I am using a router/modems configuration page. What I do use is the network manager “Manual configuration...” option when you left click the icon. Then I unlock it and select “Wireless Connection” and click “Properties”. 

```
boff@boff-laptop:~$ route 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
```

Because there is no default line, I'll download wicd later, unless you should tell me otherwise. Otherwise I shall try wicd and hope for the best. Is there anything about wicd that I should be aware of? I assume it will be pretty straight forward.

---

### Post by Crayboff on 2008-10-18
crap I'm trying to download wicd, but the repository isn't working. synaptic is giving me this error message when I try to download the repository:

```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


Failed to fetch http://apt.wicd.net/dists/hardy/extras/binary-i386/Packages.gz  403 Forbidden
Some index files failed to download, they have been ignored, or old ones used instead.


```

I can't download wicd because it can't get that package.

---

### Post by Crayboff on 2008-10-18
Ok, for some reason my internet at home is working, so I'm going to try and download wicd here before the internet spazzes again. right now it is not giving me a problem when I reload the repositories in synaptic, so wish me luck.

---

### Post by Crayboff on 2008-10-18
Ok, I installed wicd at home. Then when I tried to access the internet, it wouldn't obtain the IP address. After it attempting for like a minute or so, wicd gave up and stopped trying. Then I went back to school and now it works here. wtf is up with that?

Unfourtanatly, I believe it means it is not a problem with Network Manager, but with the connection between my FIOS modem and ubuntu. it also doesn't work if my computer is connected w/ an ethernet cable. Also the vista on my computer works, the xp comps in my house have working internet (one is a wired pc the other a laptop) even my brother's iPod touch is working. :(

---

### Post by Crayboff on 2008-10-20
hmph, now wicd doesn't seem to always want to work at school either. Will upgrading to Ubuntu 8.10 solve all of my problems? Also, I installed Ubuntu 8.04 with Wubi, how do I upgrade to Ubuntu 8.10? Do I have to uninstall hardy completely. I could probably spend the time to reinstall all of the programs I've been using, and I do not have any vital documents on my computer. But perhaps I digress from the thread. please still try to find solutions to my problems on this thread, as it has not been fixed yet.

Also, thanks soo much for helping me so far.

---

### Post by Stebalien on 2008-10-20
I doubt that Intrepid will work any better but you could try (of course a full reinstall would be more likely to fix your problem).  I still think that you have a DHCP problem (you are not getting an IP address.  In wicd, click advanced settings under your network name and setup a static IP and static DNS.  Use opendns (208.67.222.222) as your DNS (to guarantee that it is correct).

---

### Post by Crayboff on 2008-10-20
Umm, this is a little embarrassing :oops:, but, umm how do I find out all of the values for the static IP address stuff? I'm a windows convertee who never had to mess with that stuff. 

Tell me if I got this right ([http://corz.org/comms/hardware/router/static.ip.address.php):](http://corz.org/comms/hardware/router/static.ip.address.php):) I choose a number somewhere between 192.168.1.3 and 192.168.1.255 for the IP and I use the 208.67.222.222 for DNS (do I check the Global DNS servers or the Static DNS checkbox? and what do I put in the other two DNS boxes?). I guess that 255.255.255.0 can be used for the netmask. That leaves the gateway, which I assume is 192.168.1.1.

oh btw, Stebalien, I like your site, I'll get the RSS feed once I get this internet more reliable.

---

### Post by Stebalien on 2008-10-20
> **Crayboff said:**
> Umm, this is a little embarrassing :oops:, but, umm how do I find out all of the values for the static IP address stuff? I'm a windows convertee who never had to mess with that stuff. 

Tell me if I got this right ([http://corz.org/comms/hardware/router/static.ip.address.php):](http://corz.org/comms/hardware/router/static.ip.address.php):) I choose a number somewhere between 192.168.1.3 and 192.168.1.255 for the IP and I use the 208.67.222.222 for DNS (do I check the Global DNS servers or the Static DNS checkbox? and what do I put in the other two DNS boxes?). I guess that 255.255.255.0 can be used for the netmask. That leaves the gateway, which I assume is 192.168.1.1.

oh btw, Stebalien, I like your site, I'll get the RSS feed once I get this internet more reliable.

Every thing you wrote is correct (but I wouldn't use 192.168.1.255 for your IP address; choose a lower one).

Set these two IP addresses as your DNS addresses (and leave the third blank):
208.67.222.222
208.67.220.220

Check the checkbox that says static DNS.

This is the most common configuration but is not guaranteed to work.  On my network, my IP address is in the 172.16.1.1-255 range with a netmask of 255.255.0.0 and a gateway address of 172.16.0.1.  My configuration is less common but, if 192.168.1.[whatever] fails, try my setup.

---

### Post by Crayboff on 2008-10-20
Holey Moley, Batman! I think it worked. I sure hope this time it works forever. You are truely a genius, Stebalien. Thank you for all of your help. But please stay subscribed to this thread, just in case :) I restarted my computer and it is working fine, so I'll hope it stays this way. I wonder what happened to my internet in the first place  though...

---

### Post by Stebalien on 2008-10-20
Check your router configuration page ([http://192.168.1.1/](http://192.168.1.1/)) to see if [DHCP]("http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol") is on.  If it is not, turn it on.  Your router was failing to give you an IP address and turning DHCP on should fix your problem permanently.

---

### Post by Crayboff on 2008-10-20
unfourtanatly my parents are the only ones who know the password for that (that's what I get for letting the verizon guy explain it to my mom while I was at school) and therefore, I can't access the site. Also, my mom forgets what the info is, so umm ya. I'm sort of stuck on that front until I find the little piece of paper with the info on it :(

---

### Post by Stebalien on 2008-10-20
Unless you changed the password from the original, try the passwords listed on [this]("http://routerpasswords.com/") site.  Good luck.

Edit: If your parents did change the password, try their email passwords.

---

### Post by Crayboff on 2008-10-20
unfourtanatly the verizon guy changed the passwords. I found a site to reset the router (Actiontec MI424WR Router) and the usrname and pssword with it. i might try it soon, assuming you don't tell me it'd screw up my internet access... again.

---

### Post by Stebalien on 2008-10-20
I doubt that such a site would work.  If it does, your router must be very insecure.  There is most likely a reset button on your router but you would have to setup your router after reseting it (and you would have to know your DSL/FIOS login password).  What does this site claim to do? What is the URL?

---

### Post by Crayboff on 2008-10-20
my bad, I guess I didn't explain it well enough. It is an instruction manual (onlinehelp.verizon.net/consumer/bin/pdf/NetworkSteps/ConfiguringActiontecM1424WRSecurity2.pdf) and yes, it talks about the reset button.

The only usernames and passwords I know are the ones to log onto the wireless network

---

### Post by Stebalien on 2008-10-20
If you call your ISP they should be able to tell you your username and password.

---

### Post by Crayboff on 2008-10-20
Ya, I'll do that when I get the chance. I'll keep you posted. :D

---

### Post by Crayboff on 2008-10-20
figured it out. turns out the tech changed the password to something else real easy a *duh* moment. I changed it to something more suiting and now what do you want me to do?


Oh it says this
```
	Coax Status:	Connected
 	Connection Type:	DHCP
 	IP Address:	71.246.23.49
```

so i assume that this means that it is DHCP connection.

---

### Post by Stebalien on 2008-10-20
That is refering to the routers external connection (71.246.23.49 is an external IP).  There should be some advanced network settings page where you can turn DHCP on.  I do not have your router so I therefore cannot walk you through its setup.
BTW: The first draft of your post is always sent to subscribers.

---

### Post by Crayboff on 2008-10-21
what I don't understand is why it is only my ubuntu that isn't working if it the DHCP I need to turn on in the router itself. Is there something with linux requiring that you use DHCP or else it'll turn the internet off on you randomly? I'd assume I would be having a similar problem on my Vista or my parent's XP or even my brother's ipod touch. right?

also, would this mess up the static ip settings?

---

### Post by Crayboff on 2008-10-21
This look like the right thing? (Boff is the name of my laptop)

Boff:
Connection Type:	Wireless
IP Address:	192.168.1.3
IP Address Allocation:	DHCP
MAC Address:	00:1e:8c:31:74:6e

---

### Post by Stebalien on 2008-10-21
You are right about it probably having nothing to do with the router but I still think that you are having a DHCP problem.  Firestarter may have changed a setting in a program other than iptables that subsequently blocked your DHCP client.  The best way to tell for sure is to listen to the packets on your network as you connect to the internet (after reenabling DHCP in wicd).  Do you know how to do this?
> This look like the right thing?
yes.

---

### Post by Crayboff on 2008-10-21
> **Stebalien said:**
> You are right about it probably having nothing to do with the router but I still think that you are having a DHCP problem.  Firestarter may have changed a setting in a program other than iptables that subsequently blocked your DHCP client.  The best way to tell for sure is to listen to the packets on your network as you connect to the internet (after reenabling DHCP in wicd).  Do you know how to do this?

yes.
not in the slightest

---

### Post by sazan on 2008-10-21
> **Crayboff said:**
> not in the slightest

for enabling DHCP...

Systems->Administration->Network

select eth0 and from the drop down select DHCP.......this will enable ur DHCP.. 

then u can go to 'network tools'(in Adminstration) to ping to see if it is working...

---

### Post by Crayboff on 2008-10-21
> **sazan said:**
> for enabling DHCP...

Systems->Administration->Network

select eth0 and from the drop down select DHCP.......this will enable ur DHCP.. 

then u can go to 'network tools'(in Adminstration) to ping to see if it is working...
oh no, i know how to switch on DHCP, but what I don't know is how to "listen to packets"

---

