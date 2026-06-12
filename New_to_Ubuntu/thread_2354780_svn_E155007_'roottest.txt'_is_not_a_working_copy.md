---
title: "svn: E155007: '/root/test.txt' is not a working copy"
date: 2017-03-06
forum: New to Ubuntu
---

### Post by recharde on 2017-03-06
# cd myrepo
# touch file1.txt index.php
# svn add file1.txt index.php
# svn ci file1.txt index.php -m "initial commit"
after that i got this type error, when i write "svn upgrade " i got this same error.

---

### Post by opsusec on 2017-03-06
check dependencies 

apt-get update verbose afterwards and see if it has conflicts.

---

### Post by recharde on 2017-03-06
when i write "apt-get update" i got this type error
W: [http://opensource.wandisco.com/ubuntu/dists/xenial/Release.gpg:](http://opensource.wandisco.com/ubuntu/dists/xenial/Release.gpg:) Signature by key 61BE83DA54CBED682F8E9F0E922F uses weak digest algorithm (SHA1)

---

