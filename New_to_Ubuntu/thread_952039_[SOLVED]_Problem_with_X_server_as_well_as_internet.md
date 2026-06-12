---
title: "[SOLVED] Problem with X server as well as internet!"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Dark Samurai on 2008-10-18
Hey-
I was working with my visual configurations, and uninstalled xserver-xgl.  HUGE mistake on my part...
Upon reboot, my xserver could not be accessed.  So, I tried to reinstall it using:```
sudo apt-get install xserver-xgl
```
but to no avail... My wireless seems to not be working anymore, and my wired connection is not working either... I think that if I can get either the wired or wireless to work, then I should be able to reinstall xserver-xgl.  Please help!

---

### Post by phidia on 2008-10-18
With the ethernet cable plugged in and with internet service on what does > ifconfig output?

---

### Post by Dark Samurai on 2008-10-19
Ok. So I got the internet working on the wire (via turning off and on the wireless then pluging in the cable).  I still have issues with the wireless though.  This is the output for ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0b:db:07:76:4c  
          inet addr:10.10.7.61  Bcast:10.10.7.255  Mask:255.255.248.0
          inet6 addr: fe80::20b:dbff:fe07:764c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4834797 (4.6 MB)  TX bytes:732207 (715.0 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

```

And this is the output for iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I used ndiswrapper in the past, and it worked fine.  Another interesting point is that when I am in the non-graphical bootup, I keep getting this error that tells me to go to [http://linuxwireless.org/en/users/drives/b43#devicefirmware](http://linuxwireless.org/en/users/drives/b43#devicefirmware) to download the third version.
Thanks!

---

### Post by Dark Samurai on 2008-10-19
Hey-
I installed xserver-xgl, which messed up my computer.  I then unistalled it, and now my wireless does not work.  This is what I get when I type iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And this is what I get when I type ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0b:db:07:76:4c  
          inet addr:10.10.7.61  Bcast:10.10.7.255  Mask:255.255.248.0
          inet6 addr: fe80::20b:dbff:fe07:764c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15917606 (15.1 MB)  TX bytes:1504754 (1.4 MB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 B)  TX bytes:600 (600.0 B)
```

And this is what I get when I type ndiswrapper -l
```
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
```

Thanks a bunch!

---

### Post by Dark Samurai on 2008-10-19
Moved this problem to here:
[HTML]http://ubuntuforums.org/showthread.php?t=952710[/HTML]
Thanks!

---

### Post by overdrank on 2008-10-19
Please do not create duplicate threads on the same issue. Threads merged :)

---

### Post by Dark Samurai on 2008-10-19
Oh, sorry... Well, I fixed the first problem, and now I have a different problem with the wireless...
May I create another thread about my wireless problem instead?
Thanks!

---

### Post by overdrank on 2008-10-19
> **Dark Samurai said:**
> Oh, sorry... Well, I fixed the first problem, and now I have a different problem with the wireless...
May I create another thread about my wireless problem instead?
Thanks!

I am sorry I really must pay better attention. I thought you were getting the help need in your original post. I see you have not had a reply to you posting the command output but I am sure phidia or someone else will respond. Just maybe bump your post tomorrow if no help is forth coming :)

---

### Post by Dark Samurai on 2008-10-20
Bump

---

