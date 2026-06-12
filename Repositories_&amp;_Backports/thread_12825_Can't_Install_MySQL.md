---
title: "Can't Install MySQL?"
date: 2005-01-27
forum: Repositories &amp; Backports
---

### Post by AlexV on 2005-01-27
When I try to install mysql-server I get a message saying that some of the packages couldn't be retrieved. Are these packages missing from the repository?

[I]Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient12_4.0.20-2ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient12_4.0.20-2ubuntu1.1_i386.deb)
  404 Not Found [IP: 82.211.81.155 80]

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-client_4.0.20-2ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-client_4.0.20-2ubuntu1.1_i386.deb)
  404 Not Found [IP: 82.211.81.155 80]

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-server_4.0.20-2ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-server_4.0.20-2ubuntu1.1_i386.deb)
  404 Not Found [IP: 82.211.81.155 80]
[/I]

Any insight would be helpful... Don't make me migrate back to RedHat, now  ;-)

---

### Post by az on 2005-01-27
That's classic.

sudo apt-get update
sudo apt-get -f install

The packages have been updated, and so the old version is gone.

---

### Post by AlexV on 2005-01-27
Ah  :-| ... Yes  :-# ...
Thanks, that seems to have helped  ;-)

---

