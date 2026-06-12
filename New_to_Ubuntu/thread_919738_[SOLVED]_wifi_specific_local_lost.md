---
title: "[SOLVED] wifi specific local lost"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by jackBnimble on 2008-09-14
Hey I could use some help reconnecting to a wifi unencrypted at a local cafe.  I did something and it stopped working even though the signal is still good and everyone elses connection works just fine.  I know my wifi signal works and does connect at other locals.  But I would really like to get this one up again, it my favorite cafe!
What I've tried: re-installing 8.04, running a command; sudo iwilist eth1 scan  with results that say that the interface doesn't support scanning.
I also ran /sbin/ifconfig-a to get a list of devices and names.  That worked worked but I haven't a clue what to do with it.  P_Quarles said to replace eth1 with the wireless devices name, but I don't know how to do that either.  I've just been using Ubuntu 8.04 for a month now.

results from /sbin/ifconfig-a 

eth0      Link encap:Ethernet  HWaddr 00:e0:b8:91:ae:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:96:9d:38  
          inet addr:192.168.200.30  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe96:9d38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:263 errors:0 dropped:8 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16408 (16.0 KB)  TX bytes:10426 (10.1 KB)
          Interrupt:11 Base address:0xa000 Memory:e0208000-e0208fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80500 (78.6 KB)  TX bytes:80500 (78.6 KB)

Anyhelp would be great because the next step I'm going to try is the aircrack-ng.

Thanks guys

---

### Post by aloshbennett on 2008-09-14
Lol! Favourite cafe :D
Try iwconfig to see if you have not put your wireless card in Monitor mode already.

---

### Post by jackBnimble on 2008-09-15
Do I just put "iwconfig" in to the terminal and enter?  I run an internal wifi card, its an Intel/PRO 2200.  I do know my wifi card is working, I'm using right now at a different cafe not my fav though:(  My wifi went down at "Epoch" after I was cleaning up what I thought was junk.  Opps! My bad.  So my meter still reads a signal at Epoch but It doesn't connect where it counts- when I open my firefox 3 browser or updates.  I had this problem back when I ran MS/XP and found the problem was my IP address setting was changed to a static address.  Could this problem be the same?  I wouldn't know how to change that setting unless someone walked me through it.


Thanks

---

### Post by jackBnimble on 2008-09-15
I tried just running iwconfig in terminal and it came back 

rjw@jackBnimble:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"starseeds"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:01:35:52   
          Bit Rate:1 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/100  Signal level=-65 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:3   Missed beacon

Of course this is the cafe that I have the problem with.....

---

