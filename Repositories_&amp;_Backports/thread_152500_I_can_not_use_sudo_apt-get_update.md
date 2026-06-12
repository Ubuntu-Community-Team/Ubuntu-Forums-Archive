---
title: "I can not use sudo apt-get update"
date: 2006-03-30
forum: Repositories &amp; Backports
---

### Post by 5jarinko on 2006-03-30
I can not use sudo apt-get update

I have to use prosy server 

but if I put to file /etc/apt/apt.conf information about my proxy it is does not work

example: 


root@hasox:/etc/apt# cat /etc/apt/apt.conf
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "http://logi:my_password@ip_adress_of_proxy:8080";
Acquire::::Proxy "false";

---

### Post by public_void on 2006-03-30
Try
```
ACQUIRE {
http::proxy "http://[UserName]:[Password]@[Address]:[Port]/"
}
```

---

