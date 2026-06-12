---
title: "ufw not working correctly - ports not open"
date: 2015-10-11
forum: New to Ubuntu
---

### Post by bluethundr2 on 2015-10-11
Hey all, 


I've setup apache on an ubuntu 14.04 instance on AWS. Apache is started and listening on ports 80 and 443:

```
[root@ldap1:~] #lsof -i :80
COMMAND   PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
apache2 16382     root    4u  IPv6  30914      0t0  TCP *:http (LISTEN)
apache2 16385 www-data    4u  IPv6  30914      0t0  TCP *:http (LISTEN)
apache2 16386 www-data    4u  IPv6  30914      0t0  TCP *:http (LISTEN)
apache2 16387 www-data    4u  IPv6  30914      0t0  TCP *:http (LISTEN)
apache2 16388 www-data    4u  IPv6  30914      0t0  TCP *:http (LISTEN)
apache2 16389 www-data    4u  IPv6  30914      0t0  TCP *:http (LISTEN)

```

```
[root@ldap1:~] #lsof -i :443
COMMAND   PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
apache2 16382     root    6u  IPv6  30918      0t0  TCP *:https (LISTEN)
apache2 16385 www-data    6u  IPv6  30918      0t0  TCP *:https (LISTEN)
apache2 16386 www-data    6u  IPv6  30918      0t0  TCP *:https (LISTEN)
apache2 16387 www-data    6u  IPv6  30918      0t0  TCP *:https (LISTEN)
apache2 16388 www-data    6u  IPv6  30918      0t0  TCP *:https (LISTEN)
apache2 16389 www-data    6u  IPv6  30918      0t0  TCP *:https (LISTEN)

```

UFW is active and has both those ports listed as allowed:

```
[root@ldap1:~] #ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip


To                         Action      From
--                         ------      ----
443                        ALLOW IN    Anywhere
80                         ALLOW IN    Anywhere
22                         ALLOW IN    Anywhere
443 (v6)                   ALLOW IN    Anywhere (v6)
80 (v6)                    ALLOW IN    Anywhere (v6)
22 (v6)                    ALLOW IN    Anywhere (v6)

```

However for some reason I am still not able to access those ports from my browser or the command line:

```
[bluethundr@JEC206429674LM-2:~] #telnet ldap1.example.com 80
Trying 10.10.10.50...
telnet: connect to address 10.10.10.50: Operation timed out
telnet: Unable to connect to remote host


[bluethundr@JEC206429674LM-2:~] #telnet ldap1.example.com 443
Trying 10.10.10.50...
telnet: connect to address 10.10.10.50: Operation timed out
telnet: Unable to connect to remote host

```

I get no response from the web browser when hitting that web server on either port 80 or port 443

And nmap lists those ports as filtered:
```
bluethundr@JEC206429674LM-2:~] #nmap -P0 -p 80 ldap1.example.com


Starting Nmap 6.47 ( http://nmap.org ) at 2015-10-11 10:34 EDT
Nmap scan report for ldap1.example.com (10.10.10.50)
Host is up.
rDNS record for 10.10.10.50: ec2-10-10-10-50.compute-1.amazonaws.com
PORT   STATE    SERVICE
80/tcp filtered http


Nmap done: 1 IP address (1 host up) scanned in 2.27 seconds


[bluethundr@JEC206429674LM-2:~] #nmap -P0 -p 443 ldap1.example.com


Starting Nmap 6.47 ( http://nmap.org ) at 2015-10-11 10:35 EDT
Nmap scan report for ldap1.example.com (10.10.10.50)
Host is up.
rDNS record for 10.10.10.50: ec2-10-10-10-50.compute-1.amazonaws.com
PORT    STATE    SERVICE
443/tcp filtered https


Nmap done: 1 IP address (1 host up) scanned in 2.06 seconds

```

What am I doing wrong and how can I open up these ports on ubuntu 14.04?

---

### Post by bluethundr2 on 2015-10-11
oh! Never mind. I was on AWS and I forgot to open the port in the security group. Did that and it works now. Silly me!

---

