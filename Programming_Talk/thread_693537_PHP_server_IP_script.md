---
title: "PHP server IP script"
date: 2008-02-11
forum: Programming Talk
---

### Post by The Titan on 2008-02-11
Im just going to start from the beginning for this one ;)

Ok, I have a domain name hosted by a 3d party.  I also have a sorry home server that as a use as a testing environment,  The problem is i have a dynamic IP. 

 Is it possible to make a script (cron job maybe?) that gets my ip from the internet and send it to the domain with a form? I can do any scripting in PHP or do forms but i dont know how to get my server IP.

If this is confusing, or you need more information please tell me.

Thank you, 
-Dan

---

### Post by bobbocanfly on 2008-02-11
You could try

```
$_server['server_ADDR'];
```

---

### Post by The Titan on 2008-02-11
Thank you for that, How would i go about running that PHP script every 5 minutes?  Could i use a CronJob? I've never used them before.

-Dan

---

### Post by bobbocanfly on 2008-02-11
> **The Titan said:**
> Thank you for that, How would i go about running that PHP script every 5 minutes?  Could i use a CronJob? I've never used them before.

-Dan

I have never used PHP-CLI before but my guess is yeah you could use it as a cronjob. Im pretty sure there is a tutorial around here that tells you exactly what to do.

---

### Post by bsharp on 2008-02-12
...or you could use dynamic DNS which would accomplish the same thing and probably be easier to set up

---

### Post by miked595 on 2008-03-02
Yea dynamic dns would work better. I have these script on my site that work on ubuntu.

[http://www.xpertdns.com/wiki/index.php/IpTeller](http://www.xpertdns.com/wiki/index.php/IpTeller)
[http://www.xpertdns.com/wiki/index.php/Java_Apps:DynamicDNSclient](http://www.xpertdns.com/wiki/index.php/Java_Apps:DynamicDNSclient)

---

### Post by The Titan on 2008-03-02
Thank you for the replies, like bobbocanfly said there was a tutorial with exactly what i needed as far as the cronjob goes and i got it all set up.

-Dan

---

### Post by raj_arjun on 2009-07-17
OK.. well this script workson ma local system and gives me its ip correctly

hope it ll help :P
```

<?php 


$last_line = exec("/sbin/ifconfig", $op); 

$line = $op[1];
$peices =  explode(" ",trim($line));
$ips = explode(":",trim($peices[1]));
$system_ip =  trim($ips[1]);

?>
```

---

### Post by curvedinfinity on 2009-07-17
Some home routers have ddns built in. You just have to tell the router your login info and it will keep your dynamic domain's host up to date with your IP.

I know Rosewill and D-Link routers come with this.

Here's the biggest ddns provider:
[http://www.dyndns.com/](http://www.dyndns.com/)

Its a free service for a subdomain.

---

