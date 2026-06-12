---
title: "Update changing IP using urlopen with https and do login"
date: 2013-02-02
forum: Programming Talk
---

### Post by Covest on 2013-02-02
This is a newbie problem with python, advice is much appreciated. no-ip.com provides an easy way to update a computer's changing ip-address, simply open the url
```
http://user:password@dynupdate.no-ip.com/nic/update?hostname=my.host.name
```...both http and https work when entered in firefox. I tried to implement that in a script residing in "/etc/NetworkManager/dispatcher.d" to be used by Network Manager on a recent version of Ubuntu.

What works is the python script:

```
from urllib import urlopen;
urlopen("http://user:password@dynupdate.no-ip.com/nic/update?hostname=my.host.name")
```What I want to have is the same with "https", which does not work as easily. Could anyone, please,
(1) show me what the script should look like for https,
(2) give me some **keywords**, which I can use to learn about this.
(3) perhaps even explain why it does not work any more when the script is changed to using "urllib2":

```
from urllib2 import urlopen;
urlopen("http://user:password@dynupdate.no-ip.com/nic/update?hostname=my.host.name")
```Thank you!

---

### Post by greenpeace on 2013-02-02
Hey!

Have a look at this page, where someone faced the same problem.  The first example seems to be pretty complete for python 3...

[http://stackoverflow.com/questions/6999565/python-https-get-with-basic-authentication](http://stackoverflow.com/questions/6999565/python-https-get-with-basic-authentication)

if that doesn't work for you (maybe you're not using python 3), then the first answer here seems good:

[http://stackoverflow.com/questions/635113/python-urllib2-basic-http-authentication-and-tr-im](http://stackoverflow.com/questions/635113/python-urllib2-basic-http-authentication-and-tr-im)

This type of authentication is called **basic authentication** and the type of HTTP request that you're making here is a **HTTP GET** (you can tell this as the variables are included in the URL, ie. "hostname=my.host.name").

Hope that helps!

---

### Post by greenpeace on 2013-02-02
> **Covest said:**
> (3) perhaps even explain why it does not work any more when the script is changed to using "urllib2"

well, simply put, urllib != urllib2 :)

The handling of basic authentication Just Works in urllib, but isn't enabled by default in urllib2.urlopen(); so you need to add the header yourself.  Take a look here where this is described well: [http://www.voidspace.org.uk/python/articles/authentication.shtml](http://www.voidspace.org.uk/python/articles/authentication.shtml)

---

