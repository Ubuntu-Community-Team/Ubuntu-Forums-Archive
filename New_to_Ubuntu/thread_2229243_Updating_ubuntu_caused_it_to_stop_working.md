---
title: "Updating ubuntu caused it to stop working"
date: 2014-06-12
forum: New to Ubuntu
---

### Post by faraz_k86 on 2014-06-12
Hi,

I updated my kubuntu system today after I was notified of important security updates. The update ran up until 86% and then I got this error:

```
Failed to apply changes:

[http://gb.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.5.2-1ubuntu2.1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.5.2-1ubuntu2.1_amd64.deb) 404 Not Found [IP: 194.169.254.10 80]
[http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1f-1ubuntu2.1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1f-1ubuntu2.1_amd64.deb) 404 Not Found [IP: 194.169.254.10 80] 
[http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1f-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1f-1ubuntu2.1_amd64.deb) 404 Not Found [IP: 91.189.92.200 80] 
[http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.17.5ubuntu5.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.17.5ubuntu5.2_amd64.deb) 404 Not Found [IP: 91.189.92.200 80] [URL="http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.9.1+dfsg1-3ubuntu4.1_amd64.deb"]
http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.9.1+dfsg1-3ubuntu4.1_amd64.deb[/URL] 404 Not Found [IP: 91.189.92.200 80] 
[http://gb.archive.ubuntu.com/ubuntu/pool/universe/k/ktp-contact-list/kde-telepathy-contact-list_0.8.1-0ubuntu0.1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/k/ktp-contact-list/kde-telepathy-contact-list_0.8.1-0ubuntu0.1_amd64.deb) 404 Not Found [IP: 194.169.254.10 80] [URL="http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_1.0.1f-1ubuntu2.1_amd64.deb"]
http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_1.0.1f-1ubuntu2.1_amd64.deb[/URL] 404 Not Found [IP: 91.189.92.200 80] [URL="http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/libdpkg-perl_1.17.5ubuntu5.2_all.deb"]
http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/libdpkg-perl_1.17.5ubuntu5.2_all.deb[/URL] 404 Not Found [IP: 194.169.254.10 80] [URL="http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/libdpkg-perl_1.17.5ubuntu5.2_all.deb"]
http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/libdpkg-perl_1.17.5ubuntu5.2_all.deb[/URL] 404 Not Found [IP: 91.189.92.200 80] 
[http://gb.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.9.1+dfsg1-3ubuntu4.1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.9.1+dfsg1-3ubuntu4.1_amd64.deb) 404 Not Found [IP: 194.169.254.10 80] [URL="http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.9.1+dfsg1-3ubuntu4.1_amd64.deb"]
http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.9.1+dfsg1-3ubuntu4.1_amd64.deb[/URL] 404 Not Found [IP: 91.189.92.200 80] [URL="http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.13.0.27.33_amd64.deb"]
http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.13.0.27.33_amd64.deb[/URL] 404 Not Found [IP: 194.169.254.10 80] [URL="http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.13.0.27.33_amd64.deb"]
http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.13.0.27.33_amd64.deb[/URL] 404 Not Found [IP: 91.189.92.200 80] [URL="http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.13.0.27.33_amd64.deb"]
http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.13.0.27.33_amd64.deb[/URL] 404 Not Found [IP: 194.169.254.10 80] [URL="http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.13.0.27.33_amd64.deb"]
http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.13.0.27.33_amd64.deb[/URL] 404 Not Found [IP: 91.189.92.200 80] [URL="http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.13.0.27.33_amd64.deb"]
http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.13.0.27.33_amd64.deb[/URL] 404 Not Found [IP: 194.169.254.10 80] [URL="http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.13.0.27.33_amd64.deb"]
http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.13.0.27.33_amd64.deb[/URL] 404 Not Found [IP: 91.189.92.200 80] 
```

It did this for other files even after I unchecked libfreetype6 from the update list. I then proceeded to restart my computer, but when I relogged the wifi was not working and the mouse had stopped working. (My laptop worked with extaernal mouse but now even that does not work).

Can anyone help with this? Thank you

---

### Post by faraz_k86 on 2014-06-12
Right, just an update for anyone else experiencing this. I managed to fix this by changing the software source from the update manager from UK, to main server

---

