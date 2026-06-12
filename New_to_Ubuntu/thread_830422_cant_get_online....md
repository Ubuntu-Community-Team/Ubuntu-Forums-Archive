---
title: "cant get online..."
date: 2008-06-15
forum: New to Ubuntu
---

### Post by kennster on 2008-06-15
ive been online all day "playing wow and talking on yahoo/aim" and i went out to eat came back and not able to connect at all but my mom sis and my laptop have internet ... any idea how to fix it

---

### Post by superprash2003 on 2008-06-15
please go to the terminal and type ifconfig and post output.. also type ping google.com and post output

---

### Post by kennster on 2008-06-15
```
laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:73:ca:zc  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0B)  TX bytes:0 (0B)
          Interrupt:22 address:0x2000

eth1        Link encap:Ethernet  HWaddr 00:18:f3:73:d7:eb
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0B)  TX bytes:0 (0B)
          Interrupt:21 address:0x2000

eth0:avah link encap:ethernet HWaddr 00:18:f3:73:ca:2c
                   inet addr:169.254.7.92 Bcast:169.254.255.255 mask:255.255.0.0
                   UP BROADCAST MULTICAST MTU:1500 Metric:1
                   Interrupt:22 base address:0x2000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15556(15.1 KB)  TX bytes:1556 (15.1 KB)
```

thats what it ses i had to type it sorry took so olong to resopond on my laptop cuz desop top well cant get online atm

---

### Post by bukwirm on 2008-06-15
Did you try "ping www.google.com"?

---

### Post by kennster on 2008-06-15
u mean in Terminal just type ping [www.google.com?](www.google.com?)

it sed ping: unknow host [www.google.com](www.google.com)

---

### Post by Raccoon1400 on 2008-06-15
> **kennster said:**
> u mean in Terminal just type ping [www.google.com?](www.google.com?)

it sed ping: unknow host [www.google.com](www.google.com)

no www

```
ping google.com
```

---

### Post by kennster on 2008-06-15
still the same thing just ```
ping unknow host google.com
```

---

### Post by Kronie on 2008-06-15
do you have a router? well it is a laptop so i assume you do.. try restarting it. plug out the power, wait 20 secs, and plug back in. 
also, have you tried restarting the machine? sometimes it helps..

---

### Post by Kronie on 2008-06-15
do you have a router? well it is a laptop so i assume you do.. try restarting it. plug out the power, wait 20 secs, and plug back in. 
also, have you tried restarting the machine? sometimes it helps..

---

### Post by kennster on 2008-06-15
:( no didnt help man /cry i need my computer back i hardly know MAC and thats what im on... its just a pain to use this no right click and all that and i just wana play world of warcarft :D

---

### Post by cariboo on 2008-06-16
It looks like you are having a dns problem as well as other problems How do you connect to the internet?

Jim

---

### Post by kennster on 2008-06-16
> **cariboo907 said:**
> It looks like you are having a dns problem as well as other problems How do you connect to the internet?

Jim

ah from a wireless router a direct wire outta the back of it to my computer

---

### Post by cariboo on 2008-06-16
Have you tried enabling roaming mode. Go to System-->Administrtion-->Network, click unlock and enter your password, click on wired connection, then click the properties button, in the window that comes up click roaming mode in the top left corner then click OK you should see a throbber going back and forth until your network has restarted. Click the close button and give it a try.

Jim

---

### Post by superprash2003 on 2008-06-16
is DHCP enabled in your router or modem? go to system->administration->network and go to eth0 or eth1 properties( whichever is appropriate) and then set it to DHCP)

---

### Post by issih on 2008-06-16
Totally not helpful, but right click on a mac is just hold ctrl and click :).

Definitely would be helpful to know if you can ping your router (You'll need to know its ip address).

If you can, try disabling networking entirely in the networking applet. then in a terminal:

```
sudo ifconfig eth0 up
dhclient eth0 
```

Let us know if that achieves anything, or indeed if dhclient fails to get an address.

---

### Post by kennster on 2008-06-16
> **issih said:**
> Totally not helpful, but right click on a mac is just hold ctrl and click :).

Definitely would be helpful to know if you can ping your router (You'll need to know its ip address).

If you can, try disabling networking entirely in the networking applet. then in a terminal:

```
sudo ifconfig eth0 up
dhclient eth0 
```

Let us know if that achieves anything, or indeed if dhclient fails to get an address.

ok i did that and it ses i cant create and that i dont have permission. i tryed also getting on my router (192.168.1.1 name admin password password or admin right?) but i coudent ... it woudnt let me on and i also enabled roaming on both of them and still nuthing im thinking of maby reinstalling linux if it will work

---

### Post by kennster on 2008-06-16
ok im looking at my wireless router and well there are 4 eathernet slots in the back and i have 2 pluged in (xbox and the ubuntu box) well none of the lights are lighting up for them but the wireless works still... any idea's? about what may have happen and yes i have restarted the routers

---

