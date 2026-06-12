---
title: "ubuntu cannot detect router"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by coolnik6 on 2008-06-05
hi im trying very hard to connect internet on ubuntu
but ubuntu is unable to detect my adsl router
but the router is working fine on xp but not on ubuntu
typing  192.168.1.1 in address bar  is not able to show the router's page in ubuntu
where is the problem 
although router clearly shows that it is connected to ethernet card
it blinks 
my ubuntu is 8.04 lts  dual boot with xp
my router is configures in pppoe mode
adsl router is starcom ut300r2u

---

### Post by shifty_powers on 2008-06-05
is it usb or ethernet?

---

### Post by stchman on 2008-06-05
> **coolnik6 said:**
> hi im trying very hard to connect internet on ubuntu
but ubuntu is unable to detect my adsl router
but the router is working fine on xp but not on ubuntu
typing  192.168.1.1 in address bar  is not able to show the router's page in ubuntu
where is the problem 
although router clearly shows that it is connected to ethernet card
it blinks 
my ubuntu is 8.04 lts  dual boot with xp
my router is configures in pppoe mode
adsl router is starcom ut300r2u

Sounds like you have the router hooked up to your ethernet card using RJ-45.  If the router stores the username and password all should work.

---

### Post by geezerone on 2008-06-05
Hi

Open a terminal window (Applications > Accessories > Terminal). Then type **ifconfig** and output the results here.

Also, type **ping 192.168.1.1  **(IP address of router) and post also what this shows.

Is your router like [this]("http://66.102.9.104/search?q=cache:MRa1lYzDSTAJ:www.utstar.com/Document_Library/0046.pdf+ut300r2u&hl=en&ct=clnk&cd=2&gl=uk&lr=lang_en")

---

### Post by shriramiyengar on 2008-06-05
hi
i had also the same problem i tried ppppoeconf it give me error cannot find acess connector if you got the same problem please reply

---

### Post by geezerone on 2008-06-05
Carry out my instructions above and post here.

---

### Post by coolnik6 on 2008-06-06
out of 48 post 42 times i have posted this output but nobody is able to figure out wats the problem
n my adsl router is configured in pppoe mode now that means that i don't need to dial a connection u see everything is already feeded in the router my isp id n password n router connects me to internet every time i start windows  but not in ubuntu infact ubuntu can't even find my rouer forget the configuration
n somebody here replied that problem is with RJ-45 cable i mean when the router is working soo well with xp how come thatthat its not with ubuntu
the point here is there is no issues with hardwaare as far as Ethernet card n adsl router is concern but it can be that ubuntu is not compatible with my router ie starcom ut300r2u
man its been 6 months now n no solution pllz ubuntu enginers give me a solution 
niket@niket-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:44:65:0b:95  
          inet6 addr: fe80::202:44ff:fe65:b95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:14673 (14.3 KB)
          Interrupt:16 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:02:44:65:0b:95  
          inet addr:169.254.4.207  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58284 (56.9 KB)  TX bytes:58284 (56.9 KB)

---

### Post by stchman on 2008-06-06
> **coolnik6 said:**
> out of 48 post 42 times i have posted this output but nobody is able to figure out wats the problem
n my adsl router is configured in pppoe mode now that means that i don't need to dial a connection u see everything is already feeded in the router my isp id n password n router connects me to internet every time i start windows  but not in ubuntu infact ubuntu can't even find my rouer forget the configuration
n somebody here replied that problem is with RJ-45 cable i mean when the router is working soo well with xp how come thatthat its not with ubuntu
the point here is there is no issues with hardwaare as far as Ethernet card n adsl router is concern but it can be that ubuntu is not compatible with my router ie starcom ut300r2u
man its been 6 months now n no solution pllz ubuntu enginers give me a solution 
niket@niket-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:44:65:0b:95  
          inet6 addr: fe80::202:44ff:fe65:b95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:14673 (14.3 KB)
          Interrupt:16 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:02:44:65:0b:95  
          inet addr:169.254.4.207  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58284 (56.9 KB)  TX bytes:58284 (56.9 KB)

