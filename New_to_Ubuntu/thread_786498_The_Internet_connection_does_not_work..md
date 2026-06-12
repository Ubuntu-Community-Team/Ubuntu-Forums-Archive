---
title: "The Internet connection does not work."
date: 2008-05-08
forum: New to Ubuntu
---

### Post by philipsone on 2008-05-08
**The Internet connection does not work.**

I have installed Ubuntu 6.06 on a thirteen years old Toshiba Satellite laptop with 256kb ram.

There is a Network Connection: eth0 to the ADSL router. Firefox can access the router admin at 192.168.1.1

BUT Firefox (or Evolution) cannot connect to the internet. The Toshiba can see another computer connected to the router and the other computer connected to the router and on the network continues to connect to the internet as usual.

Can anyone please help me to get the internet connected?

Thanks.

---

### Post by superprash2003 on 2008-05-08
please go to the terminal and type ping google.com and post output here

---

### Post by brigux on 2008-05-08
additonaly, please post here the result of

ifconfig -a

netstat -na

cat /etc/resolv.conf

---

### Post by philipsone on 2008-05-08
ian@MonOldTosh:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:39:12:56:3B
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe12:563b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:148180 (144.7 KiB)  TX bytes:60811 (59.3 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:772 (772.0 b)  TX bytes:772 (772.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ian@MonOldTosh:~$ netstat -na
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:43465         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:52927         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:43465         127.0.0.1:47683         ESTABLISHED
tcp        0      0 127.0.0.1:47683         127.0.0.1:43465         ESTABLISHED
udp        0      0 0.0.0.0:68              0.0.0.0:*
raw        0      0 0.0.0.0:1               0.0.0.0:*               7
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path
unix  3      [ ]         DGRAM                    13323    /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     10655    /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     12245    /tmp/mapping-ian
unix  2      [ ]         DGRAM                    4964     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     10881    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     10959    @/tmp/hald-runner/dbus-tBOGJeYr4Q
unix  2      [ ACC ]     STREAM     LISTENING     11800    @/tmp/dbus-4iKcgVtFAtunix  2      [ ]         DGRAM                    10967    @/org/freedesktop/hal/udev_event
unix  2      [ ACC ]     STREAM     LISTENING     11420    /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     9632     /var/run/acpid.socketunix  2      [ ACC ]     STREAM     LISTENING     10935    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     10723    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     11795    /tmp/ssh-EKrbFZ4857/agent.4857
unix  2      [ ACC ]     STREAM     LISTENING     11819    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  2      [ ACC ]     STREAM     LISTENING     11830    /tmp/orbit-ian/linc-12f9-0-15d0a1e14a18a
unix  2      [ ACC ]     STREAM     LISTENING     10958    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  2      [ ACC ]     STREAM     LISTENING     11853    /tmp/.ICE-unix/4857
unix  2      [ ACC ]     STREAM     LISTENING     11863    /tmp/keyring-nL3eUd/socket
unix  2      [ ACC ]     STREAM     LISTENING     11876    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  2      [ ACC ]     STREAM     LISTENING     11905    /tmp/.esd-1000/socketunix  2      [ ACC ]     STREAM     LISTENING     11916    /tmp/orbit-ian/linc-1330-0-2feae26567812
unix  2      [ ACC ]     STREAM     LISTENING     11949    /tmp/orbit-ian/linc-133b-0-43c9cb9f27a0d
unix  2      [ ACC ]     STREAM     LISTENING     11978    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  2      [ ACC ]     STREAM     LISTENING     12007    /tmp/orbit-ian/linc-1345-0-4546456775bf9
unix  2      [ ACC ]     STREAM     LISTENING     12017    /tmp/orbit-ian/linc-1343-0-45464567872a1
unix  2      [ ACC ]     STREAM     LISTENING     12057    /tmp/orbit-ian/linc-134c-0-3345e5c77184c
unix  2      [ ACC ]     STREAM     LISTENING     12102    /tmp/orbit-ian/linc-134e-0-3345e5c62660b
unix  2      [ ACC ]     STREAM     LISTENING     12120    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  2      [ ACC ]     STREAM     LISTENING     12142    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  2      [ ACC ]     STREAM     LISTENING     12154    /tmp/orbit-ian/linc-1352-0-6099eaace1a76
unix  2      [ ACC ]     STREAM     LISTENING     12273    /tmp/orbit-ian/linc-1378-0-689c7fb24878
unix  2      [ ACC ]     STREAM     LISTENING     12290    /tmp/orbit-ian/linc-137b-0-689c7fb4feec
unix  2      [ ACC ]     STREAM     LISTENING     12395    /tmp/orbit-ian/linc-1376-0-61d60bc7c6e8f
unix  2      [ ACC ]     STREAM     LISTENING     12455    /tmp/orbit-ian/linc-1391-0-4ee32b326fac
unix  2      [ ACC ]     STREAM     LISTENING     12569    /tmp/orbit-ian/linc-13b7-0-5eca89d0a330b
unix  2      [ ACC ]     STREAM     LISTENING     20963    /tmp/orbit-ian/linc-34b2-0-448202b8cd104
unix  3      [ ]         STREAM     CONNECTED     20976
unix  3      [ ]         STREAM     CONNECTED     20975
unix  3      [ ]         STREAM     CONNECTED     20973    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     20972
unix  3      [ ]         STREAM     CONNECTED     20970    /tmp/orbit-ian/linc-34b2-0-448202b8cd104
unix  3      [ ]         STREAM     CONNECTED     20969
unix  3      [ ]         STREAM     CONNECTED     20968    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     20967
unix  3      [ ]         STREAM     CONNECTED     20966    /tmp/orbit-ian/linc-34b2-0-448202b8cd104
unix  3      [ ]         STREAM     CONNECTED     20965
unix  3      [ ]         STREAM     CONNECTED     20962    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     20961
unix  3      [ ]         STREAM     CONNECTED     20958    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     20957
unix  3      [ ]         STREAM     CONNECTED     20953    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20952
unix  2      [ ]         DGRAM                    16362
unix  3      [ ]         STREAM     CONNECTED     12572    /tmp/orbit-ian/linc-13b7-0-5eca89d0a330b
unix  3      [ ]         STREAM     CONNECTED     12571
unix  3      [ ]         STREAM     CONNECTED     12568    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12567
unix  3      [ ]         STREAM     CONNECTED     12553    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12552
unix  3      [ ]         STREAM     CONNECTED     12462    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12461
unix  3      [ ]         STREAM     CONNECTED     12460    @/tmp/dbus-4iKcgVtFAtunix  3      [ ]         STREAM     CONNECTED     12459
unix  3      [ ]         STREAM     CONNECTED     12458    /tmp/orbit-ian/linc-1391-0-4ee32b326fac
unix  3      [ ]         STREAM     CONNECTED     12457
unix  3      [ ]         STREAM     CONNECTED     12454    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12453
unix  3      [ ]         STREAM     CONNECTED     12449    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12448
unix  3      [ ]         STREAM     CONNECTED     12433    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12432
unix  3      [ ]         STREAM     CONNECTED     12431    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12430
unix  3      [ ]         STREAM     CONNECTED     12429    /tmp/orbit-ian/linc-1376-0-61d60bc7c6e8f
unix  3      [ ]         STREAM     CONNECTED     12428
unix  3      [ ]         STREAM     CONNECTED     12423    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12422
unix  3      [ ]         STREAM     CONNECTED     12419    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12418
unix  3      [ ]         STREAM     CONNECTED     12417    /tmp/orbit-ian/linc-1378-0-689c7fb24878
unix  3      [ ]         STREAM     CONNECTED     12416
unix  3      [ ]         STREAM     CONNECTED     12407    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12406
unix  3      [ ]         STREAM     CONNECTED     12404    /tmp/orbit-ian/linc-1330-0-2feae26567812
unix  3      [ ]         STREAM     CONNECTED     12403
unix  3      [ ]         STREAM     CONNECTED     12402    /tmp/orbit-ian/linc-1376-0-61d60bc7c6e8f
unix  3      [ ]         STREAM     CONNECTED     12401
unix  3      [ ]         STREAM     CONNECTED     12400    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12399
unix  3      [ ]         STREAM     CONNECTED     12398    /tmp/orbit-ian/linc-1376-0-61d60bc7c6e8f
unix  3      [ ]         STREAM     CONNECTED     12397
unix  3      [ ]         STREAM     CONNECTED     12394    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12393
unix  3      [ ]         STREAM     CONNECTED     12389    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12388
unix  3      [ ]         STREAM     CONNECTED     12324    /tmp/orbit-ian/linc-1330-0-2feae26567812
unix  3      [ ]         STREAM     CONNECTED     12323
unix  3      [ ]         STREAM     CONNECTED     12322    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12321
unix  3      [ ]         STREAM     CONNECTED     12319    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12318
unix  3      [ ]         STREAM     CONNECTED     12317    /tmp/orbit-ian/linc-137b-0-689c7fb4feec
unix  3      [ ]         STREAM     CONNECTED     12316
unix  3      [ ]         STREAM     CONNECTED     12310    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12309
unix  3      [ ]         STREAM     CONNECTED     12307    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12306
unix  3      [ ]         STREAM     CONNECTED     12297    /tmp/orbit-ian/linc-137b-0-689c7fb4feec
unix  3      [ ]         STREAM     CONNECTED     12296
unix  3      [ ]         STREAM     CONNECTED     12295    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12294
unix  3      [ ]         STREAM     CONNECTED     12293    /tmp/orbit-ian/linc-137b-0-689c7fb4feec
unix  3      [ ]         STREAM     CONNECTED     12292
unix  3      [ ]         STREAM     CONNECTED     12289    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12288
unix  3      [ ]         STREAM     CONNECTED     12284    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12283
unix  3      [ ]         STREAM     CONNECTED     12280    /tmp/orbit-ian/linc-1378-0-689c7fb24878
unix  3      [ ]         STREAM     CONNECTED     12279
unix  3      [ ]         STREAM     CONNECTED     12278    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12277
unix  3      [ ]         STREAM     CONNECTED     12276    /tmp/orbit-ian/linc-1378-0-689c7fb24878
unix  3      [ ]         STREAM     CONNECTED     12275
unix  3      [ ]         STREAM     CONNECTED     12272    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12271
unix  3      [ ]         STREAM     CONNECTED     12267    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12266
unix  3      [ ]         STREAM     CONNECTED     12249    /tmp/mapping-ian
unix  3      [ ]         STREAM     CONNECTED     12241
unix  3      [ ]         STREAM     CONNECTED     12210    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12209
unix  3      [ ]         STREAM     CONNECTED     12208    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12207
unix  3      [ ]         STREAM     CONNECTED     12200    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12199
unix  3      [ ]         STREAM     CONNECTED     12196    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12195
unix  3      [ ]         STREAM     CONNECTED     12194    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  3      [ ]         STREAM     CONNECTED     12193
unix  3      [ ]         STREAM     CONNECTED     12186    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  3      [ ]         STREAM     CONNECTED     12185
unix  3      [ ]         STREAM     CONNECTED     12184    /tmp/orbit-ian/linc-1343-0-45464567872a1
unix  3      [ ]         STREAM     CONNECTED     12183
unix  3      [ ]         STREAM     CONNECTED     12182    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12180
unix  3      [ ]         STREAM     CONNECTED     12181    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12176
unix  3      [ ]         STREAM     CONNECTED     12173    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12172
unix  3      [ ]         STREAM     CONNECTED     12171    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12170
unix  3      [ ]         STREAM     CONNECTED     12163    /var/run/cups/cups.sock
unix  3      [ ]         STREAM     CONNECTED     12162
unix  3      [ ]         STREAM     CONNECTED     12161    /tmp/orbit-ian/linc-1352-0-6099eaace1a76
unix  3      [ ]         STREAM     CONNECTED     12160
unix  3      [ ]         STREAM     CONNECTED     12159    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12158
unix  3      [ ]         STREAM     CONNECTED     12157    /tmp/orbit-ian/linc-1352-0-6099eaace1a76
unix  3      [ ]         STREAM     CONNECTED     12156
unix  3      [ ]         STREAM     CONNECTED     12153    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12152
unix  3      [ ]         STREAM     CONNECTED     12149    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12148
unix  3      [ ]         STREAM     CONNECTED     12147    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12146
unix  3      [ ]         STREAM     CONNECTED     12145    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12144
unix  3      [ ]         STREAM     CONNECTED     12138    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12137
unix  3      [ ]         STREAM     CONNECTED     12134    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12133
unix  3      [ ]         STREAM     CONNECTED     12127    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  3      [ ]         STREAM     CONNECTED     12126
unix  3      [ ]         STREAM     CONNECTED     12125    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12124
unix  3      [ ]         STREAM     CONNECTED     12123    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  3      [ ]         STREAM     CONNECTED     12122
unix  3      [ ]         STREAM     CONNECTED     12119    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12118
unix  3      [ ]         STREAM     CONNECTED     12114    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12113
unix  3      [ ]         STREAM     CONNECTED     12110    @/tmp/dbus-4iKcgVtFAtunix  3      [ ]         STREAM     CONNECTED     12109
unix  3      [ ]         STREAM     CONNECTED     12108    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12107
unix  2      [ ]         DGRAM                    12106
unix  3      [ ]         STREAM     CONNECTED     12105    /tmp/orbit-ian/linc-134e-0-3345e5c62660b
unix  3      [ ]         STREAM     CONNECTED     12104
unix  3      [ ]         STREAM     CONNECTED     12101    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12100
unix  3      [ ]         STREAM     CONNECTED     12094    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12093
unix  3      [ ]         STREAM     CONNECTED     12086    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12085
unix  3      [ ]         STREAM     CONNECTED     12082    /tmp/orbit-ian/linc-1343-0-45464567872a1
unix  3      [ ]         STREAM     CONNECTED     12074
unix  3      [ ]         STREAM     CONNECTED     12073    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12072
unix  3      [ ]         STREAM     CONNECTED     12067    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12066
unix  3      [ ]         STREAM     CONNECTED     12062    @/tmp/dbus-4iKcgVtFAtunix  3      [ ]         STREAM     CONNECTED     12061
unix  3      [ ]         STREAM     CONNECTED     12060    /tmp/orbit-ian/linc-134c-0-3345e5c77184c
unix  3      [ ]         STREAM     CONNECTED     12059
unix  3      [ ]         STREAM     CONNECTED     12056    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12055
unix  3      [ ]         STREAM     CONNECTED     12052    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12049
unix  3      [ ]         STREAM     CONNECTED     12045    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12044
unix  3      [ ]         STREAM     CONNECTED     12031    @/tmp/dbus-4iKcgVtFAtunix  3      [ ]         STREAM     CONNECTED     12030
unix  3      [ ]         STREAM     CONNECTED     12026    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12025
unix  3      [ ]         STREAM     CONNECTED     12023    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12022
unix  3      [ ]         STREAM     CONNECTED     12020    /tmp/orbit-ian/linc-1343-0-45464567872a1
unix  3      [ ]         STREAM     CONNECTED     12019
unix  3      [ ]         STREAM     CONNECTED     12016    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12015
unix  3      [ ]         STREAM     CONNECTED     12012    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12011
unix  3      [ ]         STREAM     CONNECTED     12010    /tmp/orbit-ian/linc-1345-0-4546456775bf9
unix  3      [ ]         STREAM     CONNECTED     12009
unix  3      [ ]         STREAM     CONNECTED     12006    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12005
unix  3      [ ]         STREAM     CONNECTED     12002    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12001
unix  3      [ ]         STREAM     CONNECTED     11997    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11996
unix  3      [ ]         STREAM     CONNECTED     11990    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11989
unix  3      [ ]         STREAM     CONNECTED     11985    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     11984
unix  3      [ ]         STREAM     CONNECTED     11983    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     11982
unix  3      [ ]         STREAM     CONNECTED     11981    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     11980
unix  3      [ ]         STREAM     CONNECTED     11977    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     11976
unix  3      [ ]         STREAM     CONNECTED     11973    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     11970
unix  3      [ ]         STREAM     CONNECTED     11964    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11963
unix  3      [ ]         STREAM     CONNECTED     11956    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     11955
unix  3      [ ]         STREAM     CONNECTED     11954    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11953
unix  3      [ ]         STREAM     CONNECTED     11952    /tmp/orbit-ian/linc-133b-0-43c9cb9f27a0d
unix  3      [ ]         STREAM     CONNECTED     11951
unix  3      [ ]         STREAM     CONNECTED     11948    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     11947
unix  3      [ ]         STREAM     CONNECTED     11919    /tmp/orbit-ian/linc-1330-0-2feae26567812
unix  3      [ ]         STREAM     CONNECTED     11918
unix  3      [ ]         STREAM     CONNECTED     11915    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     11914
unix  3      [ ]         STREAM     CONNECTED     11912    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     11910
unix  2      [ ]         STREAM                   11904
unix  3      [ ]         STREAM     CONNECTED     11894    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11893
unix  3      [ ]         STREAM     CONNECTED     11882    /tmp/orbit-ian/linc-12f9-0-15d0a1e14a18a
unix  3      [ ]         STREAM     CONNECTED     11881
unix  3      [ ]         STREAM     CONNECTED     11880    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     11879
unix  3      [ ]         STREAM     CONNECTED     11834    /tmp/orbit-ian/linc-12f9-0-15d0a1e14a18a
unix  3      [ ]         STREAM     CONNECTED     11833
unix  3      [ ]         STREAM     CONNECTED     11832    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     11829
unix  2      [ ]         DGRAM                    11814
unix  3      [ ]         STREAM     CONNECTED     11808    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11807
unix  3      [ ]         STREAM     CONNECTED     11804    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11803
unix  3      [ ]         STREAM     CONNECTED     11802
unix  3      [ ]         STREAM     CONNECTED     11801
unix  3      [ ]         STREAM     CONNECTED     11417    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11412
unix  2      [ ]         DGRAM                    11409
unix  2      [ ]         DGRAM                    11390
unix  3      [ ]         STREAM     CONNECTED     11281    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11280
unix  3      [ ]         STREAM     CONNECTED     11263    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  3      [ ]         STREAM     CONNECTED     11261
unix  3      [ ]         STREAM     CONNECTED     11262    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  3      [ ]         STREAM     CONNECTED     11255
unix  3      [ ]         STREAM     CONNECTED     11211    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  3      [ ]         STREAM     CONNECTED     11206
unix  3      [ ]         STREAM     CONNECTED     11085    /var/run/acpid.socketunix  3      [ ]         STREAM     CONNECTED     11084
unix  3      [ ]         STREAM     CONNECTED     11089    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  3      [ ]         STREAM     CONNECTED     11079
unix  3      [ ]         STREAM     CONNECTED     10962    @/tmp/hald-runner/dbus-tBOGJeYr4Q
unix  3      [ ]         STREAM     CONNECTED     10961
unix  3      [ ]         STREAM     CONNECTED     10938
unix  3      [ ]         STREAM     CONNECTED     10937
unix  2      [ ]         DGRAM                    10758
unix  4      [ ]         STREAM     CONNECTED     10892    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10732
unix  2      [ ]         DGRAM                    9833
ian@MonOldTosh:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
ian@MonOldTosh:~$ ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.

---

### Post by superprash2003 on 2008-05-08
i suggest you change your DNS server to opendns.. go here [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Nxion on 2008-05-08
When you run "ping google.com" What happens? Does it return anything or just sit there doing nothing?

---

### Post by hyper_ch on 2008-05-08
It might also be a IPv6 issue there. try to disable that.

---

### Post by philipsone on 2008-05-08
Re: The Internet connection does not work.
When you run "ping google.com" What happens? Does it return anything or just sit there doing nothing?
__________________
"Let's be bad guys." - Jane Cobb (Firefly)

It sits there doing nothing

---

### Post by brigux on 2008-05-08
how many threads did you open on this subject.. anyway I'm answering on the other one..
[http://ubuntuforums.org/showthread.php?t=786543](http://ubuntuforums.org/showthread.php?t=786543)

---

### Post by Nxion on 2008-05-08
Do:

```
sudo /etc/init.d/networking restart
```

Any change?

---

### Post by philipsone on 2008-05-08
> **Nxion said:**
> Do:

```
sudo /etc/init.d/networking restart
```

Any change?
ian@MonOldTosh:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:00:39:12:56:3b
Sending on   LPF/eth0/00:00:39:12:56:3b
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:00:39:12:56:3b
Sending on   LPF/eth0/00:00:39:12:56:3b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.4 -- renewal in 1573 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]
ian@MonOldTosh:~$

---

### Post by philipsone on 2008-05-08
> **superprash2003 said:**
> i suggest you change your DNS server to opendns.. go here [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)
Thanks but I don't know what this means or how I could reverse it.

---

### Post by philipsone on 2008-05-08
> **hyper_ch said:**
> It might also be a IPv6 issue there. try to disable that.
Sorry I do not know what this is or where I find it ?

---

### Post by Nxion on 2008-05-08
> **philipsone said:**
> ian@MonOldTosh:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:00:39:12:56:3b
Sending on   LPF/eth0/00:00:39:12:56:3b
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:00:39:12:56:3b
Sending on   LPF/eth0/00:00:39:12:56:3b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.4 -- renewal in 1573 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]
ian@MonOldTosh:~$

This is good. It released the IP and renewed it to 192.168.1.4. Thats fine The part on the bottom where it says  

> SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
All this means is that it didnt get an address for your WiFi card.

Maybe it is a firewall issue

Try:

```
sudo /etc/init.d/ufw stop
```Then:

```
sudo /etc/init.d/networking restart
```Can you access the internet now?

---

### Post by philipsone on 2008-05-08
> **Nxion said:**
> This is good. It released the IP and renewed it to 192.168.1.4. Thats fine The part on the bottom where it says  

All this means is that it didnt get an address for your WiFi card.

Maybe it is a firewall issue

Try:

```
sudo /etc/init.d/ufw stop
```Then:

```
sudo /etc/init.d/networking restart
```Can you access the internet now?
sudo /etc/init.d/ufw stop

command not found

---

### Post by Nxion on 2008-05-08
> **philipsone said:**
> sudo /etc/init.d/ufw stop

command not found

My apoligies, I forgot you are on 6.06. The above command only works on Hardy Heron. Sorry about that :|.

Do you have a firewall running?

Try:

```
sudo iptables --list
```

Post the output here.

---

### Post by philipsone on 2008-05-08
> **Nxion said:**
> My apoligies, I forgot you are on 6.06. The above command only works on Hardy Heron. Sorry about that :|.

Do you have a firewall running?

Try:

```
sudo iptables --list
```

Post the output here.

ian@MonOldTosh:~$ sudo /etc/init.d/ufw stop
Password:
sudo: /etc/init.d/ufw: command not found
ian@MonOldTosh:~$ sudo  iptables --list
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ian@MonOldTosh:~$

---

### Post by philipsone on 2008-05-08
> **philipsone said:**
> ian@MonOldTosh:~$ sudo /etc/init.d/ufw stop
Password:
sudo: /etc/init.d/ufw: command not found
ian@MonOldTosh:~$ sudo  iptables --list
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ian@MonOldTosh:~$
I do a firewall running in the router.
I have tried it entirely disabled but still no internet connection.

---

### Post by Nxion on 2008-05-08
> I have tried it entirely disabled but still no internet connection.

Try:

```
sudo /etc/init.d/iptables stop
```

Can you connect now?

---

### Post by philipsone on 2008-05-08
> **Nxion said:**
> Try:

```
sudo /etc/init.d/iptables stop
```

Can you connect now?

command not found

---

### Post by Nxion on 2008-05-08
Post output of this please.

```
lshw -C network
```

---

### Post by philipsone on 2008-05-08
> **Nxion said:**
> Post output of this please.

```
lshw -C network
```

ian@MonOldTosh:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:00:39:12:56:3b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 ip=192.168.1.2 multicast=yes
       resources: iomemory:fcee7000-fcee7fff ioport:dec0-deff irq:11
ian@MonOldTosh:~$

---

### Post by Nxion on 2008-05-08
As hyper_ch stated it might be a IPv6 issue. First do this:

```
sudo cat /etc/modprobe.d/aliases
```

can you post the output of this? We need to see if IPv6 is enabled or not. look for a line that says "alias net-pf-10 ipv6" is that in the file anywhere?

If so I can walk you threw how to disable it.

---

### Post by philipsone on 2008-05-08
> **Nxion said:**
> As hyper_ch stated it might be a IPv6 issue. First do this:

```
sudo cat /etc/modprobe.d/aliases
```

can you post the output of this? We need to see if IPv6 is enabled or not. look for a line that says "alias net-pf-10 ipv6" is that in the file anywhere?

If so I can walk you threw how to disable it.

ian@MonOldTosh:~$ sudo cat /etc/modprobe.d/aliases
Password:
# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
alias net-pf-10 ipv6
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet
# 18 ASH
alias net-pf-19 af_econet
alias net-pf-20 atm
# 22 SNA
alias net-pf-23 irda
alias net-pf-24 pppoe
alias net-pf-25 wanrouter
alias net-pf-26 llc
alias net-pf-31 bluetooth

# executables formats ########################################################
install binfmt-0000 /bin/true
alias binfmt-204 binfmt_aout
alias binfmt-263 binfmt_aout
alias binfmt-264 binfmt_aout
alias binfmt-267 binfmt_aout
alias binfmt-387 binfmt_aout

# block devices ##############################################################
alias block-major-3-*  ide_generic
alias block-major-8-*  sd_mod
alias block-major-9-*  md
alias block-major-11-* sr_mod
alias block-major-22-* ide_generic
alias block-major-33-* ide_generic
alias block-major-34-* ide_generic
alias block-major-37-* ide_tape
alias block-major-44-* ftl
alias block-major-46-* pcd
alias block-major-47-* pf
alias block-major-56-* ide_generic
alias block-major-57-* ide_generic
alias block-major-58-* lvm_mod
alias block-major-88-* ide_generic
alias block-major-89-* ide_generic
alias block-major-90-* ide_generic
alias block-major-91-* ide_generic
alias block-major-93-* nftl
alias block-major-97-* pg

# character devices ##########################################################
alias char-major-9-* st
alias char-major-10-1 psmouse
alias char-major-10-139 openprom
alias char-major-10-157 applicom
alias char-major-10-181 toshiba
alias char-major-10-183 hw_random
alias char-major-10-189 ussp
alias char-major-10-250 hci_vhci
alias char-major-13-0  joydev
alias char-major-13-1  joydev
alias char-major-13-2  joydev
alias char-major-13-3  joydev
alias char-major-13-32 mousedev
alias char-major-13-33 mousedev
alias char-major-13-34 mousedev
alias char-major-13-35 mousedev
alias char-major-13-63 mousedev
alias char-major-13-64 evdev
alias char-major-13-65 evdev
alias char-major-13-66 evdev
alias char-major-13-67 evdev
alias char-major-19-* cyclades
alias char-major-20-* cyclades
alias char-major-22-* pcxx
alias char-major-23-* pcxx
alias char-major-27-* ftape
alias char-major-34-* scc
alias char-major-35-* tclmidi
alias char-major-48-* riscom8
alias char-major-49-* riscom8
alias char-major-57-* esp
alias char-major-58-* esp
alias char-major-63-* kdebug
alias char-major-67-* coda
alias char-major-75-* specialix
alias char-major-76-* specialix
alias char-major-81-* videodev
alias char-major-83-* vtx
alias char-major-89-* i2c_dev
alias char-major-90-* mtdchar
alias char-major-96-* pt
alias char-major-97-* pg
alias char-major-107-* 3dfx
alias char-major-109-* lvm_mod
alias char-major-166-* cdc_acm
alias char-major-171-0 raw1394
alias char-major-171-1 video1394
alias char-major-171-2 dv1394
alias char-major-171-3 amdtp
alias char-major-180-* usbcore
alias char-major-195-* nvidia
alias char-major-200-* vxspec
alias char-major-202-* msr
alias char-major-203-* cpuid
alias char-major-206-* osst
alias char-major-208-* ussp
alias char-major-227-* tub3270
#alias char-major-240-* usb-serial
#alias char-major-240-* hsfserial
#alias char-major-241-* hsfserial

# misc #######################################################################
alias xfrm-type-2-4 xfrm4_tunnel
alias xfrm-type-2-50 esp4
alias xfrm-type-2-51 ah4
alias xfrm-type-2-108 ipcomp
alias xfrm-type-10-41 xfrm6_tunnel
alias xfrm-type-10-50 esp6
alias xfrm-type-10-51 ah6
alias xfrm-type-10-108 ipcomp6

alias bt-proto-0 l2cap
alias bt-proto-2 sco
alias bt-proto-3 rfcomm
alias bt-proto-4 bnep
alias bt-proto-5 cmtp
alias bt-proto-6 hidp
alias bt-proto-7 avdtp

alias cipcb0 cipcb
alias cipcb1 cipcb
alias cipcb2 cipcb
alias cipcb3 cipcb
alias dummy0 dummy
alias dummy1 dummy
alias plip0 plip
alias plip1 plip
alias slip0 slip
alias slip1 slip
alias tunl0 ipip
alias gre0 ip_gre

alias usbdevfs usbcore

ian@MonOldTosh:~$

---

### Post by sujoy on 2008-05-08
from all that i read, i am guessing it has to do with your DNS maybe, so try this, 

gedit /etc/resolv.conf

and append there

> nameserver 208.67.222.222
nameserver 208.67.220.220

and restart networking 

sudo /etc/init.d/networking restart

---

### Post by Nxion on 2008-05-08
try pinging google.com but use an ip rather then a address.

try:

```
ping 72.14.207.99
```

Did it work?

---

### Post by philipsone on 2008-05-08
> **sujoy said:**
> from all that i read, i am guessing it has to do with your DNS maybe, so try this, 

gedit /etc/resolv.conf

and append there



and restart networking 

sudo /etc/init.d/networking restart

sorry I don't quite follow this
I typed 
gedit /etc/resolv.conf
then got a new window headed *resolv.conf[Read Only](/etc)-gedit
Contents:
search 192.168.1.1 194.158.64.9
nameserver 192.168.1.1

what next ?

---

### Post by philipsone on 2008-05-08
> **Nxion said:**
> try pinging google.com but use an ip rather then a address.

try:

```
ping 72.14.207.99
```

Did it work?

No..

---

### Post by philipsone on 2008-05-09
> **Nxion said:**
> As hyper_ch stated it might be a IPv6 issue. First do this:

```
sudo cat /etc/modprobe.d/aliases
```

can you post the output of this? We need to see if IPv6 is enabled or not. look for a line that says "alias net-pf-10 ipv6" is that in the file anywhere?

If so I can walk you threw how to disable it.

Hi again Nxion

Well as you see in my next post IPv6 is enabled.

I installed openSUSE and experienced exactly the same connection problems.
I found an easy option to disable IPv6 and lo and behold BINGO full rapid internet connection.

Can you please therefore walk me through disabling it in Ubuntu?

Thanks in anticipation of my solution.

---

### Post by Nxion on 2008-05-09
> **philipsone said:**
> Hi again Nxion

Well as you see in my next post IPv6 is enabled.

I installed openSUSE and experienced exactly the same connection problems.
I found an easy option to disable IPv6 and lo and behold BINGO full rapid internet connection.

Can you please therefore walk me through disabling it in Ubuntu?

Thanks in anticipation of my solution.

I am very excited to here we have found the solution :)

ok here is how to do it Ubuntu:

Put this in a terminal:

```
sudo nano /etc/modprobe.d/aliases
```

Then change this line from:

```
alias net-pf-10 ipv6
```
  

to


```
alias net-pf-10 off
```


after that do "ctrl+x" then hit the "Y" key then the "enter" key.


After that reboot your machine and try to connect to the internet.


I am anxious to here back on if it worked!!

---

### Post by philipsone on 2008-05-09
> **Nxion said:**
> I am very excited to here we have found the solution :)

