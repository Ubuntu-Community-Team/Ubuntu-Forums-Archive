---
title: "No wireless?"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by kdub on 2008-06-03
I've got a Compaq EvoN400c intel 850 mhz,512 ram laptop.
Running kubuntu 7.10. I had been using an Intellinet wireless card.Was working reasonably well from the install and then it just stopped! What should I do?
thanx
kdub

---

### Post by cmnorton on 2008-06-03
This is not a lot of info to go on. 

Find the KNetworkManager icon. If you see your wireless network there, select it, and see if you get connectivity then.

For a few days, I was running 8.04, and had to start my wired network manually, upon booting for the first time. Then, I took my laptop home, and had to do the same for my home's wireless network. 

I am now back on 7.10 Kubuntu, where this problem does not happen, at least for the wired network.

Also, check /var/log/messages and /var/log/syslog to see if there is anything "interesting" there that might give you an idea of what is going on.

---

### Post by kdub on 2008-06-03
CmNorton,
thanx
Yeah I see my router no problem. Just no internet. I also tried 8.04 -I could connect same way you did but 8.04 seemed way to slow on my machine compared to 7.10. What or where is  "/var/log/messages and /var/log/syslog" 
 agian
thanx
kdub

---

### Post by superprash2003 on 2008-06-03
please post your ifconfig and iwconfig output

---

### Post by kdub on 2008-06-04
SuperPrash,
thanx
hers what I got,

kdub@laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0F:A3:41:DE:66
          inet6 addr: fe80::20f:a3ff:fe41:de66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:416 (416.0 b)  TX bytes:230 (230.0 b)

