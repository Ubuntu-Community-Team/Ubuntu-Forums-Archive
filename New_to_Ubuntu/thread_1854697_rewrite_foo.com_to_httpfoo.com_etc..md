---
title: "rewrite foo.com to http://foo.com etc."
date: 2011-10-04
forum: New to Ubuntu
---

### Post by AskTell on 2011-10-04
when  I enter my web address as foo.com the site loads but it doesnt change foo.com to [www.foo.com]("http://www.foo.com") or [http://foo.com](http://foo.com) or [http://www.foo.com](http://www.foo.com)

how do I set this in ubuntu 10.04 server and/or desktop?

---

### Post by bodhi.zazen on 2011-10-04
[http://www.easymodrewrite.com/example-www](http://www.easymodrewrite.com/example-www)

---

### Post by AskTell on 2011-10-05
I had to enable htaccess through /etc/apache2/sites-available/default based on [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

Where would I place my rewrite rules in /etc/apache2/sites-available/default since help.ubuntu suggests not using it if you can access the main server configuration

Quote from [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)
> *"In general, you should never use .htaccess files unless you don't  have access to the main server configuration file. There is, for  example, a prevailing misconception that user authentication should  always be done in .htaccess files. This is simply not the case. You can  put user authentication configurations in the main server configuration,  and this is, in fact, the preferred way to do things."*Thank you for your help!

---

### Post by bodhi.zazen on 2011-10-05
> **AskTell said:**
> I had to enable htaccess through /etc/apache2/sites-available/default based on [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

Where would I place my rewrite rules in /etc/apache2/sites-available/default since help.ubuntu suggests not using it if you can access the main server configuration

Quote from [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)
Thank you for your help!

Follow the link on that wiki page ...

[http://httpd.apache.org/docs/2.0/howto/htaccess.html#when](http://httpd.apache.org/docs/2.0/howto/htaccess.html#when)

> However, in general, use of .htaccess files should be avoided when possible. Any configuration that you would consider putting in a .htaccess file, can just as effectively be made in a <Directory> section in your main server configuration file.

The link also has additional information ;)

---

### Post by AskTell on 2011-10-05
Ah, sorry about having you do what I should've done myself. I'll try not to overlook the obvious next time :D 

thanks again!

---

### Post by bodhi.zazen on 2011-10-05
> **AskTell said:**
> Ah, sorry about having you do what I should've done myself. I'll try not to overlook the obvious next time :D 

thanks again!

no problem, hope you got it sorted.

It can be confusing to get apache configured, but in the long run it is better to understand the configuration files (IMO).

Come back if you run into additional problems.

---

