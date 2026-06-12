---
title: "scp between Kubuntu 12.04 as a host and Kubuntu 12.10 as a guest in VirtualBox"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by kazek on 2013-03-02
Hi,

I am using Kubuntu 12.04 as my main system. I have also installed Kubuntu 12.10 in VirtualBox. I would like to have possibility to transfer (I know about shared folders in guest additions) files using scp. I used it once, maybe twice in my life. I do not now much about it and I cannot have that working with my setup. Hmm let me mention, that I have already tried to solve this problem by myself (first I went through a tutorial how to use scp: [http://pinehead.tv/linux/ssh-and-scp-howto-tips-tricks/](http://pinehead.tv/linux/ssh-and-scp-howto-tips-tricks/)). 

Hmm I suppose, that something is wrong with my ports... port 22 seems to be off. Hmm first, I am not sure, if I configured VirtualBox properly (I have wifi router at home) - please see one of the screens in atachment.

My host Kubuntu:

```

root@pawel-desktop:/home/pawelkde/rubbish2# netstat -lnptu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      751/smbd        
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1759/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      656/cupsd       
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      751/smbd        
tcp6       0      0 :::139                  :::*                    LISTEN      751/smbd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      656/cupsd       
tcp6       0      0 :::445                  :::*                    LISTEN      751/smbd        
udp        0      0 0.0.0.0:50140           0.0.0.0:*                           583/avahi-daemon: r
udp        0      0 127.0.0.1:53            0.0.0.0:*                           1759/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1653/dhclient   
udp        0      0 192.168.0.255:137       0.0.0.0:*                           1872/nmbd       
udp        0      0 192.168.0.13:137        0.0.0.0:*                           1872/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1872/nmbd       
udp        0      0 192.168.0.255:138       0.0.0.0:*                           1872/nmbd       
udp        0      0 192.168.0.13:138        0.0.0.0:*                           1872/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1872/nmbd       
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           583/avahi-daemon: r
udp6       0      0 :::46749                :::*                                583/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                583/avahi-daemon: r

```

```

root@pawel-desktop:/home/pawelkde/rubbish2# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:22:ca:be:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:519695 (519.6 KB)  TX bytes:519695 (519.6 KB)


wlan0     Link encap:Ethernet  HWaddr 00:4f:78:01:b3:5b  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::24f:78ff:fe01:b35b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:185999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122898 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:237288453 (237.2 MB)  TX bytes:16007020 (16.0 MB)



```

My Kubuntu in virtualBox as attachments.

I will be thankful for any advice ;)

Regards,
kazek

---

### Post by kazek on 2013-03-02
And one more question. After issuing command: "ssh -p53 localhost" combination ctrl + D is not working... why is that?

---

### Post by kazek on 2013-03-02
Ok, problem solved - I simply had no ssh server installled...

---

