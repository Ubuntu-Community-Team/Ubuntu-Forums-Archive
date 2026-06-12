---
title: "Update error on ubuntu 15.10 [many packages failed to fetch with 404]"
date: 2018-02-09
forum: New to Ubuntu
---

### Post by shiroichii on 2018-02-09
Hi guys.  

I am a pretty newbie here. After extensive search on net that i find out 15.10 is no longer supporting format so that i need to move onto a different version. the problem is sudo apt-get update is not working with following errors. Is there are anyway to resolve this? really appreciate your help.

[https://scontent.fcmb5-1.fna.fbcdn.net/v/t1.0-9/27867119_1852849531401097_34013261354351290_n.jpg?oh=8e204c543df827d3fa7762befaf48153&oe=5B138696](https://scontent.fcmb5-1.fna.fbcdn.net/v/t1.0-9/27867119_1852849531401097_34013261354351290_n.jpg?oh=8e204c543df827d3fa7762befaf48153&oe=5B138696)


```
W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/wily-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-updates/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-updates/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-updates/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-proposed/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-proposed/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-proposed/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-proposed/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-proposed/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-proposed/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-proposed/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-proposed/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-backports/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-backports/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-backports/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-backports/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by deadflowr on 2018-02-09
[s][I]Thread moved to** General Help**
[/I][/s]

15.10 has reached it's end of life.
You need to install a supported release.
Try 16.04

Two methods of getting 16.04

The easy way is to simply reinstall 16.04.
Just grab a new copy from here: [https://www.ubuntu.com/download/desktop]("https://www.ubuntu.com/download/desktop")

The hard way is to run a release upgrade following the EOLUpgrades guide here: [https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

---

### Post by wildmanne39 on 2018-02-09
*Thread moved to **New to Ubuntu, a more appropriate forum**.* As the development forum is only for Ubuntu developmental versions.

Please use thumbnails or url's when posting images because many people have slow or limited connections.

Your best option is to back up your important data and do a clean install, the reason you can not upgrade is 15.10 is no longer supported and the repositories have been removed.

---

