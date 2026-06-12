---
title: "NO PUBLICKEY error ?"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by ericstrom on 2012-06-30
When I tried to install some packages I'm getting the following message:


Reading package lists...
W: GPG error: [http://cran.cnr.Berkeley.edu](http://cran.cnr.Berkeley.edu) lucid/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 51716619E084DAB9

What does this mean and what do I do about it ? I assume it means the packages didn't download ?

---

### Post by drs305 on 2012-06-30
Your system doesn't have the security key for that repository. You can add it for repositories you trust with the following command (using the last 8 alphanumerics from the error message code):
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9
```

---

