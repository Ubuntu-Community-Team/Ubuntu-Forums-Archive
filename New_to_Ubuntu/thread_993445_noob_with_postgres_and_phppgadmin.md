---
title: "noob with postgres and phppgadmin"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-11-25
I'm running lighty as a web server and using postgresql as a database. I've downloaded phppgadmin from apt-get but I cannot figure out how to set up phppgadmin for use with lighty (I've only found info on setting it up for apache in /usr/share/doc/phppgadmin). I've also found this but it has not been helpful, [http://redmine.stbuehler.de/wiki/2/Lighttpd](http://redmine.stbuehler.de/wiki/2/Lighttpd)

from the website:
```
$HTTP["host"] == "pg.example.com" {
        server.document-root = "/usr/share/phppgadmin" 
}

```

Does anyone know what I might be doing wrong or what I need to do to get phppgadmin configured with lighttpd?

---

### Post by Olivier2371 on 2008-11-25
Hello there,

I would like to help but I use xampp for my local server. Much easier to install and configure.

I am sure someone will be able to help you.

---

### Post by fontenot_1031 on 2008-11-25
> **Olivier2371 said:**
> Hello there,

I would like to help but I use xampp for my local server. Much easier to install and configure.

I am sure someone will be able to help you.

xampp is pretty good. Thanks for reading anyway man

---

### Post by Olivier2371 on 2008-11-26
It appears no one has the answer. Following the link it seems like he created a virtual host for accessing phppgadmin.

"/usr/share/phppgadmin" his.

"/usr/share/doc/phppgadmin" yours.

Why didn't you go with xampp?

---

