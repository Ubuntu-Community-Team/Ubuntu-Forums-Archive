---
title: "What is the best firewall for a web server? UFW? APF? Something Else?"
date: 2012-08-24
forum: Recurring Discussions
---

### Post by THPubs on 2012-08-24
Im trying to configure a web server and just want to know what firewall should I install in it? APF? UFW? or something else?

---

### Post by Lars Noodén on 2012-08-24
[UFW](https://help.ubuntu.com/community/UFW) and the others are just front-ends for iptables.  So you could use either.  I gather that UFW is the officially supported front-end so you could go with that unless you want or need extras like rate limiting.

---

### Post by THPubs on 2012-08-24
> **Lars Noodén said:**
> [UFW](https://help.ubuntu.com/community/UFW) and the others are just front-ends for iptables.  So you could use either.  I gather that UFW is the officially supported front-end so you could go with that unless you want or need extras like rate limiting.

We can use programs like fail2ban for rate limiting right?

---

### Post by 2F4U on 2012-08-25
> **THPubs said:**
> We can use programs like fail2ban for rate limiting right?

You are right:

[https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban)

---

### Post by Lars Noodén on 2012-08-25
Rate limiting is also built into iptables.  So if you work directly with iptables, you don't need extras.  It's a little harder to find good documentation on iptables, though, but it is the simplest way to go.

```

...
  iptables -A INPUT -p icmp --icmp-type echo-request \
        -m limit --limit 1/s -i eth0 -j ACCEPT
...
  iptables  -A INPUT -p TCP --dport 22 -m state --state NEW \
        -m limit --limit 4/minute --limit-burst 5 -j ACCEPT
...
  iptables -A INPUT -p TCP -j RETURN

```

---

### Post by samiux on 2012-08-25
> **THPubs said:**
> Im trying to configure a web server and just want to know what firewall should I install in it? APF? UFW? or something else?

I would like to recommend application firewall for web server.  However, those are add-ons to the web server.

If you want a lightweight, fast and secure web server, I would recommend [Hiawatha]("http://www.hiawatha-webserver.org/").

Why I suggest Hiawatha?  It is because of her [features]("http://www.hiawatha-webserver.org/features").

If you want to install Hiawatha on Ubuntu Server, you can refer to this [HOWTO]("http://secure-ubuntu-server.blogspot.hk/2012/06/howto-highest-secured-hiawatha-web.html").

Samiux

---

