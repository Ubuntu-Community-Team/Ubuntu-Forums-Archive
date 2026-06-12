---
title: "Blocking a website loading in the web browser..."
date: 2009-08-03
forum: Programming Talk
---

### Post by veda87 on 2009-08-03
I just came to know that to block a website loading into the web browser, I need to make an entry into my host file...

when I moved into configuration directory, I found three files namely, hosts, host.allow, host.deny ....

So I made an entry in the host.deny file```
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

ALL: 127.0.0.1 www.google.com

``` 
I tried both ```
ALL: 127.0.0.1 www.google.com
``````
ALL: www.google.com
```
But none didn't work for me.... Can anyone tell me where am I going wrong....

---

### Post by Hobgoblin on 2009-08-03
You need to add an entry to /etc/hosts

---

### Post by veda87 on 2009-08-04
> **Hobgoblin said:**
> You need to add an entry to /etc/hosts

Thanks.... I have made an entry into the **/etc/hosts** file.... its working perfectly....

But I wanted to know what these files **/etc/hosts.allow** and **/etc/hosts.deny** are used for....

Can anyone tell the use of these files....

---

### Post by fahadsadah on 2009-08-04
These are hosts that can not connect to you, if you are running any servers.

---

