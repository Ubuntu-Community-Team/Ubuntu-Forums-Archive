---
title: "apt fails with &quot;internal server error&quot;"
date: 2018-10-09
forum: New to Ubuntu
---

### Post by chris.arena on 2018-10-09
When trying to do an update I get:
```
root@crossdev:~/edi-raspbian# apt update
Hit:1 http://archive.ubuntu.com/ubuntu bionic InRelease
Err:2 http://ppa.launchpad.net/m-luescher/edi-snapshots/ubuntu bionic InRelease                               
  500  Internal Server Error [IP: 91.189.95.83 80]
Err:3 http://archive.ubuntu.com/ubuntu bionic-updates InRelease                                               
  500  Internal Server Error [IP: 91.189.88.152 80]
Err:4 http://archive.ubuntu.com/ubuntu bionic-backports InRelease                          
  500  Internal Server Error [IP: 91.189.88.152 80]
Err:5 http://archive.ubuntu.com/ubuntu bionic-security InRelease                           
  500  Internal Server Error [IP: 91.189.88.152 80]
Err:6 http://archive.canonical.com/ubuntu bionic InRelease                                 
  500  Internal Server Error [IP: 91.189.92.191 80]
Reading package lists... Done           
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease  500  Internal Server Error [IP: 91.189.88.152 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease  500  Internal Server Error [IP: 91.189.88.152 80]
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/bionic/InRelease  500  Internal Server Error [IP: 91.189.92.191 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease  500  Internal Server Error [IP: 91.189.88.152 80]
W: Failed to fetch http://ppa.launchpad.net/m-luescher/edi-snapshots/ubuntu/dists/bionic/InRelease  500  Internal Server Error [IP: 91.189.95.83 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

I don't know how to interpret this.
What's going on?
This is in a freshly installed Ubuntu 18.04.1 ... is this a networking error? I can ping those IP addresses it's reporting.

---

### Post by DuckHook on 2018-10-09
This means that the mirror you are trying to reach is either down or misconfigured so that *apt* cannot find its expected subfolders. Try changing your repository to Ubuntu's main server. You can also try a different mirror than 91.189.92.191

---