ok here is how to do it Ubuntu:

Put this in a terminal:

```
sudo nano /etc/modprobe.d/aliases
```

Then change this line from:

```
alias net-pf-10 ipv6
```
  

to


```
alias net-pf-10 off
```


after that do "ctrl+x" then hit the "Y" key then the "enter" key.


After that reboot your machine and try to connect to the internet.


I am anxious to here back on if it worked!!

Thanks Nxion.
I shall have to do it tomorrow.
Watch this space.....

---

### Post by philipsone on 2008-05-10
> **philipsone said:**
> Thanks Nxion.
I shall have to do it tomorrow.
Watch this space.....

Well is back up and IPv6 is now off but ...there is no change.
Still no connection except for numbered IPs.
It worked for openSUSE but not Ubuntu.
Curiously before disabling IPv6 in Ubuntu I could download K3b but with IPv6 I cannot. 

I rather wanted it to be Ubuntu on my old Toshiba laptop.
Could I try anything else or is it back to openSUSE ?

Thanks

---

### Post by hyper_ch on 2008-05-10
do you dual-boot? So that you have windows connecting? or do you have windows on another computer? If so, open dos-box and run:

```

ipconfig /all

```
paste the output here

furthermore post the output (again) of your linux box:
```

cat /etc/network/interfaces

```
```

cat /etc/resolv.conf

```

