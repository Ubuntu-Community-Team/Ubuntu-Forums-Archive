---
title: "Sub Domains"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by Desann243 on 2012-02-02
I know this is a pretty basic question but surprisingly i cant find much info about it.  How do I host sub domains in my apache 2 server?

---

### Post by Repus on 2012-02-03
> **Desann243 said:**
> I know this is a pretty basic question but surprisingly i cant find much info about it.  How do I host sub domains in my apache 2 server?

It has been a long while since Ive done this, so this isn't an answer as much as helpful pointing in the right direction.

I think what your looking for is virtual host configs on apache (unless you actually looking for dns subdomain entrys.) try looking here [http://httpd.apache.org/docs/1.3/vhosts/examples.html](http://httpd.apache.org/docs/1.3/vhosts/examples.html)

---

### Post by Desann243 on 2012-02-05
Thanks alot

---

### Post by Lars Noodén on 2012-02-05
> **Repus said:**
> It has been a long while since Ive done this, so this isn't an answer as much as helpful pointing in the right direction.

I think what your looking for is virtual host configs on apache (unless you actually looking for dns subdomain entrys.) try looking here [s][http://httpd.apache.org/docs/1.3/vhosts/examples.html](http://httpd.apache.org/docs/1.3/vhosts/examples.html)[/s]

Apache 1.3 is no longer used and there have been some changes, especially with virtual hosts, so it is better to use the current documentation.  Ubuntu uses Apache 2.2

[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

---

