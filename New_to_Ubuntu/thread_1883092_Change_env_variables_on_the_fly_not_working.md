---
title: "Change env variables on the fly not working"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by getut on 2011-11-18
Help me...

I have worked around the problem but I am unable to change my environment variables on the fly. I am on 64bit Oneiric Kubuntu.

In a console I can type either of the following:

export http_proxy="http:proxyserver:8080"

or split out

http_proxy="http:proxyserver:8080"
export proxy_server

I have done it with and without the quotes and then check env and nothing has changed.

I put the change in my .bashrc and then ran source ~/.bashrc and it took the changes, but why I am unable to export on the fly or what am I doing wrong?

---

### Post by Toz on 2011-11-18
Do you mean: 
```
export http_proxy="http://proxyserver:8080"
```

What does:
```
env
```
...return after you issue that command?

---