```

cat iwconfig

```

```

cat ifconfig

```

```

cat /etc/hosts

```

and use the [noparse]```

```[/noparse] tags around each output... makes it easier to read.

---

### Post by philipsone on 2008-05-10
do you dual-boot? So that you have windows connecting? or do you have windows on another computer? If so, open dos-box and run:
> I don't dual boot. I have windows on another computer.

Code:

ipconfig /all

paste the output here
> C:\Documents and Settings\User>ipconfig /all

Windows IP Configuration

Host Name . . . . . . . . . . . . : your-9ya3hf92n3
Primary Dns Suffix . . . . . . . :
Node Type . . . . . . . . . . . . : Unknown
IP Routing Enabled. . . . . . . . : No
WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

Connection-specific DNS Suffix . :
Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connecti
on
Physical Address. . . . . . . . . : 00-08-0D-93-0D-C4
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 192.168.1.5
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.1.1
DHCP Server . . . . . . . . . . . : 192.168.1.1
DNS Servers . . . . . . . . . . . : 192.168.1.1
Lease Obtained. . . . . . . . . . : 10 May 2008 11:22:30
Lease Expires . . . . . . . . . . : 10 May 2008 12:22:30

C:\Documents and Settings\User>
furthermore post the output (again) of your linux box:
Code:

