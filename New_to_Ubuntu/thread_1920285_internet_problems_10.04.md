---
title: "internet problems 10.04"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by rayeacott on 2012-02-04
I have just loaded ubuntu from the Cd supplied with Linux for Dummies
but I am unable to get Firefox to work - I have Firefox working on a windows Pc
I can ping yahoo.co.uk etc. I tried Traceroute and yahoo.co.uk does not reply
Please can somebody help

---

### Post by Kixtosh on 2012-02-04
> **rayeacott said:**
> I have just loaded ubuntu from the Cd supplied with Linux for Dummies
but I am unable to get Firefox to work - I have Firefox working on a windows Pc
I can ping yahoo.co.uk etc. I tried Traceroute and yahoo.co.uk does not reply
Please can somebody help
Have you got your internet connection working yet when using Ubuntu? A wired connection should work "out of the box", but a wireless connection may require some additional steps. Which of the two are you using?

---

### Post by rayeacott on 2012-02-05
Thanks for your interest
 
I have not managed to get the ubuntu PC to link to the net
 
I have a windows PC working via the same router and can ping yahoo via the PC running ubuntu - the trace route test was done using the ubuntu PC
 
I am using a wired connection

---

### Post by rayeacott on 2012-02-05
Re post above
 
I have tried reloading ubuntu - no change
 
Disabled network on mother board and installed network card but no change

---

### Post by rayeacott on 2012-02-05
[QUOTE=rayeacott;11665843]Re post above
 
I have tried reloading ubuntu - no change
 
Disabled network on mother board and installed network card but no change
 
Tried to get on to Ubuntu One but received [Errno socket error][Errno 110] Connection timed out

---

### Post by Kixtosh on 2012-02-05
Here is a quick troubleshooting guide. You can use it to identify your Ethernet card and then search the forum for solutions:

[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

Search the Networking & Wireless section in particular:

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Identify your card first, in my opinion. Don't bother with trying all the Terminal commands in the guide until you research potential problems with your particular card, or you may simply complicate future troubleshooting further.

---

### Post by RedSingularity on 2012-02-05
Well you CAN ping, so you have a connection to the net.....

Whats the output of "ifconfig"

---

### Post by rayeacott on 2012-02-06
Output from "ifconfig" below
 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
ray@ray-ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:04:76:d3:27:91 
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::204:76ff:fed3:2791/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:327 errors:0 dropped:0 overruns:1 frame:0
TX packets:239 errors:0 dropped:0 overruns:0 carrier:1
collisions:0 txqueuelen:1000 
RX bytes:31778 (31.7 KB) TX bytes:125437 (125.4 KB)
Interrupt:18 Base address:0x4000 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:13 errors:0 dropped:0 overruns:0 frame:0
TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:1296 (1.2 KB) TX bytes:1296 (1.2 KB)
ray@ray-ubuntu:~$
 
Is it possible that I need to use a proxy server - if so what setting should I use - I have tried my router address and port 80 but that fails

---

### Post by robsoles on 2012-02-06
Are you setting a proxy in Firefox before just trying it flat out?

If you can ping a host on the internet (like yahoo.co.uk) then your computer has a valid IP address on your local area network and is configured to use your router as the gateway.

You have a Windows machine that can use the internet? If you need proxy settings for your Ubuntu Firefox then they will be the same proxy settings that the browser on the Windows machine is using...


Reset anything you've changed in Firefox (on Ubuntu machine) back to its default and try again please.

---

### Post by rayeacott on 2012-02-06
I first tried without a proxy server
 
Windows PC will run Firefox without a proxy server
 
I tried disabling network on the mother board and install a network card then reloading ubuntu but no change
 
Trace route to yahoo.co.uk returns no reply

---

### Post by Bodsda on 2012-02-06
What error message does firefox show you when you try to browse to yahoo.co.uk?
Does the traceroute return anything at all? At the very least it should show the hop from your PC to your router.

Ping yahoo.co.uk, note down the IP address that it returns, then try browsing to that IP address through firefox. If that works, then the issue is with DNS

Bodsda

---

### Post by rayeacott on 2012-02-06
Firefox massage then trying to access Yahoo.co.uk
 
*The connection has timed out*
 
*The server at uk.yahoo.com is taking too long to respond*
 
Tried again using uk.yahoo.com - same result
 
 
TRACE ROUTE - yahoo.co.uk - below
 
Hop Hostname IP Time 1 Time 2
1 ray-ubuntu.local 192.168.1.2 0.171ms 
1 mygateway.ar7 192.168.1.1 4.389ms 
1 mygateway.ar7 192.168.1.1 0.985ms 
2 mygateway.ar7 192.168.1.1 0.974ms
2 host-84-13-16-1.opaltelecom.net 84.13.16.1 46.125ms 
3 host-78-151-225-225.static.as13285.net 78.151.225.225 46.751ms 
4 host-78-151-225-156.static.as13285.net 78.151.225.156 48.685ms 
5 xe-11-2-0-rt001.sov.as13285.net 62.24.240.5 49.626ms 
6 host-78-144-0-146.as13285.net 78.144.0.146 50.069ms 
7 xe-11-3-0-scr010.sov.as13285.net 78.144.0.221 49.668ms 
8 ge-3-3-0.pat1.tc2.yahoo.com 195.66.226.129 50.532ms 
9 ge-0-1-0.pat1.the.yahoo.com 66.196.65.28 52.279ms 
10 as-0.pat2.ams.yahoo.com 66.196.65.66 57.437ms 
11 xe-0-1-0.msr1.ch1.yahoo.com 66.196.65.69 86.514ms 
12 no reply * 
13 no reply * 
14 no reply * 
15 no reply * 
16 no reply * 
17 no reply * 
18 no reply * 
19 no reply * 
20 no reply * 
21 no reply * 
22 no reply * 
23 no reply * 
24 no reply * 
25 no reply * 
26 no reply * 
27 no reply * 
28 no reply * 
29 no reply * 
30 no reply * 
31 no reply *
 
Tried using 77.238.178.122 [yahoo.co.uk] 
 
Sorry the page you requested was not found
 
 
Then Firefox starts it tries to open start.ubuntu.com - but this fails
 
If I type in ubuntu.com the home page opens but then I try one of the tabs I receive *The connection has timed out* etc after a few seconds.
 
One other thing the update manager is working Ok i.e. down loading files
 
Ray

---

### Post by RedSingularity on 2012-02-06
I am not able to complete a traceroute to that IP either.  Looks like a problem on their end.  Can you traceroute to [www.google.com?](www.google.com?)

---

### Post by rayeacott on 2012-02-07
I loaded all of the updates (over 450)  last night and the problem has gone away

Thanks for your help

Ray

---

### Post by Kixtosh on 2012-02-07
Great! Mark the thread as "solved" using the thread tools (top right, above the first post).

---

