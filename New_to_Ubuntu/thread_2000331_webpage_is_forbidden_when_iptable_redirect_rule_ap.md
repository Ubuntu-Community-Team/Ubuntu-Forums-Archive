---
title: "webpage is forbidden when iptable redirect rule applied"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by kashif_max on 2012-06-09
Hi,
I am running squid, iptable and apache on a single machine (Ubuntu 10.04) with 1 NIC (192.x.x.1). I have the following config in apache.conf.
```
<Directory /var/www/sarg>
 order deny,allow
 deny from all
 allow from 192.x.x.10
 allow from 192.x.x.20
</Directory>
```

The users (192.x.x.10 & 192.x.x.20) can access the server's squid logs and others are forbidden. But when I apply this rule. 
```
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
```
Than no one can see the logs. Is there a way that I can tell to firewall that the users can access [http://192.x.x.1/sarg](http://192.x.x.1/sarg).

Thanks

---

### Post by SeijiSensei on 2012-06-09
The easiest solution is to bind the log virtual host to a different port than 80. 

```

Listen 8080
<VirtualHost *:8080>
[stuff]
<Directory /var/www/sarg>
 order deny,allow
 deny from all
 allow from 192.x.x.10
 allow from 192.x.x.20
</Directory>
[stuff]
</VirtualHost>

```

With iptables you could try exempting connections to the server itself like this:

```

iptables -t nat -A PREROUTING -i eth0 -p tcp -d ! 192.168.0.0/16 --dport 80 -j REDIRECT --to-port 3128
```

would only push connections for offsite destinations through Squid.

---

### Post by kashif_max on 2012-06-09
Thanks for the quick reply. I will try it out and let you know. God Bless You...

---

### Post by kashif_max on 2012-06-10
Thank you so much, both stuff are working perfectly. Just one note in my case, if apache is installed through apt-get than its likely going to include ports.conf and virtual host configuration file. Change the ports there and add the above code in virtual host file...

Thanks SeijiSensei for helping... Marking as solved

---