cat /etc/network/interfaces
> 
ian@MonOldTosh:~$ sudo cat /etc/network/interfaces
Password:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

ian@MonOldTosh:~$


Code:

cat /etc/resolv.conf
> 
ian@MonOldTosh:~$ sudo cat /etc/resolv.conf
Password:
nameserver 192.168.1.1
ian@MonOldTosh:~$


Code:

cat iwconfig

> ian@MonOldTosh:~$ sudo cat iwconfig
cat: iwconfig: No such file or directory
ian@MonOldTosh:~$


Code:

cat ifconfig

> ian@MonOldTosh:~$ sudo cat ifconfig
cat: ifconfig: No such file or directory
ian@MonOldTosh:~$


Code:

cat /etc/hosts

> ian@MonOldTosh:~$ sudo cat etc/hosts
cat: etc/hosts: No such file or directory
ian@MonOldTosh:~$

---

### Post by hyper_ch on 2008-05-10
sorry, iwconfig and ifconfig not with a "cat" :) just run them (no sudo required either)

And it's
```

cat /etc/hosts
```

---

### Post by philipsone on 2008-05-10
> **hyper_ch said:**
> sorry, iwconfig and ifconfig not with a "cat" :) just run them (no sudo required either)

And it's
```

cat /etc/hosts
```


