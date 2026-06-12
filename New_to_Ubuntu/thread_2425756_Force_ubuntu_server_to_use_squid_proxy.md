---
title: "Force ubuntu server to use squid proxy?"
date: 2019-08-29
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2019-08-29
I want to know if there is a global directive that forces Ubuntu server to use the squid proxy. I've found varying ideas, some with having to put proxy settings on every app, some with the /etc/environment file. Don't want to reboot unless I have to so what is the way to globally force my server to use the proxy?

---

### Post by SeijiSensei on 2019-08-29
We need a bit more information.  Do you have another machine running Squid?  Or is it running on the machine itself?

Squid works well for HTTP.  It takes a [bit of effort]("https://advsoft.info/articles/setting_up_HTTPS_inspection_in_squid.php") to get it to proxy HTTPS connections to avoid the appearance of "man-in-the-middle" attacks.  In order to make this work, you need to install a certificate into any client software like web browsers.  That poses a serious limit on your ability to proxy any and all SSL connections.

On the machine running Squid, you can push all the connections destined for a particular remote port through the proxy with iptables like this:

```

/sbin/iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128  --destination-port 80

```

That intercepts outbound port 80 requests and pushes them through Squid listening on port 3128.  You also need to add the "transparent" keyword to the http_port directive in squid.conf:

```
http_port 3128 transparent
```

At a client site, we have about 200 machines behind a Squid proxy running on their firewall gateway that uses this method.

I'd definitely start slowly and see if you can get HTTP requests to go through the proxy.

Pushing all outbound requests for any remote service through the proxy is pretty much not on though.

---

### Post by Tadaen_Sylvermane on 2019-08-29
It's on the machine itself. More experimentation than anything. I thought i had it working as I pointed my desktop to use the proxy for http and https and everything was going through. It's just for home use but if I can't easily proxy my whole lan without a lot of headaches it isn't worth it. It even showed my desktop running stuff in the access log on the server. Is why I thought I had it working for both.

It amazes me there isn't a simple guide that makes even just HTTP work. I had to mess with 5 or 6 guides to ultimately find all the things needed to be done just to get this far. Each one on its own just left me with unable to connect to anything from my desktop. This is on 16.04 btw.

---

