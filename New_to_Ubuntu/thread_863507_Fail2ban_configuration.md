---
title: "Fail2ban configuration"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by richiewrt on 2008-07-18
Ok, I just installed fail2ban because I read about it in another post and realized I should have it running on my server. My questions is I am trying to configure it and I am working in the jail.conf file. The default value for ignoreip is 127.0.0.1, and I want to add all the IP's behind my firewall, but they are assigned by DHCP, so my question is can I just add 192.168.1.255 and will this allow all 192.168.1.xxx addresses on the ignore list, or does it have to be specific ip addresses?

---

### Post by bodhi.zazen on 2008-07-18
I would only allow specific IP addresses.

Otherwise you may need to try a few enteries by trial and error.

I would start with :

192.168.1.1/24

---

### Post by eldragon on 2008-07-18
just remember there is a nice little bug on fail2ban which fails to start after a reboot.

to fix it, just create the dir /var/run/fail2ban and restart the service with sudo /etc/init.d/fail2ban start

---

