---
title: "google earth carsh after start"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by abdorefky on 2013-06-04
google earth crash just after start
```
  sudo google-earth
[sudo] password for abdo: 
[0604/232354:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0604/232355:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0604/232355:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.


Another crash happened while handling crash!



```

tips is false

---

### Post by Impavidus on 2013-06-04
I wouldn't start google earth with sudo. I don't think you need it and it's best practise to run every program with the least privileges possible. Also, it will store all its cache and user config data as root-owned files in your home directory, which will make it crash when you don't start it with sudo.

---

