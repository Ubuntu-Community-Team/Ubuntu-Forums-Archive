---
title: "BindException in JBoss 4.2.2"
date: 2008-01-07
forum: Programming Talk
---

### Post by HuBaghdadi on 2008-01-07
Hi.
I'm trying to run JBoss 4.2.2 under Ubuntu 7.10
Upon starting the server, I got java.net.BindException (8009 port is use).
Any ideas how to solve it?
Thanks.

---

### Post by HuBaghdadi on 2008-01-09
I figured it out.
I remembered that the port 8009 is taken by Tomcat usually, so I created a simple Java class and sent HTTP request to it.
I got HTTP response.
It seems that Tomcat installed by Synaptic is set to run automatically upoun Ubuntu boot.

---