```
ian@MonOldTosh:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       MonOldTosh

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
ian@MonOldTosh:~$
```

```
ian@MonOldTosh:~$
ian@MonOldTosh:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ian@MonOldTosh:~$
```

```
ian@MonOldTosh:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:12:56:3B
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe12:563b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:610168 (595.8 KiB)  TX bytes:191343 (186.8 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

ian@MonOldTosh:~$

```
That looks better...

---

### Post by hyper_ch on 2008-05-10
looks ok. can you ping the router?
```

ping 192.168.1.1

```
if so, can you ping an outside server (ubuntu.com)
```

ping 91.189.94.158

```

and if that works, can you actually ping domains?
```

ping ubuntu.com

```

---

### Post by philipsone on 2008-05-10
> **hyper_ch said:**
> looks ok. can you ping the router?
```

ping 192.168.1.1

```
if so, can you ping an outside server (ubuntu.com)
```

ping 91.189.94.158

```

and if that works, can you actually ping domains?
```

ping ubuntu.com

```

```
ping 192.168.1.1
```
Yes
```

ping 91.189.94.158

```
No
```

ping ubuntu.com

```
No

---

### Post by hyper_ch on 2008-05-10
but you can access the net with windows?

---

### Post by philipsone on 2008-05-10
> **hyper_ch said:**
> but you can access the net with windows?

