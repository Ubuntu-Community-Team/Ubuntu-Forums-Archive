---
title: "[SOLVED] network stops responding"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by two4two on 2008-10-15
Since I am a beginner I posted here.  If I should have posted in the Network forum please let me know.  Many times when I boot it finds my adapter, but can't connect.  But sometimes I get lucky and it finds my adapter and connects OK.  But I get ONE page return from the internet, or I get a few update downloads.  Then it stops responding.  It is a Trendnet TEW-424UB USP adapter with the RealTek RTL8187B chipset/driver and I have 8.10 Beta (because it has support for the TEW-424UB built in).  After it stops responding I can't even ping the AP any more.  And I can't ping from the AP to me either.  But the TrendNet Icon is there saying it's connected at 90% strength.  And the AP shows it's connected.  When I monitor the network it shows packets being received every few seconds and the graph spikes at those times.  The AP log has references to me, so it did in fact connect and doesn't show it disconnected.  The SYSLOG also doesn't show that it's disconnected.  I've never been able to connect and get continued network or internet response.  If any expert could help I'd appreciate it.  I can post whatever diags you need.  You might have to help me get the diags though.  Thanks all.

---

### Post by jbrown96 on 2008-10-15
Can you post the output of the following two commands both from when you know you are connected and after it stops responding? ```
ifconfig
``````
iwconfig
```

---

### Post by dhtseany on 2008-10-15
This may be a silly question but have you tried restarting your modem and router? That kinda sounds like a symptom of the router acting stupid.

Peace
Sean

---

### Post by two4two on 2008-10-16
Thanks jbrown.  I hope I'm not being stupid by giving the world the keys to my computer, but here goes:  just after I booted I entered the following as requested:


dad@Kids3-Linux:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:159368 (159.3 KB)  TX bytes:159368 (159.3 KB)

wlan0     Link encap:Ethernet  HWaddr nn:nn:nn:nn:nn:nn  
          inet addr:192.168.0.150  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: nnnn::nnn:nnnn:nnnn:nnnn/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13838 (13.8 KB)  TX bytes:5003 (5.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-nn-nn-nn-nn-nn-nn-nn-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




The internet worked fin for about 15 minutes.  I don't know if it is the cause, but after I tried to go to a web site that redirected me and Firefox blocked it and I clicked to allow it, it stopped working.  The site would have loaded an Outlook Web Access e-mail web site.  I entered my id/password and it stopped working.  And from there no more internet.  Also, I can't download the latest 8.10 updates.  The TrendNet icon is still displayed and it says the connection to the wireless network is at 90%.  When I go to Network Tools and look at device wlan0 it gives some output that shows what I referred to in my post:  "Received Packets" keeps ticking up every 15 seconds or so, and there is a spike in the monitor graph at those times.  As you requested, ifconfig now shows the following:


dad@Kids3-Linux:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:162733 (162.7 KB)  TX bytes:162733 (162.7 KB)

wlan0     Link encap:Ethernet  HWaddr nn:nn:nn:nn:nn:nn  
          inet addr:192.168.0.150  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: nnnn::nnn:nnnn:nnnn:nnnn/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5285 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4189712 (4.1 MB)  TX bytes:676428 (676.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-nn-nn-nn-nn-nn-nn-nn-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

dad@Kids3-Linux:~$ [www.ubuntux.org/image](www.ubuntux.org/image)


See anything helpful?  The only thing I see different is the counts went up, which just confirms it was connected and worked for a while.  Sorry I didn't see you said iwconfig.  My fonts are kinda small and it only became apparent after I magnified it.  If you need me to repeat the test just let me know.

---

### Post by two4two on 2008-10-16
Reboot after I discovered my error of not doing the iwconfig.  Here are both commands:


dad@Kids3-Linux:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:218300 (218.3 KB)  TX bytes:218300 (218.3 KB)

wlan0     Link encap:Ethernet  HWaddr nn:nn:nn:nn:nn:nn  
          inet addr:192.168.0.150  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: nnnn::nnn:nnnn:nnnn:nnnn/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:510 (510.0 B)  TX bytes:4958 (4.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-nn-nn-nn-nn-nn-nn-nn-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

dad@Kids3-Linux:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: nn:nn:nn:nn:nn:nn   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=90/100  Signal level:-26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.





Internet worked just great for a while.  BTW, the OWA site worked OK.  I tried to download 8.10 updates.  It got to file 34 and stopped.  Web pages stopped too.  Here are the two commands again:


dad@Kids3-Linux:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4451 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:228977 (228.9 KB)  TX bytes:228977 (228.9 KB)

wlan0     Link encap:Ethernet  HWaddr nn:nn:nn:nn:nn:nn  
          inet addr:192.168.0.150  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: nnnn::nnn:nnnn:nnnn:nnnn/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5163150 (5.1 MB)  TX bytes:520946 (520.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-nn-nn-nn-nn-nn-nn-nn-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

dad@Kids3-Linux:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: nn:nn:nn:nn:nn:nn   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=92/100  Signal level:-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

dad@Kids3-Linux:~$ 


Once again, see anything helpful?

---

### Post by dhtseany on 2008-10-16
Well so far I'm seeing that your wireless is getting an IP address from the router so that's a good sign. Was this ever working or did this problem recently start?

Peace
Sean

PS- Don't worry, the information you've posted is nothing specific. It's only your wireless configuration so you're safe :)

---

### Post by two4two on 2008-10-16
Thanks dstsheany.  Actually, I've tried it both ways:  DHCP and manual.  Same results.  This report was gotten while I was using manual settings.  I coded the IP I want and the AP IP, etc.  But if I try it all auto I get the same values, all but the IP, but the lease on the IP remains in the AP for about a week.  I thought that might be causing some confusion so I coded it all manually.  It didn't change anything.  Same scenario:  works for a time then stops.  Any more diag info anyone would like me to get?

---

### Post by two4two on 2008-11-12
8.10 release solved the problem

---