That output from what I see means the router is not assigning you an IP address.  The 169.245.xxx.xxx are not valid IP addresses.

Is the router setup for DHCP?  Is the router setup for PPoE?  Does it store you username and password?

If the answer is not yes to all three then make it yes for all of them.  Once that is done your router will login to your ISP and the ISP will issue you an IP.  The router will then create IPs for all the PCs behind it's firewall.

---

### Post by geezerone on 2008-06-06
> **coolnik6 said:**
> out of 48 post 42 times i have posted this output but nobody is able to figure out wats the problem
n my adsl router is configured in pppoe mode now that means that i don't need to dial a connection u see everything is already feeded in the router my isp id n password n router connects me to internet every time i start windows  but not in ubuntu infact ubuntu can't even find my rouer forget the configuration
n somebody here replied that problem is with RJ-45 cable i mean when the router is working soo well with xp how come thatthat its not with ubuntu
the point here is there is no issues with hardwaare as far as Ethernet card n adsl router is concern but it can be that ubuntu is not compatible with my router ie starcom ut300r2u
man its been 6 months now n no solution pllz ubuntu enginers give me a solution 
...

OK, well we understand how frustrating this must be but bare with and help us help you. 

Regarding the IP address 169.254.x.x is a failure to connect to the dhcp server (see [THIS]("http://homepage.ntlworld.com/robin.d.h.walker/cmtips/badip.html") link for more info). 
Configure a static IP address as follows:

Go to *System* > *Administration* > *Network* and click this. Then highlight '*wired*' connection and click '*properties*' to the rhs. This will open a window with tabs at the top. I presume you have DHCP (roaming) configured so create a static entry on the '*connections*' tab, untick '*roaming mode*' box. Choose '*static IP address*' under configuration, and type in an IP address for your PC (e.g. 192.168.1.50, mask 255.255.255.0 and gateway of 192.168.1.1). This will by-pass DHCP from your router. You may also wish to add DNS server addresses here (prob the 192.168.1.1 address but can add your ISP ones too).

Let us know how this goes and if not well also post the  */etc/network/interfaces* config please. Also, try pinging 127.0.0.1 and show what you get also.

---

### Post by coolnik6 on 2008-06-07
to stchman 
it seems u r not reading my replies properly
i have mentioned in my REPLIES that yes my router is configured with my ISP id n password in PPPOE mode(point to point over ethernet )
dhcp is enabled 
default route is enabled
then dns servers are enabled
everything wat a router requires to configure a connection on its own is is there
thats how i surf in my XP OS 

but u keep on asking the same question again n again

---

### Post by Kronie on 2008-06-07
wow.. for me its way different.. ubuntu detected my router all by it self, and i never got disconnected..in vista or XP i got DC from web like....8 times a day, so i had to unplug the power for 10 sect to reestablish connection o_0

---

### Post by coolnik6 on 2008-06-07
hi geezerone 
i did as u said
i assigned static ip as 192.168.1.4
n gateway as usual 192.168.1.1
but see it cannot reply back to ping cmd
i have ssen i nwin XP the ip address that r assigned to me r always in the range 117.169.somethin.somethin
niket@niket-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
From 192.168.1.4 icmp_seq=4 Destination Host Unreachable
From 192.168.1.4 icmp_seq=6 Destination Host Unreachable
From 192.168.1.4 icmp_seq=7 Destination Host Unreachable
From 192.168.1.4 icmp_seq=8 Destination Host Unreachable


