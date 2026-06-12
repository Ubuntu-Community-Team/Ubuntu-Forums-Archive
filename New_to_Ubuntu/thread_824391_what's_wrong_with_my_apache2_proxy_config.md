---
title: "what's wrong with my apache2 proxy config?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by mixersoft on 2008-06-10
I want to set up a proxy server to pass urls from only 1 domain. Here is what I have in my virtual hosts file:

<VirtualHost *>
ProxyRequests on

<Proxy "http://thisissafe.com/*">
order deny,allow
allow from all
</Proxy>

<Proxy "*">
deny from all
order deny,allow
</Proxy>
</VirtualHost>


The problem is that <Proxy "*"> always seems to take precedence the server denies all. If I remove <Proxy "*"> and just have the <Proxy "http://thisissafe.com/*"> directive, then it passes everything. Is there a default that I'm missing?

What am I doing wrong?

---

### Post by meltindar on 2008-06-10
I'm not sure whats wrong with your setup but you can try something like:
```

<Proxy *>
Order Deny,Allow
Deny from all
Allow from thisissafe.com
</Proxy> 

```

---

### Post by mixersoft on 2008-06-10
I think you have it backwards. I want to let a browser access thisissafe.com through the proxy server, not from thisissafe.com.

The whole story is that one of my servers on a dynamic IP address is blocked from accessing the dynamic dns update URL. So when the IP addr changes, I have to ask someone to email the new IP addrs and manually update. If I can set up a proxy server, then then blocked server can update the IP addr automatically.

---

