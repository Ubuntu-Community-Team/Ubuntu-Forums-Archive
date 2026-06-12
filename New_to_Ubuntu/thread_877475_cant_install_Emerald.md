---
title: "cant install Emerald"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-08-01
i use the synaptic package manager to install emerald, but i get this error message:

W: Failed to fetch [http://mirrors.acm.jhu.edu/ubuntu/pool/universe/e/emerald/libemeraldengine0_0.7.2-0ubuntu2_amd64.deb](http://mirrors.acm.jhu.edu/ubuntu/pool/universe/e/emerald/libemeraldengine0_0.7.2-0ubuntu2_amd64.deb)
  Could not connect to mirrors.acm.jhu.edu:80 (128.220.220.195), connection timed out


W: Failed to fetch [http://mirrors.acm.jhu.edu/ubuntu/pool/universe/e/emerald/emerald_0.7.2-0ubuntu2_amd64.deb](http://mirrors.acm.jhu.edu/ubuntu/pool/universe/e/emerald/emerald_0.7.2-0ubuntu2_amd64.deb)
  Unable to connect to mirrors.acm.jhu.edu http:


I guess this means my repos are bad? help plz.

---

### Post by deathvalleyjoker on 2008-08-01
i did change my download source back to the main server. 

ill let you know how that goes.

---

### Post by mevets on 2008-08-01
run a
```
sudo apt-get update
```
Sometimes apt fails to get a list from some servers. It also could have been that server was down when you tried to download the package.

---

