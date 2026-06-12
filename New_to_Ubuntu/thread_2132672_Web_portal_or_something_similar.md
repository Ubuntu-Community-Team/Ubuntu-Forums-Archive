---
title: "Web portal or something similar?"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by fatgeek on 2013-04-05
Hey All,

I have no idea if this is in the correct section. If not, I apologize.

Basically, I have multiple machines running in my house and each of those machines are running multiple HTTP servers. Things like webmin, sabnzbd, sickbeard, etc. In order to access these various services from outside of my house I have to forward multiple ports to the various machines. I wonder if there is a way to only have to only have an open port to one machine, and then access the various services through it. I have thought of possibly loading the other pages inside of a frame in an html page, or possibly using something like Glype to show them. 

Does anyone know of a good, easy, reliable way to do this?

---

### Post by sandyd on 2013-04-05
You can use iptables (for stuff without web interfaces) or nginx (for web interfaces) to accomplish this.

For example, in a nginx virtual host, you can map different urls to different servers.
```

location / {
     proxy_pass  http://ip-for-server;
     proxy_next_upstream error timeout invalid_header http_500 http_502 http_503 http_504;
     proxy_redirect off;
     proxy_buffering off;
     proxy_set_header        Host            $host;
     proxy_set_header        X-Real-IP       $remote_addr;
     proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
   }

```

Once you have that setup, you can map different urls to different places, like
```

location /deluge {
     proxy_pass  http://deluge-webinterface-ip;
     proxy_next_upstream error timeout invalid_header http_500 http_502 http_503 http_504;
     proxy_redirect off;
     proxy_buffering off;
     proxy_set_header        Host            $host;
     proxy_set_header        X-Real-IP       $remote_addr;
     proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
   }
```

---

### Post by Cheesemill on 2013-04-05
You can do the same thing using Apache and mod_proxy to redirect requests for different servers to their internal IP addresses based on the URL.

[http://httpd.apache.org/docs/2.2/vhosts/examples.html#proxy](http://httpd.apache.org/docs/2.2/vhosts/examples.html#proxy)

---

