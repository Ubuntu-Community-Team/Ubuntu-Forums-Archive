---
title: "apache 2 problem in restarting"
date: 2013-05-29
forum: Programming Talk
---

### Post by jairoh_ on 2013-05-29
[FONT=Consolas][COLOR=#000000]i tried restarting my apache server and it works fine when i browse my local sites i made. but this looks strange. I'm new to ubuntu. 
[/COLOR][/FONT]```
 * Restarting web server apache2                                               
 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed May 29 18:12:58 2013] [warn] _default_ VirtualHost overlap on port 8080, the first has precedence
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed May 29 18:12:59 2013] [warn] _default_ VirtualHost overlap on port 8080, the first has precedence
                                                                         [ OK ]
jairoh@jairoh-300E4C-300E5C-300E7C:~$ 



```[FONT=Consolas][COLOR=#000000] 

anyone can help. tnx[/COLOR][/FONT]

---

### Post by slickymaster on 2013-05-29
That's not really a problem but a warning. Just insert:```
ServerName localhost
```in your **apache2.conf** file in **/etc/apache2** and restart your apache server and the notice will disappear.
To do it:
```
gksudo gedit /etc/apache2/httpd.conf
```By default, it would be blank. Simply add the following line:```
ServerName localhost
```Save the file, exit gedit and restart the server:```
service apache2 restart
```
If you have a name inside your **/etc/hostname** file, you can also use that name instead of localhost.

---

### Post by jairoh_ on 2013-05-30
it tried ur suggestion man but it didn't work.

when i ran 
```
service apache2 restart
```

this appeared
```

* Restarting web server apache2
/usr/sbin/apache2ctl: 87: ulimit: error setting limit (Operation not permitted)
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri May 31 07:49:37 2013] [warn] _default_ VirtualHost overlap on port 8080, the first has precedence
/usr/sbin/apache2ctl: 87: ulimit: error setting limit (Operation not permitted)
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri May 31 07:49:38 2013] [warn] _default_ VirtualHost overlap on port 8080, the first has precedence
(13)Permission denied: make_sock: could not bind to address [::]:80
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
                                                                         [fail]

```



but when i ran w/ sudo as prefix


```
sudo service apache2 restart
```
this still appeared
```

* Restarting web server apache2                                                
apache2: Could not reliably determine the server's fully qualified domain name, using [COLOR=#ff0000]**127.0.1.1**[/COLOR] for ServerName
[Fri May 31 07:49:51 2013] [warn] _default_ VirtualHost overlap on port 8080, the first has precedence
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using [COLOR=#ff0000]**127.0.1.1**[/COLOR] for ServerName
[Fri May 31 07:49:52 2013] [warn] _default_ VirtualHost overlap on port 8080, the first has precedence
                                                                         [ OK ]

```

as you can see. it uses 127.0.1.1 not 127.0.0.1. tsk

---

### Post by slickymaster on 2013-05-31
It uses 127.0.1.1 because it is inside your **/etc/hosts **file:
```
127.0.0.1 localhost
127.0.1.1 myhostname
```

---

### Post by Bachstelze on 2013-05-31
You need to add

```
NameVirtualHost *:8080
```

somewher ein your config to get rid of the overlap. You can ignore the other warning.

---

