---
title: "Firefox fails to download 9.1mb file"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by padnoter on 2013-08-09
Hi,

I'm trying to download this file;

[https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar](https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar)
(same on [http://)](http://))

using ubuntu 12.04 & firefox 23.0
It starts saying it's 9.1mb, downloads a bit (about 1.7mb) and then just finishes saying it is complete - but it isn't.

Same behaviour using chromium.

But, under Windows7 the download completes & is 9.1mb. So I'm assuming it's not my internet connection or laptop (dual boot ubuntu/win7)

Can anyone help? How would I start to debug to try and see what the problem is? Are there restrictions on .jar size downloads in ubuntu?

Thanks

---

### Post by SlugSlug on 2013-08-09
Your drives not full is it?

Post output of 
```
df -h
```

---

### Post by padnoter on 2013-08-09
no not full;;

[FONT=courier new]Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       307G   85G  207G  29% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           1.2G  924K  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.9G     0  2.9G   0% /run/shm
shmfs           2.0G  252K  2.0G   1% /dev/shm

[/FONT]

---

### Post by SlugSlug on 2013-08-09
does wget say anything?

```
wget [https://www.prorealtime.com/java/Pro...0806145815.jar]("https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar")
```

---

### Post by padnoter on 2013-08-09
connection closed...?

[FONT=courier new]wget [https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar](https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar)
--2013-08-09 12:04:19--  [https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar](https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar)
Resolving [www.prorealtime.com](www.prorealtime.com) ([www.prorealtime.com](www.prorealtime.com))... 85.233.201.50
Connecting to [www.prorealtime.com](www.prorealtime.com) ([www.prorealtime.com)|85.233.201.50|:443](www.prorealtime.com)|85.233.201.50|:443)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9556597 (9.1M) [application/java-archive]
Saving to: `ProRealTime-10.1-20130806145815.jar'

17% [============>                                                                ] 1,715,964   17.0K/s   in 59s     

2013-08-09 12:05:19 (28.4 KB/s) - Connection closed at byte 1715964. Retrying.
[/FONT]

---

### Post by SlugSlug on 2013-08-09
is your internet fine?

try run a ping for a min 

ping 8.8.8.8

---

### Post by SlugSlug on 2013-08-09
and does wget always close at the same place? 
[FONT=courier new]Connection closed at byte 1715964[/FONT]

---

### Post by padnoter on 2013-08-09
> **SlugSlug said:**
> is your internet fine?

try run a ping for a min 

ping 8.8.8.8

y i think so (not fast - we're out in the sticks), but the file downloads everytime under win7 without a problem

```
ping output;
[SIZE=1][FONT=courier new]PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=48 time=36.3 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=48 time=35.3 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=48 time=36.0 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=48 time=36.1 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=48 time=35.3 ms
64 bytes from 8.8.8.8: icmp_req=6 ttl=48 time=36.1 ms
64 bytes from 8.8.8.8: icmp_req=7 ttl=48 time=36.3 ms
64 bytes from 8.8.8.8: icmp_req=8 ttl=48 time=34.8 ms
64 bytes from 8.8.8.8: icmp_req=9 ttl=48 time=36.6 ms
64 bytes from 8.8.8.8: icmp_req=10 ttl=48 time=35.3 ms
64 bytes from 8.8.8.8: icmp_req=11 ttl=48 time=36.1 ms
64 bytes from 8.8.8.8: icmp_req=12 ttl=48 time=36.1 ms
64 bytes from 8.8.8.8: icmp_req=13 ttl=48 time=35.1 ms
64 bytes from 8.8.8.8: icmp_req=14 ttl=48 time=35.9 ms
64 bytes from 8.8.8.8: icmp_req=15 ttl=48 time=46.4 ms
64 bytes from 8.8.8.8: icmp_req=16 ttl=48 time=35.2 ms
64 bytes from 8.8.8.8: icmp_req=17 ttl=48 time=36.0 ms
64 bytes from 8.8.8.8: icmp_req=18 ttl=48 time=36.3 ms
64 bytes from 8.8.8.8: icmp_req=19 ttl=48 time=35.3 ms
64 bytes from 8.8.8.8: icmp_req=20 ttl=48 time=35.7 ms
64 bytes from 8.8.8.8: icmp_req=21 ttl=48 time=35.7 ms
64 bytes from 8.8.8.8: icmp_req=22 ttl=48 time=36.3 ms
64 bytes from 8.8.8.8: icmp_req=23 ttl=48 time=36.0 ms
64 bytes from 8.8.8.8: icmp_req=24 ttl=48 time=35.1 ms
64 bytes from 8.8.8.8: icmp_req=25 ttl=48 time=36.0 ms
64 bytes from 8.8.8.8: icmp_req=26 ttl=48 time=36.4 ms
64 bytes from 8.8.8.8: icmp_req=27 ttl=48 time=35.6 ms
64 bytes from 8.8.8.8: icmp_req=28 ttl=48 time=37.0 ms
64 bytes from 8.8.8.8: icmp_req=29 ttl=48 time=36.1 ms
64 bytes from 8.8.8.8: icmp_req=30 ttl=48 time=36.5 ms
64 bytes from 8.8.8.8: icmp_req=31 ttl=48 time=36.6 ms
64 bytes from 8.8.8.8: icmp_req=32 ttl=48 time=35.2 ms
64 bytes from 8.8.8.8: icmp_req=33 ttl=48 time=35.6 ms
64 bytes from 8.8.8.8: icmp_req=34 ttl=48 time=36.3 ms
64 bytes from 8.8.8.8: icmp_req=35 ttl=48 time=36.6 ms
64 bytes from 8.8.8.8: icmp_req=36 ttl=48 time=34.9 ms
64 bytes from 8.8.8.8: icmp_req=37 ttl=48 time=35.8 ms
64 bytes from 8.8.8.8: icmp_req=38 ttl=48 time=36.0 ms
64 bytes from 8.8.8.8: icmp_req=39 ttl=48 time=36.9 ms
64 bytes from 8.8.8.8: icmp_req=40 ttl=48 time=36.0 ms
64 bytes from 8.8.8.8: icmp_req=41 ttl=48 time=35.9 ms
64 bytes from 8.8.8.8: icmp_req=42 ttl=48 time=35.7 ms
64 bytes from 8.8.8.8: icmp_req=43 ttl=48 time=35.0 ms
64 bytes from 8.8.8.8: icmp_req=44 ttl=48 time=35.6 ms
64 bytes from 8.8.8.8: icmp_req=45 ttl=48 time=36.1 ms
64 bytes from 8.8.8.8: icmp_req=46 ttl=48 time=34.6 ms
64 bytes from 8.8.8.8: icmp_req=47 ttl=48 time=36.7 ms
64 bytes from 8.8.8.8: icmp_req=48 ttl=48 time=35.8 ms
64 bytes from 8.8.8.8: icmp_req=49 ttl=48 time=37.1 ms
64 bytes from 8.8.8.8: icmp_req=50 ttl=48 time=37.6 ms
64 bytes from 8.8.8.8: icmp_req=51 ttl=48 time=35.3 ms
64 bytes from 8.8.8.8: icmp_req=52 ttl=48 time=36.3 ms
64 bytes from 8.8.8.8: icmp_req=53 ttl=48 time=36.6 ms
64 bytes from 8.8.8.8: icmp_req=54 ttl=48 time=37.1 ms
64 bytes from 8.8.8.8: icmp_req=55 ttl=48 time=35.6 ms
64 bytes from 8.8.8.8: icmp_req=56 ttl=48 time=35.3 ms
64 bytes from 8.8.8.8: icmp_req=57 ttl=48 time=36.4 ms
64 bytes from 8.8.8.8: icmp_req=58 ttl=48 time=36.6 ms
64 bytes from 8.8.8.8: icmp_req=59 ttl=48 time=34.6 ms
64 bytes from 8.8.8.8: icmp_req=60 ttl=48 time=37.0 ms
64 bytes from 8.8.8.8: icmp_req=61 ttl=48 time=35.9 ms
64 bytes from 8.8.8.8: icmp_req=62 ttl=48 time=34.9 ms
64 bytes from 8.8.8.8: icmp_req=63 ttl=48 time=36.1 ms
64 bytes from 8.8.8.8: icmp_req=64 ttl=48 time=36.8 ms
64 bytes from 8.8.8.8: icmp_req=65 ttl=48 time=37.1 ms
64 bytes from 8.8.8.8: icmp_req=66 ttl=48 time=35.6 ms
64 bytes from 8.8.8.8: icmp_req=67 ttl=48 time=34.6 ms
64 bytes from 8.8.8.8: icmp_req=68 ttl=48 time=35.1 ms
64 bytes from 8.8.8.8: icmp_req=69 ttl=48 time=35.6 ms
64 bytes from 8.8.8.8: icmp_req=70 ttl=48 time=35.6 ms
64 bytes from 8.8.8.8: icmp_req=71 ttl=48 time=35.5 ms
64 bytes from 8.8.8.8: icmp_req=72 ttl=48 time=36.3 ms
64 bytes from 8.8.8.8: icmp_req=73 ttl=48 time=37.1 ms
64 bytes from 8.8.8.8: icmp_req=74 ttl=48 time=35.3 ms
64 bytes from 8.8.8.8: icmp_req=75 ttl=48 time=35.6 ms
64 bytes from 8.8.8.8: icmp_req=76 ttl=48 time=36.1 ms
64 bytes from 8.8.8.8: icmp_req=77 ttl=48 time=34.8 ms
64 bytes from 8.8.8.8: icmp_req=78 ttl=48 time=35.0 ms
[/FONT][/SIZE]^C
--- 8.8.8.8 ping statistics ---
78 packets transmitted, 78 received, 0% packet loss, time 77113ms
rtt min/avg/max/mdev = 34.612/36.080/46.489/1.378 ms
```

[SIZE=1][FONT=courier new]

[/FONT][/SIZE]

---

### Post by padnoter on 2013-08-09
> **SlugSlug said:**
> and does wget always close at the same place? 
[FONT=courier new]Connection closed at byte 1715964[/FONT]

no not always the same point..
the retrying in wget downloads more, but doesn't complete either.. finishes at different points too, here are two ends;
[SIZE=1][FONT=courier new]
47% [+++++++++++++++++++++++++++========>                                         ] 4,570,238   1.27K/s   in 2m 59s  

2013-08-09 12:09:56 (6.25 KB/s) - Read error at byte 4570238/9556597 (Connection reset by peer).



83% [+++++++++++++++++++++++++++++++++++++++++++++++++++++++========>             ] 8,014,336    459B/s   in 6m 58s  

2013-08-09 12:29:49 (2.70 KB/s) - Read error at byte 8014336/9556597 (Connection reset by peer).

[/FONT][/SIZE]
what stumps me is why win7 can do it? btw ubuntu used to be able to download the files... these errors started about 2weeks ago, but have no idea what to check/look at /debug to try and solve??

---

### Post by SlugSlug on 2013-08-09
what about another 10meg or more file?

---

### Post by davetv on 2013-08-09
Flakey Site! Here's what I got on my Debian Wheezy box.


```

davetv@davetv:~$ wget https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar > result.txt
--2013-08-09 22:04:30--  https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar
WARNING: gnome-keyring:: couldn't connect to: /home/davetv/.cache/keyring-8NtN6F/pkcs11: No such file or directory
Resolving www.prorealtime.com (www.prorealtime.com)... 85.233.201.50
Connecting to www.prorealtime.com (www.prorealtime.com)|85.233.201.50|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9556597 (9.1M) [application/java-archive]
Saving to: `ProRealTime-10.1-20130806145815.jar'

35% [============>                          ] 3,366,652   6.24K/s   in 4m 0s   

2013-08-09 22:09:09 (13.7 KB/s) - Read error at byte 3366652/9556597 (A TLS packet with unexpected length was received.). Retrying.

--2013-08-09 22:09:10--  (try: 2)  https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar
Connecting to www.prorealtime.com (www.prorealtime.com)|85.233.201.50|:443... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 9556597 (9.1M), 6189945 (5.9M) remaining [application/java-archive]
Saving to: `ProRealTime-10.1-20130806145815.jar'

71% [+++++++++++++=============>            ] 6,790,589   10.8K/s   in 2m 40s  

2013-08-09 22:12:30 (20.8 KB/s) - Read error at byte 6790589/9556597 (A TLS packet with unexpected length was received.). Retrying.

--2013-08-09 22:12:32--  (try: 3)  https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar
Connecting to www.prorealtime.com (www.prorealtime.com)|85.233.201.50|:443... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 9556597 (9.1M), 2766008 (2.6M) remaining [application/java-archive]
Saving to: `ProRealTime-10.1-20130806145815.jar'

100%[+++++++++++++++++++++++++++===========>] 9,556,597    499K/s   in 9.5s    

2013-08-09 22:12:44 (285 KB/s) - `ProRealTime-10.1-20130806145815.jar' saved [9556597/9556597]

```

---

### Post by padnoter on 2013-08-09
yes that is fine... I just tried uploading the 9.1mb .jar file (downloaded using win7) to another website & then using firefox to download it under ubuntu - fine... and also wget.. fine;

[SIZE=1][FONT=courier new]100%[============================================================================>] 9,556,597   57.6K/s   in 2m 44s  

2013-08-09 13:16:32 (56.8 KB/s) - `ProRealTime-10.1-20130806145815.jar.3' saved [9556597/9556597][/FONT][/SIZE]

hmmm... so why does file fail from prorealtime.com for ubuntu/firefox, but ok for win7/firefox ?

---

### Post by padnoter on 2013-08-09
> **davetv said:**
> Flakey Site! Here's what I got on my Debian Wheezy box.


```

davetv@davetv:~$ wget https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar > result.txt
--2013-08-09 22:04:30--  https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar
WARNING: gnome-keyring:: couldn't connect to: /home/davetv/.cache/keyring-8NtN6F/pkcs11: No such file or directory
Resolving www.prorealtime.com (www.prorealtime.com)... 85.233.201.50
Connecting to www.prorealtime.com (www.prorealtime.com)|85.233.201.50|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9556597 (9.1M) [application/java-archive]
Saving to: `ProRealTime-10.1-20130806145815.jar'

35% [============>                          ] 3,366,652   6.24K/s   in 4m 0s   

2013-08-09 22:09:09 (13.7 KB/s) - Read error at byte 3366652/9556597 (A TLS packet with unexpected length was received.). Retrying.

--2013-08-09 22:09:10--  (try: 2)  https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar
Connecting to www.prorealtime.com (www.prorealtime.com)|85.233.201.50|:443... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 9556597 (9.1M), 6189945 (5.9M) remaining [application/java-archive]
Saving to: `ProRealTime-10.1-20130806145815.jar'

71% [+++++++++++++=============>            ] 6,790,589   10.8K/s   in 2m 40s  

2013-08-09 22:12:30 (20.8 KB/s) - Read error at byte 6790589/9556597 (A TLS packet with unexpected length was received.). Retrying.

--2013-08-09 22:12:32--  (try: 3)  https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar
Connecting to www.prorealtime.com (www.prorealtime.com)|85.233.201.50|:443... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 9556597 (9.1M), 2766008 (2.6M) remaining [application/java-archive]
Saving to: `ProRealTime-10.1-20130806145815.jar'

100%[+++++++++++++++++++++++++++===========>] 9,556,597    499K/s   in 9.5s    

2013-08-09 22:12:44 (285 KB/s) - `ProRealTime-10.1-20130806145815.jar' saved [9556597/9556597]

```


thanks for trying davetv...
but why is it only flaky for ubuntu? win7 always gets the file without problem
:-(

---

### Post by lego11 on 2013-08-09
Hi,
What network card are you using? Could be a driver issue.

---

### Post by _boxed_ksa on 2013-08-09
Try a download manager...

---

### Post by padnoter on 2013-08-10
> **lego11 said:**
> Hi,
What network card are you using? Could be a driver issue.

how do i tell?
it's a dell XPS-702x laptop... the same laptop using win7 downloads the file always

---

### Post by padnoter on 2013-08-10
> **_boxed_ksa said:**
> Try a download manager...

I can't unfortunately, as this .jar is part of a web appl'n I run from prorealtime... the download is kicked off from a .jnlp I download - the whole app fails at the moment - but have pinpointed the problem to this one file
(I have raised a log with prorealtime - but nothing as yet)

---

### Post by The Cog on 2013-08-10
It's a long shot, but I wonder if there is a problem with TCP window scaling. Try this to disabling scaling, then try theo download again:
```
sudo sh -c 'echo 0 > /proc/sys/net/ipv4/tcp_window_scaling'
```
You can re-enable scaling with 
```
sudo sh -c 'echo 1 > /proc/sys/net/ipv4/tcp_window_scaling'
```

---

### Post by Karlchen on 2013-08-10
> **padnoter said:**
> how do i tell?
it's a dell XPS-702x laptop... the same laptop using win7 downloads the file always
Run ```
sudo lshw -C network
```

By the way, there is a nifty little utility which gives a really concise overview of your system: [**inxi**]("http://www.webupd8.org/2009/11/shell-system-information-tool-for-linux.html"). It is a bit sad that it is not included in Ubuntu by default, but only in a mint-coloured Ubuntu based distribution. inxi runs fine on my Precise Pangolin, too. - It can be downloaded [here: inxi_1.8.4-1_all.deb]("ftp://cathbard.com/binary/inxi_1.8.4-1_all.deb")
**inxi -Fx** is one of the shortest commandlines, but one of the most informative ones as well.

Knowing which network adapter is in use and which Linux driver might be helpful in finding out whether you should use a different driver. - Yet, as far as I can tell from this thread so far, it seems a bit as if the problem were caused by the website rather than by your machine.

Karl

---

### Post by coytar on 2013-08-10
padnoter,
Probably doesn't help you but I just tried downloading that link on my system (Ubuntu 12.04 LTS on a VM) using Firefox 23 and it worked first time. No slowdowns, no issues.

---

### Post by Frogs Hair on 2013-08-10
The file download bogs down in Iron browser as well . I reach 1.4 MB and the download just freezes until canceled,

---

### Post by Karlchen on 2013-08-10
Hello, padnoter.

Have just downloaded this 9 MB file, [https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar](https://www.prorealtime.com/java/ProRealTime-10.1-20130806145815.jar), just for fun and to to find out whether the download would complete. It downloaded in no time at all, means less than 45 seconds.
Linux Mint 14 Nadia 32-bit, translates to Ubuntu 12.10 32-bit, Firefox 23, 6 MBit DSL connection (not too impressing I guess).
```
$ inxi -Fx
Network:   Card-1: Atheros AR9285 Wireless Network Adapter (PCI-Express) driver: ath9k bus-ID: 04:00.0
           IF: wlan0 state: up mac: 11:33:dd:bb:55:88
           Card-2: NVIDIA MCP79 Ethernet driver: forcedeth port: d080 bus-ID: 00:0a.0
           IF: eth0 state: down mac: 22:00:ee:22:66:cc
```
This little experiment may suggest either of 2 things:

[LIST]
[*]I have just been lucky. 
[*]The network card and the driver that Ubuntu uses does play a role. 
[/LIST]

Second try finished with the same time, 45 seconds, not 15 (as I initially stated, my mistake). Anyway, I guess I will risk another try in a couple of hours using a different machine having a different network card.

Karl

---

### Post by padnoter on 2013-08-10
> **Karlchen said:**
> Run ```
sudo lshw -C network
```

By .... it seems a bit as if the problem were caused by the website rather than by your machine.

Karl

here's what it give...

[SIZE=1][FONT=courier new]  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 06
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:47 ioport:2000(size=256) memory:f3004000-f3004fff memory:f3000000-f3003fff


[/FONT][/SIZE]

---

### Post by padnoter on 2013-08-10
> **coytar said:**
> padnoter,
Probably doesn't help you but I just tried downloading that link on my system (Ubuntu 12.04 LTS on a VM) using Firefox 23 and it worked first time. No slowdowns, no issues.

Hi,
thanks for trying... with a VM you say - is the base O/S windows? Only wondering as when I boot into win7 i don't have any problems..

---

### Post by padnoter on 2013-08-10
> **The Cog said:**
> It's a long shot, but I wonder if there is a problem with TCP window scaling. Try this to disabling scaling, then try theo download again:
```
sudo sh -c 'echo 0 > /proc/sys/net/ipv4/tcp_window_scaling'
```
You can re-enable scaling with 
```
sudo sh -c 'echo 1 > /proc/sys/net/ipv4/tcp_window_scaling'
```

:popcorn::popcorn::popcorn: :KS:KS

This works for me
:)

Thanks.

and the whole application now runs too... & if I flip back to "reenable scaling" if goes back to stalling & failing..

so this is a solution for me... many thanks TheCog


just wondering what this scaling is and what other effects there will be if I leave it disabled? 
Can anyone enlighten me, I will google it too.
Would you think this is disabled on win7? or is it only ubuntu anyway (I like to know what I've fiddled with)

but very pleased I can now run the appl'n again

---

### Post by The Cog on 2013-08-10
Ooh! Bingo! It really was a wild guess.

From [http://en.wikipedia.org/wiki/TCP_window_scale_option](http://en.wikipedia.org/wiki/TCP_window_scale_option) : To maintain the changes after a restart, include the line ```
net.ipv4.tcp_window_scaling=0
``` in /etc/sysctl.conf.

I think that leaving it disabled will probably not have a noticeable effect. It is supposed to increase the amount of data the far end can send before it has to stop and wait for a confirmation that it has been received. I think I read that some routers have trouble with TCP window scaling, so if you ever change your router, it would be worth trying to enable it again.

---

### Post by padnoter on 2013-08-10
> **The Cog said:**
> Ooh! Bingo! It really was a wild guess.

From [http://en.wikipedia.org/wiki/TCP_window_scale_option](http://en.wikipedia.org/wiki/TCP_window_scale_option) : To maintain the changes after a restart, include the line ```
net.ipv4.tcp_window_scaling=0
``` in /etc/sysctl.conf.

I think that leaving it disabled will probably not have a noticeable effect. It is supposed to increase the amount of data the far end can send before it has to stop and wait for a confirmation that it has been received. I think I read that some routers have trouble with TCP window scaling, so if you ever change your router, it would be worth trying to enable it again.

thanks.. I read the wiki... all a bit double dutch to me, but gathered that it seems to help T1 lines... lol... out in the sticks here I barely get 0.8mb/s broadband.. & my router is ancient (d-link dsl-g604t circa 2005?) so will probably make the change permanent after a bit more testing.

marking SOLVED

---

### Post by Frogs Hair on 2013-08-11
The  link works fine in all browsers today. ?

---

### Post by padnoter on 2013-08-11
> **Frogs Hair said:**
> The  link works fine in all browsers today. ?

yes the file download (& the full prorealtime app) works for me on both Firefox 23 & Chromium 28 with the scaling setting disabled. Without this (i.e scaling enabled), both browsers fail for me. So it's a solution for me. Thanks

---

