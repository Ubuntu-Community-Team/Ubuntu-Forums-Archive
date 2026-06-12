---
title: "Router problem"
date: 2009-09-08
forum: Philippine Team
---

### Post by guitar_man on 2009-09-08
Gandang gabi mga sir....


Papatulong lang ako sa router...
Nagkakaproblema kasi ako sa koneksyon.
Nagset-up ako ng network para sa 2 kompyuter para parehas sila may internet pero hindi ko magawa.Walang koneksyon:confused::confused:
Parehas na linux yung mga kompyuter.
D-link 704P ang raouter ko.

---

### Post by dodimar on 2009-09-09
> **guitar_man said:**
> Gandang gabi mga sir....


Papatulong lang ako sa router...
Nagkakaproblema kasi ako sa koneksyon.
Nagset-up ako ng network para sa 2 kompyuter para parehas sila may internet pero hindi ko magawa.Walang koneksyon:confused::confused:
Parehas na linux yung mga kompyuter.
D-link 704P ang raouter ko.

Na ping mo ba yung router IP from both PC? can you ping the other PC from the other (vice versa)... kung okay to, then,

What's your ISP?
Can you connect to the net if you directly connect one of the PC to the ISP?

---

### Post by guitar_man on 2009-09-09
Hindi po ma-ping yung 192.168.1.1 ng router
Smart Bro po ISP ko,nakaka-connect naman directly sa net ang isang kompyuter.

---

### Post by orlandopasionjr on 2009-09-09
pre, try mong i-clone un mac-address ng LAN card mo sa PC mo, then i-set mo sa router. try also to set your router to dhcp mode.

---

### Post by guitar_man on 2009-09-09
@orlandopasionjr
sir pano ba yun??

---

### Post by pendletone on 2009-09-09
hi guitar_man,

naging problema ko rin yan with my wireless d-link router a few months ago. i have two computers (desktop and a laptop) but can't seem to connect with the latter. sinubukan ko lahat ng powers ko para maka-connect using my lappie, but to no avail.

ultimately, ni-reset ko na lang yung router ko manually at ni-reconfigure uli yung settings niya to my ISP, and then yun ok na.

try mo rin yung suggestion ni mr. orlandopasionjr, baka naman naba-block ng router mo yung mac address ng pc mo.

type:```
ifconfig -a
``` to know your mac address and see if it's being blocked by your router.

---

### Post by guitar_man on 2009-09-09
> **pendletone said:**
> hi guitar_man,

naging problema ko rin yan with my wireless d-link router a few months ago. i have two computers (desktop and a laptop) but can't seem to connect with the latter. sinubukan ko lahat ng powers ko para maka-connect using my lappie, but to no avail.

ultimately, ni-reset ko na lang yung router ko manually at ni-reconfigure uli yung settings niya to my ISP, and then yun ok na.

try mo rin yung suggestion ni mr. orlandopasionjr, baka naman naba-block ng router mo yung mac address ng pc mo.

type:```
ifconfig -a
``` to know your mac address and see if it's being blocked by your router.




sir pano ginawa mo?
hindi ko kasi talaga alam.hehe

---

### Post by killer_d76 on 2009-09-09
before doing anything make sure na yun settings mo sa gnome network manager is on **automatic**.. kasi you cannot access your Routers IP add if may naka-assign na IP add sa network mo.

just my two cents.. ;)

---

### Post by perbiu on 2009-09-09
Assuming both your PC is connected to the router.

Go to your PC which can connect to the net.

Right click on the network icon and select connection information.

Copy the IP address of the "Default Route". (mine is 192.168.2.1)

Then paste the IP address of the Default Route to your firefox address so you can access the router.

Set it to Automatic/DHCP.

Both your PC must be in Auto also (mines Auto eth0)

The other one will connect to the net while the other will be stuck with the Smartbro portal webpage assuming that the wiring is good (is your wiring customized?).

If the other PC is stuck with Smartbro portal webpage. Go to your PC which can connect to the net and access the router, then select the clone mac address.

---

### Post by guitar_man on 2009-09-09
> **killer_d76 said:**
> before doing anything make sure na yun settings mo sa gnome network manager is on **automatic**.. kasi you cannot access your Routers IP add if may naka-assign na IP add sa network mo.

