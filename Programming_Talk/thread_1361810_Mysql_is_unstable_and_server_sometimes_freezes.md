---
title: "Mysql is unstable and server sometimes freezes"
date: 2009-12-22
forum: Programming Talk
---

### Post by cronick on 2009-12-22
Hello,

I have a server running Plesk on Ubuntu. I am not very in to the part about optimizing the MySQL server and tweaking the server in general. I spend my time making websites instead. 

I have just moved a rather "active" website to the server, which daily gets about 3000 unique visitors. I know it is also very query-consuming and uses a lot of images - and therefore generates quite some bandwidth. However, it seems to work just fine. As lang as there are not any higher than 100 online at the same time. Any more than that and some things start to happen. The mysqld service is apparently consuming a lot of CPU usage and in worst case the server suddently freezes, and I need to restart it to work normally again. 

Does anybody have an idea to what my problem is caused by, or what I might be doing wrong?

I have inserted a screendump of what the "top" command returning at some point. I have also inserted the "status" command to the /etc/init.d/mysql in case it could be of any use.

[IMG]http://img97.imageshack.us/img97/5475/ubuntutop.jpg[/IMG]

:~# /etc/init.d/mysql status
 * /usr/bin/mysqladmin  Ver 8.41 Distrib 5.0.51a, for debian-linux-gnu on x86_64
Copyright (C) 2000-2006 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Server version          5.0.51a-3ubuntu5.4
Protocol version        10
Connection              Localhost via UNIX socket
UNIX socket             /var/run/mysqld/mysqld.sock
Uptime:                 30 min 9 sec

Threads: 1  Questions: 127141  Slow queries: 6  Opens: 848  Flush tables: 1  Open tables: 64  Queries per second avg: 70.282

---

### Post by Can+~ on 2009-12-22
What's the content of mysql's log? (/var/log/mysql I guess).

---

### Post by cronick on 2009-12-22
That directory is empty. And for some reasons, so are the /var/log/mysql.log and /var/log/mysql.err.. :confused:

---

### Post by Can+~ on 2009-12-22
> **cronick said:**
> That directory is empty. And for some reasons, so are the /var/log/mysql.log and /var/log/mysql.err.. :confused:

Well, the logging might be disabled, because it's a production environment. Have it enabled for a while and collect the data.

Also, check that particular version of mysql for related bugs. And also, what type of engine is the DB? The default InnoDB? What settings?

---

### Post by mike_g on 2009-12-23
Some ideas could be:

[LIST]
[*]cache as much of your sites content as possible to reduce redundant queries
[*]enable slow query logging in my.cnf to find where your bottleneck queries are
[*]make sure all columns used in joins are indexed
[*]add flood protection to your site to limit the number of page requests that can come in quick succession
[*]split large frequently accessed tables into two with one holding smaller more frequently acccessed fields
[/LIST]

Oh, and theres also [mytop](http://jeremy.zawodny.com/mysql/mytop/)

---

### Post by Can+~ on 2009-12-23
[LIST]
[*]Abuse the keyword LIMIT X when doing queries, sometimes you end up pulling more registers than necessary. Prefer doing LIMIT than having to cut it down afterwards.
[*]Create better indices for tables that have lower insertion rate, and higher selection rate. Indices are expensive to compute and build, but they improve access time.
[/LIST]

There's so many things that could go wrong, we need more information. Can you show the data model? Do profiling? And the logs are quite important to track where the clog is (as mike_g suggested).

---

### Post by cronick on 2009-12-27
> **Can+~ said:**
> Well, the logging might be disabled, because it's a production environment. Have it enabled for a while and collect the data.
 
Also, check that particular version of mysql for related bugs. And also, what type of engine is the DB? The default InnoDB? What settings?
 
How do I enable MySQL logging?
 
The tables in the databases are apparently a mixture of both innoDB and MyISAM.
 
Thanks for the input. I will study these hard and try to make as much optimization as I can. 
 
I however have a real serious problem now regarding the server. Without me doing anything, the apache2 service is now acting really wierd. It suddently stopped working, so I restarted the server (which I had done a couple of times before when it started to act wierd - probably because of overload). This time it however did not help, since the apache2 service will not start. It is giving me the error:
 
echo655:~# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                            (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                                                     [fail]

I have searched for any similar problems that people might have had but I cannot find any solution to my problem. Sometimes I get lucky and the service do start but then after a couple of minutes it freezes again. What I don't get is why the Plesk Panel always is available through the internet - eventhough apache2 is not running. Maybe thats because of the different port it is using (8443), but I don't know.
 
Any help is appreciated.

---

### Post by cronick on 2009-12-29
I solved the issue. By looking through the incoming tcp request, a specific IP address was trying to overload the webserver - and with success. After I blocked that IP in the firewall the problem has not occured since. I believe that term for what the person was doing is called DoS attacking. Do you know how to prevent this in the future? Also, how do I setup Apache so it will not freeze again if 100 simultanious threads are running?

---

### Post by mike_g on 2010-01-05
Sound like you need to add flood protection to your site.

For Apache, heres a module that should do it: [http://www.crucialp.com/resources/tutorials/server-administration/flood-protection-dos-ddos-protection-apache-1.3-2.0-mod_dosevasive-avoiding-denial-of-service-attacks.php](http://www.crucialp.com/resources/tutorials/server-administration/flood-protection-dos-ddos-protection-apache-1.3-2.0-mod_dosevasive-avoiding-denial-of-service-attacks.php) 

Alternatively you could add a bit of script that runs at the start of any page request that adds an iplog and time to an in-ram table. The script counts the number of requests that came from the IP in the last second or so and if its greater than x you stop the page from loading. Just remember to delete all rows that are older than a second old too.

Chances are its just some idiot clicking on links as fast as possible, and the problem should go away.

---

