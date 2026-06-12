---
title: "find what app is on port 80"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by caleb12134 on 2013-03-07
so i have a install of ubuntu ***_server_*** with startx ubuntu desktop gui. I was trying out new software like, wamp, xammp and other software. and the few i didnt like it i moved the start icon to the trash. i accidentally deleted them all. then i found one i liked. ampps. i wanted to access its web panel. to cut to the chase another server was already running on port 80. how do i find what app is running on port 80 and remove it????  :)

---

### Post by steeldriver on 2013-03-07
netstat maybe?

```

sudo netstat -nlp | grep ':80'
tcp        0      0 0.0.0.0**:80**              0.0.0.0:*               LISTEN      18054/**apache2**

```

---

### Post by lfacchinelli on 2013-03-07
The easiest way to know wich process is running in a certain port is running the followin command

sudo netstat -tulpn 

In your case, just execute

```
 sudo netstat -tulpn | grep 80 (This will filter the result by showing only port 80 )
```

In my case shows this 

```
 tcp6       0      0 :::80                   :::*                    LISTEN      1411/apache2    
```

Thats means apache is using that port (also the numbers before slash is process ID )

---

### Post by caleb12134 on 2013-03-07
ok it didnt work i pasted in  [COLOR=#000000][FONT=Ubuntu Mono]sudo netstat -tulpn | grep 80. and i got the results below. also an app called AMPPS that is using wine wont work. it opens then bounces then closes?????? i would appreciate any help :) thanks a million[/FONT][/COLOR]


root@ubuntu:~# 
root@ubuntu:~# sudo netstat -tulpn | grep 80
root@ubuntu:~# sudo netstat -tulpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:2002            0.0.0.0:*               LISTEN      2502/wineserver 
tcp        0      0 127.0.0.1:5939          0.0.0.0:*               LISTEN      6065/teamviewerd
tcp        0      0 0.0.0.0:46325           0.0.0.0:*               LISTEN      2713/Plex Plug-in [
tcp        0      0 0.0.0.0:32469           0.0.0.0:*               LISTEN      1494/Plex DLNA Serv
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      898/cupsd       
tcp        0      0 0.0.0.0:61247           0.0.0.0:*               LISTEN      1494/Plex DLNA Serv
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      2502/wineserver 
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      1552/perl       
tcp        0      0 0.0.0.0:32400           0.0.0.0:*               LISTEN      1203/Plex Media Ser
tcp6       0      0 ::1:631                 :::*                    LISTEN      898/cupsd       
udp        0      0 0.0.0.0:10000           0.0.0.0:*                           1552/perl       
udp        0      0 0.0.0.0:1900            0.0.0.0:*                           1494/Plex DLNA Serv
udp        0      0 127.0.0.1:57733         0.0.0.0:*                           1203/Plex Media Ser
udp        0      0 0.0.0.0:54151           0.0.0.0:*                           878/avahi-daemon: r
udp        0      0 0.0.0.0:33189           0.0.0.0:*                           1494/Plex DLNA Serv
udp        0      0 0.0.0.0:1446            0.0.0.0:*                           1494/Plex DLNA Serv
udp        0      0 0.0.0.0:11328           0.0.0.0:*                           1494/Plex DLNA Serv
udp        0      0 0.0.0.0:68              0.0.0.0:*                           923/dhclient3   
udp        0      0 192.168.1.8:33402       0.0.0.0:*                           1203/Plex Media Ser
udp        0      0 0.0.0.0:52360           0.0.0.0:*                           6065/teamviewerd
udp        0      0 0.0.0.0:32410           0.0.0.0:*                           1203/Plex Media Ser
udp        0      0 0.0.0.0:32413           0.0.0.0:*                           1203/Plex Media Ser
udp        0      0 0.0.0.0:32414           0.0.0.0:*                           1203/Plex Media Ser
udp        0      0 127.0.0.1:60625         0.0.0.0:*                           1203/Plex Media Ser
udp        0      0 192.168.1.8:42208       0.0.0.0:*                           1203/Plex Media Ser
udp        0      0 0.0.0.0:36066           0.0.0.0:*                           1494/Plex DLNA Serv
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           878/avahi-daemon: r
udp6       0      0 :::42030                :::*                                878/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                878/avahi-daemon: r
root@ubuntu:~# sudo netstat -tulpn | grep 80
root@ubuntu:~#

---

### Post by lfacchinelli on 2013-03-07
Based in your results no process is using port 80. So you should not get any messages like "another process is using port 80"
Are you sure  ammps is installed and running ?

---

### Post by caleb12134 on 2013-03-08
yes but everytime i try to start it with wine it bounces then closes????????

---

