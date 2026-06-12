---
title: "[SOLVED] Get the Public IP address in Python."
date: 2008-09-21
forum: Programming Talk
---

### Post by LinuX-M@n1@k on 2008-09-21
I'm writing a program and I need to get the Hostname, Local IP address and the Public IP address of the machine.

For the Hostname and the Local IP address I'm using:
```
host, aliaslist, lan_ip = socket.gethostbyname_ex(socket.gethostname())
print host
print aliaslist
print lan_ip[0]
```

How can I get the Public IP address? I googled for it and couldn't find anything.
PS: It must be cross-platform. (Linux/Windows)

---

### Post by ghostdog74 on 2008-09-21
you can make a connection to [internet site](http://whatismyipaddress.com/) if you have connection to internet. Grab the value using urllib,urllib2

---

### Post by LinuX-M@n1@k on 2008-09-21
Thanks, I'll try that.

---

### Post by LinuX-M@n1@k on 2008-09-21
I found a solution:
```
pub_ip = urllib2.urlopen("http://whatismyip.com/automation/n09230945.asp").read()
print pub_ip
```

---

### Post by prismctg on 2012-01-18
how to write this code in python 3 ?????

---

### Post by Tony Flury on 2012-01-18
> **prismctg said:**
> how to write this code in python 3 ?????

It depends if urllib has a python 3 port - it seems like it does - sort of :-) Python 2.7 definition of urllib2 - note the comment at the top of this page :
[http://docs.python.org/library/urllib2.html](http://docs.python.org/library/urllib2.html)

The Web page : [http://whatismyip.com/automation/n09230945.asp](http://whatismyip.com/automation/n09230945.asp) returns a very simple page which only has your IP adress on it - no other HTML tags etc. so getting the address is pretty simple - just do a read on the file once it is open.

I think the answer is 

```

import urllib.request as urllibReq

f = urllibReq.urlopen("http://whatismyip.com/automation/n09230945.asp")
pub_ip = f.read()
f.close()

```
That should work - not sure if you need the close.

This code has not been tested.

---

### Post by slavik on 2012-01-18
The prognosis is not good. This thread is dead.

---

