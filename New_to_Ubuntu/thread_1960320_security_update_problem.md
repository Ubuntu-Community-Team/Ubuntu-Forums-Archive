---
title: "security update problem"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by Old Jimma on 2012-04-17
Hi Ubuntu Community:

I'm using Lucid 10.04.

My update manager has been trying to install security patches:
[COLOR="DarkGreen"][B]libpng12-0
libpng12-dev[/B][/COLOR]

The update manager description describes these files as follows:

> libpng is a library implementing an interface for reading and writing PNG (Portable Network Graphics) format files.
This package contains the runtime library files needed to run software using libpng.

When the update manager tries to install them I get the error message

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.42-1ubuntu2.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.42-1ubuntu2.4_amd64.deb)
  404  Not Found [IP: 91.189.92.166 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.42-1ubuntu2.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.42-1ubuntu2.4_amd64.deb)
  404  Not Found [IP: 91.189.92.166 80]

How do I get these installed?

THanks,
Phil de Duluthistan

---

### Post by plucky on 2012-04-17
It seems to be looking for the wrong file


[http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.42-1ubuntu2.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.42-1ubuntu2.4_amd64.deb)

When it should be looking for
 
[http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.42-1ubuntu2.5_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.42-1ubuntu2.5_amd64.deb)

Try from a terminal ```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
sudo apt-get upgrade
```

Good Luck

---

### Post by Old Jimma on 2012-04-17
Hi Plucky!

This solved the problem!

Thanks!

):P

Phil de Duluthistan

---

