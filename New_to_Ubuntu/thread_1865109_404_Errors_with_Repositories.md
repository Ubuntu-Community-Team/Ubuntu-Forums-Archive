---
title: "404 Errors with Repositories"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by mikodo on 2011-10-19
I received the message below, after recently re-installing Ubuntu 10.04. I ran it twice, with the same results. Should I try to change to another URL for my downloads? If so, can anybody direct me to a good guide on how to do this?

```
sudo aptitude update && sudo aptitude safe-upgrade
```Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  xserver-common xserver-xorg-core 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,494kB of archives. After unpacking 4,096B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main xserver-common 2:1.7.6-2ubuntu7.8
  404  Not Found [IP: 91.189.92.183 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main xserver-common 2:1.7.6-2ubuntu7.8
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main xserver-xorg-core 2:1.7.6-2ubuntu7.8
  404  Not Found [IP: 91.189.92.166 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.7.6-2ubuntu7.8_all.deb:](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.7.6-2ubuntu7.8_all.deb:) 404  Not Found [IP: 91.189.92.166 80]
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

mikodo@mikodo-desktop:~$

---

### Post by mikodo on 2011-10-19
I guess it was just busy. I downloaded a few more apps; tried the update and upgrade again and got through to the repositories and got the download for xserver-common xserver-xorg-cor.

Thanks!

---

