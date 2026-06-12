---
title: "how do I make Apache serve webpages only to the LAN"
date: 2015-02-13
forum: Programming Talk
---

### Post by stupidquestion on 2015-02-13
I am testing webpages and do not want the site to be visible to the outside world. How do I make sure only users on the LAN can see files under the web folder (/var/www/html)?

---

### Post by newbie-user on 2015-02-13
You can set up iptables to allow port 80 on the local network only.

Alternatively, you can tell Apache to listen on one interface only: [http://httpd.apache.org/docs/2.2/bind.html](http://httpd.apache.org/docs/2.2/bind.html)

---

### Post by YMJzskD on 2015-02-13
I am assuming you have a router between your LAN and the internet, so unless you have port 80 forwarded in your router your web pages should not be visible to the internet. No need for iptables rules.

---

### Post by Holger_Gehrke on 2015-02-16
Or you could use 'allow from' / 'deny from' inside the '<directory>' stanza in the configuration for your site in '/etc/apach2/sites/enabled/'. Like this:
```

<Directory "/var/www/MyLocalSite/">
  Order deny, allow
  Deny from all
  Allow from 192.168.1.1/255.255.255.0
</Directory>

```

---