Yes.

---

### Post by hyper_ch on 2008-05-10
hmmm..... then I don't really know...

---

### Post by philipsone on 2008-05-10
> **hyper_ch said:**
> hmmm..... then I don't really know...
Thanks for your help Nxion  :popcorn:  

For the record:
I have four machines connected to the router.

1. Laptop running Vista (can't complain too much) - connects OK.
2. 14 years old Mac Box (why do I bovver?) - connects OK.
3. Laptop running XP (hardware struggling to survive but does the job) - connects OK
4a. Very Old Laptop running Ubuntu with IPv6 on or off - this problem.  No connection.
4b. Same Very Old Laptop running openSUSE with IPv6 on - same problem.
4c. Same Very Old Laptop running openSUSE with IPv6 OFF- problem solved.

It looks like I might be obliged to go back to 4c    :(
But if anyone else has any secrets to reveal to get Ubuntu up on the faithful but Very Old Laptop then I should be chuffed ...:lolflag:
I was hoping to be able to thank everyone with a jig :guitar: but I will anyway.

---

### Post by philipsone on 2008-05-12
Hi Again

There is a happy ending (restart).

Summary:
I installed ubuntu 6.06 (from a downloaded Live CD) onto a 7 years old Toshiba Satellite (S2800-500) laptop with 256kb ram. 
(Sorry I hastily said before it was 13 years old).
The reason I chose 6.06 was because of my limited RAM. The more recent Live CD versions appeared to require more than 256kb RAM.

6.06 installed OK except I could not get the internet up in spite of all your help. We tried.

I tried openSUSE in various forms and got the internet up with a few tweaks (disable IPv6) but got other problems (including sound).

I downloaded Ubuntu 8.04, yes Hardy Heron. I chose the alternate CD option which said it needed a minimum 256kb ram.
The Live CD needed 384kb RAM.

Result:
IT ALL WORKED straight out of the box.
It's a bit slow (Pentium III) but it all works. :lolflag:

It runs like a dream.
[www.3wiw.com](www.3wiw.com)

Thanks again for your help.

---

### Post by Nxion on 2008-05-12
I am glad that you got Hardy working for ya, Sorry we couldn't get 6.06 working. I know you will love Hardy :) I am happy that this was resolved. Enjoy Ubuntu :) If you ever need any more help, you can always ask me.

---

