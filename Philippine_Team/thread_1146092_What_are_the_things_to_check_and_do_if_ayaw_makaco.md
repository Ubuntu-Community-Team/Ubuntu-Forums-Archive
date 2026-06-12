---
title: "What are the things to check and do if ayaw makaconnect ng Ubuntu sa Internet"
date: 2009-05-02
forum: Philippine Team
---

### Post by jonardds on 2009-05-02
Hi guys.  malapit na mag-24 hours since I installed Ubuntu v.8.04 using Wubi sa pc ko. But the problem is hindi ako makaconnect sa Internet although gumagana naman sya sa Windows XP.  I already tried to configure the network connection into dynamic and static IP pero parehong ayaw gumana...I also check sa Terminal yung IFCONFIG heto ang lumalabas (see attachment).

---

### Post by jonardds on 2009-05-02
I'm not sure if the following data is useful sa problem solving:
 
CPU: Intel Core 2 Duo E6850@ 3 GHz
Network Adapter: Realtek RTL8139/810x Family Fast Ethernet NIC
 
Ang internet service provider ko is KT Internet Megapass Special...sabi (quote ko lang yung nasa features) "This is an internet serviceenabled through the FTTH and VDSL lines for professionals. The fastest Internet service in the true sense of the word, it guarantees 100Mbps". pero yun nga lang hindi ko magamit sa Ubuntu.

---

### Post by tagabukid on 2009-05-02
hi jonardds. [**This**]("https://help.ubuntu.com/8.04/installation-guide/powerpc/pppoe.html") might help. If not.. Remember that google is our friend. :-) or bug the hell out of the customer-care reps of your ISP.. 

Don't get discouraged. When I first shifted from windowsXp to Ubuntu, I couldn't connect either using a cellphone and SMART (Which sadly is the only way I can get online from here). Dual booting for a while helped until i solved my problem.(by asking and combing through the forums) Since then I have gotten rid of my other OS and haven't looked back.

Hang in there and I'm sure you'll find like I did that FOSS is way better than some proprietary OS full of malware and viri. Good luck!

---

