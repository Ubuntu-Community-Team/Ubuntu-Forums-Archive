---
title: "Cannot get squid to work"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by TheTrulli on 2013-02-03
Hi,

I am trying to set up a proxy server (squid). However, when I want to connect to a website using my proxy, I recieve the following response:

```

he following error was encountered while trying to retrieve the URL: http://www.google.com/

    Connection to 2607:f8b0:400c:c03::6a failed.

The system returned: (110) Connection timed out

The remote host or network may be down. Please try the request again.

```

For me it seems that I am able to connect to squid, but squid is not able to connect to the internet. However, if I run "wget www.google.com" via SSH on the ubuntu server, the website is downloaded.

I am kind of stuck here since I do not know how to deal with that. Can anyone help, please?

Regards,

TheTrulli

---

### Post by TheFu on 2013-02-03
Are you trying to use IPv6 specifically?

---

### Post by theHAAG on 2013-04-10
im having the same issue, whats your solution???

---

### Post by labradorg13 on 2013-05-03
> **TheTrulli said:**
> Hi,

I am trying to set up a proxy server (squid). However, when I want to connect to a website using my proxy, I recieve the following response:

```

he following error was encountered while trying to retrieve the URL: http://www.google.com/

    Connection to 2607:f8b0:400c:c03::6a failed.

The system returned: (110) Connection timed out

The remote host or network may be down. Please try the request again.

```

For me it seems that I am able to connect to squid, but squid is not able to connect to the internet. However, if I run "wget www.google.com" via SSH on the ubuntu server, the website is downloaded.

I am kind of stuck here since I do not know how to deal with that. Can anyone help, please?

Regards,

TheTrulli


I hope you have a corretct installation of your squid proxy.

if nothing happens, try disable your firewall.

> 

*** [http://www.krizna.com/centos/how-to-install-squid-proxy-on-centos-6/](http://www.krizna.com/centos/how-to-install-squid-proxy-on-centos-6/)
If you not able to browse using proxy settings , Disable the firewall ( iptables ) and selinux service on your squid proxy server .
Disable firewall ( Iptables ) »
[root@leela ~]# service iptables stop
[root@leela ~]# chkconfig iptables off

Disable Selinux  » open the file /etc/selinux/config and find the line
SELINUX=enforcing

and replace with
SELINUX=disabled

now reboot the server.



---

