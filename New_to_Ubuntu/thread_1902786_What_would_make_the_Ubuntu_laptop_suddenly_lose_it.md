---
title: "What would make the Ubuntu laptop suddenly lose its assigned IP address?"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by rocksockdoc on 2011-12-31
Recently I set up a wireless network following my WISP's instructions and I was surprised to see my Ubuntu laptop's assigned IP address disappear.

Q: What would make the Ubuntu laptop's IP address suddenly disappear?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210025&stc=1&d=1325369098[/IMG]

For example, at time 0, I set the laptop's IP address to the same subnet as that of my WISP radio, e.g.:
```
$ sudo ifconfig eth0 10.0.67.1
$ ifconfig
REPORTS:
eth0      Link encap:Ethernet  HWaddr 00:A0:d3:3e:25:44  
         ** inet addr:10.0.67.1**  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::216:d3ff:fe3e:8304/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1348760 (1.3 MB)  TX bytes:331202 (331.2 KB)
          Memory:f8200000-f8220000 
```Once both the laptop and the Bullet M2 WISP radio are on the same subnet, I can log into that WISP radio just fine from my wired Ubuntu laptop (because both are now on the same subnet). 

But, soon (roughly in a few minutes), I invariably lose my connection to the wireless radio. 

At first, I didn't know why ... but then, after debugging, I belatedly realized my laptop's IP address suddenly disappeared (without me realizing that it had been deleted).

At time ~= 5 minutes, "ifconfig" reported the following on the Ubuntu laptop:
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:d3:3e:25:44  
          inet6 addr: fe80::216:d3ff:fe3e:8304/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1348760 (1.3 MB)  TX bytes:329076 (329.0 KB)
          Memory:f8200000-f8220000 
