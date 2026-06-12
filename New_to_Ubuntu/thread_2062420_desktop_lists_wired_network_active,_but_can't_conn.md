---
title: "desktop lists wired network active, but can't connect to internet"
date: 2012-09-24
forum: New to Ubuntu
---

### Post by SummerT on 2012-09-24
I had posted this in networking, but because I am really new and not great at fully understanding all the code, I wanted to repost here to see about answers that might be a little less technical.
 
This is my first time posting and very confused. My old PC had a motherboard problem, so I placed my hard drive into another similar model desktop PC. However I started having trouble connecting to the internet. Kept coming up that the connection was active but dns server not found (or firefox server not found... something like that). Thought it might be RAM problems or old ubuntu issues, so we reinstalled with an ubuntu disk the 11.10 version - wiping the hard drive.
 
We started coming up with a series of different types of errors as my partner (who is more adept at linux than I) tried entering different code strings to try and get this to work. The errors ranged from 
"failed to fetch...something wicked happened resolving... no address associated with host name" 
to "[SIZE=3][FONT=Arial]squash error unable to read fragment cashe entry [/FONT][/SIZE][SIZE=3][FONT=Arial]unable to read page[/FONT][/SIZE][SIZE=3][FONT=Arial]…. Page block 24b1475, ae2d" [/FONT][/SIZE]
[SIZE=3][FONT=Arial]to "Running /etc/init.d/networking restart is depreciated because it may not enable some interfaces. Reconfiguring network interfaces" [/FONT][/SIZE]
 
[SIZE=3][FONT=Arial]All the while, we still can't connect to the internet although the wired connection says that we are active. (I'm typing from another computer and relaying responses I find from the net to my partner on the phone with the problem computer).[/FONT][/SIZE]

[SIZE=3][FONT=Arial]We are connected manually. But we really want it to come up automatically as: Automatic dhcp.[/FONT][/SIZE]
[SIZE=3][FONT=Arial]We used the ipv4 and put the ip address in and submask in, clicked “ignored”, it says eth0, says driver 3c59x. [/FONT][/SIZE]
 
[SIZE=3][FONT=Arial]We did an iconfig and the code below is what came up (some of the numbers were changed slightly for privacy).[/FONT][/SIZE]
 
[SIZE=3][FONT=Arial]it seems a lot of posts here refer to wireless connections as opposed to wired. [/FONT][/SIZE]

[SIZE=3][FONT=Arial]Please help and if you can explain in not so technical terms it would be extremely appreciated (sorry, I'm trying) :(. Thanks to all. [/FONT][/SIZE]
 
 
```
eth0 Link encap; Ethernet HWaddr 90:fb:ab:e2:2a:cd
inet addr:127.0.0.1
bcast: 158.255.255.255 mask: 255.0.0.0
inet6addr: du70::3b0:M0ff:gidc:7029/62
scope:link
UP BROADCAST MULTICAST MTU:1500 metric:1
RX packets:6 errors:10 dropped:0 overruns:15 frame:0
TX packets:48 errors:0 dropped:0 overruns:8 carrier:0
collisions:0 txqueuelen:1000
RX bytes:420(420.0 B) TX bytes:9591(9.5kb)
Interrupt:11. Base address: 0xec00
 
 
lo Link encap: Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:384 errors:0 dropped:0 overruns:0 frame:0
TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:289440(28.9kb) TX bytes:289440(28.9kb)
```

---

