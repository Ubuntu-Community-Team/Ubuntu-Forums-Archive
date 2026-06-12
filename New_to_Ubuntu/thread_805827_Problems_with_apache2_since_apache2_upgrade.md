---
title: "Problems with apache2 since apache2 upgrade"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by reeksy on 2008-05-24
Hi

I'm trying to restart apache But i get the following:

```

$ /etc/init.d/apache2 restart

```

```

open: Permission denied
 * Restarting web server apache2                                                                                                                                                 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 6511?) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:8080
no listening sockets available, shutting down
Unable to open logs
open: Permission denied

```

..hummm!

I'm a bit stuck here!

I tried to run the command as root, this time i get a slightly different message:

```

# /etc/init.d/apache2 restart

```

```

 * Restarting web server apache2                                                                                                                                                 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:8080
no listening sockets available, shutting down
Unable to open logs

```

This suggests to me that the old version of apache is still running or port 80? But I'm not entirely sure!

Any help would be great.

Regards,
Jon

---

### Post by superprash2003 on 2008-05-24
do a [http://127.0.0.1](http://127.0.0.1) if any page opens then old apache is running

---

### Post by quelx on 2008-05-24
you need to put **sudo** in front of the apache restart, normal users can't restart most system services

```
sudo /etc/init.d/apache2 restart
```

for the hostname, edit the /etc/hosts file

```
sudo nano -w /etc/hosts
```

look for the line 127.0.0.1 and add to the end of it (probably after localhost, your hostname (i.e. myhostname.com)

```
127.0.0.1 localhost myhostname.com
```
**CTRL-X** to save and exit

restart apache again

Your wesite should show up at [http://127.0.0.1:8080](http://127.0.0.1:8080) or [http://localhost:8080](http://localhost:8080) (on the local machine only) or [http://myhostname.com:8080](http://myhostname.com:8080)

---

