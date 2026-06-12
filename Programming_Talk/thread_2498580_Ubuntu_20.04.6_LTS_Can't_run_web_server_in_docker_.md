---
title: "Ubuntu 20.04.6 LTS: Can't run web server in docker container (phpdockerio/php:8.1-fpm"
date: 2024-06-20
forum: Programming Talk
---

### Post by maketopsite on 2024-06-20
```
> [php-fpm 9/9] RUN apt-get update && apt-get upgrade -y &&     apt-get install -y nodejs  &&     npm install -g npm:        
3.102 Hit:1 http://ppa.launchpad.net/ondrej/php/ubuntu jammy InRelease
3.102 Hit:2 http://archive.ubuntu.com/ubuntu jammy InRelease
3.179 Hit:3 http://archive.ubuntu.com/ubuntu jammy-backports InRelease
3.200 Get:4 http://security.ubuntu.com/ubuntu jammy-security InRelease [129 kB]
3.504 Get:5 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [128 kB]
3.994 Reading package lists...
4.739 W: http://ppa.launchpad.net/ondrej/php/ubuntu/dists/jammy/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
4.739 E: Release file for http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease is not valid yet (invalid for another 1h 24min 35s). Updates for this repository will not be applied.
4.739 E: Release file for http://archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease is not valid yet (invalid for another 1h 25min 47s). Updates for this repository will not be applied.
------
failed to solve: process "/bin/sh -c apt-get update && apt-get upgrade -y &&     apt-get install -y nodejs  &&     npm install -g npm" did not complete successfully: exit code: 100
```


There was no problem until today. Could it please be caused by wrong computer time ?

---

### Post by currentshaft on 2024-06-20
That's likely the cause. If you run "date" does it given an accurate time? Is ntpd running on the host?

---

### Post by maketopsite on 2024-07-20
> **currentshaft said:**
> That's likely the cause. If you run "date" does it given an accurate time? Is ntpd running on the host?

solved - ntpd was blocked by firewall

---