niket@niket-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:44:65:0b:95  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe65:b95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:13046 (12.7 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64608 (63.0 KB)  TX bytes:64608 (63.0 KB)

niket@niket-desktop:~$

---

### Post by iaculallad on 2008-06-07
Drop to your terminal and issue the command:

```
netstat -rn
```

And post it

---

### Post by coolnik6 on 2008-06-07
**this is the o/p when i enabled dhcp in system< networking **

niket@niket-desktop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0
niket@niket-desktop:~$ 

**this is the o/p when i enabled static ip in system< networking **

niket@niket-desktop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
niket@niket-desktop:~$

---

### Post by philinux on 2008-06-07
Not hijacking your thread but ubuntu is the only distro to see my router on this machine. I have a distro heaven dvd with top ten live cd distro. And all fail to see my router from the live cd. Only Hardy and mint see it.

It must be hardware related. Mines an on board nic.

---

### Post by gandaran on 2008-06-07
coolnik6
        have you installed firestarter? could be the problem!

---

### Post by sharks on 2008-06-07
type sudo pppoeconf in the terminal and configure it.thats it...

---

### Post by geezerone on 2008-06-07
> **coolnik6 said:**
> hi geezerone 
i did as u said
i assigned static ip as 192.168.1.4
n gateway as usual 192.168.1.1
but see it cannot reply back to ping cmd
i have ssen i nwin XP the ip address that r assigned to me r always in the range 117.169.somethin.somethin...

Hi,

Thanks for going through these steps. You say that XP assigns an IP address of 117.169.x.x? In that case, go to XP. Connect to the internet then open a command prompt:

Start > Run , type *cmd* and press return. Then type *ifconfig /all*  (notice the space)

Note the IP address, Mask, default gateway and DNS servers and enter these details in Ubuntu as described in my previous post in configuring a static entry.

Also output the /etc/network/interfaces and route -n from terminal please.

---

### Post by coolnik6 on 2008-06-07
[b]these r the details of ipconfig /all cmd
i saw the 117.  ip's in router's configuration page just u look at them n tell me wat  to do next 
also below this i have p-asted the router's status page details [/b]


C:\Documents and Settings\Administrator>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : HOME
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethe
rnet NIC
        Physical Address. . . . . . . . . : 00-02-44-65-0B-95
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.4
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : Saturday, June 07, 2008 9:29:46 PM
        Lease Expires . . . . . . . . . . : Tuesday, June 10, 2008 9:29:46 PM

C:\Documents and Settings\Administrator>

**the below lines i copied from router's STATUS page** 

 -Ethernet
MAC Address	00:18:02:93:C6:F5
IP Address	192.168.1.1
Subnet Mask	255.255.255.0
DHCP Server	Enabled
NAT	Enabled

LAN -USB
MAC Address	00:18:02:93:C6:F5
IP Address	192.168.1.2
Subnet Mask	255.255.255.0
DHCP Server	Enabled
NAT	Enabled

WAN
Virtual Circuit	
Connection	Connected
[b]IP Address	117.xx.x.xx
Subnet Mask	255.255.255.255
Default Gateway	117.xx.x.xx[/b]

---

### Post by geezerone on 2008-06-07
The WAN 117.x.x.x is the globally significant ARPA allocated supernet address used on the WWW and is unique (I would suggest editing your post and replacing the last two octets with x's so no one else can see this, as from it I see your ISP is in New Delhi).

Your LAN IP is fine so now I would ask if you would clarify your hardware setup. In this I mean is the Windows PC the same box that Ubuntu is installed on and thus using the same ethernet cable to the same port on your router's switch?

In the mean time would you post the  */etc/network/interfaces* config please. and try pinging 127.0.0.1 (the loopback address to show that TCP/IP is working on the Ubuntu pc) and show what you get.

Thanks

---

### Post by coolnik6 on 2008-06-08
i have posted the contents of file etc/network/interfaces
also sudo plog o/p
auto lo
iface lo inet loopback








auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
-------------------------------------------
niket@niket-desktop:~$ sudo plog
[sudo] password for niket: 
Jun  8 10:09:17 niket-desktop pppd[4389]: Timeout waiting for PADO packets
Jun  8 10:09:17 niket-desktop pppd[4389]: Unable to complete PPPoE Discovery
Jun  8 10:10:22 niket-desktop pppd[4389]: Timeout waiting for PADO packets
Jun  8 10:10:22 niket-desktop pppd[4389]: Unable to complete PPPoE Discovery
Jun  8 10:11:27 niket-desktop pppd[4389]: Timeout waiting for PADO packets
Jun  8 10:11:27 niket-desktop pppd[4389]: Unable to complete PPPoE Discovery
niket@niket-desktop:~$

---

### Post by coolnik6 on 2008-06-08
here are the ping statistics for 127.0.0.1
niket@niket-desktop:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.062 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.047 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.051 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.047 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.048 ms
64 bytes from 127.0.0.1: icmp_seq=7 ttl=64 time=0.049 ms
64 bytes from 127.0.0.1: icmp_seq=8 ttl=64 time=0.049 ms
64 bytes from 127.0.0.1: icmp_seq=9 ttl=64 time=0.049 ms
64 bytes from 127.0.0.1: icmp_seq=10 ttl=64 time=0.049 ms
64 bytes from 127.0.0.1: icmp_seq=11 ttl=64 time=0.051 ms


--- 127.0.0.1 ping statistics ---
15 packets transmitted, 15 received, 0% packet loss, time 14004ms
rtt min/avg/max/mdev = 0.041/0.049/0.062/0.009 ms
niket@niket-desktop:~$ 

i forgot to answer some of ur quesytins
 yes both win xp n ubuntu 8.04 LTS  are installed on the same desktop
ubuntu is installed  as an application( the new way for installing inside windows using wubi and that i think is not an issue coz i have tried with a original os installation of 6.10 and 7.10) but the results were same as they r right now)
n i use the same router the same cable the same switch 
in short 1 have desktop pc's with  1 router  having 2 OS in it

---

### Post by geezerone on 2008-06-08
I would definitely use static ip with 192.168.1.5 

Your /etc/network/interaces file should then look like :

inet eth1 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1

Failing this have a look here:

[http://ubuntuforums.org/showthread.php?t=765041&highlight=wubi+internet](http://ubuntuforums.org/showthread.php?t=765041&highlight=wubi+internet)

HTH

---

### Post by coolnik6 on 2008-06-08
hey i tried everything from the links you 
ethtool eth0-- it actually detects the link
then  

sudo dhclient eth0 - this is not responding it says
No DHCPOFFERS received
No working leases in persistent database - sleeping

then i tried  editing rc.local file by copying these lines
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart
n restarted but i didn't got any success

now i am left with no other choice but to uninstall ubuntu 
i'll have to wait for a real user friendly ubuntu which i think will take some years(5 or more)
even though i may get a chance to run ubuntu on  a laptop or desktop afer some time assuming that i'll buy a new one
but on the back of my mind i will know that  i am pure lucky to have a working and compatible combination of hardware n the very same ubuntu 

i donno y ppl call ubuntu user friendly
after seeing those commands  i dont thing ubuntu fits in that tag of being user friendly
and the thing that soo many ppl cant connect to internet and then they have to go such thru a big process.
anyways thanks for all ur help i really appreciate ur time n it was a learning experience for me 
hey croatia  has been awarded with a penalty kick!


bye 
niket

---

### Post by OldTimeTech on 2008-06-08
You talk about using Ubuntu 6.10 and 7.10...have you tried the new Hardy (8.04) to see if it detects your configuration straight away?

---

### Post by geezerone on 2008-06-08
Hi

Very sorry to hear of your problems and is nothing I have come across before but then hardware varies I suppose.

I have used Dapper, Gutsy and now on Hardy Heron and always been able to connect to the internet even via the live CD.

I haven't used wubi so don't know how networking works with that but have you tried the live CD at all?

Of course, you could always install the free VMware server for windows and then install Ubuntu on top of windows and have the best of both worlds.

You aren't getting basic IP connectivity for some reason but if you would try the live CD and avoid wubi maybe that would help.

---

### Post by parianbu on 2008-06-14
Hi,

To coolnik6, buddy the problem is your side. Because I use the same router(UT300R2U)and the same ISP. I connect internet and reply, with your same router and OS (Ubuntu 8.04). So how is it possible, is Ubuntu doesn't support my router (UT300RU). 

Reinstall Ubuntu and go to the following link use the steps, u can connect the internet.Because I did it. 

[https://help.ubuntu.com/8.04/internet/C/adsl.html](https://help.ubuntu.com/8.04/internet/C/adsl.html)
[B]
UBUNTU ROCKS BUDDY !!!![/B] :guitar:

Follow it get the connection and reply me from ur Ubuntu.I accidentally saw this thread so i reply it.

How u messed all the things, However now u understand....

---

