---
title: "Cannot install apt-transport-https"
date: 2018-05-28
forum: New to Ubuntu
---

### Post by mariusz.w on 2018-05-28
Hi,

I'm following this [https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.7](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.7) to install Asp.Net Core on Ubuntu. When running apt-get install apt-transport-https I get:

```

Err:1 http://security.ubuntu.com/ubuntu xenial-security/main amd64 libcurl3-gnutls amd64 7.47.0-1ubuntu2.2
  404  Not Found [IP: 91.189.88.161 80]
Err:2 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 apt-transport-https amd64 1.2.20
  404  Not Found [IP: 91.189.88.161 80]
Err:1 http://security.ubuntu.com/ubuntu xenial-security/main amd64 libcurl3-gnutls amd64 7.47.0-1ubuntu2.2
  404  Not Found [IP: 91.189.88.161 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3-gnutls_7.47.0-1ubuntu2.2_amd64.deb  404  Not Found [IP: 91.189.88.161 80]


E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_1.2.20_amd64.deb  404  Not Found [IP: 91.189.88.161 80]

```

What do I do?

Installing on Ubuntu 16.04 which I believe is still supported.

---

### Post by mariusz.w on 2018-05-28
I had to do apt-get update first! This probably updated all links. It works now. Sorry for bothering.

---

