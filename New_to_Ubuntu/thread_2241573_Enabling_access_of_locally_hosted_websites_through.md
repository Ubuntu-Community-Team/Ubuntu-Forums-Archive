---
title: "Enabling access of locally hosted websites through squid"
date: 2014-08-27
forum: New to Ubuntu
---

### Post by Jovin_Thariyath on 2014-08-27
I have setup a squid proxy in my office.We have to connect to another  company VPN and have to access locally hosted websites in that  company through that VPN .The problem is that through squid we cannot access those locally  hosted websites.Everything except works great.Any suggestions?

---

### Post by SeijiSensei on 2014-08-27
Probably because squid cannot resolve the correct hostnames.  Does your organization have an internal DNS server?

Try to connect to those sites using a browser on the squid box.  If it doesn't have a GUI, use elinks.  Give it the identical URL you would use to connect from a machine behind the proxy.  What happens?

You might either need to change the DNS resolver configuration on this machine to use a DNS server with entries for those sites, or, perhaps easier, add entries for those sites to the /etc/hosts file on the squid box.

---

### Post by Jovin_Thariyath on 2014-08-28
[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195") Thanks for your reply.
I have added the other company nameservers(they are using local) to the resolv.conf of our squid machine still no change.Another question is that these websites are accessible only through their vpn and i have not connected to their vpn in my sqiud machine is that the root cause? sorry if its a dumb question.

---

### Post by sotiris2 on 2014-08-28
If the sites are in their local network then ofcourse you will need a connection to that, which probably is via the vpn. If it still doesn't work try acessing the sites via their ip (type it instead of the adress in the browser).

---

### Post by Jovin_Thariyath on 2014-08-28
Thanks for the help [**[COLOR=#000000]sotiris2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1845661") and [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195") the issue got fixed when i set up connection via vpn. :)

---