```Notice there is no IP address reported for eth0 even though I did NOT run another ifconfig command!

I'm confused WHY the Ubuntu laptop apparently LOST the IP address I had assigned to it so that I could further configure the WISP radio.

Of course, if I simply reassign the original IP address back to the laptop, that laptop can then again connect to the WISP radio ... but ... my confusion is ... 

Q: What would make the Ubuntu laptop suddenly lose its assigned IP address?

---

### Post by mapes12 on 2012-01-01
Would it not be easier to let your router automatically handle IP address assigning with DHCP? If your router has DHCP capability you should be able to set it from the Admin screen.

Either way here's a list of IP's and subnets:-

The internationally-established private IP address ranges that can be assigned to internal network computers are as follows:

        * 10.0.0.1 through 10.255.255.254
              16,777,214 addresses
              16,777,214 computers on 1 network
                (10.x.x.x)
              Uses a subnet mask of 255.0.0.0
              First octet must be the same on all computers
              A Class A address range 

        * 172.16.0.1 through 172.31.255.254
              1,048,574 addresses
              65,534 computers on each of 16 possible networks
                (172.16.x.x to 172.31.x.x)
              Uses a subnet mask of 255.255.0.0
              First two octets must be the same on all computers
              A Class B address range 

        * 192.168.0.1 through 192.168.255.254
              65,534 addresses
              254 computers on each of 256 possible networks
                (192.168.0 to 255.x)
              Uses a subnet mask of 255.255.255.0
              First three octets must be the same on all computers
              A Class C address range

---

### Post by z3nhakr on 2012-01-01
if you want to assign an ip, it would be better to do it in the router settings page and assign the ip to your computers mac

---

### Post by rocksockdoc on 2012-01-01
> **mapes12 said:**
> Would it not be easier to let your router automatically handle IP address assigning with DHCP? If your router has DHCP capability you should be able to set it from the Admin screen.

That's exactly what I'm doing in the final configuration (see diagram below)!
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210060&stc=1&d=1325429890[/IMG]

But ... the problem of the IP address suddenly being lost on the Ubuntu PC is in the initial setup of the radio when DHCP is not available (i.e., when I 'must' have the right IP address on the Ubuntu laptop).

After the initial setup, there is no DHCP from the radio (because the radio is set up in bridge mode).

Once the radio is properly set up, then (and only then) I hook up the broadband router (which** 'is' **set up to serve DHCP addresses to the Ubuntu laptop).

Above is a diagram of the final configuration - but again - the problem of the Ubuntu IP address inexplicably dropping off is in the initial setup (when DHCP is not available) - not in the final configuration.

It's not a big crisis ... but I was just wondering what it was that made the Ubuntu laptop suddenly just drop its eth0 IP address in the middle of my operations to set up the radio.

---

### Post by fdrake on 2012-01-01
did you try:?
```
vi /etc/network/interfaces
```
and add 
> 
iface eth0 inet static
address 10.0.67.1
netmask 255.0.0.0
gateway 10.0.67.10

to double check the data, first assign the ip with ifconfig like you did at the beginning  and run "route -n" and use those address to edit your interface file!

ifconfig should be good for only one session but it looks something else maybe the problem, maybe with IPv6?

---

### Post by rocksockdoc on 2012-01-01
> **z3nhakr said:**
> if you want to assign an ip, it would be better to do it in the router settings page and assign the ip to your computers mac

I understand. That's exactly what I do **in the final configuration** (see diagram above).

The problem of the Ubuntu laptop suddenly (and inexplicably) dropping the IP address assigned to eth0 during the setup of the radio as a bridge (when DHCP is not an option) is what I was wondering about.

It's not going to kill me as my workaround was simply to constantly re-assign the IP address to the Ubuntu laptop after each drop. This happened about 5 or so times (plus another couple of times as I tested it) so it's repeatable.

Reconstructing history, the sequence was the following:

[LIST]
[*]I set the IP address of the Ubuntu laptop to anything on the same subnet as the default Ubiquiti Bullet M2 radio (i.e., 192.168.1.x)
[LIST]
[*]*sudo ifconfig eth0 192.168.1.21*
[/LIST]
 
[*]Then, I connected a cat5e cable between the Ubuntu laptop & the Ubiquiti radio and logged into the Ubiquiti radio by bringing up a web browser and going to the default IP address of the Ubiquiti radio
[LIST]
[*][http://192.168.1.20]("http://192.168.1.21") (login=ubnt, passwd=ubnt)
[/LIST]
 
[*]I set the Ubiquiti Bullet M2 radio to bridge mode and I set the IP address of the Bullet M2 radio to the WISP-required IP address of 10.0.67.10.
[LIST]
[*]At that point, I lost connectivity because (predictably), now the Ubuntu laptop was on the wrong subnet! (This was expected.)
[*]Ubuntu laptop IP address = 192.168.1.21
[*]Bullet M2 radio IP address = 10.0.67.10
[/LIST]
 
[*]Then, I set the Ubuntu laptop IP address to the same subnet as the Bullet M2 radio (i.e., 10.0.67.x)
[LIST]
[*]*sudo ifconfig eth0 10.0.67.1*
[/LIST]
 
[*]At this point, I again logged into the radio using the radio's new IP address
[LIST]
[*][http://10.0.67.10](http://10.0.67.10) (login=ubnt, passwd=ubnt)
[/LIST]
 
[*]While I was logged into the radio to check the settings and to align the antenna and to select the WISP-provided SSID access point,** the IP address of the Ubuntu laptop kept (inexplicably) dropping.**
[LIST]
[*]Each time the IP address dropped on the Ubuntu laptop, I had to reset the IP address on that Ubuntu laptop to maintain the connection to the radio:
[*]*sudo ifconfig eth0 10.0.67.1*
[/LIST]
 
[/LIST]
So, I guess the question is WHY Ubuntu would just drop an IP address once it has set. 

**Q: Is there perhaps an IP-address expiration timeout in Ubuntu?**

---

### Post by Zill on 2012-01-01
> **fdrake said:**
> did you try:?
```
vi /etc/network/interfaces
```
+1

I would trust this more than NetworkManager.

---

### Post by rocksockdoc on 2012-01-01
> **fdrake said:**
> did you try
```
vi /etc/network/interfaces
```and add 
```

iface eth0 inet static
address 10.0.67.1
netmask 255.0.0.0
gateway 10.0.67.10                      
```

**T****hat's a GREAT idea!**

I am relatively new to Ubuntu so I didn't realize /etc/network/interfaces does the same thing (more permanently I guess) than does ifconfig. 

My default /etc/network/interfaces is the following:
```

auto lo
iface lo inet loopback

