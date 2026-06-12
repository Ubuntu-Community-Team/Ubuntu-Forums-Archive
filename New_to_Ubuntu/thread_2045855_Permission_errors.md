---
title: "Permission errors"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by Bhuvany on 2012-08-22
Hi all,

I am running ubuntu on i.mx53 QSB and using apache webserver for web communication. So i installed websocket plugin for apache and wrote some c code to set system time, IP etc...("my project works like this -> from a web page i will send some data to apache server so i will receive the data in my websocket plugin code and i will set the system time according to data") here the problem is while setting system time it is giving permission error even if i do this process using cgi-bin scripts through me same error.
    But if i run the same c code with my own webserver in a terminal it is working fine.
    How can i give full permissions to apache server and for the libraries its going to use?? How can i make root user the ownership to my program??

Thanks in Advance
Bhuvan Y

---

### Post by spjackson on 2012-08-22
In order to set the system time, your effective user id needs to be root. You can do this as follows:
```

sudo chown root.root myprogram
sudo chmod u+s myprogram

```

---

