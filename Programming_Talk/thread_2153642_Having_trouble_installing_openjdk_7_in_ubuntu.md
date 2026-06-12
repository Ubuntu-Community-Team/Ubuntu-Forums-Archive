---
title: "Having trouble installing openjdk 7 in ubuntu"
date: 2013-06-11
forum: Programming Talk
---

### Post by chaosgodkarl on 2013-06-11
So I type this:

sudo apt-get install openjdk-7-jdk

And it tries to install, but then I get this:

Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libxcb1-dev amd64 1.8.1-1ubuntu0.1
 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1-dev_1.8.1-1ubuntu0.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1-dev_1.8.1-1ubuntu0.1_amd64.deb)  404  Not Found [IP: 91.189.91.15 80]

Can anyone help?

---

### Post by gifford on 2013-06-11
Try switching your repository over to download from main server instead of server for US.

---

### Post by chaosgodkarl on 2013-06-14
How do I do that?

---

### Post by slickymaster on 2013-06-14
> **chaosgodkarl said:**
> How do I do that?

Here's how: [Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

