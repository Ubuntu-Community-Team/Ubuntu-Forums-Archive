---
title: "Changing var/www to something else"
date: 2014-02-13
forum: New to Ubuntu
---

### Post by kristian3 on 2014-02-13
I'm new to all this and I've installed Ubuntu Server on a Oracle VM Virtual box, and installed Apache etc.
How do I change the var/www folder that Apache uses, to something else? Can I simply rename it? I'm trying to change it to kris/core, in place of var/www.


Can I create a separate folder called kris/core and place my html files there? One of the reasons I did not do this it because I noticed that var/ has several other folders that will not be created if I simply create a new folder. So, I'm guessing the site wont work if we simply created kris/core


I'd like to store my html and php files in a folder kris/core so Apache can use it from there, rather than the default one. 

Can I simply create a folder kris/core and point Apache to it in Apache's configuration?


How do I do this? Thanks.

---

### Post by Lars Noodén on 2014-02-13
Look in your Apache virtual hosts file for the directive [DocumentRoot](http://httpd.apache.org/docs/2.4/mod/core.html#documentroot).  You can change it there.  If there are corresponding [Directory](http://httpd.apache.org/docs/2.4/mod/core.html#directory) directives giving special permissions, they should be updated, too.  For the changes to take effect you have to tell the server to reload the configuration or else restart the http daemon.

---

### Post by kristian3 on 2014-02-13
So I simply create a folder called kris/core, and tell Apache to look there by editing the document root? That'll be all?

---

### Post by Lars Noodén on 2014-02-13
That's just about it.  You do need to have the directories match the directives and vice versa.  Then reload:

```

sudo apache2ctl configtest
sudo apache2ctl graceful

```

Make a backup copy of the last known good config file before editing, just to be safe.

---

### Post by kristian3 on 2014-02-13
Thanks. I'll try it out.

---

