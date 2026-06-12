---
title: "can't connect to internet through network"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Escuro Anjo on 2008-09-01
hi ..

it's my first day in ubuntu .. i love it but it can't recognize my lan at all ..

my mother : Asus p5gc-mx/1333

i download ubuntu version : ubuntu-8.04.1-desktop-i386

works fine but the lan ..

please if some one will say some thing please say it in detail ..

y the way i have linux lan driver ( from motherboard original CD ) but i don't know what can i do with it  .

thanks .. waiting for your answer ..

---

### Post by Marshal0505 on 2008-09-01
see if this helps you

[http://ubuntuforums.org/showthread.php?t=847873](http://ubuntuforums.org/showthread.php?t=847873)

---

### Post by Escuro Anjo on 2008-09-01
i saw this thread before and i did what he said but it's didn't work with me ..

when i make this 

> make install

the terminal replied with some words i don't remember exactely what is it ..

but in the last line there was : Error 2

and some thing about entering directroy and ten leaving dir ..

---

### Post by Escuro Anjo on 2008-09-01
i have another question : is there a way to install drivers without using Terminal ?

i think ubuntu devloper have to think more of the noob like me :D ..

---

### Post by Escuro Anjo on 2008-09-01
guys .. i tried to be step by step with the read me of the driver ..

i have reached to the step :

make install

they said that this command will copy the driver to net folder in kernel ..

/lib/modules/<YOUR KERNEL VER>/kernel/drivers/net/atl2

but when i did it there is an error and then there is no atl2 folder !!

i tried it when i'm root and when i'm normal user

---

### Post by Escuro Anjo on 2008-09-02
i got a new driver 8/2008 from people.redhat ..

i extract it then i went to terminal ..

i went to the Dir then .. i tried to " make install " but it's answered me : no rule for install " ..

then i tried " make " and the result is :

[PHP]root@ahmed-desktop:~/Desktop/atl2-2.0.5# make
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/root/Desktop/atl2-2.0.5 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /root/Desktop/atl2-2.0.5/atl2_main.o
  CC [M]  /root/Desktop/atl2-2.0.5/atl2_hw.o
  CC [M]  /root/Desktop/atl2-2.0.5/atl2_ethtool.o
  CC [M]  /root/Desktop/atl2-2.0.5/atl2_param.o
  LD [M]  /root/Desktop/atl2-2.0.5/atl2.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/Desktop/atl2-2.0.5/atl2.mod.o
  LD [M]  /root/Desktop/atl2-2.0.5/atl2.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
root@ahmed-desktop:~/Desktop/atl2-2.0.5# make install
make: *** No rule to make target `install'.  Stop.
root@ahmed-desktop:~/Desktop/atl2-2.0.5# 
[/PHP]
it biult some files as you can see .. then i tried to " make install " again to make the driver going to " net " folder but i couldn't !!

can anyone tell me what i have to do after this files have shows up ?

thanks ..

---

### Post by Escuro Anjo on 2008-09-02
i tried to modprobe the module then dhclient .. some text shows up but what i can understand is there is no network connection ..

---

### Post by stunningman on 2008-09-02
> **Escuro Anjo said:**
> hi ..

it's my first day in ubuntu .. i love it but it can't recognize my lan at all ..

my mother : Asus p5gc-mx/1333

i download ubuntu version : ubuntu-8.04.1-desktop-i386

works fine but the lan ..

please if some one will say some thing please say it in detail ..

y the way i have linux lan driver ( from motherboard original CD ) but i don't know what can i do with it  .

thanks .. waiting for your answer ..
open terminal:
type sudo pppoeconf
the next screen will ask you about your ip details your isp username and password
provide it
say yes to all other option comes after that
now
when everyting is set up

type in new terminal "pon dsl-provider" to start a connection and browse from firefox

when you want to terminate the connection type "poff dsl-provider"
thats it

---

### Post by Escuro Anjo on 2008-09-02
i will try it and give you comment thanks :)

---

### Post by Escuro Anjo on 2008-09-02
i tried it first it ask my about my interface if i can show it .. ther was just one interface eth0 so i said yes then some progress bars shows up then ..

some thing about scan failure

---

### Post by jemate18 on 2008-09-02
> **Escuro Anjo said:**
> i tried it first it ask my about my interface if i can show it .. ther was just one interface eth0 so i said yes then some progress bars shows up then ..

some thing about scan failure

can you paste the result of
```
ifconfig -a
```

If settings are correct(what you have set up)
try
```
sudo /etc/init.d/networking restart
```

---

### Post by Escuro Anjo on 2008-09-02
how can i know if the ubuntu can reconize my lan card ? or i need to install a driver ?

maybe it's driver problem ..

---

### Post by Escuro Anjo on 2008-09-02
> **jemate18 said:**
> can you paste the result of
```
ifconfig -a
```

If settings are correct(what you have set up)
try
```
sudo /etc/init.d/networking restart
```
ok i will try it now .. i have to go to ubuntu :( ..

---

### Post by jemate18 on 2008-09-02
```
ifconfig -a
```
[COLOR="Red"]ifconfig[/COLOR] command is used to configure a network interface
the [COLOR="Red"]-a[/COLOR] option displays all interfaces which are currently available, even if
down

the command 
```
sudo /etc/init.d/networking restart
```
forces your network service to start all over again. If you have a DHCP, it just request for the IP Address and configures itself.

---

### Post by Escuro Anjo on 2008-09-02
first thanks for this great info :) ..

the result of sudo pppoeconf :

Sorry, I scanned 1 interface, but the Access
Concentrator of your provider did not respond. Please
check your network and modem cables. Another reason
for the scan failure may also be another running pppoe
process which controls the modem.

ifconfig -a :

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:e0:90:ff  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:dffc0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44077 (43.0 KB)  TX bytes:44077 (43.0 KB)

---

### Post by jemate18 on 2008-09-02
> **Escuro Anjo said:**
> first thanks for this great info :) ..

the result of sudo pppoeconf :

Sorry, I scanned 1 interface, but the Access
Concentrator of your provider did not respond. Please
check your network and modem cables. Another reason
for the scan failure may also be another running pppoe
process which controls the modem.

ifconfig -a :

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:e0:90:ff  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:dffc0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44077 (43.0 KB)  TX bytes:44077 (43.0 KB)

It seems that there is no problem regarding your eth0 (network interface)

So what problems are you encountering now? Where you able to connect to the internet after 
```
sudo /etc/init.d/networking restart
```
?

---

### Post by Escuro Anjo on 2008-09-02
no i tired it but i still can't .. so you saying there is no need for new driver ?

---

### Post by jemate18 on 2008-09-02
> **Escuro Anjo said:**
> no i tired it but i still can't .. so you saying there is no need for new driver ?

Yes because your Ubuntu detects it and that you have your IP Address with your eth0

Where you able to ping google?
```
ping www.google.com
```

What is the output? is there a 0% packet loss?

---

### Post by Escuro Anjo on 2008-09-02
when i ping google .. it said ..

[PHP]ping : unknown host www.google.com[/PHP]

i start to desperate

---

### Post by jemate18 on 2008-09-02
> **Escuro Anjo said:**
> when i ping google .. it said ..

[PHP]ping : unknown host www.google.com[/PHP]

i start to desperate

sounds like a resolver problem...

try this in firefox

> [http://209.85.175.99](http://209.85.175.99)

google site should be displayed

---

### Post by jemate18 on 2008-09-02
if you have been able to display google using my suggestion on my above post, then i think the problem is DNS..

this is a complete stepbystep on how to use opendns on ubuntu

> [https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

---

### Post by Escuro Anjo on 2008-09-02
no it didn't show google :( .. i don't think it's the DNS because i tried to config to ( auto and static ) and the same ..

look man when i go to network tools there is two network device ( lo and eth0) when i choose on then configure some error shows up ( interface not exit be sure that your system support )

---

### Post by jemate18 on 2008-09-02
> **Escuro Anjo said:**
> no it didn't show google :( .. i don't think it's the DNS because i tried to config to ( auto and static ) and the same ..

look man when i go to network tools there is two network device ( lo and eth0) when i choose on then configure some error shows up ( interface not exit be sure that your system support )

OK.... so if it ain't DNS, and that you are having some errors on configuration.... well most probably its a driver problem... But this is some special situation, since ifconfig -a shows your device and configuration "correctly".

.... Sorry i wasnt able to solve..... 

most probably some missing drivers for your LAN card......

---

### Post by Escuro Anjo on 2008-09-02
i got a driver a new one it's date is 8/2008 so it's new .. for my lan .. from people.redhat.com

then i download it extract it and going to terminal and did " make " some files showsup then i did " make install "

but it's say " no rule for install "

!! so what can i do ?

---

### Post by Escuro Anjo on 2008-09-02
this is what i'm talking about ..

root@ahmed-desktop:~/Desktop/atl2-2.0.5# make
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/root/Desktop/atl2-2.0.5 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /root/Desktop/atl2-2.0.5/atl2_main.o
  CC [M]  /root/Desktop/atl2-2.0.5/atl2_hw.o
  CC [M]  /root/Desktop/atl2-2.0.5/atl2_ethtool.o
  CC [M]  /root/Desktop/atl2-2.0.5/atl2_param.o
  LD [M]  /root/Desktop/atl2-2.0.5/atl2.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/Desktop/atl2-2.0.5/atl2.mod.o
  LD [M]  /root/Desktop/atl2-2.0.5/atl2.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
root@ahmed-desktop:~/Desktop/atl2-2.0.5# make install
make: *** No rule to make target `install'.  Stop.
root@ahmed-desktop:~/Desktop/atl2-2.0.5#

---

### Post by Miljet on 2008-09-02
I'm not knowledgeable enough to help solve your problem, but I can offer this advice. Ubuntu is based on Debian which uses an entirely different package management system than Red Hat. If you are trying to install drivers that you downloaded from a Red Hat site, you are going to have major problems installing it.
Maybe someone else will jump in and help.
Good luck.

---

### Post by Escuro Anjo on 2008-09-02
i think i will reinstall ubuntu and try again .. maybe this will solve this problem .. if not at least start from fresh point .. i was learing so much in this version :D .. but i still want a solution ..

thanks for you all ..

---

### Post by Escuro Anjo on 2008-09-08
so there is no solution ? :(

---

