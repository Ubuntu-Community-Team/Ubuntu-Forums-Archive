---
title: "How to test if a host &quot;exists&quot; (host anmed resolvable)   from a script?"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by javafanboy on 2012-01-05
I would like to check if a network host "exists" (I am happy with if the address can be resolved)from a script but dont know how to do it :(

I would like to use this in order to check if a proxy server exists and in that case set it up as "system wide" proxy (perhaps I also need to update or perhaps switch between two different APT config files or does APT and package manager obey the proxy environment variables?)

/Javafanboy

---

### Post by lechien73 on 2012-01-05
You can check if a network host is resolvable, and then set an environment variable accordingly by using the following script:

```

proxy=`ping -w 1 -c 1 192.168.1.1 | grep '1 received'`

if [ -n "$proxy" ];
then
   export http_proxy=http://192.168.1.1:8080
   export ftp_proxy=http://192.168.1.1:8080
fi

```apt does obey the proxy environment variables, so the above code should work. Obviously change the IP address and port for your proxy settings.

---