just my two cents.. ;)


naka-automatic na boss,,,ayaw pa din e...ayaw nga din ma-access yung router IP

> **perbiu said:**
> Assuming both your PC is connected to the router.

Go to your PC which can connect to the net.

Right click on the network icon and select connection information.

Copy the IP address of the "Default Route". (mine is 192.168.2.1)

Then paste the IP address of the Default Route to your firefox address so you can access the router.

Set it to Automatic/DHCP.

Both your PC must be in Auto also (mines Auto eth0)

The other one will connect to the net while the other will be stuck with the Smartbro portal webpage assuming that the wiring is good (is your wiring customized?).

If the other PC is stuck with Smartbro portal webpage. Go to your PC which can connect to the net and access the router, then select the clone mac address.



Hindi ko ma-access yung router IP ko:confused:

---

### Post by dodimar on 2009-09-09
What's your ifconfig?

---

### Post by guitar_man on 2009-09-10
eth0      Link encap:Ethernet  HWaddr 00:19:21:13:7b:13  
          inet addr:192.168.247.244  Bcast:192.168.255.255  Mask:255.255.224.0
          inet6 addr: fe80::219:21ff:fe13:7b13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3133309 (3.1 MB)  TX bytes:765283 (765.2 KB)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23956 (23.9 KB)  TX bytes:23956 (23.9 KB)




eto yung lagi kong ginagamit na desktop....

---

### Post by Ravskie on 2009-09-10
sir yung pong router nyo bago as in wala pang config if yes try nyo nga po i reset.....then ifconfig ka ulit.....

---

### Post by guitar_man on 2009-09-10
eth0      Link encap:Ethernet  HWaddr 00:19:21:13:7b:13  
          inet addr:192.168.247.244  Bcast:192.168.255.255  Mask:255.255.224.0
          inet6 addr: fe80::219:21ff:fe13:7b13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3861 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3028293 (3.0 MB)  TX bytes:544039 (544.0 KB)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24154 (24.1 KB)  TX bytes:24154 (24.1 KB)



eto boss,nung nireset ko yung router..

---

### Post by guitar_man on 2009-09-10
mga boss,


ok na router ko,yeah...dalawa na sila may internet connection...yeah..

Tama nga si **Ravskie**,nireset ko lang yung router at dun na ako nastuck...
Haay.kala ko basata lang pipindutin yung reset ng router...may kung anu-anong inarte pa pala yun...dapat pala PRESS reset sabay plus sa power ng router,,,,
MEGANUN!!:lolflag:

Pero ok na sya...

---

### Post by ache109 on 2009-09-10
> **guitar_man said:**
> mga boss,


ok na router ko,yeah...dalawa na sila may internet connection...yeah..

Tama nga si **Ravskie**,nireset ko lang yung router at dun na ako nastuck...
Haay.kala ko basata lang pipindutin yung reset ng router...may kung anu-anong inarte pa pala yun...dapat pala PRESS reset sabay plus sa power ng router,,,,
MEGANUN!!:lolflag:

Pero ok na sya...

good to hear na ok na ung router mo. halos ganyan din experience ko with my router. 2 days ko yata bago nasetup. the only problem is that my ISP (digitel) is PPPoE not dynamic IP (unlike PLDT w/c uses dynamic)

---

### Post by dodimar on 2009-09-10
Good job...

---

### Post by Ravskie on 2009-09-11
> **guitar_man said:**
> mga boss,


ok na router ko,yeah...dalawa na sila may internet connection...yeah..

Tama nga si **Ravskie**,nireset ko lang yung router at dun na ako nastuck...
Haay.kala ko basata lang pipindutin yung reset ng router...may kung anu-anong inarte pa pala yun...dapat pala PRESS reset sabay plus sa power ng router,,,,
MEGANUN!!:lolflag:

Pero ok na sya...


Nice to hear !!!! happy browsing !!!!!! :guitar:

---

### Post by guitar_man on 2009-09-11
Asar lang kasi kala ko basta pindutin mo lang ang reset ng router ok na...Kailangan pala hold mo then power-up sya...Ok lang..Ngayon alam ko na...
Next time hindi na ako papauto sa mga bagay na gawang tao lang:lolflag:

---

