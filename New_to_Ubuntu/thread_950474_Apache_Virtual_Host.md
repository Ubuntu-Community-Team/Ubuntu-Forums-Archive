---
title: "Apache Virtual Host"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by jamesdigby on 2008-10-17
i am very new to ubuntu and apache.

how do i set up apache

to allow me to use serve 2 seperate sites from 1 ip address

i have looked at aload of sites and have ended up very confused and killed the one site i did have working

help!!!

thankyou

ps i have a dynamic address from no-ip... if that makes any difference

---

### Post by jamesdigby on 2008-10-17
ok really killed it apache wont start

---

### Post by greg@localhost on 2008-10-17
Have you seen this?

[https://help.ubuntu.com/7.04/server/C/httpd.html](https://help.ubuntu.com/7.04/server/C/httpd.html)

---

### Post by jamesdigby on 2008-10-17
yes thats what i thought i followed .... but i messed up somewhere 

i think i need an idiots guide that will take me through it step by step..

---

### Post by greg@localhost on 2008-10-17
If you can provide full clarification as to the exact nature of the problem then myself or anyone else here can help you. In my experience, you need to provide as much information as possible and outline the problem exactly if you are looking for constructive assistance.

Most people don't want to work any harder than they have to, in order to help you out. ;)

---

### Post by stephanvaningen on 2008-10-17
Add for other readers this info:
[LIST]
[*]Which files have you changed
[*]Per changed file the modifications (without dumping K-bytes of data, just the differences with the default)
[/LIST]
See where we get from there...

---

### Post by jamesdigby on 2008-10-17
ok

i am trying so set up 2 seperate web sites on 1 ip address using apache... how do i go about this?

the ip address is not fixed i am using dynamic forwarding from no-ip.com

thankyou in advance

---

### Post by stephanvaningen on 2008-10-17
Ok, without looking at your specific problem then, I'ld suggest to follow the info located on [the Apache site]("http://httpd.apache.org/docs/1.3/vhosts/examples.html"). It shows an example, copied here:

```
    Port 80
    ServerName server.domain.tld

    NameVirtualHost *:80

    <VirtualHost *:80>
    DocumentRoot /www/domain
    ServerName www.domain.tld
    ...
    </VirtualHost>
    
    <VirtualHost *:80>
    DocumentRoot /www/subdomain
    ServerName www.sub.domain.tld
    ...
    </VirtualHost> 

```

> **jamesdigby said:**
> ok

i am trying so set up 2 seperate web sites on 1 ip address using apache... how do i go about this?

the ip address is not fixed i am using dynamic forwarding from no-ip.com

thankyou in advance

---

### Post by linux6994 on 2008-10-17
Isn't t just a matter of putting multiple filder in /var/www and have the index point to each or have just have /mysiteone and /mysitetwo in there?

---

