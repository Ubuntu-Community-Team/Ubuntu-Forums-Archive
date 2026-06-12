---
title: "Kubuntu internet problems"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by RickDJ on 2008-09-29
I have recently bit the bullet and wiped my HD and installed linux kubuntu KDE4, all installed ok. but will not connect to the internet.
 i have successfully pinged google and there is a live ethernet connection running into the laptop.
 When searching for google in konqueror it reports... 'contacted google, waiting for reply...' and hangs there untill it times out.
 I have searched many linux forums... no joy! Has anyone done a successfull clean linux install (not dual boot) ?
 
 ANY information will be much appreciated!

---

### Post by Crafty Kisses on 2008-09-29
I'd like to see the results of the following commands:
```
ifconfig
ping google.com
```

---

### Post by RickDJ on 2008-09-29
eth0      Link encap:Ethernet  HWaddr 00:1e:68:3f:ec:4a
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe3f:ec4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1320  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:988 (988.0 B)  TX bytes:5978 (5.8 KB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:06:23:ca
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-06-23-CA-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by RickDJ on 2008-09-29
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=240 time=116 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=240 time=116 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=240 time=117 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=4 ttl=240 time=112 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=5 ttl=240 time=113 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=6 ttl=240 time=115 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=7 ttl=240 time=232 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=8 ttl=240 time=114 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=9 ttl=240 time=115 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=10 ttl=240 time=118 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=11 ttl=240 time=125 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=12 ttl=240 time=221 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=13 ttl=240 time=340 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=14 ttl=240 time=478 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=15 ttl=240 time=117 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=16 ttl=240 time=112 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=17 ttl=240 time=117 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=18 ttl=240 time=129 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=19 ttl=240 time=118 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=20 ttl=240 time=230 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=21 ttl=240 time=112 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=22 ttl=240 time=114 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=23 ttl=240 time=114 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=24 ttl=240 time=211 ms


continuous.....

I was told to install firefox and use that as an internet browser instead of konqueror. 
i tried doing so and reached another hurdle.... i had to download firefox from another computer and transfer the file to my laptop and try installing firefox that way.. [problem] not sure how to load the file ( tar.bz2 file )
or should i just forget bout that idea?

---

### Post by tangibleorange on 2008-09-29
> **RickDJ said:**
> PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=240 time=116 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=240 time=116 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=240 time=117 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=4 ttl=240 time=112 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=5 ttl=240 time=113 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=6 ttl=240 time=115 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=7 ttl=240 time=232 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=8 ttl=240 time=114 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=9 ttl=240 time=115 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=10 ttl=240 time=118 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=11 ttl=240 time=125 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=12 ttl=240 time=221 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=13 ttl=240 time=340 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=14 ttl=240 time=478 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=15 ttl=240 time=117 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=16 ttl=240 time=112 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=17 ttl=240 time=117 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=18 ttl=240 time=129 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=19 ttl=240 time=118 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=20 ttl=240 time=230 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=21 ttl=240 time=112 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=22 ttl=240 time=114 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=23 ttl=240 time=114 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=24 ttl=240 time=211 ms


continuous.....

I was told to install firefox and use that as an internet browser instead of konqueror. not sure if this will work...?

what happens if you run this command:

```
sudo apt-get update
```

---

### Post by lapubell on 2008-09-29
you might want to install opera instead.  firefox is what I use, but it is based on GTK libraries, which will be heavier on your ram.  opera is based on QT so it will use the same libs as your KDE4 desktop (go KDE!  it's my favorite too, but I am still with the 3.5 branch)

opera isn't open source, but is free and is a great browser.  they have ubuntu packages at their website and it is a breeze to install.

[http://www.opera.com/download/linux/](http://www.opera.com/download/linux/)

---

### Post by RickDJ on 2008-09-29
To Tangibleorange: below is a sample of the update process in terminal after the command you gave me.

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
  Connection failed
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources


The network card appears to be sending and receiving bytes and the ethernet light is constantly flickering... im going to let the process carry on unless u tell me otherwise.

many thanks.

lapubell: thanks for the opera info.

---

### Post by RickDJ on 2008-09-29
The following is only the end part of the whole document after the updates had finished....! any ideas? because this didnt work.

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz)  Connection failed

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  Connection failed

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  Connection failed

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  Connection failed

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  Connection failed

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  Connection failed

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  Connection failed

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by nowshining on 2008-09-29
open up a terminal - cd Desktop/

then tar -xf nameoftarfile and hit enter

move the now untared folder into your home folder or wherever u want it,

then run sh /home/username/firefox or whereve the mail firefox script is, u may have to manually create a menu item.. :)

---