### Post by tagabukid on 2009-05-03
[https://help.ubuntu.com/8.04/internet/C/modems-adsl-pppoe.html#modems-adsl-pppoe-setup](https://help.ubuntu.com/8.04/internet/C/modems-adsl-pppoe.html#modems-adsl-pppoe-setup) might also work.. good luck!

---

### Post by vivatsemiramis on 2009-05-03
guys, i have a different problem re: network connections. when i was using intrepid this rarely happened:

after some time i would be disconnected from my isp. i'm subscribed to bayanDSL. then i would try to connect for several minutes but the connection would keep asking for my authentication details and would keep telling me that i was disconnected from the network. this happened to me in intrepid when the bayantel server was really down due to the typhoon. after upgrading to jaunty this always happened but i assumed there was something wrong with the bayanDSL server. i kept pestering their cust. service reps through text, but they always say my connection is up in their server. they advised me to always delete the bayanDSL connection from the network manager applet, then create another dialer. that solves the problem. 

the solution works but i don't want to do this virtually everyday, like each time i try to open my notebook and connect to their server. btw, after i installed the dialer over and over again, there is always the 'network secret thing and allow keyring'-- I wasn't able to note it in detail, I choose the always allow option, but still this always happened since i upgraded to jaunty. i upgraded to jaunty on april 24, so it's more than a week that this is happening to me.

you have any advise? other pals with similar problem as mine? regards

---

### Post by daxumaming on 2009-05-04
I'm so confident of Ubuntu that every time I lose my connection, I'll only blame either my hardware or my ISP. After powercycling and I still don't have a connection, I usually wait for a few hours and sure enough, it comes back up.

I still remember my call center days wherein I usually instruct our clients to boot into safe mode, restack tcp/ip, etc. Heh, thank god I no longer deal with those stuff.

---

### Post by vivatsemiramis on 2009-05-04
haha at least you're so patient. i do not have your patience, my gosh even if i'm not using the connection i have to know that it is working; i can imagine bayandsl reps making faces because of my being too demanding hehe

---

### Post by loell on 2009-05-04
maybe you can just disable then enable again the connection than having to re-enter the same information to reconnect?

or probably use ppoeconf and pppd directly.

---

### Post by vivatsemiramis on 2009-05-04
> **loell said:**
> maybe you can just disable then enable again the connection than having to re-enter the same information to reconnect?

or probably use ppoeconf and pppd directly.

thanks. will try it next time when it happens again. regards

---

### Post by kiminaiseah on 2009-05-05
try this orasyon under SU or using sudo

1. /etc/init.d/networking stop
2. /etc/init.d/NetworkManger stop
3. vi /etc/network/interfaces
3a.(if your using dhcp protocool)

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

4. /etc/init.d/networking restart

---

in these case or in my case i dint use NetworkManager instead it would override any configs that you made in commandline

> **jonardds said:**
> Hi guys.  malapit na mag-24 hours since I installed Ubuntu v.8.04 using Wubi sa pc ko. But the problem is hindi ako makaconnect sa Internet although gumagana naman sya sa Windows XP.  I already tried to configure the network connection into dynamic and static IP pero parehong ayaw gumana...I also check sa Terminal yung IFCONFIG heto ang lumalabas (see attachment).

---

### Post by joshua.solidum on 2009-05-06
169xxx,is a windows self assigned ip address on windows,it does this if your windows machine is not detecting any connection,But since your running it on wubi better check connections first,Are you connected via router or modem?make sure your in NAT.Previous steps by other guys will work for you also

---

### Post by kingkalag on 2009-05-08
hindi ko lang alam kong nasubukan mo na ang quick and dirty way... .. .


$ ifconfig eth0 down
$ ifconfig eth0 up
$ ifconfig eth0 dhcp

---

### Post by kiminaiseah on 2009-05-08
any updates?

---

### Post by jonardds on 2009-05-10
naku sorry ngayon lang ako nakareply...medyo busy sa work...nanghingi ako ng old pc, pentium 3 (yes, nahihingi ang old pc dito sa Korea) and tried installing the Ubuntu as the main and only OS. tapos automatic na nagrun yung internet...I have tried po yung mga suggestion nyo dun sa isang pc ko running on windows/ubuntu pero di pa rin maka-connect. I suspect it is the Wubi installation. or maybe the hardware...para masiguro ko I will try to install Ubuntu without Wubi then update ko kayo...thanks and more power to all

---

### Post by cloud69 on 2009-05-12
> **jonardds said:**
> Hi guys.  malapit na mag-24 hours since I installed Ubuntu v.8.04 using Wubi sa pc ko. But the problem is hindi ako makaconnect sa Internet although gumagana naman sya sa Windows XP.  I already tried to configure the network connection into dynamic and static IP pero parehong ayaw gumana...I also check sa Terminal yung IFCONFIG heto ang lumalabas (see attachment).

base on the picture you have posted your LAN card didn't get any IP address from your DHCP server that is why you can't connect to the internet.
And maybe because you are installing ubuntu within Windows.

---

### Post by badrra on 2009-05-16
I am using wubi from Hardy to interpid and now jaunty. I only experienced the problem twice when globe took my old router and replaced it with crap Aztech. They told me they wanted to upgrade the modem. Ngayon me untang na loob pa ko sa kanila. 

Anyway when I access the gui and attempt to configure it,  the gui freezes up then DHCP fails so I get a 169 on both PC (windows and ubuntu). Lalo na pag ginalaw ko wireless setting. So Check your modem router as well baka nanadyan ang problema. I can see sa screen shot na yung network connection mo is "on" pero 169. 

So ako naman ang gawa ko reset ko ng matagal mga 3 times halos mabutas yung modem. Ayun meron nang DHCP. So check nyo din firmware ng router nyo baka yun ang sira.

---

### Post by rozzpalacio76 on 2009-05-17
[QUOTE=jonardds;7197643]Hi guys.  malapit na mag-24 hours since I installed Ubuntu v.8.04 using Wubi sa pc ko. But the problem is hindi ako makaconnect sa Internet although gumagana naman sya sa Windows XP.  I already tried to configure the network connection into dynamic and static IP pero parehong ayaw gumana...I also check sa Terminal yung IFCONFIG heto ang lumalabas (see attachment).[/QU

I also have that experience but after some google & ubuntu searching I found this WICD network manager application. Try to download it using WindowsXP muna from softpedia.com and may installation procedure nang kasama. Right now Im happy using both Wired and Wi-Fi connection. Hope this will help.

---

### Post by genius24k on 2009-05-18
Suggestion, open terminal

Make sure your lan is up eth0 or eth1 and is set to dhcp

$ ifconfig 
 
to check if its set to dhcp

$ cat /etc/network/interfaces

when you do ifconfig and you see ip assigned to it and still cannot connect check /etc/resolv.conf and make usre there are dns entry there

Then restart network
$ /etc/init.d/networking stop
$ /etc/init.d/networking start

you might also want to check routing table

$ route

make sure the defaut gateway ip is correct.


More howto on troubleshooitng network issue 
[http://www.review-ninja.com/2008/08/network-troubleshooting-dns-problem-my.html](http://www.review-ninja.com/2008/08/network-troubleshooting-dns-problem-my.html)

---

