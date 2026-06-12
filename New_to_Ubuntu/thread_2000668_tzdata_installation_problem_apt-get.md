---
title: "tzdata installation problem apt-get"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by Julius1988 on 2012-06-09
Hi,

I have problems in installing tzdata in ubuntu 10.04. I get the following error when I try to install the package.


```
Setting up tzdata (2012b-0ubuntu0.10.04) ...
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by daslinkard on 2012-06-18
What happens when you run the following commands:

```
sudo apt-get update
``` 
```
sudo apt-get upgrade
```

---

