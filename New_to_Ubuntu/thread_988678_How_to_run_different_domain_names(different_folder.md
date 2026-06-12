---
title: "How to run different domain names(different folders) on one server"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Grace.zhang on 2008-11-20
I have set up Tomcat with apache2 on my Ubuntu server with two different folders containing two
different web applications using port 80, let's say A(jsp-examples) and B(servlets-examples).

I can access them thus :- [http://localhost/A/index.htm](http://localhost/A/index.htm) and
[http://localhost/B/index.htm](http://localhost/B/index.htm)

If my PC is connected to the internet with a static ip address of say
123.123.81.81 and I have rented two different domain names say mynameA.com
and mynameB.com, how do I set Tomcat up so that the domain names relate to
folders A and B.

For example so that 123.123.84.84/A = mynameA.com and 123.123.84.84/B =
mynameB.com.

The objective is to access the two different web applications using the
relevant domain names on Tomcat.

Is this possible and how can it be set up? Or can you please direct me to a
book which explains how this can be achieved.

Appreciated!

---

### Post by paultag on 2008-11-20
I see what you did there :)

Consider not doing it like this?
Putting that aside:

I think you should be able to point to that location from your DNS Server. If not, I know it can be done with subdomains, but that is, indeed messy for what you need.

Also, consider two different ports? again, something that I _think_ can be set up via your DNS Server.

Cheers, let us know how it goes,
Tag

---

### Post by halitech on 2008-11-20
not sure about Tomcat but for apache you need to set up virtual servers to point to each directory depending on which domain is requested

---

### Post by DaveyG on 2008-11-20
On Tomcat, you could set up something like so:

```

<Host name="domainA.com" appBase="webapps">
<Context path="" docBase="domainA"/>
<Alias>www.domainA.com</Alias>
</Host>

<Host name="domainB.com" appBase="webapps">
<Context path="" docBase="domainB"/>
<Alias>www.domainB.com</Alias>
</Host>

```

in server.xml, before </Engine> ;)

---

### Post by Grace.zhang on 2008-11-24
Thank you all! I tried your method, but it doesn't work.

I want [www.jsp-examples.com](www.jsp-examples.com) points to /usr/local/tomcat5.5/webapps/jsp-examples/

and used:

<Host name="www.jsp-examples.com" appBase="webapps">
<Context path="" docBase="jsp-examples"/>
<Alias>jsp-examples.com</Alias>
</Host>

Anything wrong?

I also found even I delete the default host in server.xml, tomcat still works. It's weird.

I guess because I installed mod_jk to connect tomcat5.5 and apache2.

> **DaveyG said:**
> On Tomcat, you could set up something like so:

```

<Host name="domainA.com" appBase="webapps">
<Context path="" docBase="domainA"/>
<Alias>www.domainA.com</Alias>
</Host>

<Host name="domainB.com" appBase="webapps">
<Context path="" docBase="domainB"/>
<Alias>www.domainB.com</Alias>
</Host>

```

in server.xml, before </Engine> ;)

---

### Post by Grace.zhang on 2008-11-25
As far as I know DNS server can point a domain name to a ip address, such as: point [www.mydomain.com](www.mydomain.com) to 128.238.1.2

Is it possible to point [www.mydomain1.com](www.mydomain1.com) to 128.238.1.2/mydomain1
             and point [www.mydomain2.com](www.mydomain2.com) to 128.238.1.2/mydomain2  , where mydomain1 and mydomain2 are folders of the same server

If possible, could you give me any link? Thank you


> **paultag said:**
> I see what you did there :)

Consider not doing it like this?
Putting that aside:

I think you should be able to point to that location from your DNS Server. If not, I know it can be done with subdomains, but that is, indeed messy for what you need.

Also, consider two different ports? again, something that I _think_ can be set up via your DNS Server.

Cheers, let us know how it goes,
Tag

---

### Post by DaveyG on 2008-11-27
> **Grace.zhang said:**
> Thank you all! I tried your method, but it doesn't work.

I want [www.jsp-examples.com](www.jsp-examples.com) points to /usr/local/tomcat5.5/webapps/jsp-examples/

and used:

<Host name="www.jsp-examples.com" appBase="webapps">
<Context path="" docBase="jsp-examples"/>
<Alias>jsp-examples.com</Alias>
</Host>

Anything wrong?

I also found even I delete the default host in server.xml, tomcat still works. It's weird.

I guess because I installed mod_jk to connect tomcat5.5 and apache2.

I'm not sure about configuring Virtual Hosts if you're using Apache with mod_jk..

Have you tried something like this:

```

    NameVirtualHost *:80

    <VirtualHost *:80>
    ServerName www.domainA.com
    ServerAlias domainA.com
    DocumentRoot /www/domainA
    </VirtualHost>

    <VirtualHost *:80>
    ServerName www.domainB.com
    ServerAlias domainB.com
    DocumentRoot /www/domainB
    </VirtualHost>

```

And have the Virtual Host config set up in Apache, instead on Tomcat?

---

