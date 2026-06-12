---
title: "apt-proxy 503 service unavailable problem"
date: 2006-02-21
forum: Repositories &amp; Backports
---

### Post by pvdr on 2006-02-21
Hi there; I am a ubuntu/debian newbie...I tried using apt-proxy to keep my internet-less computer at home updated. (I did this in gentoo by simply copying the sources)

Withou apt-proxy; I used this simple /etc/apt/sources.list:
[SIZE="1"]# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse[/SIZE]

I read all the info I could find on apt-proxy including [https://wiki.ubuntu.com/AptProxyHowTo](https://wiki.ubuntu.com/AptProxyHowTo) and have made the changes I feel was nescesary :
/etc/apt/sources.list:
[SIZE="1"]# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://127.0.0.1:9999/ubuntu](http://127.0.0.1:9999/ubuntu) breezy main restricted
deb [http://127.0.0.1:9999/ubuntu](http://127.0.0.1:9999/ubuntu) breezy-updates main restricted
deb [http://127.0.0.1:9999/ubuntu-security](http://127.0.0.1:9999/ubuntu-security) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://127.0.0.1:9999/ubuntu](http://127.0.0.1:9999/ubuntu) breezy universe multiverse
deb [http://127.0.0.1:9999/ubuntu](http://127.0.0.1:9999/ubuntu) breezy-updates universe multiverse
deb [http://127.0.0.1:9999/ubuntu-security](http://127.0.0.1:9999/ubuntu-security) breezy-security universe multiverse[/SIZE]
/etc/apt-proxy/apt-proxy-v2.conf:
[SIZE="1"]...
debug = all:4 db:0

timeout = 30
passive_ftp = on

;;--------------------------------------------
;; Cache housekeeping

cleanup_freq = 1d
max_age = 120d
max_versions = 3

;;--------------------------------------------
;; Backend servers
;;
;; Place each server in its own [section]

[ubuntu]
; Ubuntu archive
backends = [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu)

[ubuntu-security]
; Ubuntu security updates
backends = [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[/SIZE]

but now I get the following outpout with apt-get update:
[SIZE="1"]Ign [http://127.0.0.1](http://127.0.0.1) breezy Release.gpg
Ign [http://127.0.0.1](http://127.0.0.1) breezy-updates Release.gpg
Ign [http://127.0.0.1](http://127.0.0.1) breezy-security Release.gpg
Ign [http://127.0.0.1](http://127.0.0.1) breezy Release
Ign [http://127.0.0.1](http://127.0.0.1) breezy-updates Release
Ign [http://127.0.0.1](http://127.0.0.1) breezy-security Release
Ign [http://127.0.0.1](http://127.0.0.1) breezy/main Packages
Ign [http://127.0.0.1](http://127.0.0.1) breezy/restricted Packages
Ign [http://127.0.0.1](http://127.0.0.1) breezy/universe Packages
Ign [http://127.0.0.1](http://127.0.0.1) breezy/multiverse Packages
Ign [http://127.0.0.1](http://127.0.0.1) breezy-updates/main Packages
Ign [http://127.0.0.1](http://127.0.0.1) breezy-updates/restricted Packages
Ign [http://127.0.0.1](http://127.0.0.1) breezy-updates/universe Packages
Ign [http://127.0.0.1](http://127.0.0.1) breezy-updates/multiverse Packages
Ign [http://127.0.0.1](http://127.0.0.1) breezy-security/main Packages
Ign [http://127.0.0.1](http://127.0.0.1) breezy-security/restricted Packages
Ign [http://127.0.0.1](http://127.0.0.1) breezy-security/universe Packages
Ign [http://127.0.0.1](http://127.0.0.1) breezy-security/multiverse Packages
Err [http://127.0.0.1](http://127.0.0.1) breezy/main Packages
  503 Service Unavailable
Ign [http://127.0.0.1](http://127.0.0.1) breezy/restricted Packages
  503 Service Unavailable
Ign [http://127.0.0.1](http://127.0.0.1) breezy/universe Packages
  503 Service Unavailable
....etc[/SIZE]

Please someone help me; I am going MAD ;-)

---

