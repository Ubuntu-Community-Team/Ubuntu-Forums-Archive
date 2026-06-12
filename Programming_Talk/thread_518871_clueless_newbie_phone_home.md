---
title: "clueless newbie phone home?"
date: 2007-08-06
forum: Programming Talk
---

### Post by davidpbrown on 2007-08-06
Can I get some pointers on how to implement the following?

I'd like to setup a startup script that checks the computer is on my network and if it's not then it phones home, reporting the network's mac and ip.

I've no serious reason to do this but I'm thinking it would be fun to try..

So far I have the 'plain English version but no sense of how to put it into ?python etc..

If (arp -a | grep "00:20:4F:5G:2E:C4") exists then do nothing 
else phone home by POSTing (arp -a) and (the real ip address)

0. Should I look to use python for this or another?

1. How do I get the real ip address if I'm behind a firewall? Is there a way to query the router rather than relying on internet whoami services?

2. How do I write the IF (arp grep) EXISTS test into python?

3. Is there a simple way to POST data from python?

---

### Post by Nekiruhs on 2007-08-06
0x3A28213A
0x6339392C
0x7363682E

Ha, get it? Pointers?

---

### Post by Wybiral on 2007-08-06
> **Nekiruhs said:**
> 0x3A28213A
0x6339392C
0x7363682E

Ha, get it? Pointers?

lol (only the C programmers here will get it)

---

### Post by pmasiar on 2007-08-06
> **davidpbrown said:**
> 
0. Should I look to use python for this or another?

Python is simpler and has all the tools (but I don;t use most of them so...)

> 2. How do I write the IF (arp grep) EXISTS test into python?

Save arp results in a file, then:

```

pattern = '...'
for line in open('file.name'):
     if pattern in line:
          # do something

```

> 3. Is there a simple way to POST data from python?[/QUOTE]

[urllib2](http://docs.python.org/lib/module-urllib2.html)

urlopen(  	url[, data])
    Open the URL url, which can be either a string or a Request object.

    data may be a string specifying additional data to send to the server, or None if no such data is needed. Currently HTTP requests are the only ones that use data; the HTTP request will be a POST instead of a GET when the data parameter is provided.

---

### Post by AlexThomson_NZ on 2007-08-06
> **Wybiral said:**
> lol (only the C programmers here will get it)

I'm a Java programmer- I don't get it! ;)

---

### Post by davidpbrown on 2007-08-09
Thanks for the help

The other step, getting IP address is
lynx -dump [http://www.whatismyip.com](http://www.whatismyip.com) | awk '/Your IP Is/ { print $4; }'

---

