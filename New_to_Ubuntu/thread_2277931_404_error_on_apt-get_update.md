---
title: "404 error on apt-get update"
date: 2015-05-12
forum: New to Ubuntu
---

### Post by dilantha on 2015-05-12
Hi,

Im using ubuntu 12.10. I tried to install maven in my laptop. and it gives 404 error for most of the required libraries. 

```
Err http://lk.archive.ubuntu.com/ubuntu/ quantal/main libgcj-common all 1:4.6.3-5ubuntu2
  404  Not Found [IP: 91.189.91.24 80]
Err http://lk.archive.ubuntu.com/ubuntu/ quantal/main gcj-4.7-base amd64 4.7.2-1ubuntu1
  404  Not Found [IP: 91.189.91.24 80]
Err http://lk.archive.ubuntu.com/ubuntu/ quantal/main libgcj13 amd64 4.7.2-1ubuntu1
  404  Not Found [IP: 91.189.91.24 80]
Err http://lk.archive.ubuntu.com/ubuntu/ quantal/main libgcj-bc amd64 4.7.2-1ubuntu2
  404  Not Found [IP: 91.189.91.24 80]
Err http://lk.archive.ubuntu.com/ubuntu/ quantal/main libxerces2-java all 2.11.0-6
  404  Not Found [IP: 91.189.91.24 80]
Err http://lk.archive.ubuntu.com/ubuntu/ quantal/main ant all 1.8.2-4build2
  404  Not Found [IP: 91.189.91.24 80]
Err http://lk.archive.ubuntu.com/ubuntu/ quantal/main ant-optional all 1.8.2-4build2
  404  Not Found [IP: 91.189.91.24 80]
Err http://lk.archive.ubuntu.com/ubuntu/ quantal/main bsh all 2.0b4-12ubuntu1
  404  Not Found [IP: 91.189.91.24 80]
Err http://lk.archive.ubuntu.com/ubuntu/ quantal/main bsh-gcj amd64 2.0b4-12ubuntu1
  404  Not Found [IP: 91.189.91.24 80]
Err http://lk.archive.ubuntu.com/ubuntu/ quantal/main libxalan2-java all 2.7.1-7ubuntu1
  404  Not Found [IP: 91.189.91.24 80]
Err http://lk.archive.ubuntu.com/ubuntu/ quantal/main libavalon-framework-java all 4.2.0-8build1
  404  Not Found [IP: 91.189.91.24 80]
Err http://lk.archive.ubuntu.com/ubuntu/ quantal/main libcommons-io-java all 1.4-4build1
  404  Not Found [IP: 91.189.91.24 80]
Err http://lk.archive.ubuntu.com/ubuntu/ quantal/main libcommons-logging-java all 1.1.1-9ubuntu1
  404  Not Found [IP: 91.189.91.24 80]

```
Then i tried to run apt-get update and getting the same type of error. 

```
gn http://lk.archive.ubuntu.com quantal-updates/restricted amd64 Packages/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-updates/universe amd64 Packages/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-updates/multiverse amd64 Packages/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-updates/main i386 Packages/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-updates/restricted i386 Packages/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-updates/universe i386 Packages/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-updates/multiverse i386 Packages/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-backports/main Sources/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-backports/restricted Sources/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-backports/universe Sources/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-backports/multiverse Sources/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-backports/main amd64 Packages/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-backports/restricted amd64 Packages/DiffIndex
Ign https://private-ppa.launchpad.net quantal/main Translation-en_US
Ign http://lk.archive.ubuntu.com quantal-backports/universe amd64 Packages/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-backports/multiverse amd64 Packages/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-backports/main i386 Packages/DiffIndex
Ign https://private-ppa.launchpad.net quantal/main Translation-en
Ign http://lk.archive.ubuntu.com quantal-backports/restricted i386 Packages/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-backports/universe i386 Packages/DiffIndex
Ign http://lk.archive.ubuntu.com quantal-backports/multiverse i386 Packages/DiffIndex
Ign http://security.ubuntu.com quantal-security/main Translation-en_US
Ign http://security.ubuntu.com quantal-security/main Translation-en
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://security.ubuntu.com quantal-security/restricted Translation-en
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US
Ign http://security.ubuntu.com quantal-security/universe Translation-en
Err http://security.ubuntu.com quantal-security/main Sources
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com quantal-security/restricted Sources
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com quantal-security/universe Sources
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com quantal-security/multiverse Sources
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com quantal-security/main amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com quantal-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com quantal-security/universe amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com quantal-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com quantal-security/main i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com quantal-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com quantal-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com quantal-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Ign http://lk.archive.ubuntu.com quantal/main Translation-en_US
Ign http://lk.archive.ubuntu.com quantal/main Translation-en
Ign http://lk.archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://lk.archive.ubuntu.com quantal/multiverse Translation-en
Ign http://lk.archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://lk.archive.ubuntu.com quantal/restricted Translation-en
Ign http://lk.archive.ubuntu.com quantal/universe Translation-en_US
Ign http://lk.archive.ubuntu.com quantal/universe Translation-en
Ign http://lk.archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://lk.archive.ubuntu.com quantal-updates/main Translation-en
Ign http://lk.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://lk.archive.ubuntu.com quantal-updates/multiverse Translation-en
Ign http://lk.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://lk.archive.ubuntu.com quantal-updates/restricted Translation-en
Ign http://lk.archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://lk.archive.ubuntu.com quantal-updates/universe Translation-en
Ign http://lk.archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://lk.archive.ubuntu.com quantal-backports/main Translation-en
Ign http://lk.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://lk.archive.ubuntu.com quantal-backports/multiverse Translation-en
Ign http://lk.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://lk.archive.ubuntu.com quantal-backports/restricted Translation-en
Ign http://lk.archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://lk.archive.ubuntu.com quantal-backports/universe Translation-en
Err http://lk.archive.ubuntu.com quantal/main Sources
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal/restricted Sources
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal/universe Sources
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal/multiverse Sources
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal/main amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal/universe amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal/multiverse amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal/main i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal/restricted i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal/universe i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal-updates/main Sources
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal-updates/restricted Sources
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal-updates/universe Sources
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal-updates/multiverse Sources
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal-updates/main amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://lk.archive.ubuntu.com quantal-updates/main i386 Packages
  404  Not Found [IP: 91.189.92.200 80] 
Err http://lk.archive.ubuntu.com quantal-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.92.200 80]

```


I saw this was answered [here]("http://ubuntuforums.org/showthread.php?t=1856375"). But the answer is directing to another url and it doesnt seems to be working anymore :( . Really appreciate any help on this

---

### Post by QIII on 2015-05-12
Hello!

12.10 is well past End of Life and is no longer supported.  The repos have been moved, which is why you are getting the 404s.

I would strongly recommend installing a supported LTS version:  12.04LTS, 14.04LTS

---

