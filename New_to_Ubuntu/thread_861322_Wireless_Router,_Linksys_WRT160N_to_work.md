---
title: "Wireless Router, Linksys WRT160N to work"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by impkind on 2008-07-16
I am running Gusty on our family PC (Sony vgc-ra810g). We had to purchase a new wireless router since our old one no longer works. My pro-windows husband purchased the Linksys WRT160N, and hooked it up while I was away for the day. Of course it didn't work out (the cd it comes with is MS/Mac only). Once again we have technical strife under our roof since my change of OS. He's complained of Linux, and I called him stubborn/lazy... in so-many words. 

So, before I seriously consider to implement my evil idea of changing his two laptop OS's to Linux while he is at work :twisted:; could someone kindly walk this very green newbie through getting Gusty to even recognize our now back-in-the-box, brand new router, so we can once again safely live with our technical peace agreement? I have already scoured the forum and partially the internet regarding this issue, but couldn't find something that I could follow with success. Thank-you.

---

### Post by halitech on 2008-07-16
as long as you didn't change anything in your computer it should still work. Are you using wireless or wired connection to your computer?

---

### Post by impkind on 2008-07-16
Wired connection to my computer.

---

### Post by halitech on 2008-07-16
when you were using the old router, did you have a static IP address or were you using DHCP?

---

### Post by impkind on 2008-07-16
I seriously believe it was DHCP; yet I could be very wrong

---

### Post by halitech on 2008-07-16
okay, 2 steps for you here.

1. check the router documentation for the IP adress of the router

2. open a terminal and type 
```
ifconfig
```

see if they match. if not, you may have a static ip address and just need to change it (or set it back to DHCP) to get back online.

edit: sorry, they shouldn't completely match but they should be the same for the first 3 octets (IE. 192.168.1.xxx)

---

### Post by impkind on 2008-07-16
Alright here is what I got. 

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2F:0D:E9:19  
          inet addr:61.213.185.179  Bcast:61.213.185.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe0d:e919/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:95178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:51882029 (49.4 MB)  TX bytes:10438359 (9.9 MB)
          Base address:0xcc00 Memory:dfec0000-dfee0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


The router's default IP is 192.168.1.1. I am going to tackel this problem when it is not 02:44 in the morning. I truly thank you for your help, and will use it after about 6hr of sleep.

---

### Post by halitech on 2008-07-16
ok, here is the problem

```

eth0 Link encap:Ethernet HWaddr 00:11:2F:0D:E9:19
[COLOR="Red"]inet addr:61.213.185.179 Bcast:61.213.185.255 Mask:255.255.255.0[/COLOR]
inet6 addr: fe80::211:2fff:fe0d:e919/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:95178 errors:0 dropped:0 overruns:0 frame:0
TX packets:42636 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:51882029 (49.4 MB) TX bytes:10438359 (9.9 MB)
Base address:0xcc00 Memory:dfec0000-dfee0000 

```

your computer has a different IP address. try a reboot (if you haven't already) and if not, open a terminal and run
```
gksu gedit /etc/network/interfaces
```
and see if it is indicating a static or dynamic ip address

sleep well and good luck

---

