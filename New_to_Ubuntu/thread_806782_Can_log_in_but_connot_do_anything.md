---
title: "Can log in but connot do anything"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by lsemmens on 2008-05-25
I had some troubles getting Ubuntu to recognise my modem,[http://ubuntuforums.org/showthread.php?p=4933320&posted=1#post4933320](http://ubuntuforums.org/showthread.php?p=4933320&posted=1#post4933320). This problem seems to be resolved, however, despite the fact that terminal indicates that I am connected and allocated an IP address, nothing will allow me to interrogate the internet. Firefox does nothing, I cannot even download an updated file list in synaptic package manager. Is there a solution? Or shall I stick with my windoze box until I can afford broadband again?

---

### Post by cprofitt on 2008-05-25
Could you provide more detail as to the nature of your connection?

Cable modem?
Router?

What IP address are you getting?

---

### Post by superprash2003 on 2008-05-25
also please post the output of ifconfig

---

### Post by lsemmens on 2008-05-27
I chose not to re-iterate my problems from the other thread, hence, the link. This describes my setup as dial up using a generic conextant modem driver from dell. The terminal and Gnome PP logs posted there both show an IP address (which is dynamic) as having been allocated.

Usins Sudo Wvdial I get an unremarkable log which seems to indicate that I am connected. If I use GnomePPP all I get is the pop up that says "Authenticating" and goes no further. The log indicates possible issues but continues to allocate an IP.
A copy of the relevant portion of the log C&P from the other thread is here:
> 
WvDial<*1>: Looks like a welcome message.
WvDial<Notice>: Starting pppd at Sat May 17 11:18:37 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 5745
WvDial<*1>: Using interface ppp0
WvDial<*1>: local IP address 144.134.7.198
WvDial<*1>: remote IP address 139.134.59.227
WvDial<*1>: primary DNS address 203.49.70.20
WvDial<*1>: secondary DNS address 139.134.2.190

---

### Post by lsemmens on 2008-05-27
> **superprash2003 said:**
> also please post the output of ifconfig

does ifconfig need to be run while I am supposedly logged into the internet as the results appear to be less than informative

> *ifconfig log*

eth0      Link encap:Ethernet  HWaddr 00:0D:61:AD:C8:0A  
          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20d:61ff:fead:c80a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35025 (34.2 KB)  TX bytes:37765 (36.8 KB)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



---

