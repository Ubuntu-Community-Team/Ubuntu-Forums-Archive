---
title: "Proxychains how does it work?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-08-09
If proxy is defined as the server which does the work on behalf of the client. Therefore when i say i connect to proxy 10.1.1.223. I am connected to the server which is at this address, and this server will execute all that i want it to do. 

Is my concept correct.

Now what does proxychains do?

---

### Post by aloshbennett on 2008-08-10
Proxy is a server which acts as the entire Internet for you. If you want to talk to google.com, you dont contact google.com. Instead, you talk to the proxy. Proxy then talks to google.com and send you the results back.
Proxies can be used to monitor and filter your requests.

Proxy chains adds a lot of proxies between you and google.com. If you are trying to do something to google.com which you shouldnt be doing, proxy chain gives you more anonymity.

There's a good explanation here:
[http://www.proxyblind.org/proxy_chaining.shtml](http://www.proxyblind.org/proxy_chaining.shtml)

PS: 

[http://proxychains.sourceforge.net/](http://proxychains.sourceforge.net/) acts as a tunneler, and you can get around your univ. proxy. I am not sure if p2p would work still.

---

### Post by 7raTEYdCql on 2008-08-12
I downloaded the proxychains package and installed it. In the /etc/proxychainsans.conf file i didn't understand the meaning of chain_len = 2. What does the chain length mean.

Anybody???

---

