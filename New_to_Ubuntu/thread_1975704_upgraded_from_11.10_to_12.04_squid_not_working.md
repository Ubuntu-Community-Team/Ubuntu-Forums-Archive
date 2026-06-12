---
title: "upgraded from 11.10 to 12.04 squid not working"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by lance bermudez on 2012-05-07
hi want squid working again set fire fox for my ip 1.2.4.5 port 3128 get 
The proxy server is refusing connections
Firefox is configured to use a proxy server that is refusing connections.
Check the proxy settings to make sure that they are correct.
Contact your network administrator to make sure the proxy server is working.

I have attaced my config file. and no I keep the same old config I did not change it and yes it was working under the old 11.10 system.

---

### Post by lance bermudez on 2012-05-07
[https://help.ubuntu.com/12.04/serverguide/squid.html](https://help.ubuntu.com/12.04/serverguide/squid.html)
[https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)

Had to install squid3 still will not work. used the above to configure squid3. need squid3 to work with squidGuard. attached is config file

---

### Post by lance bermudez on 2012-05-08
made backups then used synaptic to remove squid, squid3 and squidGuard with all config files. delete /etc/squid then used synaptic to reinstall squid3 and squidGuard. Squid3 is now in /etc/squid3 had it working with the changes I had made in the old config. reinstalled squidGuard is in /etc/squid not /etc/squid3 made changes that i had in old config. Now it hangs during install and squid say 
The following error was encountered while trying to retrieve the URL: [http://admin.foo.bar.de/cgi-bin/blocked.cgi?](http://admin.foo.bar.de/cgi-bin/blocked.cgi?)
    Unable to determine IP address from host name "admin.foo.bar.de"
The DNS server returned:
    Name Error: The domain name does not exist.
This means that the cache was not able to resolve the hostname presented in the URL. Check if the address is correct.
Your cache administrator is webmaster.

used script (made to run with cron) in /root/bin
#!/bin/bash
#[http://www.shallalist.de/](http://www.shallalist.de/)
#
cd /var/lib/squidguard/db;
rm -vrf */ ;
axel [http://www.shallalist.de/Downloads/shallalist.tar.gz](http://www.shallalist.de/Downloads/shallalist.tar.gz) ;
tar --strip 1 -xvzf shallalist.tar.gz ;
rm shallalist.tar.gz ;
chown -R proxy:proxy /var/lib/squidguard/db/;
find /var/lib/squidguard/db -type f | xargs chmod 644 ;
find /var/lib/squidguard/db -type d | xargs chmod 755 ;
sudo -u proxy squidGuard -b -C all;

I have attached my config files.

---

### Post by lance bermudez on 2012-05-08
in the squidGuard.conf comment out

default {
pass local none
redirect [http://admin.foo.bar.de/cgi-bin/bloc...roup=%t&url=%u](http://admin.foo.bar.de/cgi-bin/bloc...roup=%t&url=%u)
}
} 

#default {
#pass local none
#redirect [http://admin.foo.bar.de/cgi-bin/bloc...roup=%t&url=%u](http://admin.foo.bar.de/cgi-bin/bloc...roup=%t&url=%u)
#}
#} 

working agin is squid now not squidguard it still hangs look at pic.

---

### Post by lance bermudez on 2012-05-08
working now 
squidGuard.conf looks like

#
# CONFIG FILE FOR SQUIDGUARD
#
# Caution: do NOT use comments inside { }
#

dbhome /var/lib/squidguard/db
logdir /var/log/squid

dest remotecontrol {
        domainlist      remotecontrol/domains
        urllist         remotecontrol/urls
}

dest spyware {
        domainlist      spyware/domains
        urllist         spyware/urls
}

dest porn {
        domainlist      porn/domains
        urllist         porn/urls
}


acl {
        default {
                pass !remotecontrol !spyware !porn all
                redirect [http://www.linuxjournal.com/magazine/paranoid-penguin-building-secure-squid-web-proxy-part-iv](http://www.linuxjournal.com/magazine/paranoid-penguin-building-secure-squid-web-proxy-part-iv)
	}
}

---

