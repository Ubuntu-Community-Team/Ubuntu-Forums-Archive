---
title: "unable to access my web site"
date: 2014-05-03
forum: New to Ubuntu
---

### Post by Richardc0077 on 2014-05-03
Hi to all

I have ubuntu 14.04 server running apache2 mysql and php. I have a program that i want out on the web but am having trouble getting it out there.

I have install No-ip and have followed the setup to the letter. I have and set the server to have ports 80 443 open and for noip they request 8245 open. I have done this on the server and on the router. What do i set the ip address on the router I have 192.168.1.1 is the hub 192.168.1.20 is the server and the laptop i use for putty is 192.168.1.100

when i do netstat grep all i get is tpc6 0    0 ::[COLOR=#ff0000]:80 [/COLOR]And on grep LISTEN i get tcp    0    0   0.0.0.0:22         0.0.0.0:*         [COLOR=#ff0000] LISTEN
                                                                                                       [/COLOR]tcp    0     0  127.0.0.1:3309    0.0.0.0:*[COLOR=#ff0000]        LISTEN
                                                                                                      [/COLOR]tcp6   0     0   :::22               :::*[COLOR=#ff0000]                 LISTEN
                                                                                                    [/COLOR]  tcp6   0     0   :::80               :::*[COLOR=#ff0000]                 LISTEN

[/COLOR]Am i to presume that the items in red have a problem[COLOR=#ff0000]
                                                                                   
[/COLOR]Some help in this matter would be very gratefull
 

Many thanks
 
Richard C   [COLOR=#ff0000]              


[/COLOR][COLOR=#ff0000][/COLOR]

---

### Post by lisati on 2014-05-03
Have you configured port forwarding on the router? (The particular method depends on the router)

---

### Post by Richardc0077 on 2014-05-03
yes i have setup the router for 80 , 443, 8245

---

### Post by Richardc0077 on 2014-05-05
the problem is in the noip. i can not get port 8245 open i have check firewalls my router and the program itself. i have tried to open on another computer thou a different modem and still it will not open. 

any ideas would be very greatfull

Many thanks

Richard C

---

### Post by Danger_Monkey on 2014-05-05
One thing I noticed on upgrading to 14.04 was that the default site had been reconfigured from /var/www to /var/www/html, where there were no files.  You might want to make sure your settings are correct for your virtual server in:

```

/etc/apache2/sites-enabled/000-default.conf (or whatever yours is named)

```

You may also want to make sure that the virtual server is still configured for 8245 in there.

---

### Post by Richardc0077 on 2014-05-06
A Big Thank you for that will check that on the weekend

RichardC

---

