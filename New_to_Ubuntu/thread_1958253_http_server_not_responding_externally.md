---
title: "http server not responding externally"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by sirgogo on 2012-04-13
Hi all,

Sorry, a little out of touch setting up http servers in Linux. Here is my console output.

```
user@compy386:~$ netstat -lnptu
(No info could be read for "-p": geteuid()=1000 but you should be root.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
udp        0      0 0.0.0.0:33734           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 192.168.1.14:123        0.0.0.0:*                           -               
udp        0      0 127.0.0.1:123           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:123             0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp6       0      0 :::47194                :::*                                -               
udp6       0      0 ::1:123                 :::*                                -               
udp6       0      0 fe80::216:17ff:feee:123 :::*                                -               
udp6       0      0 :::123                  :::*                                -               
udp6       0      0 :::5353                 :::*                                -     
```

Here is what my /etc/apache2/apache2.conf looks like:

```
user@compy386:~$ cat /etc/apache2/sites-available/default
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	ServerName my.server.ip.here

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

I set up port forwarding for http and for ssh via my router. The ssh port forwarding seems to be working since I can ssh into my server. The apache server on seems to be working because I can point my browser to the local IP and to the external IP while I'm on LAN and it will be directed to the index.html page I set. However, I get an "unable to connect" type return when pointing my browser from outside my LAN.

Check this:
```
ping 68.99.181.151
PING 68.99.181.151 (68.99.181.151) 56(84) bytes of data.
64 bytes from 68.99.181.151: icmp_req=1 ttl=241 time=31.7 ms
64 bytes from 68.99.181.151: icmp_req=2 ttl=241 time=23.9 ms
^C
--- 68.99.181.151 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 23.911/27.836/31.761/3.925 ms

```
but
```
ping 68.99.181.151:80
ping: unknown host 68.99.181.151:80

```

Any ideas guys? Thanks in advance

---

### Post by alex2e1gzy on 2012-04-14
Can you ping to port 80 like that? Wouldn't it be better to telnet insted?
 
I would suggest that the problem lies with your port forwarding rule. Could you try forwarding port external:8080 to internal:80? Are you able to post your rule? Another idea would be to check your error log... could Apache be ignoring the requests from IP addresses other than those inside your network?

---

### Post by sirgogo on 2012-04-15
Thanks for the reply dude.

Good catch, I wasn't using the ping command properly. But alas, still no luck:
```
telnet 68.99.181.155 80
Trying 68.99.181.155...
^C

```

Where do I find my rule?

---

### Post by sirgogo on 2012-04-16
I think I figured it out. My ISP (Cox) blocks incoming port 80, that's why I could access the site internally but couldn't ping the port externally.

---

