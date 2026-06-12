---
title: "Firewall and ftp access"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by JuanNZ on 2012-02-08
Hi All,

I enabled a firewall on my PC using the ufw GUI version provided in Ubuntu 11.04. I did so, and created a set of rules, following the instructions given in this wonderful thread about... [firewalls]("http://ubuntuforums.org/showthread.php?t=1871177")

Every now and then I need to access files on an ftp server at my workplace. I was accessing the ftp server via Nautilus OK. This ftp server is set up using Windows protocols.

Now I cannot access it any more while the firewall is enabled. I tried to include the ports that enable SAMBA and ftp on the firewall rules, but this does not solve the problem. I heard that ftp is incredibly insecure as well, so I will not like to compromise my security by disabling the firewall just to access the ftp server. 

Any ideas?

Thanks, 

Juan

---

### Post by SeijiSensei on 2012-02-08
See if you can connect to the server in "passive" mode.

---

### Post by JuanNZ on 2012-02-08
> **SeijiSensei said:**
> See if you can connect to the server in "passive" mode.

Sorry, can you please elaborate more on this?

---

### Post by alphacrucis2 on 2012-02-08
ftp has two methods of transferring data. Active and passive mode. See this:

[http://slacksite.com/other/ftp.html](http://slacksite.com/other/ftp.html)

That said the firewall should handle both as netfilter/iptables should recognise both as long as your rules allow RELATED connections via conntracking.

Some more here:

[http://beginlinux.com/blog/2009/10/ubuntu-9-10-ftp-connections/](http://beginlinux.com/blog/2009/10/ubuntu-9-10-ftp-connections/)

Make sure your ufw default config is loading the appropriate conntrack modules. From the link above:


/etc/default/ufw

IPV6=no
DEFAULT_INPUT_POLICY=&#8221;DROP&#8221;
DEFAULT_OUTPUT_POLICY=&#8221;ACCEPT&#8221;
DEFAULT_FORWARD_POLICY=&#8221;DROP&#8221;
DEFAULT_APPLICATION_POLICY=&#8221;SKIP&#8221;
MANAGE_BUILTINS=no
IPT_SYSCTL=/etc/ufw/sysctl.conf
[COLOR="Red"]IPT_MODULES=&#8221;nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc&#8221;[/COLOR]

---

### Post by JuanNZ on 2012-02-08
Thanks for the links, 

> 

[http://beginlinux.com/blog/2009/10/ubuntu-9-10-ftp-connections/](http://beginlinux.com/blog/2009/10/ubuntu-9-10-ftp-connections/)

Though I could not open the above link for some reason.

> 

Make sure your ufw default config is loading the appropriate conntrack modules. From the link above:


```
/etc/default/ufw

IPV6=no
DEFAULT_INPUT_POLICY=&#8221;DROP&#8221;
DEFAULT_OUTPUT_POLICY=&#8221;ACCEPT&#8221;
DEFAULT_FORWARD_POLICY=&#8221;DROP&#8221;
DEFAULT_APPLICATION_POLICY=&#8221;SKIP&#8221;
MANAGE_BUILTINS=no
IPT_SYSCTL=/etc/ufw/sysctl.conf
IPT_MODULES=&#8221;nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc&#8221;
```

I opened the document you suggested. The module you mention is correct. 

However the  default output policy is like this:

DEFAULT_OUTPUT_POLICY=&#8221;DROP&#8221;

So I suppose I did not configured my firewall properly?

Hi All, 

I managed to solve the problem by allowing one more outbound rule on my firewall. The rule allows the outbound traffic of ports 1024:65535. This enables nautilus to connect to the FTP server with a passive protocol.

Now my question is, the range 1024:65535 is  very big. Does that put me in any kind of risk?

---

### Post by SeijiSensei on 2012-02-10
If that's an outbound rule, then no, it shouldn't matter.  Limiting outbound traffic makes sense if you don't trust the client machines on your network or the people using them.  

For instance, at one client site, we block all traffic from those high ports to remote high ports to block torrents, streaming services, and the like.  But we don't block connections from client high ports to remote restricted ports in the 0-1023 range.

---

