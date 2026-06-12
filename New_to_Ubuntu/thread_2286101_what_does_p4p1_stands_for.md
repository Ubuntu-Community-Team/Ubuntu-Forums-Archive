---
title: "what does p4p1 stands for"
date: 2015-07-10
forum: New to Ubuntu
---

### Post by houmingc on 2015-07-10
lo stands for local, what does p4p1 stands for in my network config? 
what is  inet addr:192.168.1.106 ?
Also how to create a home network using ubuntu OS
My ifconfig shows  



 
lo       Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:401586 (401.5 KB)  TX bytes:401586 (401.5 KB)

p4p1  Link encap:Ethernet  HWaddr c0:3f:d5:aa:11:4b  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c23f:d5ff:feaa:114b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28972577 (28.9 MB)  TX bytes:3554201 (3.5 MB)

---

### Post by Bucky Ball on 2015-07-10
Follow this thread from [here]("http://ubuntuforums.org/showthread.php?t=2078294&p=12327235&viewfull=1#post12327235") and see if it sheds any light. It appears to be your eth0 connection (wired ethernet) in disguise.

---