eth0      Link encap:Ethernet  HWaddr 00:D0:59:C5:55:B4
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fec5:55b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28952 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21601257 (20.6 MB)  TX bytes:5167310 (4.9 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8794 (8.5 KB)  TX bytes:8794 (8.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-A3-41-DE-66-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:14178 (13.8 KB)  TX bytes:943 (943.0 b)
          Interrupt:11

kdub@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:D1:25:68
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-43 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

thanx

---

### Post by cmnorton on 2008-06-04
> **kdub said:**
> CmNorton,
thanx
Yeah I see my router no problem. Just no internet. I also tried 8.04 -I could connect same way you did but 8.04 seemed way to slow on my machine compared to 7.10. What or where is  "/var/log/messages and /var/log/syslog" 
 agian
thanx
kdub

These are two of your many logs. You see the most recent entries by

sudo tail /var/log/messages
sudo tail /var/log/syslog

tail can be used with -n to change the default number of lines from 10 to something else.

dmesg may also have some information in it as well.

---

### Post by kdub on 2008-06-04
CmNorton this is what I got

kdub@laptop:~$ sudo tail /var/log/messages
[sudo] password for kdub:
Jun  4 09:07:08 laptop kernel: [168817.064000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:49:21:00:00:40:11:30:85:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:60:01:01:01:06:00:84:d8:c1:89:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=18721 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:17:08 laptop kernel: [169417.156000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:49:87:00:00:40:11:30:1f:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:ff:01:01:06:00:84:d8:c1:8b:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=18823 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:17:29 laptop kernel: [169438.148000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:49:dc:00:00:40:11:2f:ca:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:fd:01:01:06:00:84:d8:c1:8d:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=18908 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:27:08 laptop kernel: [170017.040000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:49:e0:00:00:40:11:2f:c6:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:fb:01:01:06:00:84:d8:c1:8f:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=18912 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:28:08 laptop kernel: [170076.948000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4a:39:00:00:40:11:2f:6d:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:f9:01:01:06:00:84:d8:c1:91:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19001 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:30:08 laptop kernel: [170197.168000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4a:c4:00:00:40:11:2e:e2:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:f7:01:01:06:00:84:d8:c1:93:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19140 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:32:08 laptop kernel: [170317.288000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4b:34:00:00:40:11:2e:72:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:f5:01:01:06:00:84:d8:c1:95:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19252 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:34:08 laptop kernel: [170437.000000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4b:8e:00:00:40:11:2e:18:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:f3:01:01:06:00:84:d8:c1:97:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19342 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:36:08 laptop kernel: [170557.224000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4c:03:00:00:40:11:2d:a3:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:f1:01:01:06:00:84:d8:c1:99:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19459 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:37:08 laptop kernel: [170617.132000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4c:0f:00:00:40:11:2d:97:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:ef:01:01:06:00:84:d8:c1:9b:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19471 PROTO=UDP SPT=68 DPT=67 LEN=308

and this
 kdub@laptop:~$ sudo tail /var/log/syslog
Jun  4 09:17:29 laptop kernel: [169438.148000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:49:dc:00:00:40:11:2f:ca:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:fd:01:01:06:00:84:d8:c1:8d:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=18908 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:27:08 laptop kernel: [170017.040000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:49:e0:00:00:40:11:2f:c6:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:fb:01:01:06:00:84:d8:c1:8f:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=18912 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:28:08 laptop kernel: [170076.948000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4a:39:00:00:40:11:2f:6d:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:f9:01:01:06:00:84:d8:c1:91:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19001 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:30:08 laptop kernel: [170197.168000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4a:c4:00:00:40:11:2e:e2:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:f7:01:01:06:00:84:d8:c1:93:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19140 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:32:08 laptop kernel: [170317.288000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4b:34:00:00:40:11:2e:72:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:f5:01:01:06:00:84:d8:c1:95:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19252 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:34:08 laptop kernel: [170437.000000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4b:8e:00:00:40:11:2e:18:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:f3:01:01:06:00:84:d8:c1:97:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19342 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:36:08 laptop kernel: [170557.224000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4c:03:00:00:40:11:2d:a3:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:f1:01:01:06:00:84:d8:c1:99:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19459 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:37:08 laptop kernel: [170617.132000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4c:0f:00:00:40:11:2d:97:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:ef:01:01:06:00:84:d8:c1:9b:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19471 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:47:08 laptop kernel: [171217.120000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4c:71:00:00:40:11:2d:35:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:ed:01:01:06:00:84:d8:c1:9d:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19569 PROTO=UDP SPT=68 DPT=67 LEN=308
Jun  4 09:47:30 laptop kernel: [171238.932000] Unknown InputIN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:ab:41:03:f4:08:00:45:00:01:48:4c:b8:00:00:40:11:2c:ee:00:00:00:00:ff:ff:ff:ff:00:44:00:43:01:34:5f:eb:01:01:06:00:84:d8:c1:9f:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:17:ab:41:03:f4:00:00:00:00:00:00:00:00:00:00:00:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=19640 PROTO=UDP SPT=68 DPT=67 LEN=308
thanx
kdub

---

### Post by superprash2003 on 2008-06-04
ok.. so you are able to connect to your router.. go to system->administration->network and then go to ath0 properties and set it to say DHCP mode.. and then post ifconfig

---

### Post by kdub on 2008-06-04
SuperPrash2003,
This is what I got:
kdub@laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0F:A3:41:DE:66
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:a3ff:fe41:de66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6254 (6.1 KB)  TX bytes:684 (684.0 b)

eth0      Link encap:Ethernet  HWaddr 00:D0:59:C5:55:B4
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fec5:55b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3083191 (2.9 MB)  TX bytes:600949 (586.8 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:89 (89.0 b)  TX bytes:89 (89.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-A3-41-DE-66-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3773 errors:0 dropped:0 overruns:0 frame:3
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:335996 (328.1 KB)  TX bytes:4825 (4.7 KB)
          Interrupt:11

kdub@laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0F:A3:41:DE:66
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:a3ff:fe41:de66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6254 (6.1 KB)  TX bytes:684 (684.0 b)

eth0      Link encap:Ethernet  HWaddr 00:D0:59:C5:55:B4
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fec5:55b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3083191 (2.9 MB)  TX bytes:600949 (586.8 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:89 (89.0 b)  TX bytes:89 (89.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-A3-41-DE-66-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3773 errors:0 dropped:0 overruns:0 frame:3
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:335996 (328.1 KB)  TX bytes:4825 (4.7 KB)
          Interrupt:11

kdub@laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0F:A3:41:DE:66
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:a3ff:fe41:de66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6254 (6.1 KB)  TX bytes:684 (684.0 b)

eth0      Link encap:Ethernet  HWaddr 00:D0:59:C5:55:B4
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fec5:55b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3083191 (2.9 MB)  TX bytes:600949 (586.8 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:89 (89.0 b)  TX bytes:89 (89.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-A3-41-DE-66-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3773 errors:0 dropped:0 overruns:0 frame:3
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:335996 (328.1 KB)  TX bytes:4825 (4.7 KB)
          Interrupt:11

kdub@laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0F:A3:41:DE:66
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:a3ff:fe41:de66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6254 (6.1 KB)  TX bytes:684 (684.0 b)

eth0      Link encap:Ethernet  HWaddr 00:D0:59:C5:55:B4
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fec5:55b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3083191 (2.9 MB)  TX bytes:600949 (586.8 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:89 (89.0 b)  TX bytes:89 (89.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-A3-41-DE-66-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3773 errors:0 dropped:0 overruns:0 frame:3
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:335996 (328.1 KB)  TX bytes:4825 (4.7 KB)
          Interrupt:11

thanx
kdub

---

### Post by Unix_Slayer on 2008-06-04
If your wired card is plugged in, the wireless won't work. Did you try unplugging the cat5, and trying it?

mgm@GatesOfHell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:30:b3:dd
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:54478318 (51.9 MB)  TX bytes:3279383 (3.1 MB)
          Base address:0x2000 Memory:e7200000-e7220000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:da:93:86
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:e5ff:feda:9386/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8923 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10501036 (10.0 MB)  TX bytes:728225 (711.1 KB)

mgm@GatesOfHell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"@Hell"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:E1:97:2C
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr[:]off   Fragment thr[:]off
          Power Management[:]off
          Link Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by superprash2003 on 2008-06-05
good.. you are one step closer .. now your ath0 is getting an ip 192.168.1.102 .. do you know your router's ip address? please try to ping your router's ip address and post output here.. also type ping google.com and post output.. do this when only connected via wireless not with wired..

---

### Post by kdub on 2008-06-05
SuperPrash,
how do I ping?
kdub

---

### Post by cmnorton on 2008-06-05
at a command line

ping -c 5 192.168.1.102

---

### Post by kdub on 2008-06-05
Ok,I got this:
kdub@laptop:~$ kdub@laptop:~$ ping -c 5 192.168.1.102
bash: kdub@laptop:~$: command not found
kdub@laptop:~$ PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.
bash: syntax error near unexpected token `('
kdub@laptop:~$ 64 bytes from 192.168.1.102: icmp_seq=1 ttl=64 time=0.154 ms
bash: 64: command not found
kdub@laptop:~$ 64 bytes from 192.168.1.102: icmp_seq=2 ttl=64 time=0.138 ms
bash: 64: command not found
kdub@laptop:~$ 64 bytes from 192.168.1.102: icmp_seq=3 ttl=64 time=0.144 ms
bash: 64: command not found
kdub@laptop:~$ 64 bytes from 192.168.1.102: icmp_seq=4 ttl=64 time=0.142 ms
bash: 64: command not found
kdub@laptop:~$ 64 bytes from 192.168.1.102: icmp_seq=5 ttl=64 time=0.138 ms
bash: 64: command not found
kdub@laptop:~$
kdub@laptop:~$ --- 192.168.1.102 ping statistics ---
bash: ---: command not found
kdub@laptop:~$ 5 packets transmitted, 5 received, 0% packet loss, time 3999ms
bash: 5: command not found
kdub@laptop:~$ rtt min/avg/max/mdev = 0.138/0.143/0.154/0.009 ms
bash: rtt: command not found
kdub@laptop:~$ kdub@laptop:~$
bash: kdub@laptop:~$: command not found
kdub@laptop:~$
kdub@laptop:~$     
and this:
Server not found

      

      
      
      

      
        
        

          

Firefox can't find the server at [www.google.com](www.google.com).

        


        
        


    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

   thanx,
kdub

---

### Post by superprash2003 on 2008-06-05
192.168.1.102 is ubuntu's ip address.. but are you able to ping your router's ip address? normally your router's ip address is 192.168.1.1

---

### Post by kdub on 2008-06-05
So,
Now I got this,
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.102 icmp_seq=1 Destination Host Unreachable
From 192.168.1.102 icmp_seq=2 Destination Host Unreachable
From 192.168.1.102 icmp_seq=3 Destination Host Unreachable
From 192.168.1.102 icmp_seq=5 Destination Host Unreachable
From 192.168.1.102 icmp_seq=6 Destination Host Unreachable
From 192.168.1.102 icmp_seq=7 Destination Host Unreachable
From 192.168.1.102 icmp_seq=9 Destination Host Unreachable
From 192.168.1.102 icmp_seq=10 Destination Host Unreachable
From 192.168.1.102 icmp_seq=11 Destination Host Unreachable
From 192.168.1.102 icmp_seq=13 Destination Host Unreachable
From 192.168.1.102 icmp_seq=14 Destination Host Unreachable
From 192.168.1.102 icmp_seq=15 Destination Host Unreachable
From 192.168.1.102 icmp_seq=17 Destination Host Unreachable
From 192.168.1.102 icmp_seq=18 Destination Host Unreachable
From 192.168.1.102 icmp_seq=19 Destination Host Unreachable
From 192.168.1.102 icmp_seq=21 Destination Host Unreachable
From 192.168.1.102 icmp_seq=22 Destination Host Unreachable
From 192.168.1.102 icmp_seq=23 Destination Host Unreachable
From 192.168.1.102 icmp_seq=25 Destination Host Unreachable
From 192.168.1.102 icmp_seq=26 Destination Host Unreachable
From 192.168.1.102 icmp_seq=27 Destination Host Unreachable
From 192.168.1.102 icmp_seq=29 Destination Host Unreachable
and so on and so on
thanx
kdub

---

### Post by kdub on 2008-06-07
what if I repartition my drive to give this install a min of space,reinstall kubuntu in the new larger partition,wireless should work in that partition-and then move my info to the new install and get rid of the old partition? Do able?
kdub

---

