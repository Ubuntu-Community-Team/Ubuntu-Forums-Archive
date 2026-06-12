---
title: "cant see  adsl router setup page"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by coolnik6 on 2008-05-31
when i type 192.168.1.1 in address bar i dont get router's page page
in win xp there is no problem
my router is set in pppoe mode n it does all veryfications in win xp so i was hoping the same in ubuntu also but in ubuntu its not working
plzz help me out im trying to connect internet in ubuntu for the past 6 months now but there is no solution no body is able to figure out where is the problem
im using win xp with ubuntu 8.04 lts 
please dont ask me ifconfig i have been giving it for last 6 months but no body is able to detect where is the problem
wat i think is router shud get detect at the first place then everything else will fall in right places
that damn page is just not popping up
 plzz help folks 
the router's LED'S though blink  but ubuntu is not able to open  plzz for god sake give me a solution
my router is starcom ut300r2u im using my router in pppoe mode
so i expect that once i login in to ubuntu i shud be able to straight away surf the firefox but its just not happening damnnnnnnnn

---

### Post by Biggy on 2008-05-31
install [UbuDSL]("http://www.ubudsl.com/")

---

### Post by superprash2003 on 2008-05-31
is your router connected to your pc via usb or LAN? go to System->administration->network and choose your network interface(mostly is eth0) and click on properties.. then select Static IP address (disable roaming mode if selected).. and enter ip address as 192.168.1.4 and gateway as 192.168.1.1

---

### Post by coolnik6 on 2008-06-01
suprash i did as u said still no success

---

### Post by superprash2003 on 2008-06-01
i know this is irritating  :D but please give ifconfig output

---

### Post by londonlad on 2008-06-01
> **coolnik6 said:**
> when i type 192.168.1.1 in address bar i dont get router's page page
in win xp there is no problem
my router is set in pppoe mode n it does all veryfications in win xp so i was hoping the same in ubuntu also but in ubuntu its not working
plzz help me out im trying to connect internet in ubuntu for the past 6 months now but there is no solution no body is able to figure out where is the problem
im using win xp with ubuntu 8.04 lts 
please dont ask me ifconfig i have been giving it for last 6 months but no body is able to detect where is the problem
wat i think is router shud get detect at the first place then everything else will fall in right places
that damn page is just not popping up
 plzz help folks 
the router's LED'S though blink  but ubuntu is not able to open  plzz for god sake give me a solution
my router is starcom ut300r2u im using my router in pppoe mode
so i expect that once i login in to ubuntu i shud be able to straight away surf the firefox but its just not happening damnnnnnnnn

*ah ha, i type in exactly the same address, & i get:

[IMG]http://i164.photobucket.com/albums/u11/simonrogers_video/192.png[/IMG]

mine opens straight away, how very strange, how are you writing it into the address bar?

---

### Post by coolnik6 on 2008-06-02
superprash this is my ifconfig output
plzz help me this, i have taken in roaming mode
because my router does the loging n all for me in win xp so  i expect the same in ubuntu or shud i sleect automatci ie DHCP
u tell me, 

niket@niket-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:44:65:0b:95  
          inet6 addr: fe80::202:44ff:fe65:b95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7436 (7.2 KB)
          Interrupt:16 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:02:44:65:0b:95  
          inet addr:169.254.4.207  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1434 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78168 (76.3 KB)  TX bytes:78168 (76.3 KB)

---

### Post by superprash2003 on 2008-06-02
yes please do use DHCP mode and then post ifconfig.. and while in DHCP mode type ping 192.168.1.1 and see if you are able to ping successfully.. if that doesnt work then try post no 3 of this thread again and type ping 192.168.1.1 in the terminal and check if you are able to ping successfully

---

### Post by coolnik6 on 2008-06-02
this is the o/p after i enabled dhcp in network
and the ping output is in next reply after this
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

### Post by coolnik6 on 2008-06-02
look yaar its not pinging
wat it means it cannot found router??
and i'll post the ping o/p of static ip as per ur third reply after short time

niket@niket-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.4.207 icmp_seq=1 Destination Host Unreachable
From 169.254.4.207 icmp_seq=2 Destination Host Unreachable
From 169.254.4.207 icmp_seq=3 Destination Host Unreachable
From 169.254.4.207 icmp_seq=4 Destination Host Unreachable
From 169.254.4.207 icmp_seq=5 Destination Host Unreachable
From 169.254.4.207 icmp_seq=6 Destination Host Unreachable
From 169.254.4.207 icmp_seq=7 Destination Host Unreachable
From 169.254.4.207 icmp_seq=8 Destination Host Unreachable
From 169.254.4.207 icmp_seq=9 Destination Host Unreachable
From 169.254.4.207 icmp_seq=10 Destination Host Unreachable
From 169.254.4.207 icmp_seq=11 Destination Host Unreachable
From 169.254.4.207 icmp_seq=12 Destination Host Unreachable
From 169.254.4.207 icmp_seq=13 Destination Host Unreachable
From 169.254.4.207 icmp_seq=14 Destination Host Unreachable

---

### Post by Joeb454 on 2008-06-02
It looks like you're not getting an IP address from your router.

How're you connecting to it? Through a wired or wireless connection?

---

### Post by coolnik6 on 2008-06-02
look prash again no results 
i used 192.168.1.14 as ip n 192.168.1.1 ad gateway
is still cannot ping 
n i have also paste the ifconfig in static mode 

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

### Post by coolnik6 on 2008-06-02
hi joeb

im using wired router utstarcom ut300r2u
in pppoe mode 
i dont need to dial a connection 
router does this for me everytime i login in win  xp
i expect the same in ubuntu
but its not happening
n also i have tried bridge mode intially but that also didnt work

---

### Post by coolnik6 on 2008-06-02
its 192.168.1.4 and not 192.168.1.14 
it was a typing mistake

---

### Post by superprash2003 on 2008-06-02
since you say that you use "Automatically Assign ip address" in windows.. that means DHCP is switched on in your router.. now when you set eth0 to DHCP mode in ubuntu.. please reboot your modem and your ubuntu to be on the safe side and you should get an ip address then..do an ifconfig in the terminal after the reboot and see if you are getting any ip address of the form 192.168.1.x in the ifconfig output

---

