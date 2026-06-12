---
title: "How to connect to own server using ip-address?"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by kramer65 on 2012-06-01
Hello,

Using [this guide]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3") I created a server in a virtualbox installation. From my guest-OS (also Ubuntu 12.04) I can now type in the browser the ip-address 192.168.1.99 and I get the Apache page saying "*It works!*". So far so good.

In the [ISPConfig panel]("http://www.ispconfig.org/") (which I installed on the server) I now added a new website (test.nl) which created a new folder: /var/www/test.nl/. In that folder, I added an index.html file which I now wanted to view by typing in the following address in my browser: [http://192.168.1.99/test.nl/](http://192.168.1.99/test.nl/) . Unfortunately, this doesn't work. I only get a '*403 Forbidden*' error.

Does anybody know how I can solve this? All tips are welcome!

---

### Post by dthacker on 2012-06-01
Check the ownership and permissions on the test.nl file.   Your webserver must be able to read the file and probably should own the file. 

Cheers!  Dave

---

### Post by PunkLV on 2012-06-01
I belive Apache is configured to look for index.html in the /var/www dir, not the /var/www/test.nl. I could be wrong though.

On the other hand:
```
sudo chown *username* /var/www/test.nl
sudo chmod u+rwx /var/www/test.nl
```

---

### Post by kramer65 on 2012-06-01
Unfortunately, 'test.nl' is not a file, but a folder. 

But nevermind. I just found a solution. I edited /etc/hosts on my Ubuntu guest-OS and added the line:
```
192.168.1.99    www.test.nl
```
and everything works like a charm now!

Thanks again!

---