```If I change it (almost) to what you wrote ... I would agree, it's more likely that change would remain more permanently than does the ifconfig method. 

Plus, you just resolved the problem of setting the 'gateway'. I needed to set the gateway to the WISP-provided gateway ... but I didn't know how to set the gateway using ifconfig. So I had to skip that test and simply set the gateway in the home broadband router later in the testing stage. 

But, if something had gone wrong in the initial setup, I would have needed to eliminate the home broadband router for debugging - in which case, knowing how to set the gateway in the Ubuntu PC is important (because, you can't get 'on' the Internet with the test setup without setting the gateway somewhere!).

With your advice, it looks like I can kill two birds with one stone because with /etc/network/interfaces:

[LIST=1]
[*]I can "more permanently" set the IP address of the Ubuntu laptop, and,
[*]I can set the gateway to the WISP-provided gateway for initial setup testing
[/LIST]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210063&stc=1&d=1325434319[/IMG]
*Note: Once fully configured, there would be no need to set the gateway in the Ubuntu laptop because the home router will be added to the mix - and the home router has the gateway set up in it.*

One question with your example:
I noticed you suggested a netmask of 255.0.0.0 ... but ... if I understand the netmask (it has always confused me) ... don't I want to set mine to 255.255.255.0?

I assume it should be 255.255.255.0 because, in this test setup, all the IP addresses are of the form 10.0.67.something.

[LIST=1]
[*]The WISP-provided AP gateway is 10.0.67.1
[*]The WISP-provided IP address for my radio is 10.0.67.10
[*]The Ubuntu laptop can have any IP address that will connect to those two (e.g., 10.0.67.12).
[/LIST]
**Given that, shouldn't I use 255.255.255.0 and not 255.0.0.0 ?**

  > **fdrake said:**
> ifconfig should be good for only one session but it looks something else maybe the problem, maybe with IPv6?

Perhaps ifconfig has an expiration timeout that /etc/network/interfaces doesn't have?

Or, maybe, as I was setting things up in the radio, maybe the radio somehow 'told' the Ubuntu laptop to drop its IP address???

> **Zill said:**
> I would trust this more than NetworkManager.

Now you tell me! :)

By way of explanation, I had not realized I 'could' use /etc/network/interfaces to do what ifconfig does.

BTW, I wonder ... is there a way to set the gateway in 'ifconfig'? (I didn't see it in 'man ifconfig' output.)

---

### Post by fdrake on 2012-01-01
my post takes in consideration the entry you provide in the 1st post :
ip:10.0.67.1 and gateway 10.0.67.10 if you change your setting you can try first with ifconfig. If ifconfig works then use the values from "route -n" to find the values for the entry in /etc/network/interfaces.

---

### Post by rocksockdoc on 2012-01-01
> **fdrake said:**
> my post takes in consideration the entry you provide in the 1st post :ip:10.0.67.1 and gateway 10.0.67.10 

I apologize. 

 I may have confused things a bit in the first post because I didn't take into consideration the WISP-provided gateway address (which wasn't needed in the initial setup of the radio but which **'is'** needed for the final setup).

Also, I didn't realize until I just now checked the settings, that there is an ADDITIONAL IP ADDRESS to take into account!

In the final setup, the broadband router seems to have an "incoming?" IP address of one more than that of the WISP-provided radio IP address. 

[LIST=1]
[*]The WISP provides the gateway address (of 10.0.67.1)
[*]The WISP provides the address for my radio (of 10.0.67.10)
[*]The WISP (apparently) also provided the (incoming?) address for my home broadband router (of 10.0.67.11)
[/LIST]
So, here's the corrected annotated diagram with the test sequence on the top half, and the final setup on the bottom half.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210065&stc=1&d=1325437347[/IMG]

[SIZE=3][COLOR=DarkRed]**Here is what the final radio setup looks like:**[/COLOR][/SIZE]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210066&stc=1&d=1325437347[/IMG]

[SIZE=3][COLOR=DarkRed]**And, h****ere is what the final broadband home router setup looks like:**[/COLOR][/SIZE][IMG]http://ubuntuforums.org/attachment.php?attachmentid=210067&stc=1&d=1325437347[/IMG]

**Notice I'm confused about WHY/WHERE the IP address 10.0.67.11 came from?**

I remember the WISP telling me what to do on the telephone so they must have provided that IP address for me - but (being relatively new to networking) I don't know why the home router needs TWO IP addresses!

---

