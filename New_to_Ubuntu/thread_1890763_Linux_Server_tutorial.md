---
title: "Linux Server tutorial"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by amry87 on 2011-12-04
Hi guys, 
I am new here and new in linux server. 
I have installed linux server, 
and would like to use for further tasks. As I found out it has no interface ... just commands, 
so I have install LAMP to my server and would like to check if it works or not, 
but I do not know how to check it.
And further I would like to check php, mysql and so on, but have no clue how to do it, 
Any helps, ideas ...
Thanks forward.

---

### Post by sanderd17 on 2011-12-04
To check your lamp, you should go to [http://your-ip-address:80](http://your-ip-address:80) from a desktop computer. If you don't know your ip-address, you can find it with the command "ifconfig". That will show all network devices and which are active.

Mine is:
```

[sander@arch ~]$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500  metric 1
        ether 00:90:f5:b3:36:63  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 43  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 16436  metric 1
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 0  (Local Loopback)
        RX packets 4877  bytes 4525914 (4.3 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4877  bytes 4525914 (4.3 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500  metric 1
        inet **192.168.1.3**  netmask 255.255.255.0  broadcast 192.168.1.255
        ether e0:91:53:2d:b5:04  txqueuelen 1000  (Ethernet)
        RX packets 446819  bytes 535795913 (510.9 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 284254  bytes 41110703 (39.2 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

And my ip-address is in bold.

Normally, if you have php installed, it will run a little php script an show that php is working well.

To test mysql, you will need to log in to the mysql server, but lets start with the rest.

Btw, you could also just use the desktop CD (with a graphical environment). Installing a Lamp is easier on a desktop CD, but a desktop CD is heavier for your computer.

---

### Post by 2F4U on 2011-12-04
I would start by reading the official documentation provided by the project:

[https://help.ubuntu.com/11.10/serverguide/C/index.html](https://help.ubuntu.com/11.10/serverguide/C/index.html)

---

### Post by Gone fishing on 2011-12-04
I have always found the howtoforge tutorials very useful [http://www.howtoforge.com](http://www.howtoforge.com) Webmin is a handy tool [http://www.webmin.com](http://www.webmin.com) it might be worth looking at SME - what do you want this server to do, what's it for?

---

